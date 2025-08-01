---
title: Configure Contentkalender for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Contentkalender.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 08/20/2024
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Contentkalender so that I can control who has access to Contentkalender, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Contentkalender for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Contentkalender with Microsoft Entra ID. When you integrate Contentkalender with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Contentkalender.
* Enable your users to be automatically signed-in to Contentkalender with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

* A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* Contentkalender single sign-on (SSO) enabled subscription (contact Contentkalender [customer service](mailto:info@contentkalender.nl)).
* Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID.
For more information, see [Azure built-in roles](~/identity/role-based-access-control/permissions-reference.md).

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Contentkalender supports **SP** initiated SSO.
* Contentkalender supports **Just In Time** user provisioning.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Contentkalender from the gallery

To configure the integration of Contentkalender into Microsoft Entra ID, you need to add Contentkalender from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Contentkalender** in the search box.
1. Select **Contentkalender** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso-for-contentkalender'></a>

## Configure and test Microsoft Entra SSO for Contentkalender

Configure and test Microsoft Entra SSO with Contentkalender using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Contentkalender.

To configure and test Microsoft Entra SSO with Contentkalender, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Contentkalender SSO](#configure-contentkalender-sso)** - to configure the single sign-on settings on application side.
   1. **[Create Contentkalender test user](#create-contentkalender-test-user)** - to have a counterpart of B.Simon in Contentkalender that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Contentkalender** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the URL:
    `https://db.contentkalender.app` 

   b. In the **Reply URL** text box, type the URL:
   `https://db.contentkalender.app/api:TRiyKmLW:production/sso/callback`
   
   c. In the **Sign on URL** text box, type the URL:
   `https://contentkalender.app`

   d. In the **Logout URL** text box, type the URL:
   `https://db.contentkalender.app/api:TRiyKmLW:production/sso/logout`

1. Your Contentkalender application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows an example for this. The default value of **Unique User Identifier** is **user.userprincipalname** but Contentkalender expects this to be mapped with the user's email address. For that you can use **user.mail** attribute from the list or use the appropriate attribute value based on your organization configuration.

	![Screenshot shows the image of attribute mappings.](common/default-attributes.png "Attributes")

1. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![Screenshot shows the Certificate download link.](common/copy-metadataurl.png "Certificate")

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Contentkalender SSO

To configure single sign-on on **Contentkalender** side, you need to send the **App Federation Metadata Url** to [Contentkalender support team](mailto:info@contentkalender.nl). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Contentkalender test user

In this section, a user called B.Simon is created in Contentkalender. Contentkalender supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Contentkalender, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Contentkalender Sign-on URL where you can initiate the login flow. 

* Go to Contentkalender Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Contentkalender tile in the My Apps, this option redirects to Contentkalender Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Contentkalender you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
