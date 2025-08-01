---
title: Configure Vera Suite for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Vera Suite.

author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu


# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Vera Suite so that I can control who has access to Vera Suite, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Vera Suite for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Vera Suite with Microsoft Entra ID. Vera Suite helps auto dealers maintain cultures of safety, streamline operations and manage risk. Vera Suite offers dealership workforce and workplace compliance solutions for EHS, HR and F&I managers. When you integrate Vera Suite with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Vera Suite.
* Enable your users to be automatically signed-in to Vera Suite with their Microsoft Entra accounts.
* Manage your accounts in one central location.

You configure and test Microsoft Entra single sign-on for Vera Suite in a test environment. Vera Suite supports **SP** initiated single sign-on and **Just In Time** user provisioning.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Prerequisites

To integrate Microsoft Entra ID with Vera Suite, you need:

* A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
* One of the following roles: [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
* A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* Vera Suite single sign-on (SSO) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Vera Suite application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

<a name='add-vera-suite-from-the-azure-ad-gallery'></a>

### Add Vera Suite from the Microsoft Entra gallery

Add Vera Suite from the Microsoft Entra application gallery to configure single sign-on with Vera Suite. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](~/identity/enterprise-apps/add-application-portal.md).

<a name='create-and-assign-azure-ad-test-user'></a>

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](~/identity/enterprise-apps/add-application-portal-assign-users.md) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides). 

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Vera Suite** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.

1. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

    ![Screenshot shows the Certificate download link.](common/copy-metadataurl.png "Certificate")

## Configure Vera Suite SSO

To configure single sign-on on **Vera Suite** side, you need to send the **App Federation Metadata Url** to [Vera Suite support team](mailto:support@kpa.io). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Vera Suite test user

In this section, a user called B.Simon is created in Vera Suite. Vera Suite supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Vera Suite, a new one is commonly created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Vera Suite Sign-on URL where you can initiate the login flow. 

* Go to Vera Suite Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Vera Suite tile in the My Apps, this option redirects to Vera Suite Sign-on URL. For more information, see [Microsoft Entra My Apps](/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

* [What is single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)
* [Plan a single sign-on deployment](~/identity/enterprise-apps/plan-sso-deployment.md).

## Related content

Once you configure Vera Suite you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).
