---
title: Configure Configure Playvox for for automatic user provisioning with Microsoft Entra ID
description: Learn how to automatically provision and de-provision user accounts from Microsoft Entra ID to Playvox.
author: adimitui
manager: jeedes
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: addimitu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to Playvox so that I can streamline the user management process and ensure that users have the appropriate access to Playvox.
---

# Configure Configure Playvox for for automatic user provisioning with Microsoft Entra ID

This article describes the steps to follow in both Playvox and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users or groups to [Playvox](https://www.playvox.com) by using the Microsoft Entra provisioning service. For important details on what this service does and how it works, and for frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md).

## Capabilities supported
> [!div class="checklist"]
> * Create users in Playvox.
> * Remove users in Playvox when they don't need access anymore.
> * Keep user attributes synchronized between Microsoft Entra ID and Playvox.

## Prerequisites

The scenario in this article assumes that you already have the following prerequisites:

* [A Microsoft Entra tenant](~/identity-platform/quickstart-create-new-tenant.md).
* One of the following roles: [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
* A user account in [Playvox](https://www.playvox.com) with Super Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn [how the provisioning service works](~/identity/app-provisioning/user-provisioning.md).

2. Determine who's [in scope for provisioning](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

3. Determine what data to [map between Microsoft Entra ID and Playvox](~/identity/app-provisioning/customize-application-attributes.md).

<a name='step-2-configure-playvox-to-support-provisioning-by-using-azure-ad'></a>

## Step 2: Configure Playvox to support provisioning by using Microsoft Entra ID

1. Log in to the Playvox admin console and go to **Settings > API Keys**.

2. Select **Create API Key**.

    ![Partial screenshot showing the location of the Create API Key button in the Playvox user interface.](media/playvox-provisioning-tutorial/create.png)

3. Enter a meaningful name for the API key, and then select **Save**. After the API key is generated, select **Close**.

4. On the API key that you created, select the **Details** icon.

    ![Partial screenshot showing the location of the Details icon, which is a magnifying glass, in the Playvox user interface.](media/playvox-provisioning-tutorial/api.png)

5. Copy and save the **BASE64 KEY** value. Later, in the Azure portal, you enter this value in the **Secret Token** text box in the **Provisioning** tab of your Playvox application.

    ![Screenshot of the Details API Key message box, with the BASE64 KEY value highlighted.](media/playvox-provisioning-tutorial/token.png)

<a name='step-3-add-playvox-from-the-azure-ad-application-gallery'></a>

## Step 3: Add Playvox from the Microsoft Entra application gallery

To start to manage provisioning to Playvox, add Playvox to your Microsoft Entra tenant from the application gallery. To learn more, see [Quickstart: Add an application to your Microsoft Entra tenant](~/identity/enterprise-apps/add-application-portal.md).

If you've previously set up Playvox for single sign-on (SSO), you can use the same application. However, we recommend that you create a separate app when testing the integration initially.

## Step 4: Define who is in scope for provisioning

[!INCLUDE [create-assign-users-provisioning.md](~/identity/saas-apps/includes/create-assign-users-provisioning.md)]

## Step 5: Configure automatic user provisioning to Playvox

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users or groups, based on user or group assignments in Microsoft Entra ID.

To configure automatic user provisioning for Playvox in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps**.

    ![Partial screenshot of the Azure portal, with Enterprise applications and All applications items highlighted](common/enterprise-applications.png)

2. In the applications list, search for and select **Playvox**.

    ![Partial screenshot of the applications list, with the application search box highlighted.](common/all-applications.png)

3. Select the **Provisioning** tab.

    ![Partial screenshot showing the Provisioning menu item.](common/provisioning.png)

4. Set the **Provisioning Mode** to **Automatic**.

    ![Partial screenshot of the Provisioning tab, showing the Automatic option selected in the Provisioning Mode drop-down list box.](common/provisioning-automatic.png)

5. In the **Admin Credentials** section, enter your Playvox **Tenant URL** as:

    `https://{tenant}.playvox.com/scim/v1`

    Enter the **Secret Token** that you copied earlier in Step 2. Then, select **Test Connection** to ensure that Microsoft Entra ID can connect to Playvox. If the connection fails, make sure your Playvox account has Admin permissions and try again.

    ![Partial screenshot showing the Admin Credentials section, including Tenant URL and Secret Token text boxes, and with the Test Connection link highlighted.](common/provisioning-testconnection-tenanturltoken.png)

6. In the **Notification Email** text box, enter the email address of a person or group who receives the provisioning error notifications. Then, select the **Send an email notification when a failure occurs** check box.

    ![Partial screenshot showing the Notification Email text box and the email notification check box.](common/provisioning-notification-email.png)

7. Select **Save**.

8. In the **Mappings** section, select **Synchronize Microsoft Entra users to Playvox**.

9. Review the user attributes that are synchronized from Microsoft Entra ID to Playvox in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Playvox for update operations. If you choose to change the [matching target attribute](~/identity/app-provisioning/customize-application-attributes.md), make sure that the Playvox API supports filtering users based on that attribute. Select **Save** to commit any changes.

   |Attribute|Type|Supported for filtering|
   |---|---|---|
   |userName|String|&check;|
   |active|Boolean|
   |displayName|String|
   |emails[type eq "work"].value|String|
   |name.givenName|String|
   |name.familyName|String|
   |name.formatted|String|
   |externalId|String|

10. To configure scoping filters, see the instructions in the [Scoping filter  article](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

11. To enable the Microsoft Entra provisioning service for Playvox, change the **Provisioning Status** to **On** in the **Settings** section.

    ![Partial screenshot  of Settings section, showing the Provisioning Status set to On.](common/provisioning-toggle-on.png)

12. Still in **Settings**, define the users or groups to provision to Playvox by choosing the values you want in **Scope**.

    ![Partial screenshot of the Settings section, showing the Scope drop-down list box.](common/provisioning-scope.png)

13. When you're ready to provision, select **Save**.

    ![Partial screenshot showing Save and Discard options.](common/provisioning-configuration-save.png)

This operation starts the initial synchronization cycle of all users and groups defined in **Scope** in the **Settings** section. The initial cycle takes longer than later cycles. Later cycles occur approximately every 40 minutes, provided that the Microsoft Entra provisioning service is running.

## Step 6: Monitor your deployment

[!INCLUDE [monitor-deployment.md](~/identity/saas-apps/includes/monitor-deployment.md)]

## Additional resources

* [Managing user account provisioning for enterprise apps](~/identity/app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

## Related content

* [Learn how to review logs and get reports on provisioning activity](~/identity/app-provisioning/check-status-user-account-provisioning.md)
