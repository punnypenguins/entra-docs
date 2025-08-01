---
title: Configure Burp Suite Enterprise Edition for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Burp Suite Enterprise Edition.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Burp Suite Enterprise Edition so that I can control who has access to Burp Suite Enterprise Edition, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Burp Suite Enterprise Edition for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Burp Suite Enterprise Edition with Microsoft Entra ID. When you integrate Burp Suite Enterprise Edition with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Burp Suite Enterprise Edition.
* Enable your users to be automatically signed-in to Burp Suite Enterprise Edition with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Burp Suite Enterprise Edition single sign-on (SSO) enabled subscription.

> [!NOTE]
> This integration is also available to use from Microsoft Entra US Government Cloud environment. You can find this application in the Microsoft Entra US Government Cloud Application Gallery and configure it in the same way as you do from public cloud.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Burp Suite Enterprise Edition supports **IDP** initiated SSO.

* Burp Suite Enterprise Edition supports **Just In Time** user provisioning.

## Add Burp Suite Enterprise Edition from the gallery

To configure the integration of Burp Suite Enterprise Edition into Microsoft Entra ID, you need to add Burp Suite Enterprise Edition from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Burp Suite Enterprise Edition** in the search box.
1. Select **Burp Suite Enterprise Edition** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso-for-burp-suite-enterprise-edition'></a>

## Configure and test Microsoft Entra SSO for Burp Suite Enterprise Edition

Configure and test Microsoft Entra SSO with Burp Suite Enterprise Edition using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Burp Suite Enterprise Edition.

To configure and test Microsoft Entra SSO with Burp Suite Enterprise Edition, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Burp Suite Enterprise Edition SSO](#configure-burp-suite-enterprise-edition-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Burp Suite Enterprise Edition test user](#create-burp-suite-enterprise-edition-test-user)** - to have a counterpart of B.Simon in Burp Suite Enterprise Edition that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Burp Suite Enterprise Edition** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier** text box, type a URL using the following pattern:
    `https://<BURPSUITEDOMAIN:PORT>/saml`

    b. In the **Reply URL** text box, type a URL using the following pattern:
    `https://<BURPSUITEDOMAIN:PORT>/api-internal/saml/acs`

	> [!NOTE]
	> These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Burp Suite Enterprise Edition Client support team](mailto:support@portswigger.net) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. Burp Suite Enterprise Edition application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

	![image](common/edit-attribute.png)

1. In addition to above,  Burp Suite Enterprise Edition application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirement.

	| Name | Source Attribute|
	| ---------------| --------------- |    
	| Group | user.groups |

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/certificatebase64.png)

1. On the **Set up Burp Suite Enterprise Edition** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Burp Suite Enterprise Edition SSO

To configure single sign-on on **Burp Suite Enterprise Edition** side, you need to send the downloaded **Certificate (Base64)** and appropriate copied URLs from the application configuration to [Burp Suite Enterprise Edition support team](mailto:support@portswigger.net). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Burp Suite Enterprise Edition test user

In this section, a user called Britta Simon is created in Burp Suite Enterprise Edition. Burp Suite Enterprise Edition supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Burp Suite Enterprise Edition, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options.

* Select **Test this application**, and you should be automatically signed in to the Burp Suite Enterprise Edition for which you set up the SSO

* You can use Microsoft My Apps. When you select the Burp Suite Enterprise Edition tile in the My Apps, you should be automatically signed in to the Burp Suite Enterprise Edition for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Burp Suite Enterprise Edition you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
