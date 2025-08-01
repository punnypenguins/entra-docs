---
title: Configure MemoMeister for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and MemoMeister.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu

# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and MemoMeister so that I can control who has access to MemoMeister, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure MemoMeister for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate MemoMeister with Microsoft Entra ID. When you integrate MemoMeister with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to MemoMeister.
* Enable your users to be automatically signed-in to MemoMeister with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* MemoMeister single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* MemoMeister supports only **SP** initiated SSO.

## Add MemoMeister from the gallery

To configure the integration of MemoMeister into Microsoft Entra ID, you need to add MemoMeister from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **MemoMeister** in the search box.
1. Select **MemoMeister** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for MemoMeister

Configure and test Microsoft Entra SSO with MemoMeister using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in MemoMeister.

To configure and test Microsoft Entra SSO with MemoMeister, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure MemoMeister SSO](#configure-memomeister-sso)** - to configure the single sign-on settings on application side.
    1. **[Create MemoMeister test user](#create-memomeister-test-user)** - to have a counterpart of B.Simon in MemoMeister that's linked to the Microsoft Entra ID representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **MemoMeister** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier (Entity ID)** text box, type a URL:
    `urn:amazon:cognito:sp:eu-central-1_<ID>`

    b. In the **Reply URL** textbox, type the URL:
    `https://memomeister-production.auth.eu-central-1.amazoncognito.com/saml2/idpresponse`

    c. In the **Sign on URL** text box, type the URL:
    `https://web.memomeister.com/login`

    > [!NOTE]
	> The Identifier value isn't real. Update the value with the actual Identifier. Contact [MemoMeister support team](mailto:support@memomeister.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.

1. MemoMeister application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

	![Screenshot shows the image of attributes configuration.](common/default-attributes.png "Image")

1. In addition to above, MemoMeister application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
	
	| Name |   Source Attribute|
	| ---- | --------- |
	| address_city | user.city |
	| address_country | user.country |
	| mobile_phone | user.mobilephone |
	| telephone_number | user.telephonenumber |
	| address_streetaddress | user.streetaddress |
	| preferred_language | user.preferredlanguage |
	| address_postalcode | user.postalcode |
	| company_name | user.companyname |
	| groups | user.groups |    

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![Screenshot shows the Certificate download link.](common/copy-metadataurl.png "Certificate")

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure MemoMeister SSO

To configure single sign-on on **MemoMeister** side, you need to send the **App Federation Metadata Url** to [MemoMeister support team](mailto:support@memomeister.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create MemoMeister test user

In this section, you create a user called B.Simon in MemoMeister. Work with [MemoMeister support team](mailto:support@memomeister.com) to add the users in the MemoMeister platform. Users must be created and activated before you use single sign-on.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options.
 
* Select **Test this application** in Microsoft Entra admin center. This option redirects to MemoMeister Sign-on URL where you can initiate the login flow.
 
* Go to MemoMeister Sign-on URL directly and initiate the login flow from there.
 
* You can use Microsoft My Apps. When you select the MemoMeister tile in the My Apps, this option redirects to MemoMeister Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure MemoMeister you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
