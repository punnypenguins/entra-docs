---
title: Configure AlexisHR for automatic user provisioning with Microsoft Entra ID
description: Learn how to automatically provision and de-provision user accounts from Microsoft Entra ID to AlexisHR.

author: adimitui
manager: jeedes
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: addimitu

# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to AlexisHR so that I can streamline the user management process and ensure that users have the appropriate access to AlexisHR.

---

# Configure AlexisHR for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both AlexisHR and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [AlexisHR](https://alexishr.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md). 


## Capabilities Supported
> [!div class="checklist"]
> * Create users in AlexisHR.
> * Remove users in AlexisHR when they don't require access anymore.
> * Keep user attributes synchronized between Microsoft Entra ID and AlexisHR.
> * [Single sign-on](alexishr-tutorial.md) to AlexisHR (recommended).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

* [A Microsoft Entra tenant](~/identity-platform/quickstart-create-new-tenant.md). 
* One of the following roles: [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
* A user account in AlexisHR with Admin permissions.


## Step 1: Plan your provisioning deployment
1. Learn about [how the provisioning service works](~/identity/app-provisioning/user-provisioning.md).
1. Determine who is in [scope for provisioning](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).
1. Determine what data to [map between Microsoft Entra ID and AlexisHR](~/identity/app-provisioning/customize-application-attributes.md). 

<a name='step-2-configure-alexishr-to-support-provisioning-with-azure-ad'></a>

## Step 2: Configure AlexisHR to support provisioning with Microsoft Entra ID

1. Log in to [AlexisHR Admin Console](https://app.alexishr.com/login/). Navigate to **Settings > Access tokens**.

	![Access User Management](media/alexishr-provisioning-tutorial/login.png)

1. Once on the Access token page, fill in the **Name** and **Description** textbox and select **Save**.A pop-up window appears with the token in it.Copy and save the token. This value is entered in the **Secret Token** * field in the Provisioning tab of your AlexisHR application.

	![Access tokens](media/alexishr-provisioning-tutorial/token.png)

<a name='step-3-add-alexishr-from-the-azure-ad-application-gallery'></a>

## Step 3: Add AlexisHR from the Microsoft Entra application gallery

Add AlexisHR from the Microsoft Entra application gallery to start managing provisioning to AlexisHR. If you have previously setup AlexisHR for SSO you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](~/identity/enterprise-apps/add-application-portal.md). 

## Step 4: Define who is in scope for provisioning 

[!INCLUDE [create-assign-users-provisioning.md](~/identity/saas-apps/includes/create-assign-users-provisioning.md)]

## Step 5: Configure automatic user provisioning to AlexisHR 

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in AlexisHR based on user and/or group assignments in Microsoft Entra ID.

<a name='to-configure-automatic-user-provisioning-for-alexishr-in-azure-ad'></a>

### To configure automatic user provisioning for AlexisHR in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps**

	![Enterprise applications blade](common/enterprise-applications.png)

1. In the applications list, select **AlexisHR**.

	![The AlexisHR link in the Applications list](common/all-applications.png)

1. Select the **Provisioning** tab.

	![Provisioning tab](common/provisioning.png)

1. Set the **Provisioning Mode** to **Automatic**.

	![Provisioning tab automatic](common/provisioning-automatic.png)

1. In the **Admin Credentials** section, input your AlexisHR **Tenant URL** and **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to AlexisHR. If the connection fails , ensure your AlexisHR account has Admin permissions and try again.

	![Token](common/provisioning-testconnection-tenanturltoken.png)

1. In the **Notification Email** field, enter the email address of a person or group who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

	![Notification Email](common/provisioning-notification-email.png)

1. Select **Save**.

1. In the **Mappings** section, select **Synchronize Microsoft Entra users to AlexisHR**.

1. Review the user attributes that are synchronized from Microsoft Entra ID to AlexisHR in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in AlexisHR for update operations. If you choose to change the [matching target attribute](~/identity/app-provisioning/customize-application-attributes.md), you need to ensure that the AlexisHR API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

   |Attribute|Type|Supported for filtering|Required by AlexisHR
   |---|---|---|---|
   |userName|String|&check;|&check;
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager|Reference||
   |active|Boolean||&check;
   |title|String||
   |emails[type eq "work"].value|String||&check;
   |name.givenName|String||&check;
   |name.familyName|String||&check;
   |phoneNumbers[type eq "work"].value|String||&check;
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department|String||
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter|String||
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division|String||
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization|String||

	> [!NOTE]
	> phonenumbers value should be in E164 format. For example +16175551212

1. To configure scoping filters, refer to the following instructions provided in the [Scoping filter  article](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

1. To enable the Microsoft Entra provisioning service for AlexisHR, change the **Provisioning Status** to **On** in the **Settings** section.

	![Provisioning Status Toggled On](common/provisioning-toggle-on.png)

1. Define the users and/or groups that you would like to provision to AlexisHR by choosing the desired values in **Scope** in the **Settings** section.

	![Provisioning Scope](common/provisioning-scope.png)

1. When you're ready to provision, select **Save**.

	![Saving Provisioning Configuration](common/provisioning-configuration-save.png)

This operation starts the initial synchronization cycle of all users and groups defined in **Scope** in the **Settings** section. The initial cycle takes longer to perform than subsequent cycles, which occur approximately every 40 minutes as long as the Microsoft Entra provisioning service is running. 

## Step 6: Monitor your deployment

[!INCLUDE [monitor-deployment.md](~/identity/saas-apps/includes/monitor-deployment.md)]

## More resources

* [Managing user account provisioning for Enterprise Apps](~/identity/app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

## Related content

* [Learn how to review logs and get reports on provisioning activity](~/identity/app-provisioning/check-status-user-account-provisioning.md)
