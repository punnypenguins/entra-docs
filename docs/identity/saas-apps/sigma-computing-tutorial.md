---
title: Configure Sigma Computing for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Sigma Computing.
author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Sigma Computing so that I can control who has access to Sigma Computing, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Sigma Computing for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Sigma Computing with Microsoft Entra ID. When you integrate Sigma Computing with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Sigma Computing.
* Enable your users to be automatically signed-in to Sigma Computing with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Sigma Computing single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Sigma Computing supports **SP and IDP** initiated SSO.
* Sigma Computing supports **Just In Time** user provisioning.
* Sigma Computing supports [Automated user provisioning](sigma-computing-provisioning-tutorial.md).

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding Sigma Computing from the gallery

To configure the integration of Sigma Computing into Microsoft Entra ID, you need to add Sigma Computing from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Sigma Computing** in the search box.
1. Select **Sigma Computing** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

<a name='configure-and-test-azure-ad-sso-for-sigma-computing'></a>

## Configure and test Microsoft Entra SSO for Sigma Computing

Configure and test Microsoft Entra SSO with Sigma Computing using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Sigma Computing.

To configure and test Microsoft Entra SSO with Sigma Computing, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Sigma Computing SSO](#configure-sigma-computing-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Sigma Computing test user](#create-sigma-computing-test-user)** - to have a counterpart of B.Simon in Sigma Computing that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Sigma Computing** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.

1. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type a URL using one of the following patterns:

	| Sign-on URL |
	|------------|
	| `https://app.sigmacomputing.com/<CustomerOrg>`|
	| `https://aws.sigmacomputing.com/<CustomerOrg>`|

    > [!NOTE]
	> The value isn't real. Update the value with the actual Sign-on URL. Contact [Sigma Computing Client support team](mailto:support@sigmacomputing.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. Select **Save**.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/certificatebase64.png)

1. On the **Set up Sigma Computing** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Sigma Computing SSO

1. Log in to your Sigma account.

1. Navigate to the **Admin Portal** by selecting **Administration** from the user menu.

1. Perform the following steps in the below page.

	![Configure Sigma Computing SSO section](./media/sigma-computing-tutorial/authentication.png)

	a. Select the **Authentication** page from the left panel.

	b. Under **Authentication Method**, select **SAML** or **SAML or password**.

	c. In the **Identity provider login URL** textbox, paste the **Login URL** value which you copied previously.

	d. Open the downloaded **Certificate (Base64)** into Notepad and paste the content into the **Identity Provider X509 certificate** textbox.

	e.  Select **Save**.

### Create Sigma Computing test user

In this section, a user called Britta Simon is created in Sigma Computing. Sigma Computing supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Sigma Computing, a new one is created after authentication.

Sigma Computing also supports automatic user provisioning, you can find more details [here](./sigma-computing-provisioning-tutorial.md) on how to configure automatic user provisioning.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to Sigma Computing Sign on URL where you can initiate the login flow.  

* Go to Sigma Computing Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the Sigma Computing for which you set up the SSO 

You can also use Microsoft My Apps to test the application in any mode. When you select the Sigma Computing tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Sigma Computing for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Sigma Computing you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
