---
title: Configure OrgChart Now for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and OrgChart Now.

author: nguhiu
manager: mwongerapk
ms.reviewer: celested
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu

# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and OrgChart Now so that I can control who has access to OrgChart Now, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---
# Configure OrgChart Now for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate OrgChart Now with Microsoft Entra ID. When you integrate OrgChart Now with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to OrgChart Now.
* Enable your users to be automatically signed-in to OrgChart Now with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* OrgChart Now single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra single sign-on in a test environment.

* OrgChart Now supports **SP** and **IDP** initiated SSO.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add OrgChart Now from the gallery

To configure the integration of OrgChart Now into Microsoft Entra ID, you need to add OrgChart Now from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **OrgChart Now** in the search box.
1. Select **OrgChart Now** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso-for-orgchart-now'></a>

## Configure and test Microsoft Entra SSO for OrgChart Now

Configure and test Microsoft Entra SSO with OrgChart Now using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in OrgChart Now.

To configure and test Microsoft Entra SSO with OrgChart Now, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure OrgChart Now SSO](#configure-orgchart-now-sso)** - to configure the single sign-on settings on application side.
    1. **[Create OrgChart Now test user](#create-orgchart-now-test-user)** - to have a counterpart of B.Simon in OrgChart Now that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO 

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **OrgChart Now** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, If you wish to configure the application in **IDP** initiated mode, perform the following step:

    a. In the **Identifier** text box, type the URL:
    `https://<OrgChartNowServer>.orgchartnow.com/saml/sso_metadata?entityID=<Your_Azure_AD_Entity_ID>`

	b. In the **Reply URL** text box, type a URL using the following pattern:
    `https://<OrgChartServer>.orgchartnow.com/saml/sso_acs?entityID=<Your_Azure_AD_Entity_ID>`

5. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type a URL using the following pattern:
    `https://<OrgChartServer>.orgchartnow.com/saml/sso_acs?entityID=<Your_Azure_AD_Entity_ID>`

	> [!NOTE]
	> `<YourEntityID>` is the **Microsoft Entra Identifier** copied from the **Set up OrgChart Now** section, described later in article.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

7. On the **Set up OrgChart Now** section, copy the appropriate URL(s) as per your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure OrgChart Now SSO

To configure single sign-on in OrgChart Now, follow the steps enumerated in the [SSO Configuration article](https://help.orgchartnow.com/en/topics/sso-configuration.html#configuring-sso-41334) on OrgChart Now's Help site.

### Create OrgChart Now test user

To enable Microsoft Entra users to log in to OrgChart Now, they must be set up as a user in OrgChart Now, or **Auto-Provisioning** must be enabled in the [SSO Configuration](https://help.orgchartnow.com/en/topics/sso-configuration.html#configuring-sso-41334) panel.

If you don't wish to enable auto-provisioning at this time, you can manually add a user to OrgChart Now for SSO testing purposes. To do so, follow the steps enumerated in the [Creating a New User](https://help.orgchartnow.com/en/account-settings/manage-users.html#UUID-a921b00b-a5a2-3099-8fe5-d0f28f5a50b9_bridgehead-idm4532421481724832584395125038) section of the [Account Settings: Manage Users](https://help.orgchartnow.com/en/account-settings/manage-users.html) article.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

#### SP initiated:

* Select **Test this application**, this option redirects to OrgChart Now Sign on URL where you can initiate the login flow.  

* Go to OrgChart Now Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Select **Test this application**, and you should be automatically signed in to the OrgChart Now for which you set up the SSO. 

You can also use Microsoft My Apps to test the application in any mode. When you select the OrgChart Now tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the OrgChart Now for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure OrgChart Now you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad).
