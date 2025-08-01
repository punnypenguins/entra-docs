---
title: Identity synchronization and duplicate attribute resiliency
description: New behavior of how to handle objects with UPN or ProxyAddress conflicts during directory sync using Microsoft Entra Connect.
author: omondiatieno
manager: mwongerapk
ms.assetid: 537a92b7-7a84-4c89-88b0-9bce0eacd931
ms.service: entra-id
ms.tgt_pltfrm: na
ms.custom: no-azure-ad-ps-ref, sfi-image-nochange
ms.topic: how-to
ms.date: 04/09/2025
ms.subservice: hybrid-connect
ms.author: jomondi
---
# Identity synchronization and duplicate attribute resiliency
Duplicate Attribute Resiliency is a feature in Microsoft Entra ID that eliminates friction caused by **UserPrincipalName** and SMTP **ProxyAddress** conflicts when running one of Microsoft’s synchronization tools.

These two attributes are required to be unique across all **User**, **Group**, or **Contact** objects in a given Microsoft Entra tenant.

> [!NOTE]
> Only Users can have UPNs.
> 
> 

The new behavior that this feature enables is in the cloud portion of the sync pipeline, therefore it's client agnostic and relevant for any Microsoft synchronization product including Microsoft Entra Connect, DirSync, and MIM + Connector. The generic term “sync client” is used in this document to represent any one of these products.

## Current behavior
If there is an attempt to provision a new object with a UPN or ProxyAddress value that violates this uniqueness constraint, Microsoft Entra ID blocks that object from being created. Similarly, if an object is updated with a non-unique UPN or ProxyAddress, the update fails. The sync client retries the provisioning attempt or update upon each export cycle, and it continues to fail until the conflict is resolved. An error report email is generated upon each attempt and an error is logged by the sync client.

## Behavior with Duplicate Attribute Resiliency
Instead of completely failing to provision or update an object with a duplicate attribute, Microsoft Entra ID “quarantines” the duplicate attribute which would violate the uniqueness constraint. If this attribute is required for provisioning, like UserPrincipalName, the service assigns a placeholder value. The format of these temporary values is  
_**\<OriginalPrefix>+\<4DigitNumber>\@\<InitialTenantDomain>.onmicrosoft.com**_.

The attribute resiliency process handles only UPN and SMTP **ProxyAddress** values.

If the attribute isn't required, like a  **ProxyAddress**, Microsoft Entra ID simply quarantines the conflict attribute and proceeds with the object creation or update.

Upon quarantining the attribute, information about the conflict is sent in the same error report email used in the old behavior. However, this info only appears in the error report one time, when the quarantine happens, it doesn't continue to be logged in future emails. Also, since the export for this object is successful, the sync client doesn't log an error and doesn't retry the create / update operation upon subsequent sync cycles.

To support this behavior a new attribute is added to the User, Group, and Contact object classes:  
**DirSyncProvisioningErrors**

This is a multi-valued attribute that is used to store the conflicting attributes that would violate the uniqueness constraint should they be added normally. A background timer task is enabled in Microsoft Entra ID that runs every hour to look for duplicate attribute conflicts that have been resolved, and automatically removes the attributes in question from quarantine.

### Enabling Duplicate Attribute Resiliency
Duplicate Attribute Resiliency is the new default behavior across all Microsoft Entra tenants. It's on by default for all tenants that enabled synchronization for the first time on August 22nd, 2016 or later. Tenants that enabled sync before this date have the feature enabled in batches. This rollout began in September 2016, and an email notification is sent to each tenant's technical notification contact with the specific date when the feature is enabled.

> [!NOTE]
> Once Duplicate Attribute Resiliency is turned on it cannot be disabled.

To check if the feature is enabled for your tenant, you can do so by downloading the latest version of the Azure Active Directory PowerShell module and running:

`Get-EntraDirSyncFeature -Feature DuplicateUPNResiliency`

`Get-EntraDirSyncFeature -Feature DuplicateProxyAddressResiliency`

> [!NOTE]
> You can't use the `Set-EntraDirSyncFeature` cmdlet to proactively enable the Duplicate Attribute Resiliency feature before it's turned on for your tenant. To be able to test the feature, you'll need to create a new Microsoft Entra tenant.

## Identifying Objects with DirSyncProvisioningErrors
There are currently two methods to identify objects that have these errors due to duplicate property conflicts, Microsoft Entra PowerShell and the [Microsoft 365 admin center](https://admin.microsoft.com). There are plans to extend to additional portal based reporting in the future.

### Microsoft Entra PowerShell
For the PowerShell cmdlets in this topic, the following is true:

* All of the following cmdlets are case sensitive.

First, get started by running **Connect-Entra** and entering credentials for a tenant administrator.

Then, use the following cmdlets and operators to view errors in different ways:

1. [See All](#see-all)
2. [By Property Type](#by-property-type)
3. [By Conflicting Value](#by-conflicting-value)
4. [Using a String Search](#using-a-string-search)
5. Sorted
6. [In a Limited Quantity](#in-a-limited-quantity)

#### See all
Once connected, to see a general list of attribute provisioning errors in the tenant run:

`Get-MsolDirSyncProvisioningError`

#### By property type
To see errors by property type, specify **UserPrincipalName** or **ProxyAddresses**:

`Get-EntraDirectoryObjectOnPremisesProvisioningError | Where-Object PropertyCausingError -eq 'UserPrincipalName'`

Or

`Get-EntraDirectoryObjectOnPremisesProvisioningError | Where-Object PropertyCausingError -eq 'ProxyAddresses'`

#### By conflicting value
To see errors relating to a specific property add the value:

`Get-EntraDirectoryObjectOnPremisesProvisioningError | Where-Object PropertyCausingError -eq 'UserPrincipalName' | Where-Object Value -eq 'User@domain.com'`

#### Using a string search
To do a broad string search:

`Get-EntraDirectoryObjectOnPremisesProvisioningError | Select-Object 'User@domain.com'`

#### In a limited quantity
Use the following command to limit the query to a specific number of values.

`Get-EntraDirectoryObjectOnPremisesProvisioningError | Select-Object -First 10`

## Microsoft 365 admin center
You can view directory synchronization errors in the Microsoft 365 admin center. The report in the Microsoft 365 admin center only displays **User** objects that have these errors. It doesn't show info about conflicts between **Groups** and **Contacts**.

![Screenshot that shows directory synchronization errors in the Microsoft 365 admin center.](./media/how-to-connect-syncservice-duplicate-attribute-resiliency/1234.png "Active Users")

For instructions on how to view directory synchronization errors in the Microsoft 365 admin center, see [Identify directory synchronization errors in Microsoft 365](https://support.office.com/article/Identify-directory-synchronization-errors-in-Office-365-b4fc07a5-97ea-4ca6-9692-108acab74067).

### Identity synchronization error report
When an object with a duplicate attribute conflict is handled with this new behavior, a notification is included in the standard Identity Synchronization Error Report email that is sent to the Technical Notification contact for the tenant. However, there is an important change in this behavior. In the past, information about a duplicate attribute conflict would be included in every subsequent error report until the conflict was resolved. With this new behavior, the error notification for a given conflict does only appear once- at the time the conflicting attribute is quarantined.

Here is an example of what the email notification looks like for a ProxyAddress conflict:  
    ![Screenshot that shows an example of an email notification for a ProxyAddress conflict.](./media/how-to-connect-syncservice-duplicate-attribute-resiliency/6.png "Active Users")  

## Resolving conflicts
Troubleshooting strategy and resolution tactics for these errors shouldn't differ from the way duplicate attribute errors were handled in the past. The only difference is that the timer task sweeps through the tenant on the service-side to automatically add the attribute in question to the proper object once the conflict is resolved.

The following article outlines various troubleshooting and resolution strategies: [Duplicate or invalid attributes prevent directory synchronization in Office 365](/microsoft-365/troubleshoot/active-directory/duplicate-attributes-prevent-dirsync).

## Known issues
None of these known issues causes data loss or service degradation. Several of them are aesthetic, others cause standard “*pre-resiliency*” duplicate attribute errors to be thrown instead of quarantining the conflict attribute, and another causes certain errors to require extra manual fix-up.

**Core behavior:**

1. Objects with specific attribute configurations continue to receive export errors as opposed to the duplicate attribute(s) being quarantined.  
   For example:
   
    a. New user is created in AD with a UPN of **Joe\@contoso.com** and ProxyAddress **smtp:Joe\@contoso.com**
   
    b. The properties of this object conflict with an existing Group, where ProxyAddress is **SMTP:Joe\@contoso.com**.
   
    c. Upon export, a **ProxyAddress conflict** error is thrown instead of having the conflict attributes quarantined. The operation is retried upon each subsequent sync cycle, as it would have been before the resiliency feature was enabled.
2. If two Groups are created on-premises with the same SMTP address, one fails to provision on the first attempt with a standard duplicate **ProxyAddress** error. However, the duplicate value is properly quarantined upon the next sync cycle.

**Office Portal Report**:

1. The detailed error message for two objects in a UPN conflict set is the same. This indicates that they have both had their UPN changed / quarantined, when in fact only a one of them had any data changed.
2. The detailed error message for a UPN conflict shows the wrong displayName for a user whose UPN changed/quarantined. For example:
   
    a. **User A** syncs up first with **UPN = User\@contoso.com**.
   
    b. **User B** is attempted to be synced up next with **UPN = User\@contoso.com**.
   
    c. **User B’s** UPN is changed to **User1234\@contoso.onmicrosoft.com** and **User\@contoso.com** is added to **DirSyncProvisioningErrors**.
   
    d. The error message for **User B** should indicate that **User A** already has **User\@contoso.com** as a UPN, but it shows **User B’s** own displayName.

**Identity synchronization error report**:

The link for *steps on how to resolve this issue* is incorrect:  
    ![Active Users](./media/how-to-connect-syncservice-duplicate-attribute-resiliency/6.png "Active Users")  

It should point to [https://aka.ms/duplicateattributeresiliency]().

## See also
* [Microsoft Entra Connect Sync](how-to-connect-sync-whatis.md)
* [Integrating your on-premises identities with Microsoft Entra ID](../whatis-hybrid-identity.md)
* [Identify directory synchronization errors in Microsoft 365](https://support.office.com/article/Identify-directory-synchronization-errors-in-Office-365-b4fc07a5-97ea-4ca6-9692-108acab74067)
