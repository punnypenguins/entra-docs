---
title: Configure Blinq for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Blinq.
author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Blinq so that I can control who has access to Blinq, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Blinq for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Blinq with Microsoft Entra ID. When you integrate Blinq with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Blinq.
* Enable your users to be automatically signed-in to Blinq with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Blinq single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Blinq supports only **SP** initiated SSO.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Blinq from the gallery

To configure the integration of Blinq into Microsoft Entra ID, you need to add Blinq from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Blinq** in the search box.
1. Select **Blinq** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

[!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

## Configure and test Microsoft Entra SSO for Blinq

Configure and test Microsoft Entra SSO with Blinq using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Blinq.

To configure and test Microsoft Entra SSO with Blinq, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Blinq SSO](#configure-blinq-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Blinq test user](#create-blinq-test-user)** - to have a counterpart of B.Simon in Blinq that's linked to the Microsoft Entra ID representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Blinq** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier (Entity ID)** text box, type the URL:
    `https://auth.blinq.me/`

    b. In the **Reply URL** text box, type a URL using the following pattern:
    `https://auth.blinq.me/authorize/callback/<ID>`

    c. In the **Sign on URL** text box, type a URL using the following pattern:
    `https://auth.blinq.me/authorize/callback/<ID>`

	> [!NOTE]
	> These values aren't real. Update these values with the actual Reply URL and Sign on URL. Contact [Blinq support team](mailto:support@blinq.me) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

	![Screenshot shows the Certificate download link.](common/certificatebase64.png "Certificate")

1. On the **Set up Blinq** section, copy the appropriate URL(s) based on your requirement.

	![Screenshot shows to copy configuration URLs.](common/copy-configuration-urls.png "Metadata")

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Blinq SSO

1. Log in to Blinq company site as an administrator.

1. Go to **My Team** > **Team Settings** > **Integrations** and perform the following steps:

   ![Screenshot shows the Configuration.](./media/blinq-tutorial/settings.png "Configuration")

   1. In the **Identity Provider Entity ID** textbox, paste the **Microsoft Entra Identifier** value, which you have copied from the Microsoft Entra admin center.

   1. In the **Single Sign On URL** text box, paste the **Login URL** value, which you have copied from the Microsoft Entra admin center.

   1. Open the downloaded **Certificate (Base64)** into Notepad and paste the content into the **Certificate** textbox.

   1. Copy the **Service Provider Entity ID** and paste it in the **Identifier (Entity ID)** textbox in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

   1. Copy the **ACS URL** and paste it in the **Reply URL** textbox in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

   1. Select **Save**

### Create Blinq test user

1. In a different web browser window, sign into Blinq website as an administrator.

1. Go to **Team members** and select **Add team member +**.

    ![Screenshot shows how to add New User.](./media/blinq-tutorial/user.png "New User")

1. Perform the following steps in the below page.

   ![Screenshot shows a New User section where you enter user information.](./media/blinq-tutorial/profile.png "User Information")

    1. In the **Email** textbox, enter a valid emailaddress of the user.

    1. Invite as **Member** or **Administrator** from the drop-down according to your organization requirement.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options.
 
* Select **Test this application** in Microsoft Entra admin center. this option redirects to Blinq Sign-on URL where you can initiate the login flow.
 
* Go to Blinq Sign-on URL directly and initiate the login flow from there.
 
* You can use Microsoft My Apps. When you select the Blinq tile in the My Apps, this option redirects to Blinq Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Blinq you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
