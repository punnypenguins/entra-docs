---
title: Configure Lucidchart for automatic user provisioning with Microsoft Entra ID
description: Learn how to automatically provision and de-provision user accounts from Microsoft Entra ID to Lucidchart.

author: adimitui
manager: mwongerapk
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: addimitu

# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to Lucidchart so that I can streamline the user management process and ensure that users have the appropriate access to Lucidchart.
---

# Configure Lucidchart for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Lucidchart and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Lucidchart](https://www.lucidchart.com/user/117598685#/subscriptionLevel) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md). 


## Capabilities supported
> [!div class="checklist"]
> * Create users in Lucidchart
> * Remove users in Lucidchart when they don't require access anymore
> * Keep user attributes synchronized between Microsoft Entra ID and Lucidchart
> * Provision groups and group memberships in Lucidchart
> * [Single sign-on](./lucidchart-tutorial.md) to Lucidchart (recommended)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

* [A Microsoft Entra tenant](~/identity-platform/quickstart-create-new-tenant.md) 
* A user account in Microsoft Entra ID with [permission](~/identity/role-based-access-control/permissions-reference.md) to configure provisioning (like [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications)). 
* A LucidChart tenant with the [Enterprise plan](https://www.lucidchart.com/user/117598685#/subscriptionLevel) or better enabled.
* A user account in LucidChart with Admin permissions.

## Step 1: Plan your provisioning deployment
1. Learn about [how the provisioning service works](~/identity/app-provisioning/user-provisioning.md).
2. Determine who's in [scope for provisioning](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).
3. Determine what data to [map between Microsoft Entra ID and Lucidchart](~/identity/app-provisioning/customize-application-attributes.md). 

<a name='step-2-configure-lucidchart-to-support-provisioning-with-azure-ad'></a>

## Step 2: Configure Lucidchart to support provisioning with Microsoft Entra ID

1. Login to [Lucidchart admin console](https://lucid.app/). Navigate to **Team > App Integration**.

      :::image type="content" source="./media/lucidchart-provisioning-tutorial/team1.png" alt-text="Screenshot of the Lucidchart admin console. The Team menu is highlighted and open. Under Admin, App Integration is highlighted." border="false":::

2. Navigate to **SCIM**.

      :::image type="content" source="./media/lucidchart-provisioning-tutorial/scim.png" alt-text="Screenshot of the Lucidchart admin console. Within a large S C I M button, the text S C I M is highlighted, and an enabled banner is visible." border="false":::

3. Scroll down to see the **Bearer token** and **Lucidchart Base URL**. Copy and save the **Bearer token**. This value is entered in the **Secret Token** * field in the Provisioning tab of your LucidChart application. 

      ![Lucidchart token](./media/lucidchart-provisioning-tutorial/token.png)

<a name='step-3-add-lucidchart-from-the-azure-ad-application-gallery'></a>

## Step 3: Add Lucidchart from the Microsoft Entra application gallery

Add Lucidchart from the Microsoft Entra application gallery to start managing provisioning to Lucidchart. If you have previously setup Lucidchart for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](~/identity/enterprise-apps/add-application-portal.md). 

## Step 4: Define who is in scope for provisioning 

[!INCLUDE [create-assign-users-provisioning.md](~/identity/saas-apps/includes/create-assign-users-provisioning.md)]

## Step 5: Configure automatic user provisioning to Lucidchart 

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

<a name='to-configure-automatic-user-provisioning-for-lucidchart-in-azure-ad'></a>

### To configure automatic user provisioning for Lucidchart in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps**

	![Enterprise applications blade](common/enterprise-applications.png)

1. In the applications list, select **Lucidchart**.

	![The Lucidchart link in the Applications list](common/all-applications.png)

3. Select the **Provisioning** tab.

	![Screenshot of the Manage options with the Provisioning option called out.](common/provisioning.png)

4. Set the **Provisioning Mode** to **Automatic**.

	![Screenshot of the Provisioning Mode dropdown list with the Automatic option called out.](common/provisioning-automatic.png)

5. Under the **Admin Credentials** section, input the **Bearer Token**  value retrieved earlier in **Secret Token** field. Select **Test Connection** to ensure Microsoft Entra ID can connect to Lucidchart. If the connection fails, ensure your Lucidchart account has Admin permissions and try again.

      ![provisioning](./media/Lucidchart-provisioning-tutorial/lucidchart1.png)

6. In the **Notification Email** field, enter the email address of a person or group who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

	![Notification Email](common/provisioning-notification-email.png)

7. Select **Save**.

8. Under the **Mappings** section, select **Synchronize Microsoft Entra users to Lucidchart**.

9. Review the user attributes that are synchronized from Microsoft Entra ID to Lucidchart in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Lucidchart for update operations. If you choose to change the [matching target attribute](~/identity/app-provisioning/customize-application-attributes.md), you need to ensure that the Lucidchart API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

   |Attribute|Type|
   |---|---|
   |userName|String|
   |emails[type eq "work"].value|String|
   |active|Boolean|
   |name.givenName|String|
   |name.familyName|String|
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department|String|
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division|String|
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter|String|
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization|String|
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber|String|
   |urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager|Reference|
   |urn:ietf:params:scim:schemas:extension:lucidchart:1.0:User:canEdit|Boolean|

10. Under the **Mappings** section, select **Synchronize Microsoft Entra groups to Lucidchart**.

11. Review the group attributes that are synchronized from Microsoft Entra ID to Lucidchart in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Lucidchart for update operations. Select the **Save** button to commit any changes.

      |Attribute|Type|
      |---|---|
      |displayName|String|
      |members|Reference|

12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter  article](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

13. To enable the Microsoft Entra provisioning service for Lucidchart, change the **Provisioning Status** to **On** in the **Settings** section.

	![Provisioning Status Toggled On](common/provisioning-toggle-on.png)

14. Define the users and/or groups that you would like to provision to Lucidchart by choosing the desired values in **Scope** in the **Settings** section.

	![Provisioning Scope](common/provisioning-scope.png)

15. When you're ready to provision, select **Save**.

	![Saving Provisioning Configuration](common/provisioning-configuration-save.png)

This operation starts the initial synchronization cycle of all users and groups defined in **Scope** in the **Settings** section. The initial cycle takes longer to perform than subsequent cycles, which occur approximately every 40 minutes as long as the Microsoft Entra provisioning service is running. 

## Step 6: Monitor your deployment

[!INCLUDE [monitor-deployment.md](~/identity/saas-apps/includes/monitor-deployment.md)]

## Change log

* 04/30/2020 - Added support for enterprise extension attribute and custom attribute "CanEdit" for users.
* 06/15/2020 - Soft deletion of users is enabled (Supporting [active](https://tools.ietf.org/html/rfc7643) attribute).

## Additional resources

* [Managing user account provisioning for Enterprise Apps](~/identity/app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

## Related content

* [Learn how to review logs and get reports on provisioning activity](~/identity/app-provisioning/check-status-user-account-provisioning.md)
