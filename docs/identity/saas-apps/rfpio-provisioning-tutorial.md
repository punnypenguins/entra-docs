---
title: Configure RFPIO for automatic user provisioning with Microsoft Entra ID
description: Learn how to configure Microsoft Entra ID to automatically provision and de-provision user accounts to RFPIO.
author: adimitui
manager: mwongerapk
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 05/20/2025
ms.author: addimitu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to RFPIO so that I can streamline the user management process and ensure that users have the appropriate access to RFPIO.
---

# Configure RFPIO for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in RFPIO and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to RFPIO.

> [!NOTE]
> This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md).
>

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)].
* [A RFPIO tenant](https://www.rfpio.com/product/).
* A user account in RFPIO with Admin permissions.

## Assigning users to RFPIO

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to RFPIO. Once decided, you can assign these users and/or groups to RFPIO by following the instructions here:
* [Assign a user or group to an enterprise app](~/identity/enterprise-apps/assign-user-or-group-access-portal.md)

## Important tips for assigning users to RFPIO

* It's recommended that a single Microsoft Entra user is assigned to RFPIO to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.

* When assigning a user to RFPIO, you must select any valid application-specific role (if available) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up RFPIO for provisioning

Before configuring RFPIO for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on RFPIO.

1. 	Sign in to your RFPIO Admin Console. On the bottom left of the admin console, select **Tenant**.

	![RFPIO Admin Console](media/rfpio-provisioning-tutorial/aadtest0.png)

2.	Select **Organization Settings**.
	
	![RFPIO Admin](media/rfpio-provisioning-tutorial/aadtest.png)

3.	Navigate to **USER MANAGEMENT** > **SECURITY** > **SCIM**.

	![RFPIO Add SCIM](media/rfpio-provisioning-tutorial/scim.png)

4.	Ensure that **Auto User Provisioning** is enabled. Select **GENERATE SCIM API TOKEN**.

	![Screenshot of the S C I M section with the GENERATE S C I M A P I TOKEN option called out.](media/rfpio-provisioning-tutorial/generate.png)

5.	Save the **SCIM API Token** as this token isn't displayed again for security purpose. This value is entered in the **Secret Token** field in the Provisioning tab of your RFPIO application.

	![Screenshot of the S C I M section with the Warning dialog box that appears after you select SUBMIT.](media/rfpio-provisioning-tutorial/auth.png)

## Add RFPIO from the gallery

To configure RFPIO for automatic user provisioning with Microsoft Entra ID, you need to add RFPIO from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add RFPIO from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **RFPIO**, select **RFPIO** in the results panel, and then select the 	**Add** button to add the application.

	![RFPIO in the results list](common/search-new-app.png)

## Configuring automatic user provisioning to RFPIO 

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in RFPIO based on user and/or group assignments in Microsoft Entra ID.

> [!TIP]
> You may also choose to enable SAML-based single sign-on for RFPIO, following the instructions provided in the [RFPIO Single sign-on  article](rfpio-tutorial.md). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

<a name='to-configure-automatic-user-provisioning-for-rfpio-in-azure-ad'></a>

### To configure automatic user provisioning for RFPIO in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps**

	![Enterprise applications blade](common/enterprise-applications.png)

1. In the applications list, select **RFPIO**.

	![The RFPIO link in the Applications list](common/all-applications.png)

3. Select the **Provisioning** tab.

	![Screenshot of the Manage options with the Provisioning option called out.](common/provisioning.png)

4. Set the **Provisioning Mode** to **Automatic**.

	![Screenshot of the Provisioning Mode dropdown list with the Automatic option called out.](common/provisioning-automatic.png)

5. Under the **Admin Credentials** section, input `https://<RFPIO tenant instance>.rfpio.com/rfpserver/scim/v2 ` in **Tenant URL**. An example value is `https://Azure-test1.rfpio.com/rfpserver/scim/v2`. Input the **SCIM API Token** value retrieved earlier in **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to RFPIO. If the connection fails, ensure your RFPIO account has Admin permissions and try again.

	![Tenant URL + Token](common/provisioning-testconnection-tenanturltoken.png)

6. In the **Notification Email** field, enter the email address of a person or group who should receive the provisioning error notifications and check the checkbox - **Send an email notification when a failure occurs**.

	![Notification Email](common/provisioning-notification-email.png)

7. Select **Save**.

8. Under the **Mappings** section, select **Synchronize Microsoft Entra users to RFPIO**.

9. Review the user attributes that are synchronized from Microsoft Entra ID to RFPIO in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in RFPIO for update operations. Select the **Save** button to commit any changes.

	![RFPIO User Attributes](media/rfpio-provisioning-tutorial/userattributes.png)

10. To configure scoping filters, refer to the following instructions provided in the [Scoping filter  article](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

11. To enable the Microsoft Entra provisioning service for RFPIO, change the **Provisioning Status** to **On** in the **Settings** section.

	![Provisioning Status Toggled On](common/provisioning-toggle-on.png)

12. Define the users and/or groups that you would like to provision to RFPIO by choosing the desired values in **Scope** in the **Settings** section.

	![Provisioning Scope](common/provisioning-scope.png)

13. When you're ready to provision, select **Save**.

	![Saving Provisioning Configuration](common/provisioning-configuration-save.png)

This operation starts the initial synchronization of all users and/or groups defined in **Scope** in the **Settings** section. The initial sync takes longer to perform than subsequent syncs, which occur approximately every 40 minutes as long as the Microsoft Entra provisioning service is running. You can use the **Synchronization Details** section to monitor progress and follow links to provisioning activity report, which describes all actions performed by the Microsoft Entra provisioning service on RFPIO.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](~/identity/app-provisioning/check-status-user-account-provisioning.md).

## Connector Limitations

* RFPIO doesn't support groups provisioning currently.

## Additional resources

* [Managing user account provisioning for Enterprise Apps](~/identity/app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

## Related content

* [Learn how to review logs and get reports on provisioning activity](~/identity/app-provisioning/check-status-user-account-provisioning.md)
