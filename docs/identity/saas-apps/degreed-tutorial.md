---
title: Configure Degreed for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Degreed.

author: nguhiu
manager: mwongerapk
ms.reviewer: celested
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu

# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Degreed so that I can control who has access to Degreed, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---
# Configure Degreed for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Degreed with Microsoft Entra ID. When you integrate Degreed with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Degreed.
* Enable your users to be automatically signed-in to Degreed with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Degreed single sign-on (SSO) enabled subscription.

> [!NOTE]
> This integration is also available to use from Microsoft Entra US Government Cloud environment. You can find this application in the Microsoft Entra US Government Cloud Application Gallery and configure it in the same way as you do from public cloud.

## Scenario description

In this article,  you configure and test Microsoft Entra single sign-on in a test environment.

* Degreed supports **SP** initiated SSO.

* Degreed supports **Just In Time** user provisioning.

## Add Degreed from the gallery

To configure the integration of Degreed into Microsoft Entra ID, you need to add Degreed from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Degreed** in the search box.
1. Select **Degreed** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso'></a>

## Configure and test Microsoft Entra SSO

Configure and test Microsoft Entra SSO with Degreed using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Degreed.

To configure and test Microsoft Entra SSO with Degreed, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Degreed SSO](#configure-degreed-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Degreed test user](#create-degreed-test-user)** - to have a counterpart of B.Simon in Degreed that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Degreed** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, perform the following steps:

	a. In the **Sign on URL** text box, type a URL using the following pattern:
    `https://degreed.com/?orgsso=<company code>`

    b. In the **Identifier (Entity ID)** text box, type a URL using the following pattern:
    `https://degreed.com/<instancename>`

    c. In the **Reply URL** text box, type a URL using the following pattern:
    `https://degreed.com/SAML/<instancename>`
	
	> [!NOTE]
	> These values aren't real. Update these values with the actual Sign-on URL, Identifier and Reply URL. Contact [Degreed Client support team](mailto:admin@degreed.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

6. On the **Set up Degreed** section, copy the appropriate URL(s) as per your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

### Configure Degreed SSO

To configure single sign-on on **Degreed** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Degreed support team](mailto:sso@degreed.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Degreed test user

In this section, a user called B.Simon is created in Degreed. Degreed supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Degreed, a new one is created after authentication.

> [!NOTE]
> If you need to create a user manually, you need to contact the [Degreed support team](mailto:sso@degreed.com).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Degreed Sign-on URL where you can initiate the login flow. 

* Go to Degreed Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Degreed tile in the My Apps, this option redirects to Degreed Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Degreed you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad).
