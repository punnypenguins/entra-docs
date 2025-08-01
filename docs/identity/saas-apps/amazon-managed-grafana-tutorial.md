---
title: Configure Amazon Managed Grafana for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Amazon Managed Grafana.
author: nguhiu
manager: mwongerapk
ms.reviewer: CelesteDG
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and Amazon Managed Grafana so that I can control who has access to Amazon Managed Grafana, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---

# Configure Amazon Managed Grafana for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Amazon Managed Grafana with Microsoft Entra ID. When you integrate Amazon Managed Grafana with Microsoft Entra ID, you can:

* Control in Microsoft Entra ID who has access to Amazon Managed Grafana.
* Enable your users to be automatically signed-in to Amazon Managed Grafana with their Microsoft Entra accounts.
* Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Amazon Web Services (AWS) [free account](https://aws.amazon.com/free/).
* Amazon Managed Grafana single sign-on (SSO) enabled subscription.

## Scenario description

In this article,  you configure and test Microsoft Entra SSO in a test environment.

* Amazon Managed Grafana supports **SP** initiated SSO.
* Amazon Managed Grafana supports **Just In Time** user provisioning.

## Add Amazon Managed Grafana from the gallery

To configure the integration of Amazon Managed Grafana into Microsoft Entra ID, you need to add Amazon Managed Grafana from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Amazon Managed Grafana** in the search box.
1. Select **Amazon Managed Grafana** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 [!INCLUDE [sso-wizard.md](~/identity/saas-apps/includes/sso-wizard.md)]

<a name='configure-and-test-azure-ad-sso-for-amazon-managed-grafana'></a>

## Configure and test Microsoft Entra SSO for Amazon Managed Grafana

Configure and test Microsoft Entra SSO with Amazon Managed Grafana using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Amazon Managed Grafana.

To configure and test Microsoft Entra SSO with Amazon Managed Grafana, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
    1. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.
1. **[Configure Amazon Managed Grafana SSO](#configure-amazon-managed-grafana-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Amazon Managed Grafana test user](#create-amazon-managed-grafana-test-user)** - to have a counterpart of B.Simon in Amazon Managed Grafana that's linked to the Microsoft Entra representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

<a name='configure-azure-ad-sso'></a>

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Amazon Managed Grafana** > **Single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, perform the following steps:

	a. In the **Identifier (Entity ID)** text box, type a URL using the following pattern:
    `https://<namespace>.grafana-workspace.<region>.amazonaws.com/saml/metadata`

	b. In the **Sign on URL** text box, type a URL using the following pattern:
    `https://<namespace>.grafana-workspace.<region>.amazonaws.com/login/saml`

	> [!NOTE]
	> These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Amazon Managed Grafana Client support team](https://aws.amazon.com/contact-us/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

1. Amazon Managed Grafana application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

	![image](common/default-attributes.png)

1. In addition to above, Amazon Managed Grafana application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
	
	| Name | Source attribute |
	| ----------| --------- |
	| displayName | user.displayname |
	| mail | user.userprincipalname |

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

1. On the **Set up Amazon Managed Grafana** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

## Configure Amazon Managed Grafana SSO

1. Log in to your Amazon Managed Grafana Console as an administrator.

1. Select **Create workspace**. 

	![Screenshot shows creating workspace.](./media/amazon-managed-grafana-tutorial/console.png "Workspace")

1. In the **Specify workspace details** page, type a unique **Workspace name** and select **Next**.

	![Screenshot shows workspace details.](./media/amazon-managed-grafana-tutorial/details.png "Specify details")

1. In the **Configure settings** page, select **Security Assertion Markup Language(SAML)** checkbox and enable **Service managed** as permission type and select **Next**.

	![Screenshot shows workspace settings.](./media/amazon-managed-grafana-tutorial/security.png "Settings")

1. In the **Service managed permission settings**, select **Current account** and select **Next**.

	![Screenshot shows permission settings.](./media/amazon-managed-grafana-tutorial/setting.png "permissions")

1. In the **Review and create** page, verify all the workspace details and select **Create workspace**.

	![Screenshot shows review and create page.](./media/amazon-managed-grafana-tutorial/review-workspace.png "Create Workspace")

1. After creating workspace, select **Complete setup** to complete the SAML configuration.

	![Screenshot shows SAML configuration.](./media/amazon-managed-grafana-tutorial/setup.png "SAML Configuration")

1. In the **Security Assertion Markup Language(SAML)** page, perform the following steps.

	![Screenshot shows SAML Setup.](./media/amazon-managed-grafana-tutorial/configuration.png "SAML Setup")

	1. Copy **Service provider identifier(Entity ID)** value, paste this value into the **Identifier** text box in the **Basic SAML Configuration** section.

	1. Copy **Service provider reply URL(Assertion consumer service URL)** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section.

	1. Copy **Service provider login URL** value, paste this value into the **Sign on URL** text box in the **Basic SAML Configuration** section.

	1. Open the downloaded **Federation Metadata XML** into Notepad and upload the XML file by selecting **Choose file** option.

	1. In the **Assertion mapping** section, fill the required values according to your requirement.

	1. Select **Save SAML configuration**.

### Create Amazon Managed Grafana test user

In this section, a user called Britta Simon is created in Amazon Managed Grafana. Amazon Managed Grafana supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Amazon Managed Grafana, a new one is created after authentication.

## Test SSO 

In this section, you test your Microsoft Entra single sign-on configuration with following options. 

* Select **Test this application**, this option redirects to Amazon Managed Grafana Sign-on URL where you can initiate the login flow. 

* Go to Amazon Managed Grafana Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you select the Amazon Managed Grafana tile in the My Apps, this option redirects to Amazon Managed Grafana Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Amazon Managed Grafana you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad).
