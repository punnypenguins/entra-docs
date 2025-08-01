---
title: Configure Ocurus for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Ocurus.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu

# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Ocurus so that I can control who has access to Ocurus, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Ocurus for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Ocurus with Microsoft Entra ID. When you integrate Ocurus with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Ocurus.
* Enable your users to be automatically signed-in to Ocurus with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Ocurus single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Ocurus supports only **SP** initiated SSO.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Ocurus from the gallery

To configure the integration of Ocurus into Microsoft Entra ID, you need to add Ocurus from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Ocurus** in the search box.
1. Select **Ocurus** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

[!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

## Configure and test Microsoft Entra SSO for Ocurus

Configure and test Microsoft Entra SSO with Ocurus using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Ocurus.

To configure and test Microsoft Entra SSO with Ocurus, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Ocurus SSO](#configure-ocurus-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Ocurus test user](#create-ocurus-test-user)** - to have a counterpart of B.Simon in Ocurus that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Ocurus** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier (Entity ID)** text box, type the URL:
    `https://solarturbines.ocurus.com/saml2/ms/metadata`

    b. In the **Reply URL** text box, type the URL:
    `https://solarturbines.ocurus.com/saml2/ms/acs`

    c. In the **Sign on URL** text box, type the URL:
    `https://solarturbines.ocurus.com/sso-ms`

1. Ocurus application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

	![Screenshot shows the image of attributes configuration.](common/default-attributes.png "Image")

1. In addition to above, Ocurus application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
	
	| Name |  Source Attribute|
	| -----| ---------------- |
	| catcupid | user.employeeid |

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![Screenshot shows the Certificate download link.](common/copy-metadataurl.png "Certificate")

<a name='create-a-microsoft-entra-id-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Ocurus SSO

To configure single sign-on on **Ocurus** side, you need to send the **App Federation Metadata Url** to [Ocurus support team](mailto:support@ocurus.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Ocurus test user

In this section, you create a user called B.Simon in Ocurus. Work with [Ocurus support team](mailto:support@ocurus.com) to add the users in the Ocurus platform. Users must be created and activated before you use single sign-on.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options.
 
* Select **Test this application** in Microsoft Entra admin center. this option redirects to Ocurus Sign-on URL where you can initiate the login flow.
 
* Go to Ocurus Sign-on URL directly and initiate the login flow from there.
 
* You can use Microsoft My Apps. When you select the Ocurus tile in the My Apps, this option redirects to Ocurus Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Ocurus you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
