---
title: Troubleshoot issues with Permissions Management
description: Troubleshoot issues with Permissions Management
author: jenniferf-skc
manager: pmwongera
ms.service: entra-permissions-management

ms.topic: troubleshooting
ms.date: 04/01/2025
ms.author: jfields
---

# Troubleshoot issues with Permissions Management

> [!NOTE]
> Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

This section addresses how to troubleshoot issues with Permissions Management.

## One time passcode (OTP) email

### The user didn't receive the OTP email.

- Check your junk or Spam mail folder for the email.

## Reports

### The individual files are generated according to the authorization system (subscription/account/project).

- Select the **Collate** option in the **Custom Report** screen in the Permissions Management **Reports** tab.

## Data collection in AWS

### Data collection > AWS Authorization system data collection status is offline. Upload and transform is also offline.

- Check the Permissions Management-related role that exists in these accounts.
- Validate the trust relationship with the OpenID Connect (OIDC) role.

<!---Next steps--->
