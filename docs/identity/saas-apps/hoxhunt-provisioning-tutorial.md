---
title: Configure Hoxhunt for automatic user provisioning with Microsoft Entra ID
description: Learn how to automatically provision and de-provision user accounts from Microsoft Entra ID to Hoxhunt.

author: adimitui
manager: jeedes
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: addimitu

# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to Hoxhunt so that I can streamline the user management process and ensure that users have the appropriate access to Hoxhunt.
---

# Configure Hoxhunt for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Hoxhunt and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Hoxhunt](https://www.hoxhunt.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md). 


## Capabilities Supported
> [!div class="checklist"]
> * Create users in Hoxhunt
> * Remove users in Hoxhunt when they don't require access anymore
> * Keep user attributes synchronized between Microsoft Entra ID and Hoxhunt
> * [Single sign-on](hoxhunt-tutorial.md) to Hoxhunt (recommended)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* A Hoxhunt tenant.
* SCIM API key and SCIM endpoint URL for your organization (configured by Hoxhunt support).
## Step 1: Plan your provisioning deployment
1. Learn about [how the provisioning service works](~/identity/app-provisioning/user-provisioning.md).
2. Determine who's in [scope for provisioning](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).
3. Determine what data to [map between Microsoft Entra ID and Hoxhunt](~/identity/app-provisioning/customize-application-attributes.md). 

<a name='step-2-configure-hoxhunt-to-support-provisioning-with-azure-ad'></a>

## Step 2: Configure Hoxhunt to support provisioning with Microsoft Entra ID
Contact [Hoxhunt support](mailto:support@hoxhunt.com) to receive SCIM API key and SCIM endpoint URL to configure Hoxhunt to support provisioning with Microsoft Entra ID.
<a name='step-3-add-hoxhunt-from-the-azure-ad-application-gallery'></a>

## Step 3: Add Hoxhunt from the Microsoft Entra application gallery

Add Hoxhunt from the Microsoft Entra application gallery to start managing provisioning to Hoxhunt. If you have previously setup Hoxhunt for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](~/identity/enterprise-apps/add-application-portal.md). 

## Step 4: Define who is in scope for provisioning 

[!INCLUDE [create-assign-users-provisioning.md](~/identity/saas-apps/includes/create-assign-users-provisioning.md)]

## Step 5: Configure automatic user provisioning to Hoxhunt 

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

<a name='to-configure-automatic-user-provisioning-for-hoxhunt-in-azure-ad'></a>

### To configure automatic user provisioning for Hoxhunt in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps**

	![Screenshot of Enterprise applications blade.](common/enterprise-applications.png)

1. In the applications list, select **Hoxhunt**.

	![Screenshot of the Hoxhunt link in the Applications list.](common/all-applications.png)

3. Select the **Provisioning** tab.

	![Screenshot of Provisioning tab.](common/provisioning.png)

4. Set the **Provisioning Mode** to **Automatic**.

	![Screenshot of Provisioning tab automatic.](common/provisioning-automatic.png)

5. Under the **Admin Credentials** section, input your Hoxhunt Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Hoxhunt. If the connection fails, ensure your Hoxhunt account has Admin permissions and try again.

 	![Token](common/provisioning-testconnection-tenanturltoken.png)

6. In the **Notification Email** field, enter the email address of a person or group who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

	![Screenshot of Notification Email.](common/provisioning-notification-email.png)

7. Select **Save**.

8. Under the **Mappings** section, select **Synchronize Microsoft Entra users to Hoxhunt**.

9. Review the user attributes that are synchronized from Microsoft Entra ID to Hoxhunt in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Hoxhunt for update operations. If you choose to change the [matching target attribute](~/identity/app-provisioning/customize-application-attributes.md), you need to ensure that the Hoxhunt API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

   |Attribute|Type|Supported for filtering|Required by Hoxhunt|
   |---|---|---|---|
   |userName|String|&check;|&check;|
   |emails[type eq "work"].value|String||&check;|
   |active|Boolean|||
   |name.givenName|String|||
   |name.familyName|String|||
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department|String|||
   |addresses[type eq "work"].country|String|||
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division|String|||
   |preferredLanguage|String|||
   |addresses[type eq "work"].locality|String|||
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager|Reference|||


10. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

11. To enable the Microsoft Entra provisioning service for Hoxhunt, change the **Provisioning Status** to **On** in the **Settings** section.

	![Screenshot of Provisioning Status Toggled On.](common/provisioning-toggle-on.png)

12. Define the users and/or groups that you would like to provision to Hoxhunt by choosing the desired values in **Scope** in the **Settings** section.

	![Screenshot of Provisioning Scope.](common/provisioning-scope.png)

13. When you're ready to provision, select **Save**.

	![Screenshot of Saving Provisioning Configuration.](common/provisioning-configuration-save.png)

This operation starts the initial synchronization cycle of all users and groups defined in **Scope** in the **Settings** section. The initial cycle takes longer to perform than subsequent cycles, which occur approximately every 40 minutes as long as the Microsoft Entra provisioning service is running. 

## Step 6: Monitor your deployment

[!INCLUDE [monitor-deployment.md](~/identity/saas-apps/includes/monitor-deployment.md)]

## Change Log
* 04/20/2021 - Added support for core user attribute **preferredLanguage** and enterprise extension attribute **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division**.
* 08/08/2023 - Added support for core user attribute **addresses[type eq "work"].locality|String** and enterprise extension attribute **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager**.

## Additional resources

* [Managing user account provisioning for Enterprise Apps](~/identity/app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

## Related content

* [Learn how to review logs and get reports on provisioning activity](~/identity/app-provisioning/check-status-user-account-provisioning.md)
