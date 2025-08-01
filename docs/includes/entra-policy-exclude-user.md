---
ms.service: entra-id
ms.subservice: conditional-access
ms.topic: include
ms.date: 09/17/2024

ms.author: joflore
author: MicrosoftGuyJFlo
manager: dougeby
---
Conditional Access policies are powerful tools, we recommend excluding the following accounts from your policies:

- **Emergency access** or **break-glass** accounts to prevent lockout due to policy misconfiguration. In the unlikely scenario all administrators are locked out, your emergency-access administrative account can be used to log in and take steps to recover access.
   - More information can be found in the article, [Manage emergency access accounts in Microsoft Entra ID](~/identity/role-based-access-control/security-emergency-access.md).
- **Service accounts** and **Service principals**, such as the Microsoft Entra Connect Sync Account. Service accounts are non-interactive accounts that aren't tied to any particular user. They're normally used by back-end services allowing programmatic access to applications, but are also used to sign in to systems for administrative purposes. Calls made by service principals won't be blocked by Conditional Access policies scoped to users. Use Conditional Access for workload identities to define policies targeting service principals.
   - If your organization has these accounts in use in scripts or code, consider replacing them with [managed identities](~/identity/managed-identities-azure-resources/overview.md).
