---
title: Configure Lucid (All Products) for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Lucid (All Products).

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Lucid (All Products) so that I can control who has access to Lucid (All Products), enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Lucid (All Products) for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Lucid (All Products) with Microsoft Entra ID. When you integrate Lucid (All Products) with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Lucid (All Products).
* Enable your users to be automatically signed-in to Lucid (All Products) with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Lucid (All Products) single sign-on (SSO) enabled subscription.

> [!NOTE]
> This integration is also available to use from Microsoft Entra US Government Cloud environment. You can find this application in the Microsoft Entra US Government Cloud Application Gallery and configure it in the same way as you do from public cloud.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Lucid (All Products) supports **SP and IDP** initiated SSO.
* Lucid (All Products) supports **Just In Time** user provisioning.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Lucid (All Products) from the gallery

To configure the integration of Lucid (All Products) into Microsoft Entra ID, you need to add Lucid (All Products) from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Lucid (All Products)** in the search box.
1. Select **Lucid (All Products)** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

<a name='configure-and-test-azure-ad-sso-for-lucid-all-products'></a>

## Configure and test Microsoft Entra SSO for Lucid (All Products)

Configure and test Microsoft Entra SSO with Lucid (All Products) using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Lucid (All Products).

To configure and test Microsoft Entra SSO with Lucid (All Products), perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Lucid (All Products) SSO](#configure-lucid-all-products-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Lucid (All Products) test user](#create-lucid-all-products-test-user)** - to have a counterpart of B.Simon in Lucid (All Products) that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Lucid (All Products)** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following step:

    In the **Reply URL** text box, type a URL using the following pattern:
    `https://lucid.app/saml/sso/<TENANT_NAME>?idpHash=<HASH_ID>`

1. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type a URL using the following pattern:
    `https://lucid.app/saml/sso/<TENANT_NAME>?idpHash=<HASH_ID>`

	> [!NOTE]
	> These values aren't real. Update these values with the actual Reply URL and Sign-On URL. Contact [Lucid (All Products) Client support team](mailto:support@lucidchart.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

1. On the **Set up Lucid (All Products)** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Lucid (All Products) SSO

To configure single sign-on on **Lucid (All Products)** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Lucid (All Products) support team](mailto:support@lucidchart.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Lucid (All Products) test user

In this section, a user called Britta Simon is created in Lucid (All Products). Lucid (All Products) supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Lucid (All Products), a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to the Lucid (All Products) sign-on URL where you can initiate the login flow.  

* Go to Lucid (All Products) Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the Lucid (All Products) for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Lucid (All Products) tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Lucid (All Products) for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Lucid (All Products) you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
