---
title: Configure goFLUENT for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and goFLUENT.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and goFLUENT so that I can control who has access to goFLUENT, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure goFLUENT for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate goFLUENT with Microsoft Entra ID. goFLUENT, the world's leading language training provider, delivers a hyper-personalized learning experience that builds confidence, empowers career growth, and establishes an inclusive global culture. When you integrate goFLUENT with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to goFLUENT.
* Enable your users to be automatically signed-in to goFLUENT with their Microsoft Entra accounts.
* Manage your accounts in one central location.

You configure and test Microsoft Entra single sign-on for goFLUENT in a test environment. goFLUENT supports **SP** initiated single sign-on and **Just In Time** user provisioning.

## Prerequisites

To integrate Microsoft Entra ID with goFLUENT, you need:

* A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
* One of the following roles: [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
* A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* goFLUENT single sign-on (SSO) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the goFLUENT application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

<a name='add-gofluent-from-the-azure-ad-gallery'></a>

### Add goFLUENT from the Microsoft Entra gallery

Add goFLUENT from the Microsoft Entra application gallery to configure single sign-on with goFLUENT. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](~/identity/enterprise-apps/add-application-portal.md).

<a name='create-and-assign-azure-ad-test-user'></a>

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](~/identity/enterprise-apps/add-application-portal-assign-users.md) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides). 

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **goFLUENT** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](common/edit-urls.png "Basic Configuration")

1. On the **Basic SAML Configuration** section, perform the following steps:

    a. In the **Identifier** textbox, type a URL using the following pattern:
    `https://CustomerName.gofluent.com/app/samlconnector?client=<CustomerName>`

    b. In the **Reply URL** textbox, type a URL using the following pattern:
    `https://<CustomerName>.gofluent.com/app/samlconnector?client=<CustomerName>`

	c. In the **Sign on URL** textbox, type a URL using the following pattern:
	`https://<CustomerName>.gofluent.com`

	> [!NOTE]
    > These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [goFLUENT Client support team](mailto:presales-team@gofluent.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

    ![Screenshot shows the Certificate download link.](common/metadataxml.png "Certificate")

1. On the **Set up goFLUENT** section, copy the appropriate URL(s) based on your requirement.

	![Screenshot shows to copy configuration appropriate URL.](common/copy-configuration-urls.png "Metadata")

## Configure goFLUENT SSO

To configure single sign-on on **goFLUENT** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [goFLUENT support team](mailto:presales-team@gofluent.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create goFLUENT test user

In this section, a user called B.Simon is created in goFLUENT. goFLUENT supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in goFLUENT, a new one is commonly created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to goFLUENT Sign-on URL where you can initiate the login flow. 

* Go to goFLUENT Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the goFLUENT tile in the My Apps, this option redirects to goFLUENT Sign-on URL. For more information, see [Microsoft Entra My Apps](/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

* [What is single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)
* [Plan a single sign-on deployment](~/identity/enterprise-apps/plan-sso-deployment.md).

## Related content

Once you configure goFLUENT you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).