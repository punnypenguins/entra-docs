---
title: Configure Planview Admin for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Planview Admin.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Planview Admin so that I can control who has access to Planview Admin, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Planview Admin for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Planview Admin with Microsoft Entra ID. When you integrate Planview Admin with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Planview Admin.
* Enable your users to be automatically signed-in to Planview Admin with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

* A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* Planview Admin single sign-on (SSO) enabled subscription.
* Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID.
For more information, see [Azure built-in roles](~/identity/role-based-access-control/permissions-reference.md).

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Planview Admin supports **SP** and **IDP** initiated SSO.

## Add Planview Admin from the gallery

To configure the integration of Planview Admin into Microsoft Entra ID, you need to add Planview Admin from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Planview Admin** in the search box.
1. Select **Planview Admin** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

<a name='configure-and-test-azure-ad-sso-for-planview-admin'></a>

## Configure and test Microsoft Entra SSO for Planview Admin

Configure and test Microsoft Entra SSO with Planview Admin using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Planview Admin.

To configure and test Microsoft Entra SSO with Planview Admin, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Planview Admin SSO](#configure-planview-admin-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Planview Admin test user](#create-planview-admin-test-user)** - to have a counterpart of B.Simon in Planview Admin that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Planview Admin** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier** textbox, type a URL using the following pattern:
    `https://id.planview.com/<EntityID>`

    b. In the **Reply URL** textbox, type a URL using the following pattern:
    `https://<Region>.id.planview.com/api/loginsso/callback`

1. Perform the following step, if you wish to configure the application in **SP** initiated mode:    

    In the **Sign-on URL** text box, type a URL using the following pattern:
    `https://<Region>.id.planview.com`

    > [!Note]
    > These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Planview Admin support team](mailto:jordan.nguyen@planview.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![Screenshot shows the Certificate download link.](common/copy-metadataurl.png "Certificate")

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Planview Admin SSO

To configure single sign-on on **Planview Admin** side, you need to send the **App Federation Metadata Url** to [Planview Admin support team](mailto:jordan.nguyen@planview.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Planview Admin test user

In this section, you create a user called Britta Simon in Planview Admin. Work with [Planview Admin support team](mailto:jordan.nguyen@planview.com) to add the users in the Planview Admin platform. Users must be created and activated before you use single sign-on.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to Planview Admin Sign-on URL where you can initiate the login flow.  

* Go to Planview Admin Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the Planview Admin for which you set up the SSO. 

You can also use Microsoft My Apps to test the application in any mode. When you select the Planview Admin tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Planview Admin for which you set up the SSO. For more information, see [Microsoft Entra My Apps](/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Planview Admin you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).
