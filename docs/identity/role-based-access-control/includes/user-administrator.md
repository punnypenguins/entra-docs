---
title: User Administrator
description: User Administrator
ms.service: entra-id
ms.subservice: role-based-access-control
ms.topic: include
ms.date: 07/09/2025
ms.custom: include file
---

[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md)

This is a [privileged role](../privileged-roles-permissions.md). Assign the User Administrator role to users who need to do the following:

| Permission | More information |
| --- | --- |
| Create users |  |
| Update most user properties for all users, including all administrators | [Who can perform sensitive actions](../privileged-roles-permissions.md#who-can-perform-sensitive-actions) |
| Update sensitive properties (including user principal name) for some users | [Who can perform sensitive actions](../privileged-roles-permissions.md#who-can-perform-sensitive-actions) |
| Disable or enable some users | [Who can perform sensitive actions](../privileged-roles-permissions.md#who-can-perform-sensitive-actions) |
| Delete or restore some users | [Who can perform sensitive actions](../privileged-roles-permissions.md#who-can-perform-sensitive-actions) |
| Create and manage user views |  |
| Create and manage all groups |  |
| Assign and read licenses for all users, including all administrators |  |
| Reset passwords | [Who can reset passwords](../privileged-roles-permissions.md#who-can-reset-passwords) |
| Invalidate refresh tokens | [Who can reset passwords](../privileged-roles-permissions.md#who-can-reset-passwords) |
| Update (FIDO) device keys |  |
| Update password expiration policies |  |
| Create and manage support tickets in Azure and the Microsoft 365 admin center |  |
| Monitor service health |  |

Users with this role **cannot** do the following:

- Cannot manage MFA.
- Cannot change the credentials or reset MFA for members and owners of a [role-assignable group](../groups-concept.md).
- Cannot manage shared mailboxes.
- Cannot modify security questions for password reset operation.

> [!IMPORTANT]
> Users with this role can change passwords for people who may have access to sensitive or private information or critical configuration inside and outside of Microsoft Entra ID. Changing the password of a user may mean the ability to assume that user's identity and permissions. For example:
>
>- Application Registration and Enterprise Application owners, who can manage credentials of apps they own. Those apps may have privileged permissions in Microsoft Entra ID and elsewhere not granted to User Administrators. Through this path a User Administrator may be able to assume the identity of an application owner and then further assume the identity of a privileged application by updating the credentials for the application.
>- Azure subscription owners, who may have access to sensitive or private information or critical configuration in Azure.
>- Security Group and Microsoft 365 group owners, who can manage group membership. Those groups may grant access to sensitive or private information or critical configuration in Microsoft Entra ID and elsewhere.
>- Administrators in other services outside of Microsoft Entra ID like Exchange Online, Microsoft 365 Defender portal, Microsoft Purview compliance portal, and human resources systems.
>- Non-administrators like executives, legal counsel, and human resources employees who may have access to sensitive or private information.
<!-- autogenerated content starts here -->

> [!div class="mx-tableFixed"]
> | Actions | Description |
> | --- | --- |
> | microsoft.azure.serviceHealth/allEntities/allTasks | Read and configure Azure Service Health |
> | microsoft.azure.supportTickets/allEntities/allTasks | Create and manage Azure support tickets |
> | microsoft.directory/accessReviews/definitions.applications/allProperties/allTasks | Manage access reviews of application role assignments in Microsoft Entra ID |
> | microsoft.directory/accessReviews/definitions.directoryRoles/allProperties/read | Read all properties of access reviews for Microsoft Entra role assignments |
> | microsoft.directory/accessReviews/definitions.entitlementManagement/allProperties/allTasks | Manage access reviews for access package assignments in entitlement management |
> | microsoft.directory/accessReviews/definitions.groups/allProperties/read | Read all properties of access reviews for membership in Security and Microsoft 365 groups, including role-assignable groups. |
> | microsoft.directory/accessReviews/definitions.groups/allProperties/update | Update all properties of access reviews for membership in Security and Microsoft 365 groups, excluding role-assignable groups. |
> | microsoft.directory/accessReviews/definitions.groups/create | Create access reviews for membership in Security and Microsoft 365 groups. |
> | microsoft.directory/accessReviews/definitions.groups/delete | Delete access reviews for membership in Security and Microsoft 365 groups. |
> | microsoft.directory/contacts/basic/update | Update basic properties on contacts |
> | microsoft.directory/contacts/create | Create contacts |
> | microsoft.directory/contacts/delete | Delete contacts |
> | microsoft.directory/deletedItems.groups/restore | Restore soft deleted groups to original state |
> | microsoft.directory/deletedItems.users/restore | Restore soft deleted users to original state |
> | microsoft.directory/entitlementManagement/allProperties/allTasks | Create and delete resources, and read and update all properties in Microsoft Entra entitlement management |
> | microsoft.directory/groups/assignLicense | Assign product licenses to groups for group-based licensing |
> | microsoft.directory/groups/basic/update | Update basic properties on Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/classification/update | Update the classification property on Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/create | Create Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/delete | Delete Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/dynamicMembershipRule/update | Update the dynamic membership rule on Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/groupType/update | Update properties that would affect the group type of Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/hiddenMembers/read | Read hidden members of Security groups and Microsoft 365 groups, including role-assignable groups |
> | microsoft.directory/groups/members/update | Update members of Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/onPremWriteBack/update | Update Microsoft Entra groups to be written back to on-premises with Microsoft Entra Connect |
> | microsoft.directory/groups/owners/update | Update owners of Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/groups/reprocessLicenseAssignment | Reprocess license assignments for group-based licensing |
> | microsoft.directory/groups/restore | Restore groups from soft-deleted container |
> | microsoft.directory/groups/settings/update | Update settings of groups |
> | microsoft.directory/groups/visibility/update | Update the visibility property of Security groups and Microsoft 365 groups, excluding role-assignable groups |
> | microsoft.directory/oAuth2PermissionGrants/allProperties/allTasks | Create and delete OAuth 2.0 permission grants, and read and update all properties<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/onPremisesSynchronization/standard/read | Read standard on-premises directory synchronization information |
> | microsoft.directory/policies/standard/read | Read basic properties on policies |
> | microsoft.directory/servicePrincipals/appRoleAssignedTo/update | Update service principal role assignments |
> | microsoft.directory/users/assignLicense | Manage user licenses |
> | microsoft.directory/users/basic/update | Update basic properties on users |
> | microsoft.directory/users/convertExternalToInternalMemberUser | Convert external user to internal user |
> | microsoft.directory/users/create | Add users<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/users/delete | Delete users<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/users/disable | Disable users<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/users/enable | Enable users<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/users/invalidateAllRefreshTokens | Force sign-out by invalidating user refresh tokens<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/users/inviteGuest | Invite guest users |
> | microsoft.directory/users/lifeCycleInfo/read | Read lifecycle information of users, such as employeeLeaveDateTime<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/users/manager/update | Update manager for users |
> | microsoft.directory/users/password/update | Reset passwords for all users<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.directory/users/photo/update | Update photo of users |
> | microsoft.directory/users/reprocessLicenseAssignment | Reprocess license assignments for users |
> | microsoft.directory/users/restore | Restore deleted users |
> | microsoft.directory/users/sponsors/update | Update sponsors of users |
> | microsoft.directory/users/usageLocation/update | Update usage location of users |
> | microsoft.directory/users/userPrincipalName/update | Update User Principal Name of users<br/>[![Privileged label icon.](../media/permissions-reference/privileged-label.png)](../privileged-roles-permissions.md) |
> | microsoft.office365.serviceHealth/allEntities/allTasks | Read and configure Service Health in the Microsoft 365 admin center |
> | microsoft.office365.supportTickets/allEntities/allTasks | Create and manage Microsoft 365 service requests |
> | microsoft.office365.webPortal/allEntities/standard/read | Read basic properties on all resources in the Microsoft 365 admin center |

