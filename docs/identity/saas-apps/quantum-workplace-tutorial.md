---
title: Configure Quantum Workplace for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Quantum Workplace.

author: nguhiu
manager: mwongerapk
ms.reviewer: celested
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu

# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Quantum Workplace so that I can control who has access to Quantum Workplace, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---
# Configure Quantum Workplace for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Quantum Workplace with Microsoft Entra ID. When you integrate Quantum Workplace with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Quantum Workplace.
* Enable your users to be automatically signed-in to Quantum Workplace with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Quantum Workplace single sign-on enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra single sign-on in a test environment.

* Quantum Workplace supports **SP and IDP** initiated SSO.

## Add Quantum Workplace from the gallery

To configure the integration of Quantum Workplace into Microsoft Entra ID, you need to add Quantum Workplace from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Quantum Workplace** in the search box.
1. Select **Quantum Workplace** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

<a name='configure-and-test-azure-ad-sso-for-quantum-workplace'></a>

## Configure and test Microsoft Entra SSO for Quantum Workplace

Configure and test Microsoft Entra SSO with Quantum Workplace using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Quantum Workplace.

To configure and test Microsoft Entra SSO with Quantum Workplace, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Quantum Workplace SSO](#configure-quantum-workplace-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Quantum Workplace test user](#create-quantum-workplace-test-user)** - to have a counterpart of B.Simon in Quantum Workplace that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Quantum Workplace** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, the application is pre-configured and the necessary URLs are already pre-populated with Azure. The user needs to save the configuration by selecting the **Save** button.

5. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type the URL:
    `https://auth.quantumworkplace.com/Account/Login`

6. On the **Set up Single Sign-On with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

	![The Certificate download link](common/copy-metadataurl.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Quantum Workplace SSO

To configure single sign-on on **Quantum Workplace** side, you need to send the **App Federation Metadata Url** to [Quantum Workplace support team](mailto:support@quantumworkplace.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Quantum Workplace test user

In this section, you create a user called Britta Simon in Quantum Workplace. Work with [Quantum Workplace support team](mailto:support@quantumworkplace.com) to add the users in the Quantum Workplace platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to Quantum Workplace Sign on URL where you can initiate the login flow.  

* Go to Quantum Workplace Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the Quantum Workplace for which you set up the SSO. 

You can also use Microsoft My Apps to test the application in any mode. When you select the Quantum Workplace tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Quantum Workplace for which you set up the SSO. For more information, see [Microsoft Entra My Apps](/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Quantum Workplace you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).
