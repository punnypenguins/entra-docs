---
title: Configure Alcumus Info Exchange for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Alcumus Info Exchange.

author: nguhiu
manager: mwongerapk
ms.reviewer: celested
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu

# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Alcumus Info Exchange so that I can control who has access to Alcumus Info Exchange, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---
# Configure Alcumus Info Exchange for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Alcumus Info Exchange with Microsoft Entra ID. When you integrate Alcumus Info Exchange with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Alcumus Info Exchange.
* Enable your users to be automatically signed-in to Alcumus Info Exchange with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Alcumus Info Exchange single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra single sign-on in a test environment.

* Alcumus Info Exchange supports **IDP** initiated SSO.

## Add Alcumus Info Exchange from the gallery

To configure the integration of Alcumus Info Exchange into Microsoft Entra ID, you need to add Alcumus Info Exchange from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Alcumus Info Exchange** in the search box.
1. Select **Alcumus Info Exchange** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso-for-alcumus-info-exchange'></a>

## Configure and test Microsoft Entra SSO for Alcumus Info Exchange

Configure and test Microsoft Entra SSO with Alcumus Info Exchange using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Alcumus Info Exchange.

To configure and test Microsoft Entra SSO with Alcumus Info Exchange, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Alcumus Info Exchange SSO](#configure-alcumus-info-exchange-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Alcumus Info Exchange test user](#create-alcumus-info-exchange-test-user)** - to have a counterpart of B.Simon in Alcumus Info Exchange that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Alcumus Info Exchange** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Set up Single Sign-On with SAML** page, perform the following steps:

    a. In the **Identifier** text box, type a URL using the following pattern:
    `https://<SUBDOMAIN>.info-exchange.com`

    b. In the **Reply URL** text box, type a URL using the following pattern:
    `https://<SUBDOMAIN>.info-exchange.com/Auth/`

    > [!NOTE]
    > These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Alcumus Info Exchange Client support team](mailto:helpdesk@alcumusgroup.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

    ![The Certificate download link](common/metadataxml.png)

1. On the **Set up Alcumus Info Exchange** section, copy the appropriate URL(s) as per your requirement.

    ![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Alcumus Info Exchange SSO

To configure single sign-on on **Alcumus Info Exchange** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Alcumus Info Exchange support team](mailto:helpdesk@alcumusgroup.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Alcumus Info Exchange test user

In this section, you create a user called Britta Simon in Alcumus Info Exchange. Work with [Alcumus Info Exchange support team](mailto:helpdesk@alcumusgroup.com) to add the users in the Alcumus Info Exchange platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

* Select **Test this application**, and you should be automatically signed in to the Alcumus Info Exchange for which you set up the SSO.

* You can use Microsoft My Apps. When you select the Alcumus Info Exchange tile in the My Apps, you should be automatically signed in to the Alcumus Info Exchange for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Alcumus Info Exchange you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad).
