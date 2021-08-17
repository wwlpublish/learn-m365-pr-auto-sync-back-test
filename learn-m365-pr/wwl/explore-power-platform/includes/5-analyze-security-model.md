Because Microsoft Power Platform is governed and authenticated through Azure Active Directory, users must sign in with their work or school Azure AD account to use the service. As a result, administrators have complete visibility into everything Microsoft Power Platform makers and users do. This design makes Microsoft Power Platform products governable, automatable, auditable, and manageable by default.

Microsoft Power Platform’s security model consists of the following layers of security:

 -  **Authentication.** Users are authenticated by Azure Active Directory (Azure AD), and use can be restricted using conditional access policies.
 -  **Licensing.** Licensing is the first control-gate to allowing access to Power Apps components.
 -  **Security roles.** Security roles provide permissions that control the ability to create applications, portals, and workflows.
 -  **Sharing.** A user’s ability to see and use Microsoft Power Platform resources is controlled by sharing the application with the user.
    
     -  Sharing canvas apps is done directly with the user or Azure AD group.
     -  Sharing of model-driven apps is done by assigning the user the appropriate Common Data Service security role.
 -  **Environments.** Environments act as security boundaries by allowing different security needs to be implemented in each environment.
 -  **Connector permissions.** Workflows and canvas apps use connectors. The specific connection’s credentials and associated service entitlements determine permissions when apps use the connectors.
 -  **Advanced security in CDS instances.** Environments with a Common Data Service (CDS) instance add support for more advanced security models that are specific to controlling access to data and services in that CDS instance.
 -  **DLP policies.** Connector use can be further restricted with Data Loss Prevention (DLP) policies. Cross-tenant inbound and outbound restrictions can also be applied to the connectors.

> [!IMPORTANT]
> *When accessing data sources through connectors, all the underlying security that the data source offers is applied, along with the layers of security in the Microsoft Power Platform security model.*

### Environments

Environments are spaces to store, manage, and share an organization’s business data, apps, and flows. They also serve as containers to separate apps that may have different roles, security requirements, or target audiences. How administrators choose to use environments depends on the organization and the apps users are trying to build. For example, organizations can consider the following options when building apps:

 -  Build all apps in a single environment.
 -  Create separate environments that group the Test and Production versions of apps.
 -  Create separate environments that correspond to specific teams or departments in the company. Each environment contains the relevant data and apps for its particular audience.
 -  Create separate environments for different global branches of your company.

When users create an app in an environment, that app is only permitted to connect to the data sources that are also deployed in that same environment, including connections, gateways, flows, and Common Data Service databases. For example, consider a scenario where there are two environments named ‘Test’ and ‘Dev’, respectively, and a Common Data Service database in each of the environments. In this scenario, an app in the ‘Test’ environment is only permitted to connect to the ‘Test’ database; it can't connect to the ‘Dev’ database.

Environments have two built-in roles that provide access to permissions within an environment:

 -  **The Environment Admin role.** The environment administrator can complete all administrative actions on an environment. These actions include adding and removing users or groups to the Environment Admin or Environment Maker role, provisioning a Common Data Service database, setting data loss prevention policies, and viewing and managing all resources in the environment.
 -  **The Environment Maker role.** The environment maker can create resources within an environment, including apps, connections, custom connectors, gateways, and flows using Power Automate.

Users or security groups can be assigned to either of these two roles by an Environment Admin from the Microsoft Power Platform admin center.
