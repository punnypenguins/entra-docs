---
title: Configure Corptax for Single sign-on with Microsoft Entra ID
description: Learn how to configure single sign-on between Microsoft Entra ID and Corptax.
author: nguhiu
manager: mwongerapk
ms.reviewer: celested
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: how-to
ms.date: 03/25/2025
ms.author: gideonkiratu
ms.custom: sfi-image-nochange
# Customer intent: As an IT administrator, I want to learn how to configure single sign-on between Microsoft Entra ID and CorpTax so that I can control who has access to CorpTax, enable automatic sign-in with Microsoft Entra accounts, and manage my accounts in one central location.
---
# Configure Corptax for Single sign-on with Microsoft Entra ID

In this article,  you learn how to integrate Corptax with Microsoft Entra ID.
Integrating Corptax with Microsoft Entra ID provides you with the following benefits:

* You can control in Microsoft Entra ID who has access to Corptax.
* You can enable your users to be automatically signed-in to Corptax (Single Sign-On) with their Microsoft Entra accounts.
* You can manage your accounts in one central location.

If you want to know more details about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](~/identity/enterprise-apps/what-is-single-sign-on.md).
If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/free/) before you begin.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

[!INCLUDE [common-prerequisites.md](~/identity/saas-apps/includes/common-prerequisites.md)]
* Corptax single sign-on enabled subscription

## Scenario description

In this article,  you configure and test Microsoft Entra single sign-on in a test environment.

* Corptax supports **SP** initiated SSO

## Adding Corptax from the gallery

To configure the integration of Corptax into Microsoft Entra ID, you need to add Corptax from the gallery to your list of managed SaaS apps.

**To add Corptax from the gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **New application**.
1. In the **Add from the gallery** section, type **Corptax** in the search box.
1. Select **Corptax** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

<a name='configure-and-test-azure-ad-single-sign-on'></a>

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with Corptax based on a test user called **Britta Simon**.
For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in Corptax needs to be established.

To configure and test Microsoft Entra single sign-on with Corptax, you need to complete the following building blocks:

1. **[Configure Microsoft Entra Single Sign-On](#configure-azure-ad-single-sign-on)** - to enable your users to use this feature.
2. **[Configure Corptax Single Sign-On](#configure-corptax-single-sign-on)** - to configure the Single Sign-On settings on application side.
3. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
4. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.
5. **[Create Corptax test user](#create-corptax-test-user)** - to have a counterpart of Britta Simon in Corptax that's linked to the Microsoft Entra representation of user.
6. **[Test single sign-on](#test-single-sign-on)** - to verify whether the configuration works.

<a name='configure-azure-ad-single-sign-on'></a>

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with Corptax, perform the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Entra ID** > **Enterprise apps** > **Corptax** application integration page, select **Single sign-on**.

    ![Configure single sign-on link](common/select_sso.png)

1. On the **Select a Single sign-on method** dialog, select **SAML/WS-Fed** mode to enable single sign-on.

1. On the **Set up Single Sign-On with SAML** page, select **Edit** icon to open **Basic SAML Configuration** dialog.

	![Edit Basic SAML Configuration](common/edit_urls.png)

1. On the **Basic SAML Configuration** section, perform the following steps:

    ![Corptax Domain and URLs single sign-on information](common/sp_intiated.png)

    In the **Sign-on URL** text box, type a URL:
    `https://asp.corptax.com`

1. On the **Set up Single Sign-On with SAML** page, In the **SAML Signing Certificate** section, select **Download** to download **Federation Metadata XML** and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

### Configure Corptax Single Sign-On

To configure single sign-on on **Corptax** side, you need to send the downloaded **Federation Metadata XML** to [Corptax support team](https://connect.corptax.com/). They set this setting to have the SAML SSO connection set properly on both sides.

<a name='create-an-azure-ad-test-user'></a>

[!INCLUDE [create-assign-users-sso.md](~/identity/saas-apps/includes/create-assign-users-sso.md)]

### Create Corptax test user

In this section, you create a user called Britta Simon in Corptax. Work with [Corptax support team](https://connect.corptax.com/) to add the users in the Corptax platform. Users must be created and activated before you use single sign-on.

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.
When you select the Corptax tile in the Access Panel, you should be redirected to the below Corptax page- 

![image](media/corptax-tutorial/corptaxlogin.png)

In **Environment** text box, type your appropriate environment, you should be automatically signed in to the Corptax for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional Resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](./tutorial-list.md)

- [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

- [What is Conditional Access in Microsoft Entra ID?](~/identity/conditional-access/overview.md)
