---
title: Configure U.S. Bank Prepaid for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and U.S. Bank Prepaid.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and U.S. Bank Prepaid so that I can control who has access to U.S. Bank Prepaid, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure U.S. Bank Prepaid for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate U.S. Bank Prepaid with Microsoft Entra ID. When you integrate U.S. Bank Prepaid with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to U.S. Bank Prepaid.
* Enable your users to be automatically signed-in to U.S. Bank Prepaid with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* U.S. Bank Prepaid single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* U.S. Bank Prepaid supports **SP and IDP** initiated SSO.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add U.S. Bank Prepaid from the gallery

To configure the integration of U.S. Bank Prepaid into Microsoft Entra ID, you need to add U.S. Bank Prepaid from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **U.S. Bank Prepaid** in the search box.
1. Select **U.S. Bank Prepaid** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

<a name='configure-and-test-azure-ad-sso-for-us-bank-prepaid'></a>

## Configure and test Microsoft Entra SSO for U.S. Bank Prepaid

Configure and test Microsoft Entra SSO with U.S. Bank Prepaid using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in U.S. Bank Prepaid.

To configure and test Microsoft Entra SSO with U.S. Bank Prepaid, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure U.S. Bank Prepaid SSO](#configure-us-bank-prepaid-sso)** - to configure the single sign-on settings on application side.
    1. **[Create U.S. Bank Prepaid test user](#create-us-bank-prepaid-test-user)** - to have a counterpart of B.Simon in U.S. Bank Prepaid that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **U.S. Bank Prepaid** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.

1. On the **Basic SAML Configuration** section, if you wish to configure the application in **SP** initiated mode then perform the following steps:

    a. In the **Identifier** text box, type the value:
    `USBank:SAML2.0:Prepaid_SP`

    b. In the **Reply URL** text box, type the URL:
    `https://federation.usbank.com/sp/ACS.saml2`

    c. In the **Sign-on URL** text box, type the URL:
    `https://federation.usbank.com/sp/startSSO.ping?PartnerIdpId=<ID>`

    > [!NOTE]
    > The Sign-on URL value isn't real. Update this value with the actual Sign-on URL. Contact [U.S. Bank Prepaid Client support team](mailto:web.access.management@usbank.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
    
1. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![The Certificate download link](common/copy-metadataurl.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure U.S. Bank Prepaid SSO

To configure single sign-on on **U.S. Bank Prepaid** side, you need to send the **App Federation Metadata Url** to [U.S. Bank Prepaid support team](mailto:web.access.management@usbank.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create U.S. Bank Prepaid test user

In this section, you create a user called Britta Simon in U.S. Bank Prepaid. Work with [U.S. Bank Prepaid support team](mailto:web.access.management@usbank.com) to add the users in the U.S. Bank Prepaid platform. Users must be created and activated before you use single sign-on.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to U.S. Bank Prepaid Sign on URL where you can initiate the login flow.  

* Go to U.S. Bank Prepaid Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the U.S. Bank Prepaid for which you set up the SSO. 

You can also use Microsoft My Apps to test the application in any mode. When you select the U.S. Bank Prepaid tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the U.S. Bank Prepaid for which you set up the SSO. For more information, see [Microsoft Entra My Apps](/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure U.S. Bank Prepaid you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).
