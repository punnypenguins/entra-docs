---
title: Configure Banyan Security Zero Trust Remote Access Platform for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Banyan Security Zero Trust Remote Access Platform.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Banyan Security Zero Trust Remote Access Platform so that I can control who has access to Banyan Security Zero Trust Remote Access Platform, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Banyan Security Zero Trust Remote Access Platform for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Banyan Security Zero Trust Remote Access Platform with Microsoft Entra ID. When you integrate Banyan Security Zero Trust Remote Access Platform with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Banyan Security Zero Trust Remote Access Platform.
* Enable your users to be automatically signed-in to Banyan Security Zero Trust Remote Access Platform with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Banyan Security Zero Trust Remote Access Platform single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Banyan Security Zero Trust Remote Access Platform supports **SP and IDP** initiated SSO.
* Banyan Security Zero Trust Remote Access Platform supports **Just In Time** user provisioning.

## Add Banyan Security Zero Trust Remote Access Platform from the gallery

To configure the integration of Banyan Security Zero Trust Remote Access Platform into Microsoft Entra ID, you need to add Banyan Security Zero Trust Remote Access Platform from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Banyan Security Zero Trust Remote Access Platform** in the search box.
1. Select **Banyan Security Zero Trust Remote Access Platform** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso-for-banyan-security-zero-trust-remote-access-platform'></a>

## Configure and test Microsoft Entra SSO for Banyan Security Zero Trust Remote Access Platform

Configure and test Microsoft Entra SSO with Banyan Security Zero Trust Remote Access Platform using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Banyan Security Zero Trust Remote Access Platform.

To configure and test Microsoft Entra SSO with Banyan Security Zero Trust Remote Access Platform, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Banyan Security Zero Trust Remote Access Platform SSO](#configure-banyan-security-zero-trust-remote-access-platform-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Banyan Security Zero Trust Remote Access Platform test user](#create-banyan-security-zero-trust-remote-access-platform-test-user)** - to have a counterpart of B.Simon in Banyan Security Zero Trust Remote Access Platform that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Banyan Security Zero Trust Remote Access Platform** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following steps:

    a. In the **Identifier** text box, type a URL using the following pattern:
    `https://net.banyanops.com/api/v1/sso?orgname=<YOUR_ORG_NAME>`

    b. In the **Reply URL** text box, type a URL using the following pattern:
    `https://net.banyanops.com/api/v1/sso?orgname=<YOUR_ORG_NAME>`

1. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type a URL using the following pattern:
    `https://net.banyanops.com/api/v1/sso?orgname=<YOUR_ORG_NAME>`

	> [!NOTE]
	> These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Banyan Security Zero Trust Remote Access Platform Client support team](mailto:support@banyansecurity.io) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![The Certificate download link](common/copy-metadataurl.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Banyan Security Zero Trust Remote Access Platform SSO

1. Log in to your Banyan Security Zero Trust Remote Access Platform website as an administrator.

1. Go to **Admin Settings -> Admin Sign-on**.

1. Perform the following steps in the **Sign-on Settings** page.

    ![Screenshot for Sign-on Settings.](./media/banyan-command-center-tutorial/configuration.png)

    a. Select **Sign-On Method** as a **Single Sign On - SAML 2.0** from the dropdown.

    b. Copy **IDP Issuer** value, paste this value into the **Microsoft Entra Identifier** text box in the Basic SAML Configuration section.

    c. Paste the **App Federation Metadata Url** value in to the **IDP Metadata URL** textbox.

    d. Select the **Update** button.

### Create Banyan Security Zero Trust Remote Access Platform test user

In this section, a user called Britta Simon is created in Banyan Security Zero Trust Remote Access Platform. Banyan Security Zero Trust Remote Access Platform supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Banyan Security Zero Trust Remote Access Platform, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to Banyan Security Zero Trust Remote Access Platform Sign on URL where you can initiate the login flow.  

* Go to Banyan Security Zero Trust Remote Access Platform Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the Banyan Security Zero Trust Remote Access Platform for which you set up the SSO. 

You can also use Microsoft My Apps to test the application in any mode. When you select the Banyan Security Zero Trust Remote Access Platform tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Banyan Security Zero Trust Remote Access Platform for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Banyan Security Zero Trust Remote Access Platform you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
