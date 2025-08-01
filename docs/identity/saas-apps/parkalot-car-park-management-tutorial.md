---
title: Configure Parkalot - Car park management for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Parkalot - Car park management.
author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Parkalot - Car park management so that I can control who has access to Parkalot - Car park management, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Parkalot - Car park management for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Parkalot - Car park management with Microsoft Entra ID. When you integrate Parkalot - Car park management with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Parkalot - Car park management.
* Enable your users to be automatically signed-in to Parkalot - Car park management with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Parkalot - Car park management single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Parkalot - Car park management supports **SP** initiated SSO

* Parkalot - Car park management supports **Just In Time** user provisioning

## Adding Parkalot - Car park management from the gallery

To configure the integration of Parkalot - Car park management into Microsoft Entra ID, you need to add Parkalot - Car park management from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Parkalot - Car park management** in the search box.
1. Select **Parkalot - Car park management** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)


<a name='configure-and-test-azure-ad-sso-for-parkalot---car-park-management'></a>

## Configure and test Microsoft Entra SSO for Parkalot - Car park management

Configure and test Microsoft Entra SSO with Parkalot - Car park management using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Parkalot - Car park management.

To configure and test Microsoft Entra SSO with Parkalot - Car park management, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Parkalot-Car park management SSO](#configure-parkalot-car-park-management-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Parkalot-Car park management test user](#create-parkalot-car-park-management-test-user)** - to have a counterpart of B.Simon in Parkalot - Car park management that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Parkalot - Car park management** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, enter the values for the following fields:

    a. In the **Identifier (Entity ID)** text box, type a URL using one of the following patterns:

    | Identifier (Entity ID) |
    | -------------- |
    | `https://parkalot.io` |
    | `https://<CUSTOMERNAME>.parkalot.io` |
    |

    b. In the **Reply URL** text box, type a URL using one of the following patterns:

    | Reply URL |
    | -------------- |
    | `https://<CUSTOMERNAME>.parkalot.io` |
    | `https://parkalot-saml.firebaseapp.com/__/auth/handler` |
    | `https://parkalot-saml.web.app/__/auth/handler` |
    | `https://<CustomerName>.parkalot.io/__/auth/handler` |
    |

    c. In the **Sign-on URL** text box, type a URL using one of the following patterns:

    | Sign-on URL |
    | -------------- |
    | `https://<CUSTOMERNAME>.parkalot.io/#/login` |
    | `https://parkalot-saml.firebaseapp.com/#/login` |
    | `https://parkalot-saml.web.app/#/login` |
    |

	> [!NOTE]
	> These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Parkalot - Car park management Client support team](mailto:contact-us@parkalot.io) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/certificatebase64.png)

1. On the **Set up Parkalot - Car park management** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Parkalot-Car park management SSO

1. In a different web browser window, sign in to your Parkalot - Car park management company site as an administrator.

1. Select **Setup SAML** and select the **Edit** icon on **Add New** card.

    ![Add New EDIT icon.](./media/parkalot-car-park-management-tutorial/setup-saml.png)

1. Perform the below mentioned steps in the following page.

    ![Configure Parkalot - Car park management SSO.](./media/parkalot-car-park-management-tutorial/configuration.png)

    a. In the **Display Name** textbox, give a valid name to it.

    b. In the **IdP Entity ID** textbox, paste the **Microsoft Entra Identifier** value, which you copied previously.

    c. In the **SSO url** textbox, paste the **Login URL** value, which you copied previously.

    d. Open the downloaded **Certificate (Base64)** into Notepad and paste the content into the **Certificate** textbox.

    e. Select **SAVE**.

### Create Parkalot-Car park management test user

In this section, a user called Britta Simon is created in Parkalot - Car park management. Parkalot - Car park management supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Parkalot - Car park management, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Parkalot - Car park management Sign-on URL where you can initiate the login flow. 

* Go to Parkalot - Car park management Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Parkalot - Car park management tile in the My Apps, this option redirects to Parkalot - Car park management Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).


## Related content

Once you configure Parkalot - Car park management you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
