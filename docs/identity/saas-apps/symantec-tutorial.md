---
title: Configure Symantec Web Security Service (WSS) for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Symantec Web Security Service (WSS).

author: nguhiu
manager: mwongerapk
ms.reviewer: celested
ms.service: entra-id
ms.subservice: saas-apps

ms.topic: how-to
ms.date: 05/20/2025
ms.author: gideonkiratu

# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Symantec Web Security Service (WSS) so that I can control who has access to Symantec Web Security Service (WSS), enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---
# Configure Symantec Web Security Service (WSS) for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate your Symantec Web Security Service (WSS) account with your Microsoft Entra account so that WSS can authenticate an end user provisioned in the Microsoft Entra ID using SAML authentication and enforce user or group level policy rules.

Integrating Symantec Web Security Service (WSS) with Microsoft Entra ID provides you with the following benefits:

* Manage all of the end users and groups used by your WSS account from your Azure portal.

* Allow the end users to authenticate themselves in WSS using their Microsoft Entra credentials.

* Enable the enforcement of user and group level policy rules defined in your WSS account.

## Prerequisites
The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Symantec Web Security Service (WSS) single sign-on (SSO) enabled subscription.

> [!NOTE]
> This integration is also available to use from Microsoft Entra US Government Cloud environment. You can find this application in the Microsoft Entra US Government Cloud Application Gallery and configure it in the same way as you do from public cloud.

## Scenario description

In this article,  you configure and test Microsoft Entra single sign-on in a test environment.

* Symantec Web Security Service (WSS) supports **IDP** initiated SSO.

> [!NOTE]
> Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Symantec Web Security Service (WSS) from the gallery

To configure the integration of Symantec Web Security Service (WSS) into Microsoft Entra ID, you need to add Symantec Web Security Service (WSS) from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Symantec Web Security Service (WSS)** in the search box.
1. Select **Symantec Web Security Service (WSS)** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

<a name='configure-and-test-azure-ad-sso-for-symantec-web-security-service-wss'></a>

## Configure and test Microsoft Entra SSO for Symantec Web Security Service (WSS)

Configure and test Microsoft Entra SSO with Symantec Web Security Service (WSS) using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Symantec Web Security Service (WSS).

To configure and test Microsoft Entra SSO with Symantec Web Security Service (WSS), perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Symantec Web Security Service (WSS) SSO](#configure-symantec-web-security-service-wss-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Symantec Web Security Service (WSS) test user](#create-symantec-web-security-service-wss-test-user)** - to have a counterpart of B.Simon in Symantec Web Security Service (WSS) that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Symantec Web Security Service (WSS)** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** dialog, perform the following steps:

    a. In the **Identifier** text box, type the URL:
    `https://saml.threatpulse.net:8443/saml/saml_realm`

    b. In the **Reply URL** text box, type the URL:
    `https://saml.threatpulse.net:8443/saml/saml_realm/bcsamlpost`

	> [!NOTE]
	> Contact [Symantec Web Security Service (WSS) Client support team](https://www.symantec.com/contact-us) f the values for the **Identifier** and **Reply URL** aren't working for some reason.. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Symantec Web Security Service (WSS) SSO

To configure single sign-on on the Symantec Web Security Service (WSS) side, refer to the WSS online documentation. The downloaded **Federation Metadata XML** will need to be imported into the WSS portal. Contact the [Symantec Web Security Service (WSS) support team](https://www.symantec.com/contact-us) if you need assistance with the configuration on the WSS portal.

### Create Symantec Web Security Service (WSS) test user

In this section, you create a user called Britta Simon in Symantec Web Security Service (WSS). The corresponding end username can be manually created in the WSS portal or you can wait for the users/groups provisioned in the Microsoft Entra ID to be synchronized to the WSS portal after a few minutes (~15 minutes). Users must be created and activated before you use single sign-on. The public IP address of the end user machine, which is used to browse websites also need to be provisioned in the Symantec Web Security Service (WSS) portal.

> [!NOTE]
> Please select [here](https://www.bing.com/search?q=my+ip+address&qs=AS&pq=my+ip+a&sc=8-7&cvid=29A720C95C78488CA3F9A6BA0B3F98C5&FORM=QBLH&sp=1) to get your machine's public IPaddress.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options.

* Select **Test this application**, and you should be automatically signed in to the Symantec Web Security Service (WSS) for which you set up the SSO.

* You can use Microsoft My Apps. When you select the Symantec Web Security Service (WSS) tile in the My Apps, you should be automatically signed in to the Symantec Web Security Service (WSS) for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Symantec Web Security Service (WSS) you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
