---
title: Plan a Microsoft Entra application proxy deployment
description: An end-to-end guide for planning the deployment of application proxy within your organization

author: kenwith
manager: dougeby 
ms.service: entra-id
ms.subservice: app-proxy
ms.topic: conceptual
ms.date: 05/01/2025
ms.author: kenwith
ai-usage: ai-assisted
---

# Plan a Microsoft Entra application proxy deployment

Microsoft Entra application proxy is a secure and cost-effective remote access solution for on-premises applications. It provides an immediate transition path for "Cloud First" organizations to manage access to legacy on-premises applications that aren’t yet capable of using modern protocols. For more introductory information, see [What is application proxy](overview-what-is-app-proxy.md).

Application proxy is recommended for giving remote users access to internal resources. Application proxy replaces the need for a VPN or reverse proxy for these remote access use cases. It isn't intended for users who are on the corporate network. These users who use application proxy for intranet access might experience undesirable performance issues.

This article includes the resources you need to plan, operate, and manage Microsoft Entra application proxy.

## Plan your implementation

The following section provides a broad view of the key planning elements that set you up for an efficient deployment experience.

### Prerequisites

You need to meet the following prerequisites before beginning your implementation. You can see more information on setting up your environment, including these prerequisites, in the [tutorial](application-proxy-add-on-premises-application.md).

* **Connectors**: Connectors are lightweight agents that you can deploy onto:
   * Physical hardware on-premises
   * A Virtual Machine (VM) hosted within any hypervisor solution
   * A VM hosted in Azure to enable outbound connection to the application proxy service.

* See [Understand Microsoft Entra private network connectors](application-proxy-connectors.md) for a more detailed overview.

     * Connector machines must [be enabled for Transport Layer Security (TLS) 1.2](application-proxy-add-on-premises-application.md) before installing the connectors.

     * If possible, deploy connectors in the [same network](application-proxy-network-topology.md) and segment as the back-end web application servers. It's best to deploy connectors after you complete a discovery of applications.
     * We recommend that each connector group has at least two connectors to provide high availability and scale. Having three connectors is optimal for servicing a machine at any point. Review the [connector capacity table](./application-proxy-connectors.md#capacity-planning) to help decide the type of machine for the connector.

* **Network access settings**: Microsoft Entra private network connectors [connect to Azure via HTTPS (Transmission Control Protocol (TCP) Port 443) and HTTP (TCP Port 80)](application-proxy-add-on-premises-application.md).

   * Terminating connector TLS traffic isn't supported and prevents connectors from establishing a secure channel with their respective Microsoft Entra application proxy endpoints.

   * Avoid all forms of inline inspection on outbound TLS communications between connectors and Azure. Internal inspection between a connector and backend applications is possible, but could degrade the user experience, and as such, isn't recommended.

   * Load balancing of the connectors themselves is also not supported, or even necessary.

<a name='important-considerations-before-configuring-azure-ad-application-proxy'></a>

### Important considerations before configuring Microsoft Entra application proxy

The following core requirements must be met in order to configure and implement Microsoft Entra application proxy.

*  **Azure onboarding**: Before you deploy application proxy, user identities must be synchronized from an on-premises directory or created directly within your Microsoft Entra tenants. Identity synchronization allows Microsoft Entra ID to preauthenticate users before granting them access to application proxy published applications and to have the necessary user identifier information to perform single sign-on (SSO).

* **Conditional Access requirements**: We don't recommend using application proxy for intranet access because it adds latency that affects users. We recommend using application proxy with preauthentication and Conditional Access policies for remote access from the internet. An approach to provide Conditional Access for intranet use is to modernize applications so they can directly authenticate with Microsoft Entra ID. For more information, see [Resources for migrating applications to Microsoft Entra ID](~/identity/enterprise-apps/migration-resources.md).

* **Service limits**: To protect against overconsumption of resources by individual tenants, there are throttling limits set per application and tenant. To see these limits refer to [Microsoft Entra service limits and restrictions](~/identity/users/directory-service-limits-restrictions.md). These throttling limits are based on a benchmark beyond typical usage volume and provide ample buffer for most deployments.

* **Public certificate**: If you're using custom domain names, you must procure a TLS certificate. Depending on your organizational requirements, getting a certificate can take some time and we recommend beginning the process as early as possible. Azure application proxy supports standard, [wildcard](application-proxy-wildcard.md), or SAN-based certificates. For more information, see [Configure custom domains with Microsoft Entra application proxy](how-to-configure-custom-domain.md).

* **Domain requirements**: To use Kerberos Constrained Delegation (KCD) for single sign-on, ensure both the connector server and application server are domain-joined and either in the same domain or in trusted domains. The connector service runs under the local system account and shouldn't use a custom identity. For more information, see [KCD for single sign-on](how-to-configure-sso-with-kcd.md).

* **DNS records for URLs**

   * Before using custom domains in application proxy you must create a CNAME record in public Domain Name System (DNS), allowing clients to resolve the custom defined external URL to the predefined application proxy address. Failing to create a CNAME record for an application that uses a custom domain prevents remote users from connecting to the application. Steps required to add CNAME records can vary from DNS provider to provider, so learn how to [manage DNS records and record sets by using the Microsoft Entra admin center](/azure/dns/dns-operations-recordsets-portal).

   * Similarly, connector hosts must be able to resolve the internal URL of applications being published.

* **Administrative rights and roles**

   * **Connector installation** requires local admin rights to the Windows server that it's being installed on. It also requires a minimum of an *Application Administrator* role to authenticate and register the connector instance to your Microsoft Entra tenant.

   * **Application publishing and administration** require the *Application Administrator* role. Application Administrators can manage all applications in the directory including registrations, SSO settings, user, and group assignments and licensing, application proxy settings, and consent. It doesn't grant the ability to manage Conditional Access. The *Cloud Application Administrator* role has all the abilities of the Application Administrator, except that it doesn't allow management of application proxy settings.

* **Licensing**: application proxy is available through a Microsoft Entra ID P1 or P2 subscription. Refer to the [Microsoft Entra pricing page](https://www.microsoft.com/security/business/identity-access-management/azure-ad-pricing) for a full list of licensing options and features.

### Application Discovery

Compile an inventory of all in-scope applications that are being published via application proxy by collecting the following information:

| Information Type| Information to collect |
|---|---|
| Service Type| For example: SharePoint, SAP, CRM, Custom Web Application, API |
| Application platform | For example: Windows Internet Information Services (IIS), Apache on Linux, Tomcat, NGINX |
| Domain membership| Web server’s fully qualified domain name (FQDN) |
| Application location | Where the web server or farm is located in your infrastructure |
| Internal access | The exact URL used when accessing the application internally. <br> If a farm, what type of load balancing is in use? <br> Whether the application draws content from sources other than itself.<br> Determine if the application operates over WebSockets. |
| External access | The vendor solution that the application might already be exposed through, externally. <br> The URL you want to use for external access. If SharePoint, ensure Alternate Access Mappings are configured per [the guidance](/SharePoint/administration/configure-alternate-access-mappings). If not, you need to define external URLs. |
| Public certificate | If using a custom domain, procure a certificate with a corresponding subject name. if a certificate exists note the serial number and location from where it can be obtained. |
| Authentication type| The type of authentication supported by the application support such as Basic, Windows Integration Authentication, forms-based, header-based, and claims. <br>If the application is configured to run under a specific domain account, note the Fully Qualified Domain Name (FQDN) of the service account.<br> If SAML-based, the identifier and reply URLs. <br> If header-based, the vendor solution and specific requirement for handling authentication type. |
| Connector group name | The logical name for the group of connectors that are designated to provide the conduit and SSO to the backend application. |
| Users/Groups access | The users or user groups that are granted external access to the application. |
| More requirements | Note any more remote access or security requirements that should be factored into publishing the application. |

You can download the [application inventory spreadsheet](https://aka.ms/appdiscovery) to inventory your apps.

### Define organizational requirements

The following are areas for which you should define your organization’s business requirements. Each area contains examples of requirements

 **Access**

* Remote users with domain-joined or Microsoft Entra joined devices can access published applications securely with seamless single sign-on (SSO).

* Remote users with approved personal devices can securely access published applications provided they're enrolled in MFA and registered the Microsoft Authenticator app on their mobile phone as an authentication method.

**Governance**

* Administrators can define and monitor the lifecycle of user assignments to applications published through application proxy.

**Security**

* Only users assigned to applications via group membership or individually can access those applications.

**Performance**

* There's no degradation of application performance compared to accessing application from the internal network.

**User Experience**

* Users are aware of how to access their applications by using familiar company URLs on any device platform.

**Auditing**
* Administrators are able to audit user access activity.


### Best practices for a pilot

Determine the amount of time and effort needed to fully commission a single application for remote access with Single sign-on (SSO). Do so by running a pilot that considers its initial discovery, publishing, and general testing. Using a simple IIS-based web application that is already preconfigured for integrated Windows authentication (IWA) would help establish a baseline, as the setup requires minimal effort to successfully pilot remote access and SSO.

The following design elements should increase the success of your pilot implementation directly in a production tenant.

**Connector management**:

Connectors play a key role in providing the on-premises conduit to your applications. Using the **Default** connector group is adequate for initial pilot testing of published applications before commissioning them into production. Successfully tested applications can then be moved to production connector groups.

**Application management**:

Your workforce is most likely to remember an external URL is familiar and relevant. Avoid publishing your application using our predefined msappproxy.net or onmicrosoft.com suffixes. Instead, provide a familiar top-level verified domain, prefixed with a logical hostname such as *intranet.<customers_domain>.com*.

Restrict visibility of the pilot application’s icon to a pilot group by hiding its launch icon from the Azure MyApps portal. When ready for production you can scope the app to its respective targeted audience, either in the same preproduction tenant, or by also publishing the  application in your production tenant.

**Single sign-on settings**:
Some SSO settings have specific dependencies that can take time to set up, so avoid change control delays by ensuring dependencies are addressed ahead of time. The process includes domain joining connector hosts to perform SSO using Kerberos Constrained Delegation (KCD) and taking care of other time-consuming activities.

**TLS Between Connector Host and Target Application**: Security is paramount, so TLS between the connector host and target applications should always be used. Particularly if the web application is configured for forms-based authentication (FBA), as user credentials are then effectively transmitted in clear text.

**Implement incrementally and test each step**.
Conduct basic functional testing after publishing an application to ensure that all user and business requirements are met:

Test and validate general access to the web application with preauthentication disabled.
If successful, then enable preauthentication and assign users and groups. Then test and validate access.
Next, add the SSO method for your application and test again to validate access.
Finally, apply Conditional Access and MFA policies as required. Test and validate access.

**Troubleshooting Tools**: Start troubleshooting by checking access to the published application directly from the browser on the connector host. Ensure the application works as expected. Simplify your setup to isolate issues, such as using a single connector and disabling SSO. Tools like Telerik’s Fiddler can help debug access or content issues by tracing traffic, including for mobile platforms like iOS and Android. For more information, see the [troubleshooting guide](application-proxy-troubleshoot.md).

## Implement Your Solution

### Deploy application proxy

The steps to deploy your application proxy are covered in the [tutorial for adding an on-premises application for remote access](application-proxy-add-on-premises-application.md). If the installation isn't successful, select  **Troubleshoot application proxy**  in the portal or use the troubleshooting guide [for Problems with installing the application proxy Agent Connector](application-proxy-connector-installation-problem.md).

### Publish applications via application proxy

Publishing applications assumes that you satisfied all the prerequisites and that you have several connectors showing as registered and active in the application proxy page.

You can also publish applications by using [PowerShell](/powershell/module/azuread/?view=azureadps-2.0-preview&preserve-view=true).

Best practices to follow when publishing an application:

* **Use Connector Groups**: Assign a connector group that is designated for publishing each respective application. We recommend that each connector group has at least two connectors to provide high availability and scale. Having three connectors is optimal in case you need to service a machine at any point. Additionally, see [Understand Microsoft Entra private network connector groups](../../global-secure-access/concept-connector-groups.md) to see how you can also use connector groups to segment your connectors by network or location.

* **Set Backend Application Timeout**: The setting is useful in scenarios where the application might require more than 75 seconds to process a client transaction. For example, when a client sends a query to a web application that acts as a front end to a database. The front end sends the query to its back-end database server and waits for a response, but by the time it receives a response, the client side of the conversation times out. Setting the time-out to Long provides 180 seconds for longer transactions to complete.

* **Use Appropriate Cookie Types**

   * **HTTP-Only Cookie**: Provides extra security by having application proxy include the HTTPOnly flag in set-cookie HTTP response headers. The setting helps to mitigate exploits such as cross-site scripting (XSS). Leave set to No for clients/user agents that do require access to the session cookie. For example, RDP/MTSC client connecting to a Remote Desktop Gateway published via application proxy.

   * **Secure Cookie**: When a cookie is set with the Secure attribute, the user agent (Client-side app) only includes the cookie in HTTP requests if the request is transmitted over a TLS secured channel. The setting helps mitigate the risk of a cookie being compromised over clear text channels, so should be enabled.

   * **Persistent Cookie**: Allows the application proxy session cookie to persist between browser closures by remaining valid until it either expires or is deleted. Used for scenarios where a rich application such as office accesses a document within a published web application, without the user being reprompted for authentication. Enable with caution however, as persistent cookies can ultimately leave a service at risk of unauthorized access, if not used with other compensating controls. This setting should only be used for older applications that can't share cookies between processes. It's better to update your application to handle sharing cookies between processes instead of using the setting.

* **Translate URLs in Headers**: You enable the setting for scenarios where internal DNS can't be configured to match the organization’s public namespace(a.k.a Split DNS). Unless your application requires the original host header in the client request, leave the value set to Yes. The alternative is to have the connector use the FQDN in the internal URL for routing of the actual traffic, and the FQDN in the external URL, as the host-header. In most cases the alternative should allow the application to function as normal, when accessed remotely, but your users lose the benefits of having a matching inside & outside URL.

* **Translate URLs in Application Body**: Turn on Application Body link translation for an app when you want the links from that app to be translated in responses back to the client. If enabled, the function provides a best effort attempt at translating all internal links that application proxy finds in HTML and CSS responses being returned to clients. It's useful when publishing apps that contain either hard-coded absolute or NetBIOS shortname links in the content, or apps with content that links to other on-premises applications.

For scenarios where a published app links to other published apps, enable link translation for each application so that you have control over the user experience at the per-app level.

For example, suppose that you have three applications published through application proxy that all link to each other: Benefits, Expenses, and Travel, plus a fourth app, Feedback that isn't published through application proxy.

![Diagram showing link translation.](media/app-proxy-deployment-plan/link-translation.png)
When link translation is enabled for the Benefits app, links to the Expenses and Travel apps are redirected to their external URLs, allowing external users to access them. However, links from Expenses and Travel back to Benefits doesn't work unless link translation is also enabled for those apps. The Feedback app link isn't redirected because it lacks an external URL, preventing external users from accessing it via the Benefits app. For more information, see [link translation and redirect options](application-proxy-configure-hard-coded-link-translation.md).

### Access your application

Manage access to application proxy published resources by selecting the approach that best fits your scenario and scalability requirements. Common methods include syncing on-premises groups via Microsoft Entra Connect, creating Dynamic Groups in Microsoft Entra ID based on user attributes, enabling self-service groups managed by resource owners, or combining these strategies. Explore the linked resources to understand the benefits of each method.

The most straight forward way of assigning users access to an application is going into the **Users and Groups** options from the left-hand pane of your published application and directly assigning groups or individuals.

![Picture 24](media/App-proxy-deployment-plan/add-user.png)

You can also allow users to self-service access to your application by assigning a group that they aren't currently a member of and configuring the self-serve options.

![Picture 25](media/App-proxy-deployment-plan/allow-access.png)

If enabled, users sign in to the MyApps portal to request access. They're either automatically approved and added to the self-service group or require approval from a designated approver.

Guest users can also be [invited to access internal applications published via application proxy through Microsoft Entra B2B](~/external-id/add-users-information-worker.md).

For on premises applications that are normally accessible anonymously, requiring no authentication, you might want to disable the option located in the application’s **Properties**.

![Picture 26](media/App-proxy-deployment-plan/assignment-required.png)


Leaving the option set to No allows users to access the on-premises application via Microsoft Entra application proxy without permissions, so use with caution.

Once your application is published, it should be accessible by typing its external URL in a browser or by its icon at [https://myapps.microsoft.com](https://myapps.microsoft.com/).

### Enable preauthentication

Verify that your application is accessible through application proxy accessing it via the external URL.
1. Browse to **Entra ID** > **Enterprise apps** > **All applications** and choose the app you want to manage.


2. Select **application proxy**.

3. In the **Pre-Authentication** field, use the dropdown list to select **Microsoft Entra ID**, and select **Save**.
With preauthentication enabled, Microsoft Entra ID first authenticates users. If single sign-on is set up, the back-end application also verifies the user before granting access. Switching the preauthentication mode from Passthrough to Microsoft Entra ID secures the external URL with HTTPS, ensuring that any application initially using HTTP now operates over HTTPS.

### Enable single sign-on

SSO improves user experience and security by allowing users to sign in once with Microsoft Entra ID. After preauthentication, the private network connector signs in to the on-premises application for the user, making it appear as if the user signed in directly.

Choosing the **Passthrough** option allows users to access the published application without ever having to authenticate to Microsoft Entra ID.

To enable SSO, your application must preauthenticate users with Microsoft Entra ID. Without preauthentication, SSO options are unavailable.

Read [Single sign-on to applications in Microsoft Entra ID](~/identity/enterprise-apps/what-is-single-sign-on.md) to help you choose the most appropriate SSO method when configuring your applications.

###  Working with other types of applications

Microsoft Entra application proxy supports applications built with the [Microsoft Authentication Library (MSAL)](~/identity-platform/v2-overview.md). It handles native client apps by using Microsoft Entra ID tokens in client request headers to preauthenticate users.

Learn about available configurations of application proxy. Read [publishing native and mobile client apps](./application-proxy-configure-native-client-application.md) and [claims-based applications](./application-proxy-configure-for-claims-aware-applications.md).

### Strengthen security with Conditional Access

Application security requires an advanced set of security capabilities that can protect from and respond to complex threats on-premises and in the cloud. Use Conditional Access policies to control access to your applications based on many conditions like location, risk, device type, device compliance, and more. For examples of policies you might deploy, see the article [Conditional Access templates](../conditional-access/concept-conditional-access-policy-common.md).

The following capabilities can be used to support Microsoft Entra application proxy:

* User and location-based Conditional Access: Keep sensitive data protected by limiting user access based on geo-location or an IP address with [location-based Conditional Access policies](~/identity/conditional-access/concept-assignment-network.md).

* Device-based Conditional Access: Ensure only enrolled, approved, and compliant devices can access corporate data with [device-based Conditional Access](~/identity/conditional-access/concept-conditional-access-grant.md).

* Application-based Conditional Access: Work doesn't have to stop when a user isn't on the corporate network. [Secure access to corporate cloud and on-premises apps](~/identity/conditional-access/policy-all-users-device-compliance.md) and maintain control with Conditional Access.

* Risk-based Conditional Access: Protect your data from malicious hackers with a [risk-based Conditional Access policy](https://www.microsoft.com/cloud-platform/conditional-access) that can be applied to all apps and all users, whether on-premises or in the cloud.

* Microsoft Entra My Apps: With your application proxy service deployed, and applications securely published, offer your users a simple hub to discover and access all their applications. Increase productivity with self-service capabilities, such as the ability to request access to new apps and groups or manage access to these resources on behalf of others, through [My Apps](https://aka.ms/AccessPanelDPDownload).

## Manage your implementation

### Required roles

Microsoft advocates the principle of granting the least possible privilege to perform needed tasks with Microsoft Entra ID. [Review the different Azure roles that are available](~/identity/role-based-access-control/permissions-reference.md) and choose the right one to address the needs of each persona. Some roles must be applied temporarily and removed after the deployment is completed.

| Business role| Business tasks| Microsoft Entra roles |
|---|---|---|
| Help desk admin | Handles basic user support tasks like resetting passwords, invalidating refresh tokens, and checking service health. | Helpdesk Administrator |
| Identity admin| Read Microsoft Entra sign-in reports and audit logs to debug application proxy related issues.| Security reader |
| Application owner| Create and manage all aspects of enterprise applications, application registrations, and application proxy settings.| Application Administrator |
| Infrastructure admin | Certificate Rollover Owner | Application Administrator |

Minimizing the number of people who have access to secure information or resources help in reducing the chance of a malicious actor obtaining unauthorized access, or an authorized user inadvertently impacting a sensitive resource.

To manage administrative access effectively and ensure proper auditing, we recommend using just-in-time (JIT) access with [Privileged Identity Management](~/id-governance/privileged-identity-management/pim-configure.md). This approach provides on-demand privileged access to Azure resources and Microsoft Entra ID only when needed.

### Reporting and monitoring

Microsoft Entra ID provides more insights into your organization’s application usage and operational health through [audit logs and reports](~/identity/monitoring-health/concept-provisioning-logs.md?context=azure/active-directory/manage-apps/context/manage-apps-context). Application proxy also makes it easy to monitor connectors from the Microsoft Entra admin center and Windows Event Logs.

#### Application audit logs

These logs provide detailed information about logins to applications configured with application proxy and the device and the user accessing the application. [Audit logs](~/identity/monitoring-health/concept-provisioning-logs.md?context=azure/active-directory/manage-apps/context/manage-apps-context) are located in the Microsoft Entra admin center and in [Audit API](/graph/api/resources/directoryaudit) for export. Additionally, [usage and insights reports](~/identity/monitoring-health/concept-usage-insights-report.md?context=azure/active-directory/manage-apps/context/manage-apps-context) are also available for your application.

#### Private network connector monitoring

The connectors and the service take care of all the high availability tasks. You can monitor the status of your connectors from the application proxy page in the Microsoft Entra admin center. For more information about connector maintenance, see [Understand Microsoft Entra private network connectors](./application-proxy-connectors.md#maintenance).

#### Windows event logs and performance counters

Connectors have both admin and session logs. The admin logs include key events and their errors. The session logs include all the transactions and their processing details. Logs and counters are located in Windows Event Logs. For more information, see [Understand Microsoft Entra private network connectors](./application-proxy-connectors.md#under-the-hood). Follow the [tutorial to configure event log data sources in Azure Monitor](/azure/azure-monitor/agents/data-sources-windows-events).

### Troubleshooting guide and steps

Learn more about common issues and how to resolve them with our guide to [troubleshooting](application-proxy-troubleshoot.md) error messages.

## Related content

The following articles cover common scenarios that can also be used to create troubleshooting guides for your support organization.

- [Troubleshoot links on application page not working](application-proxy-page-links-broken-problem.md)
- [Open ports for my app](application-proxy-add-on-premises-application.md)
- [Configure single sign-on](how-to-configure-sso.md)
- [Configure Kerberos Constrained Delegation](application-proxy-back-end-kerberos-constrained-delegation-how-to.md)
- [Configure with PingAccess](application-proxy-ping-access-publishing-guide.md)
- [Troubleshoot Access the Corporate Application error](application-proxy-sign-in-bad-gateway-timeout-error.md)
- [Troubleshoot installing the application proxy Agent Connector](application-proxy-connector-installation-problem.md)
- [Troubleshoot sign-in problem](application-proxy-troubleshoot.md)
