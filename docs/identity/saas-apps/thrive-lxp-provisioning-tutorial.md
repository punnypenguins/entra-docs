---
title: Configure Thrive LXP for automatic user provisioning with Microsoft Entra ID
description: Learn how to automatically provision and de-provision user accounts from Microsoft Entra ID to Thrive LXP.

author: adimitui
manager: jeedes
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 05/20/2025
ms.author: addimitu

# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to Thrive LXP so that I can streamline the user management process and ensure that users have the appropriate access to Thrive LXP.
---

# Configure Thrive LXP for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Thrive LXP and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Thrive LXP](https://thrivelearning.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md). 


## Capabilities Supported
> [!div class="checklist"]
> * Create users in Thrive LXP
> * Remove users in Thrive LXP when they don't require access anymore
> * Keep user attributes synchronized between Microsoft Entra ID and Thrive LXP
> * Provision groups and group memberships in Thrive LXP
> * [Single sign-on](./thrive-lxp-tutorial.md) to Thrive LXP (recommended)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* A **SCIM token** supplied by your contact at THRIVE LXP.

## Step 1: Plan your provisioning deployment
1. Learn about [how the provisioning service works](~/identity/app-provisioning/user-provisioning.md).
2. Determine who's in [scope for provisioning](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).
3. Determine what data to [map between Microsoft Entra ID and Thrive LXP](~/identity/app-provisioning/customize-application-attributes.md). 

<a name='step-2-configure-thrive-lxp-to-support-provisioning-with-azure-ad'></a>

## Step 2: Configure Thrive LXP to support provisioning with Microsoft Entra ID

Reach out to your [Thrive LXP Client support team](mailto:support@thrivelearning.com) to generate your **Tenant url** and **Secret Token**. These values are entered in the Tenant URL and Secret Token field in the Provisioning tab of your Thrive LXP application.

<a name='step-3-add-thrive-lxp-from-the-azure-ad-application-gallery'></a>

## Step 3: Add Thrive LXP from the Microsoft Entra application gallery

Add Thrive LXP from the Microsoft Entra application gallery to start managing provisioning to Thrive LXP. If you have previously setup Thrive LXP for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](~/identity/enterprise-apps/add-application-portal.md). 

## Step 4: Define who is in scope for provisioning 

[!INCLUDE [create-assign-users-provisioning.md](~/identity/saas-apps/includes/create-assign-users-provisioning.md)]

## Step 5: Configure automatic user provisioning to Thrive LXP 

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

<a name='to-configure-automatic-user-provisioning-for-thrive-lxp-in-azure-ad'></a>

### To configure automatic user provisioning for Thrive LXP in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps**

	![Enterprise applications blade](common/enterprise-applications.png)

1. In the applications list, select **Thrive LXP**.

	![The Thrive LXP link in the Applications list](common/all-applications.png)

3. Select the **Provisioning** tab.

	![Provisioning tab](common/provisioning.png)

4. Set the **Provisioning Mode** to **Automatic**.

	![Provisioning tab automatic](common/provisioning-automatic.png)

5. Under the **Admin Credentials** section, input your Thrive LXP Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Thrive LXP. If the connection fails, ensure your Thrive LXP account has Admin permissions and try again.

 	![Token](common/provisioning-testconnection-tenanturltoken.png)

6. In the **Notification Email** field, enter the email address of a person or group who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

	![Notification Email](common/provisioning-notification-email.png)

7. Select **Save**.

8. Under the **Mappings** section, select **Synchronize Microsoft Entra users to Thrive LXP**.

9. Review the user attributes that are synchronized from Microsoft Entra ID to Thrive LXP in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Thrive LXP for update operations. If you choose to change the [matching target attribute](~/identity/app-provisioning/customize-application-attributes.md), you need to ensure that the Thrive LXP API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

   |Attribute|Type|Supported For Filtering|
   |---|---|---|
   |userName|String|&check;|
   |title|String|
   |active|Boolean|
   |emails[type eq "work"].value|String|
   |preferredLanguage|String|
   |name.givenName|String|
   |name.familyName|String|
   |timezone|String|
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager|Reference|

10. Under the **Mappings** section, select **Synchronize Microsoft Entra groups to Thrive LXP**.

11. Review the group attributes that are synchronized from Microsoft Entra ID to Thrive LXP in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Thrive LXP for update operations. Select the **Save** button to commit any changes.

      |Attribute|Type|Supported For Filtering|
      |---|---|---|
      |displayName|String|&check;|
      |externalId|String|
      |members|Reference|

12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter  article](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

13. To enable the Microsoft Entra provisioning service for Thrive LXP, change the **Provisioning Status** to **On** in the **Settings** section.

	![Provisioning Status Toggled On](common/provisioning-toggle-on.png)

14. Define the users and/or groups that you would like to provision to Thrive LXP by choosing the desired values in **Scope** in the **Settings** section.

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
