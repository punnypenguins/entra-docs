---
title: Configure SeattleTimesSSO for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and SeattleTimesSSO.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and SeattleTimesSSO so that I can control who has access to SeattleTimesSSO, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure SeattleTimesSSO for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SeattleTimesSSO with Microsoft Entra ID. This is the Institutional Subscription SSO for The Seattle Times. When you integrate SeattleTimesSSO with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to SeattleTimesSSO.
* Enable your users to be automatically signed-in to SeattleTimesSSO with their Microsoft Entra accounts.
* Manage your accounts in one central location.

You configure and test Microsoft Entra single sign-on for SeattleTimesSSO in a test environment. SeattleTimesSSO supports **IDP** initiated single sign-on.

## Prerequisites

To integrate Microsoft Entra ID with SeattleTimesSSO, you need:

* A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
* One of the following roles: [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
* A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* SeattleTimesSSO single sign-on (SSO) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the SeattleTimesSSO application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

<a name='add-seattletimessso-from-the-azure-ad-gallery'></a>

### Add SeattleTimesSSO from the Microsoft Entra gallery

Add SeattleTimesSSO from the Microsoft Entra application gallery to configure single sign-on with SeattleTimesSSO. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](~/identity/enterprise-apps/add-application-portal.md).

<a name='create-and-assign-azure-ad-test-user'></a>

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](~/identity/enterprise-apps/add-application-portal-assign-users.md) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides). 

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **SeattleTimesSSO** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.

1. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

    ![Screenshot shows the Certificate download link.](common/certificatebase64.png "Certificate")

1. On the **Set up SeattleTimesSSO** section, copy the appropriate URL(s) based on your requirement.

	![Screenshot shows to copy configuration appropriate URL.](common/copy-configuration-urls.png "Metadata")

## Configure SeattleTimesSSO SSO

To configure single sign-on on **SeattleTimesSSO** side, you need to send the downloaded **Certificate (Base64)** and appropriate copied URLs from the application configuration to [SeattleTimesSSO support team](mailto:it-hostingadmin@seattletimes.com). They set this setting to have the SAML SSO connection set properly on both sides

### Create SeattleTimesSSO test user

In this section, you create a user called Britta Simon in SeattleTimesSSO. Work with [SeattleTimesSSO support team](mailto:it-hostingadmin@seattletimes.com) to add the users in the SeattleTimesSSO platform. Users must be created and activated before you use single sign-on.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options.

* Select **Test this application**, and you should be automatically signed in to the SeattleTimesSSO for which you set up the SSO.

* You can use Microsoft My Apps. When you select the SeattleTimesSSO tile in the My Apps, you should be automatically signed in to the SeattleTimesSSO for which you set up the SSO. For more information, see [Microsoft Entra My Apps](/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure SeattleTimesSSO you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).
