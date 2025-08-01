---
title: 'Tutorial - Provision groups to Active Directory Domain Services (AD DS) by using Microsoft Entra Cloud Sync'
description: This tutorial shows how to setup and configure Microsoft Entra Cloud Sync to provision groups to Active Directory Domain Services (AD DS).
author: omondiatieno
manager: mwongerapk
ms.service: entra-id
ms.topic: how-to
ms.date: 08/01/2025
ms.subservice: hybrid-cloud-sync
ms.author: jomondi
ms.custom: no-azure-ad-ps-ref, sfi-image-nochange
---

# Tutorial - Provision groups to Active Directory Domain Services by using Microsoft Entra Cloud Sync

This tutorial walks you through how to configure Cloud Sync to sync groups to on-premises Active Directory Domain Services (AD DS). 

> [!IMPORTANT]
> We recommend using **Selected security groups** as the default scoping filter when you configure group provisioning to AD DS. This default scoping filter helps prevent any performance issues when you provision groups.  

[!INCLUDE [pre-requisites](../includes/gpad-prereqs.md)]

## Assumptions
This tutorial assumes:
- You have an AD DS on-premises environment
- You have cloud sync setup to synchronize users to Microsoft Entra ID.
- You have two users that are synchronized: Britta Simon and Lola Jacobson. These users exist on-premises and in Microsoft Entra ID.
- An organizational unit (OU) is created in AD DS for each of the following departments:

  Display name | Distinguished name
  -------------|-------------------
  Groups       | OU=Marketing,DC=contoso,DC=com
  Sales        | OU=Sales,DC=contoso,DC=com
  Marketing    | OU=Groups,DC=contoso,DC=com


## Add users to cloud-native or SOA converted security groups

To add synced users, follow these steps:

>[!NOTE]
>Only synced user member references are provisioned to AD. 

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Hybrid Identity Administrator](~/identity/role-based-access-control/permissions-reference.md#hybrid-identity-administrator).
2. Browse to **Entra ID** > **Groups** > **All groups**.
3. At the top, in the search box, enter **Sales**.
4. Click the new **Sales** group.
5. On the left, click **Members**.
6. At the top, click **Add members**.
7. At the top, in the search box, enter **Britta Simon**.
8. Put a check next to **Britta Simon** and click **Select**.
9. It should successfully add the user to the group.
10. On the far left, click **All groups**. Repeat this process by using the **Sales** group, and add **Lola Jacobson** to that group.

## Configure provisioning

To configure provisioning, follow these steps:

   [!INCLUDE [sign in](../../../includes/cloud-sync-sign-in.md)]
   3. Select **New configuration**.
   4. Select **Microsoft Entra ID to AD sync**.

      :::image type="content" source="media/how-to-configure-entra-to-active-directory/entra-to-ad-1.png" alt-text="Screenshot of configuration selection." lightbox="media/how-to-configure-entra-to-active-directory/entra-to-ad-1.png":::

   5. On the configuration screen, select your domain and whether to enable password hash sync. Click **Create**. 

      :::image type="content" source="media/how-to-configure/new-ux-configure-2.png" alt-text="Screenshot of a new configuration." lightbox="media/how-to-configure/new-ux-configure-2.png":::

   6. The **Get started** screen opens. From here, you can continue configuring cloud sync.
   7. On the left, click **Scoping filters**.
   8. For **Groups scope**, select **Selected security groups**.

      :::image type="content" source="media/how-to-configure-entra-to-active-directory/entra-to-ad-3.png" alt-text="Screenshot of the scoping filters sections." lightbox="media/how-to-configure-entra-to-active-directory/entra-to-ad-3.png":::

   9. There are two possible approaches to set the OU:

      - You can preserve the original OU path from on-premises. With this approach, you to set the attribute mapping based on an extensionAttribute value. For more information, see [Preserve the original OU path](how-to-preserve-original-organizational-unit.md).  
   
      Or

      - Under **Target container** click **Edit attribute mapping**.

   10. Change **Mapping type** to **Expression**.
   11. In the expression box, enter:

       ```Switch([displayName],"OU=Groups,DC=contoso,DC=com","Marketing","OU=Marketing,DC=contoso,DC=com","Sales","OU=Sales,DC=contoso,DC=com") ```

   12. Change the **Default value** to be `OU=Groups,DC=contoso,DC=com`.

       :::image type="content" source="media/tutorial-group-provision/change-default.png" alt-text="Screenshot of how to change the default value of the OU." lightbox="media/tutorial-group-provision/change-default.png":::

   13. Click **Apply** - This changes the target container depending on the group displayName attribute.
   14. Click **Save**.
   15. On the left, click **Overview**.
   16. At the top, click **Review and enable**.
   17. On the right, click **Enable configuration**.


## Test configuration 
>[!NOTE]
>When you run on-demand provisioning, members aren't automatically provisioned. You need to select the members you want to test, and the limit is five members.

 [!INCLUDE [sign in](../../../includes/cloud-sync-sign-in.md)]

 3. Under **Configuration**, select your configuration.
 4. On the left, select **Provision on demand**.
 5. Enter **Sales** in the **Selected group** box.
 6. From the **Selected users** section, select some users to test.
    
    :::image type="content" source="media/tutorial-group-provision/select-user.png" alt-text="Screenshot of adding members." lightbox="media/tutorial-group-provision/select-user.png":::

 7. Click **Provision**.
 8. You should see the group provisioned.
 
   :::image type="content" source="media/tutorial-group-provision/success.png" alt-text="Screenshot of successful provisioning on demand." lightbox="media/tutorial-group-provision/success.png":::

## Verify in AD DS

Follow these steps to make sure the group is provisioned to AD DS:

1.  Sign-in to your on-premises environment.
2.  Launch **Active Directory Users and Computers**
3.  Verify the new group is provisioned.

    :::image type="content" source="media/tutorial-group-provision/verify.png" alt-text="Screenshot of the newly provisioned group." lightbox="media/tutorial-group-provision/verify.png":::

## Group Provision to AD behavior for SOA converted objects

When you convert the **Source of Authority (SOA)** to cloud for an on-premises group, that group becomes eligible for group provisioning to AD DS.

For example, in the following diagram, **SOATestGroup1** SOA is converted to the cloud.
As a result, it becomes available for the **GPAD job scope**.

:::image type="content" border="true" source="media/tutorial-group-provision/in-scope.png" alt-text="Screenshot of job in scope." lightbox="media/tutorial-group-provision/entry-level-error.png":::

- When a **GPAD job** runs, the SOA-converted group is provisioned successfully.

- In the **Provisioning Logs**, you can search for the group name and verify that the group was provisioned.

  :::image type="content" border="true" source="media/tutorial-group-provision/provisioning-logs.png" alt-text="Screenshot of the Provisioning logs." lightbox="media/tutorial-group-provision/provisioning-logs.png":::

- The details show that the group was matched with an existing target group.

  :::image type="content" border="true" source="media/tutorial-group-provision/matched.png" alt-text="Screenshot of matched attributes." lightbox="media/tutorial-group-provision/matched.png":::

- Additionally, you can confirm that the **Admin Description** and **CN (Common Name)** of the target group are updated.

  :::image type="content" border="true" source="media/tutorial-group-provision/confirm-updates.png" alt-text="Screenshot of updated attributes." lightbox="media/tutorial-group-provision/confirm-updates.png":::

- When you look at AD, you can find that the original AD group is updated.

  :::image type="content" border="true" source="media/tutorial-group-provision/updated-group.png" alt-text="Screenshot of the updated group." lightbox="media/tutorial-group-provision/updated-group.png":::

  :::image type="content" border="true" source="media/tutorial-group-provision/group-properties.png" alt-text="Screenshot of group properties." lightbox="media/tutorial-group-provision/group-properties.png":::

### Nested Groups and membership references handling

The following table explains how the provisioning handles membership references when you convert SOA for some groups within a nested group structure and add it into scope for provisioning to AD.

Use case | Parent group type | Member group type | Job | How sync works
---------|-------------------|-------------------|-----|-----------------------
A Microsoft Entra parent security group has only Microsoft Entra members. | Microsoft Entra security group |Microsoft Entra security group |AAD2ADGroupProvisioning (Group Provisioning to AD) | The job provisions the parent group with all its member references (member groups).
A Microsoft Entra parent security group has some members that are synced groups. |Microsoft Entra security group |AD security groups (synced groups)| AAD2ADGroupProvisioning (Group Provisioning to AD)| The job provisions the parent group, but all the member references (member Groups) that are AD groups aren't provisioned.
A Microsoft Entra parent security group has some members that are synced groups whose SOA is converted to cloud. |Microsoft Entra security group | AD security groups whose SOA is converted to cloud. |AAD2ADGroupProvisioning (Group Provisioning to AD)| The job provisions the parent group with all its member references (member groups).
You convert the SOA of a synced group (parent) that has cloud-owned groups as members. | AD security groups with SOA converted to cloud | Microsoft Entra security group| AAD2ADGroupProvisioning (Group Provisioning to AD)| The job provisions the parent group with all its member references (member groups).
You convert the SOA of a synced group (parent) that has other synced groups as members. |AD security groups with SOA converted to cloud| AD security groups (synced groups) | AAD2ADGroupProvisioning (Group Provisioning to AD) |The job provisions the parent group, but all the member references (member Groups) that are AD security groups aren't provisioned.
You convert the SOA of a synced group (parent) whose members are other synced groups that have SOA converted to cloud. | AD security groups with SOA converted to cloud | AD security groups with SOA converted to cloud | AAD2ADGroupProvisioning (Group Provisioning to AD) | The job provisions the parent group with all its member references (member groups).

## Group provision to AD behavior after you roll back SOA converted groups

If you have SOA converted groups in scope and you roll back the SOA converted group to make it an AD owned group, **Group Provisioning to AD (GPAD)** will stop syncing the changes, but it doesn't delete the on-premises group. It also removes the group from GPAD configuration scope. On-premises control of the group resumes in the next sync cycle.

- You can verify in the Audit Logs that sync won't happen for this object because it's managed on-premises. 
  
  :::image type="content" border="true" source="media/tutorial-group-provision/audit-log-details.png" alt-text="Screenshot of Audit log details." lightbox="media/tutorial-group-provision/audit-log-details.png":::

  You can also check in AD that the group is still intact and not deleted.  

  :::image type="content" border="true" source="media/tutorial-group-provision/users-and-computers.png" alt-text="Screenshot of Users and Computers." lightbox="media/tutorial-group-provision/users-and-computers.png":::

## Next steps 
- [Group writeback with Microsoft Entra Cloud Sync ](../group-writeback-cloud-sync.md)
- [Govern on-premises AD DS based apps (Kerberos) using Microsoft Entra ID Governance](govern-on-premises-groups.md)
- [Migrate Microsoft Entra Connect Sync group writeback V2 to Microsoft Entra Cloud Sync](migrate-group-writeback.md)
