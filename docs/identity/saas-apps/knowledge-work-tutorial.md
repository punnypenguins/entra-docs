---
title: Configure Knowledge Work for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Knowledge Work.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 08/13/2024
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Knowledge Work so that I can control who has access to Knowledge Work, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Knowledge Work for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Knowledge Work with Microsoft Entra ID. "Knowledge Work" is a cloud service that realizes various elements of sales enablement with a single tool and improves the sales productivity of companies. Specifically, it's possible to share sales materials and sales know-how, and provide learning programs for sales. When you integrate Knowledge Work with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Knowledge Work.
* Enable your users to be automatically signed-in to Knowledge Work with their Microsoft Entra accounts.
* Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Knowledge Work in a test environment. Knowledge Work supports only **SP** initiated single sign-on and **Just In Time** user provisioning.

## Prerequisites

To integrate Microsoft Entra ID with Knowledge Work, you need:

* A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
* One of the following roles: [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
* A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* Knowledge Work single sign-on (SSO) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Knowledge Work application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

<a name='add-knowledge-work-from-the-azure-ad-gallery'></a>

### Add Knowledge Work from the Microsoft Entra gallery

Add Knowledge Work from the Microsoft Entra application gallery to configure single sign-on with Knowledge Work. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](~/identity/enterprise-apps/add-application-portal.md).

<a name='create-and-assign-azure-ad-test-user'></a>

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](~/identity/enterprise-apps/add-application-portal-assign-users.md) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides). 

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Knowledge Work** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier** textbox, type a URL using the following pattern:
    `https://<CustomerName>.kwork.cloud/saml`

    b. In the **Reply URL** textbox, type the URL:
    `https://auth.kwork.cloud/_auth/saml/callback`

    c. In the **Sign on URL** textbox, type a URL using the following pattern:
    `https://<CustomerName>.kwork.cloud/redirect`

    > [!Note]
    > These values aren't real. Update these values with the actual Identifier and Sign-on URL. Contact [Knowledge Work Client support team](mailto:support@knowledgework.com) to get these values. You can also refer to the patterns shown in the Basic SAML Configuration section.

1. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

    ![Screenshot shows the Certificate download link.](common/certificatebase64.png "Certificate")

1. On the **Set up Knowledge Work** section, copy the appropriate URL(s) based on your requirement.

	![Screenshot shows to copy configuration appropriate URL.](common/copy-configuration-urls.png "Metadata")

## Configure Knowledge Work SSO

To configure single sign-on on **Knowledge Work** side, you need to send the downloaded **Certificate (Base64)** and appropriate copied URLs from the application configuration to [Knowledge Work support team](mailto:support@knowledgework.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Knowledge Work test user

In this section, a user called B.Simon is created in Knowledge Work. Knowledge Work supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Knowledge Work, a new one is commonly created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Knowledge Work Sign-on URL where you can initiate the login flow. 

* Go to Knowledge Work Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Knowledge Work tile in the My Apps, this option redirects to Knowledge Work Sign-on URL. For more information, see [Microsoft Entra My Apps](/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

* [What is single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)
* [Plan a single sign-on deployment](~/identity/enterprise-apps/plan-sso-deployment.md).

## Related content

Once you configure Knowledge Work you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).
