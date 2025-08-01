---
title: Configure Canvas for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Canvas.
author: nguhiu
manager: mwongerapk
ms.reviewer: celested
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Canvas Lms so that I can control who has access to Canvas Lms, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---
# Configure Canvas for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Canvas with Microsoft Entra ID. When you integrate Canvas with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Canvas.
* Enable your users to be automatically signed-in to Canvas with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Canvas single sign-on (SSO)-enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra single sign-on in a test environment.

* Canvas supports **SP** initiated SSO.

## Add Canvas from the gallery

To configure the integration of Canvas into Microsoft Entra ID, you need to add Canvas from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Canvas** in the search box.
1. Select **Canvas** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso-for-canvas'></a>

## Configure and test Microsoft Entra SSO for Canvas

Configure and test Microsoft Entra SSO with Canvas using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Canvas.

To configure and test Microsoft Entra SSO with Canvas, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Canvas SSO](#configure-canvas-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Canvas test user](#create-canvas-test-user)** - to have a counterpart of B.Simon in Canvas that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Canvas** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, perform the following steps:

    b. In the **Sign on URL** text box, type a URL using the following pattern:
    `https://<tenant-name>.instructure.com`

    a. In the **Identifier (Entity ID)** text box, type a URL using the following pattern:
    `https://<tenant-name>.instructure.com/saml2`

    > [!NOTE]
    > These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Canvas Client support team](https://community.canvaslms.com/community/help) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![The Certificate download link](common/copy-metadataurl.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Canvas SSO

1. In a different web browser window, log in to your Canvas company site as an administrator.

2. Go to **Admin > Microsoft OneNote > Authentication**.
3. Choose an authentication service as **SAML**. 

    ![Canvas](./media/canvas-lms-tutorial/admin.png "Canvas")

4. On the **Current Provider** page, perform the following steps:

    ![Current Integration](./media/canvas-lms-tutorial/current-provider.png "Current Integration")

    a. In **IdP Metadata URI** textbox, paste the value of **App Federation Metadata URL** value.

    b. Select **Save**.

### Create Canvas test user

To enable Microsoft Entra users to log in to Canvas, they must be provisioned into Canvas. In the case of Canvas, user provisioning is a manual task.

**To provision a user account, perform the following steps:**

1. Log in to your **Canvas** tenant.

2. Go to **Admin > Microsoft OneNote > People**.

3. Select **+People**.

4. On the Add a New User dialog page, perform the following steps:

   ![Add User](./media/canvas-lms-tutorial/new-user.png "Add User")

   a. In the **Full Name** textbox, enter the name of user like **BrittaSimon**.

   b. In the **Email** textbox, enter the email of user like **brittasimon\@contoso.com**.

   c. Select **Add User**.

> [!NOTE]
> You can use any other Canvas user account creation tools or APIs provided by Canvas to provision Microsoft Entra user accounts.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Canvas Sign on URL where you can initiate the login flow. 

* Go to Canvas Sign on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Canvas tile in the My Apps, you should be automatically signed in to the Canvas for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Canvas you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
