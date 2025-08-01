---
title: Configure Timeclock 365 SAML for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Timeclock 365 SAML.
author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Timeclock 365 SAML so that I can control who has access to Timeclock 365 SAML, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Timeclock 365 SAML for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Timeclock 365 SAML with Microsoft Entra ID. When you integrate Timeclock 365 SAML with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Timeclock 365 SAML.
* Enable your users to be automatically signed-in to Timeclock 365 SAML with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Timeclock 365 SAML single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Timeclock 365 SAML supports **SP** initiated SSO.
* Timeclock 365 SAML supports [Automated user provisioning](timeclock-365-saml-provisioning-tutorial.md).

## Adding Timeclock 365 SAML from the gallery

To configure the integration of Timeclock 365 SAML into Microsoft Entra ID, you need to add Timeclock 365 SAML from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Timeclock 365 SAML** in the search box.
1. Select **Timeclock 365 SAML** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

<a name='configure-and-test-azure-ad-sso-for-timeclock-365-saml'></a>

## Configure and test Microsoft Entra SSO for Timeclock 365 SAML

Configure and test Microsoft Entra SSO with Timeclock 365 SAML using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Timeclock 365 SAML.

To configure and test Microsoft Entra SSO with Timeclock 365 SAML, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Timeclock 365 SAML SSO](#configure-timeclock-365-saml-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Timeclock 365 SAML test user](#create-timeclock-365-saml-test-user)** - to have a counterpart of B.Simon in Timeclock 365 SAML that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Timeclock 365 SAML** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, enter the values for the following fields:

    In the **Sign-on URL** text box, type the URL:
    `https://live.timeclock365.com/login`


1. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![The Certificate download link](common/copy-metadataurl.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Timeclock 365 SAML SSO




1. In a different web browser window, sign in to your up Timeclock 365 SAML company site as an administrator

1. Perform the below mentioned steps.

    ![Timeclock configuration](./media/timeclock-365-saml-tutorial/saml-configuration.png)

    a. Go to the **Settings > Company profile > Settings** tab.

    b. In the **IDP metadata path**, paste the **App Federation Metadata Url** that you copied previously.

    c. Then, select **Update**.

### Create Timeclock 365 SAML test user

1. Open a new tab in your browser, and sign in to your Timeclock 365 SAML company site as an administrator.

1. Go to the **Users > Add new user**.

    ![Create test user1](./media/timeclock-365-saml-tutorial/add-user-1.png)

1. Provide all the required information  in the **User information** page and select **Save**.

    ![Create test user2](./media/timeclock-365-saml-tutorial/add-user-2.png)

1. Select **Create** button to create the test user.

> [!NOTE]
> Timeclock 365 SAML also supports automatic user provisioning, you can find more details [here](./timeclock-365-saml-provisioning-tutorial.md) on how to configure automatic user provisioning.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Timeclock 365 SAML Sign-on URL where you can initiate the login flow. 

* Go to Timeclock 365 SAML Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Timeclock 365 SAML tile in the My Apps, this option redirects to Timeclock 365 SAML Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Timeclock 365 SAML you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
