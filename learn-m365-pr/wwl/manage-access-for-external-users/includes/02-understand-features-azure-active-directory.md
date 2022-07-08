Azure Active Directory (Azure AD), part of Microsoft Entra, is the cloud-based identity and access management service for Microsoft 365. 

You can use Azure AD to control access to your apps and your app resources, based on your business requirements. For example, you can use Azure AD to require multifactor authentication when accessing important organizational resources. Additionally, you can use Azure AD to automate user provisioning between your existing Windows Server AD and your cloud apps, including Microsoft 365. Finally, Azure AD gives you powerful tools to automatically help protect user identities and credentials and to meet your access governance requirements.

:::image type="content" source="../media/microsoft-entra.png" alt-text="Microsoft Entra Admin center":::

## Features in Azure AD

|Category|Description|
|-------|-----------|
|Application management|Manage your cloud and on-premises apps using Application Proxy, single sign-on, the My Apps portal (also known as the Access panel), and Software as a Service (SaaS) apps. |
|Authentication|Manage Azure Active Directory self-service password reset, multifactor authentication, custom banned password list, and smart lockout. |
|Azure Active Directory for developers|Build apps that sign in all Microsoft identities, get tokens to call Microsoft Graph, other Microsoft APIs, or custom APIs. |
|Business-to-Business (B2B)|Manage your guests and external partners, while maintaining control over your own corporate data. |
|Business-to-Customer (B2C)|Customize and control how users sign up, sign in, and manage their profiles when using your apps. |
|Conditional Access|Manage access to your cloud apps. |
|Device Management|Manage how your cloud or on-premises devices access your corporate data. |
|Domain services|Join Azure virtual machines to a domain without using domain controllers. |
|Enterprise users|Manage license assignment, access to apps, and set up delegates using groups and administrator roles. |
|Hybrid identity|Use Azure Active Directory Connect and Connect Health to provide a single user identity for authentication and authorization to all resources, regardless of location (cloud or on-premises).|
|Identity governance|Manage your organization's identity through employee, business partner, vendor, service, and app access controls. You can also perform access reviews. |
|Identity protection|Detect potential vulnerabilities affecting your organization's identities, configure policies to respond to suspicious actions, and then take appropriate action to resolve them. |
|Managed identities for Azure resources|Provides your Azure services with an automatically managed identity in Azure AD that can authenticate any Azure AD-supported authentication service, including Key Vault. |
|Privileged identity management (PIM)|Manage, control, and monitor access within your organization. This feature includes access to resources in Azure AD and Azure, and other Microsoft Online Services, like Microsoft 365 and Intune. |
|Reports and monitoring|Gain insights into the security and usage patterns in your environment. |

## External collaboration in Azure Active Directory and Microsoft 365

Microsoft Teams, SharePoint, and OneDrive are three of the most used ways to collaborate and share content with external users.

Azure Active Directory (Azure AD) business-to-business (B2B) collaboration is a feature within External Identities that lets you invite guests to collaborate with your organization. With B2B collaboration, you can securely share Microsoft 365 applications and services with guests from any other organization, while maintaining control over your own corporate data.

:::image type="content" source="../media/aad-b2b.png" alt-text="Azure Active Directory (Azure AD) business-to-business (B2B)":::

With Azure AD B2B, the partner uses their own identity management solution, so there is no external administrative overhead for your organization. Guests sign in to your apps and services with their own work, school, or social identities.

* The partner uses their own identities and credentials; Azure AD is not required.

* You don't need to manage external accounts or passwords.

* You don't need to sync accounts or manage account lifecycles.

## Azure AD entitlement management

Employees in organizations need access to various groups, applications, and sites to perform their job. Managing this access is challenging, as requirements change. Enterprise organizations often face challenges when managing employee access to resources such as:

* Users may not know what access they should have, and even if they do, they may have difficulty locating the right individuals to approve their access

* Once users find and receive access to a resource, they may hold on to access longer than is required for business purposes

These problems are compounded for users who need access from another organization, such as external users that are from supply chain organizations or other business partners. For example, you may not know who in the other organization needs access to your organization's resources, and they won't know what applications, groups, or sites your organization is using.

Azure Active Directory (Azure AD) entitlement management is an **identity governance feature** that enables organizations to manage identity and access lifecycle at scale, by automating access request workflows, access assignments, reviews, and expiration. Azure AD entitlement management can help you more efficiently manage access to groups, applications, and SharePoint sites for internal users, and also for users outside your organization who need access to those resources.

With entitlement management, you can delegate access governance to these non-administrators because they're the ones who know which users need access, for how long, and to which resources. Delegating to non-administrators ensures the right people are managing access for their departments.

:::image type="content" source="../media/delegate-admin-dept-managers.png" alt-text="Delegate from IT administrator to managers":::



### Access packages
Entitlement management introduces to Azure AD the concept of an access package. An access package is a bundle of all the resources with the access a user needs to work on a project or perform their task. Access packages are used to govern access for your internal employees and users outside your organization. You can manage user access to the following resources with entitlement management:

* Membership of Azure AD security groups.
* Membership of Microsoft 365 Groups and Teams.
* Assignment to Azure AD enterprise applications, including SaaS applications and custom-integrated applications that support federation/single sign-on and/or provisioning.
* Membership of SharePoint sites.

You can also control access to other resources that rely upon Azure AD security groups or Microsoft 365 Groups. For example, you can provide:

* Licenses for Microsoft 365 by using an Azure AD security group in an access package and configuring group-based licensing for that group.
* Access to manage Azure resources by using an Azure AD security group in an access package and creating an Azure role assignment for that group.
* Access to manage Azure AD roles by using groups assignable to Azure AD roles in an access package and assigning an Azure AD role to that group.

:::image type="content" source="../media/access-package.png" alt-text="Access package":::


