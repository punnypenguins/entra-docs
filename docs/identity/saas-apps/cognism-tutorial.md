---
title: Configure Cognism for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Cognism.
author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Cognism so that I can control who has access to Cognism, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Cognism for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Cognism with Microsoft Entra ID. When you integrate Cognism with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Cognism.
* Enable your users to be automatically signed-in to Cognism with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Cognism single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Cognism supports only **IDP** initiated SSO.
* Cognism supports **Just In Time** user provisioning.

## Add Cognism from the gallery

To configure the integration of Cognism into Microsoft Entra ID, you need to add Cognism from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Cognism** in the search box.
1. Select **Cognism** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

[!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

## Configure and test Microsoft Entra SSO for Cognism

Configure and test Microsoft Entra SSO with Cognism using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Cognism.

To configure and test Microsoft Entra SSO with Cognism, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Cognism SSO](#configure-cognism-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Cognism test user](#create-cognism-test-user)** - to have a counterpart of B.Simon in Cognism that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Cognism** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier** text box, type a URL using one of the following patterns:

    |**Environment**|**URL**|
    |--------------|-------|
    |Production|`https://app.cognism.com/<ID>`|
    |Staging|`https://app-staging.cognism.com/<ID>`|
   
    b. In the **Reply URL** text box, type a URL using one of the following patterns:

    |**Environment**|**URL**|
    |---------------|-------|
    |Production|`https://app.cognism.com/api/users/sso/azureSamlResponse/<ID>`|
    |Staging|`https://app-staging.cognism.com/api/users/sso/azureSamlResponse/<ID>`|

	> [!NOTE]
	> These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Cognism support team](mailto:help@cognism.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

	![Screenshot shows the Certificate download link.](common/certificatebase64.png "Certificate")

1. On the **Set up Cognism** section, copy the appropriate URL(s) based on your requirement.

	![Screenshot shows to copy configuration URLs.](common/copy-configuration-urls.png "Metadata")

<a name='create-a-microsoft-entra-id-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Cognism SSO

1. Log in to Cognism company site as an administrator.

1. Go to **Settings** > **Single sign-on** > **Microsoft Azure** and select **Configure**.

    ![Screenshot shows Settings for the configuration.](./media/cognism-tutorial/settings.png "Settings")

1. In the **Microsoft Azure SSO Configuration** section, perform the following steps:

    ![Screenshot shows the Configuration.](./media/cognism-tutorial/configure.png "Configuration")

    1. Copy the **Identifier (Entity ID)** and paste it in the **Identifier (Entity ID)** textbox in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

    1. Copy the **ACS URL** and paste it in the **Reply URL** textbox in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

    1. In the **Entity ID** textbox, paste the **Microsoft Entra Identifier** which you have copied from the Microsoft Entra admin center.

    1. Open the downloaded **Certificate (Base64)** into Notepad and paste the content into the **X.509 Certificate** textbox.

    1. Select **Enable**.

### Create Cognism test user

In this section, a user called B.Simon is created in Cognism. Cognism supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Cognism, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options.
 
* Select Test this application in Microsoft Entra admin center and you should be automatically signed in to the Cognism for which you set up the SSO.
 
* You can use Microsoft My Apps. When you select the Cognism tile in the My Apps, you should be automatically signed in to the Cognism for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Cognism you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
