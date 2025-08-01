---
title: Configure Synerise AI Growth Operating System for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Synerise AI Growth Operating System.
author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Synerise AI Growth Operating System so that I can control who has access to Synerise AI Growth Operating System, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Synerise AI Growth Operating System for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Synerise with Microsoft Entra ID. When you integrate Synerise with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Synerise.
* Enable your users to be automatically signed-in to Synerise with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Synerise single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Synerise supports **SP and IDP** initiated SSO
* Synerise supports **Just In Time** user provisioning

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.


## Adding Synerise AI Growth Operating System from the gallery

To configure the integration of Synerise into Microsoft Entra ID, you need to add Synerise from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Synerise AI Growth Operating System** in the search box.
1. Select **Synerise AI Growth Operating System** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)


<a name='configure-and-test-azure-ad-sso-for-synerise-ai-growth-operating-system'></a>

## Configure and test Microsoft Entra SSO for Synerise AI Growth Operating System

Configure and test Microsoft Entra SSO with Synerise using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Synerise.

To configure and test Microsoft Entra SSO with Synerise, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Synerise AI Growth Operating System SSO](#configure-synerise-ai-growth-operating-system-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Synerise AI Growth Operating System test user](#create-synerise-ai-growth-operating-system-test-user)** - to have a counterpart of B.Simon in Synerise that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Synerise AI Growth Operating System** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

    In the **Reply URL** text box, type a URL using the following pattern:
    `https://app.synerise.com/api-portal/uauth/saml/auth/<PROFILE_HASH>`

1. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type a URL using the following pattern:
    `https://app.synerise.com/api-portal/uauth/saml/auth/<PROFILE_HASH>`

	> [!NOTE]
	> These values aren't real. Update these values with the actual Reply URL and Sign-on URL. Contact [Synerise support team](mailto:support@synerise.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/certificatebase64.png)

1. On the **Set up Synerise** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)
<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Synerise AI Growth Operating System SSO

1. Log in to the Synerise as an administrator.

1. Go to the **Settings > Access Control**.

    ![Synerise settings](./media/synerise-ai-growth-ecosystem-tutorial/settings.png)

1. In the **Access Control** page, select **Show** button in the **Single Sign-On** tab.

    ![Synerise Access Control](./media/synerise-ai-growth-ecosystem-tutorial/single-sign-on.png)

1. Perform the following steps in the below page.

    ![Synerise configuration](./media/synerise-ai-growth-ecosystem-tutorial/configuration.png)

    a. In the **Identifier Provider Entity ID** textbox, paste the **Microsoft Entra Identifier** value which you copied previously.

    b. In the **SSO endpoint(https)** textbox, paste the **Login URL** value which you copied previously.

    c. In the **Identity Provider application ID** textbox, paste the **application ID** value.

    d. Copy **Service Provider redirect URI** value, paste this value into the **Reply URL** text box in the Basic SAML Configuration section.

    e. Select **HTTP REDIRECT** in the **Request binding**.

    f. Switch on the **Request signature**.

    g. Upload the downloaded **Certificate(Base64)** file in to the **Identity Provider Signature Certificate**.

    i. Select **Apply**.

### Create Synerise AI Growth Operating System test user

In this section, a user called Britta Simon is created in Synerise. Synerise supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Synerise, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to Synerise Sign on URL where you can initiate the login flow.  

* Go to Synerise Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the Synerise for which you set up the SSO 

You can also use Microsoft My Apps to test the application in any mode. When you select the Synerise tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Synerise for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).


## Related content

Once you configure Synerise you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
