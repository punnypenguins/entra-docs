---
title: Configure Exium for automatic user provisioning with Microsoft Entra ID
description: Learn how to automatically provision and de-provision user accounts from Microsoft Entra ID to Exium.


author: adimitui
manager: jeedes

ms.service: entra-id
ms.subservice: saas-apps


ms.topic: how-to
ms.date: 03/25/2025
ms.author: addimitu

# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to Exium so that I can streamline the user management process and ensure that users have the appropriate access to Exium.
---

# Configure Exium for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Exium and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Exium](https://exium.net/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md). 


## Capabilities supported
> [!div class="checklist"]
> * Create users in Exium
> * Remove users in Exium when they don't require access anymore
> * Keep user attributes synchronized between Microsoft Entra ID and Exium
> * Provision groups and group memberships in Exium

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* A user account in Exium with administrator permissions.
* A workspace in Exium to generate a Microsoft Entra Secret Token. A new workspace can be created [here](https://service.exium.net/sign-up).
* [Single sign-on](./exium-tutorial.md) should be enabled.

## Step 1: Plan your provisioning deployment
1. Learn about [how the provisioning service works](~/identity/app-provisioning/user-provisioning.md).
2. Determine who's in [scope for provisioning](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).
3. Determine what data to [map between Microsoft Entra ID and Exium](~/identity/app-provisioning/customize-application-attributes.md). 

<a name='step-2-configure-azure-ad-to-support-provisioning-with-exium'></a>

## Step 2: Configure Microsoft Entra ID to support provisioning with Exium
1. Log in to [Exium workspace](https://service.exium.net/sign-in).

2. On Exium workspace [profile settings](https://service.exium.net/sign-in) page, navigate to **SCIM Configuration** tab.

3. Copy the **SCIM 2.0 Bearer Token**. This value is entered in the **Secret Token** field in the Provisioning tab of your Exium application.

   	![The Exium SCIM Configuration](media/exium-provisioning-tutorial/api.png)

4. The Exium **Tenant URL** is `https://subapi.exium.net/scim`. This value is entered in the **Tenant URL** field in the Provisioning tab of your Exium application.

<a name='step-3-add-exium-from-the-azure-ad-application-gallery'></a>

## Step 3: Add Exium from the Microsoft Entra application gallery

Add Exium from the Microsoft Entra application gallery to start managing provisioning to Exium. If you have previously setup Exium for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](~/identity/enterprise-apps/add-application-portal.md). 

## Step 4: Define who is in scope for provisioning 

[!INCLUDE [create-assign-users-provisioning.md](~/identity/saas-apps/includes/create-assign-users-provisioning.md)]

## Step 5: Configure automatic user provisioning to Exium 

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

<a name='to-configure-automatic-user-provisioning-for-exium-in-azure-ad'></a>

### To configure automatic user provisioning for Exium in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps**

	![Enterprise applications blade](common/enterprise-applications.png)

1. In the applications list, select **Exium**.

	![The Exium link in the Applications list](common/all-applications.png)

3. Select the **Provisioning** tab.

	![Provisioning tab](common/provisioning.png)

4. Set the **Provisioning Mode** to **Automatic**.

	![Provisioning tab automatic](common/provisioning-automatic.png)

5. Under the **Admin Credentials** section, input your Exium Tenant URL and Secret Token retrieved in Step 2. Select **Test Connection** to ensure Microsoft Entra ID can connect to Exium. If the connection fails, ensure your Exium account has Admin permissions and try again.

 	![Token](common/provisioning-testconnection-tenanturltoken.png)

6. In the **Notification Email** field, enter the email address of a person or group who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

	![Notification Email](common/provisioning-notification-email.png)

7. Select **Save**.

8. Under the **Mappings** section, select **Synchronize Microsoft Entra users to Exium**.

9. Review the user attributes that are synchronized from Microsoft Entra ID to Exium in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Exium for update operations. If you choose to change the [matching target attribute](~/identity/app-provisioning/customize-application-attributes.md), you need to ensure that the Exium API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

   |Attribute|Type|Supported for filtering|
   |---|---|---|
   |userName|String|&check;|
   |displayName|String||
   |active|Boolean||
   |emails[type eq "work"].value|String||
   |name.givenName|String||
   |name.familyName|String||
   |addresses[type eq "work"].streetAddress|String||
   |addresses[type eq "work"].locality|String||
   |addresses[type eq "work"].region|String||
   |addresses[type eq "work"].postalCode|String||
   |addresses[type eq "work"].country|String||
   |phoneNumbers[type eq "work"].value|String||
   |externalId|String||
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department|String||
   |timezone|String||
   |userType|String||

10. Under the **Mappings** section, select **Synchronize Microsoft Entra groups to Exium**.

11. Review the group attributes that are synchronized from Microsoft Entra ID to Exium in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Exium for update operations. Select the **Save** button to commit any changes.

      |Attribute|Type|Supported for filtering|
      |---|---|---|
      |displayName|String|&check;|
      |members|Reference||

12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

13. To enable the Microsoft Entra provisioning service for Exium, change the **Provisioning Status** to **On** in the **Settings** section.

	![Provisioning Status Toggled On](common/provisioning-toggle-on.png)

14. Define the users and/or groups that you would like to provision to Exium by choosing the desired values in **Scope** in the **Settings** section.

	![Provisioning Scope](common/provisioning-scope.png)

15. When you're ready to provision, select **Save**.

	![Saving Provisioning Configuration](common/provisioning-configuration-save.png)

This operation starts the initial synchronization cycle of all users and groups defined in **Scope** in the **Settings** section. The initial cycle takes longer to perform than subsequent cycles, which occur approximately every 40 minutes as long as the Microsoft Entra provisioning service is running. 

## Step 6: Monitor your deployment

[!INCLUDE [monitor-deployment.md](~/identity/saas-apps/includes/monitor-deployment.md)]

## Additional resources

* [Managing user account provisioning for Enterprise Apps](~/identity/app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

## Related content

* [Learn how to review logs and get reports on provisioning activity](~/identity/app-provisioning/check-status-user-account-provisioning.md)
