---
title: Configure Accenture Academy for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Accenture Academy.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Accenture Academy so that I can control who has access to Accenture Academy, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Accenture Academy for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Accenture Academy with Microsoft Entra ID. When you integrate Accenture Academy with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Accenture Academy.
* Enable your users to be automatically signed-in to Accenture Academy with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Accenture Academy single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Accenture Academy supports **SP and IDP** initiated SSO
* Accenture Academy supports **Just In Time** user provisioning

## Adding Accenture Academy from the gallery

To configure the integration of Accenture Academy into Microsoft Entra ID, you need to add Accenture Academy from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Accenture Academy** in the search box.
1. Select **Accenture Academy** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]


<a name='configure-and-test-azure-ad-sso-for-accenture-academy'></a>

## Configure and test Microsoft Entra SSO for Accenture Academy

Configure and test Microsoft Entra SSO with Accenture Academy using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Accenture Academy.

To configure and test Microsoft Entra SSO with Accenture Academy, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Accenture Academy SSO](#configure-accenture-academy-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Accenture Academy test user](#create-accenture-academy-test-user)** - to have a counterpart of B.Simon in Accenture Academy that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Accenture Academy** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

    a. In the **Identifier** text box, type a URL using the following pattern:
    `https://www.accentureacademy.com/a/integration/saml_sso/<Customer ID>/`

    b. In the **Reply URL** text box, type a URL using the following pattern:
    `https://www.accentureacademy.com/a/integration/saml_sso/<Customer ID>/acs/`

1. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type a URL using the following pattern:
    `https://www.accentureacademy.com/a/integration/saml_sso/<Customer ID>/request_idp_auth/`

	> [!NOTE]
	> These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Accenture Academy Client support team](mailto:support@accentureacademy.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

1. On the **Set up Accenture Academy** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)
<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Accenture Academy SSO

To configure single sign-on on **Accenture Academy** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Accenture Academy support team](mailto:support@accentureacademy.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Accenture Academy test user

In this section, a user called Britta Simon is created in Accenture Academy. Accenture Academy supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Accenture Academy, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to Accenture Academy Sign on URL where you can initiate the login flow.  

* Go to Accenture Academy Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the Accenture Academy for which you set up the SSO 

You can also use Microsoft My Apps to test the application in any mode. When you select the Accenture Academy tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Accenture Academy for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Accenture Academy you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
