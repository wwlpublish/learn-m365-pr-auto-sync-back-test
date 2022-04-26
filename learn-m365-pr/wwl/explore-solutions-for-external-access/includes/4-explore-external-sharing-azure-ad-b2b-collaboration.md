Azure Active Directory (Azure AD) B2B collaboration is a feature within External Identities that lets you invite guest users to collaborate with your organization. With B2B collaboration, you can securely share your company's applications and services with guest users from any other organization, while maintaining control over your own corporate data. Work safely and securely with external partners, large or small, even if they don't have Azure AD or an IT department.

:::image type="content" source="../media/b2b-collaboration-overview-24c3069f.png" alt-text="Graphic shows Azure Active Directory B2B collaboration workflow.":::


A simple invitation and redemption process lets partners use their own credentials to access your organization's resources. You can also enable self-service sign-up user flows to let external users sign up for apps or resources themselves. Once the external user has redeemed their invitation or completed sign-up, they're represented in your directory as a user object. B2B collaboration user objects are typically given a user type of "guest." They can also be identified by the \#EXT\# extension in their user principal name.

Developers can use Azure AD business-to-business APIs to customize the invitation process or write applications like self-service sign-up portals. For more information on licensing and pricing information related to guest users, see [Azure Active Directory External Identities pricing](https://azure.microsoft.com/pricing/details/active-directory/external-identities?azure-portal=true).

### Collaborate with any partner using their identities

With Azure AD B2B, the partner uses their own identity management solution. As such, there's no external administrative overhead for your organization. Guest users sign in to your apps and services with their own work, school, or social identities.

 -  The partner uses their own identities and credentials, whether or not they have an Azure AD account.
 -  You don't need to manage external accounts or passwords.
 -  You don't need to sync accounts or manage account lifecycles.

### Manage external access with inbound and outbound settings

B2B collaboration is enabled by default. However, comprehensive admin settings let you control your B2B collaboration with external partners and organizations:

 -  For B2B collaboration with other Azure AD organizations, you can use [cross-tenant access settings](/azure/active-directory/external-identities/cross-tenant-access-overview?azure-portal=true) to manage inbound and outbound B2B collaboration and scope access to specific users, groups, and applications. You can set a default configuration that applies to all external organizations. You can then create individual, organization-specific settings as needed. Using cross-tenant access settings, you can also trust multifactor authentication and device claims (compliant claims and hybrid Azure AD joined claims) from other Azure AD organizations.
 -  You can use [external collaboration settings](/azure/active-directory/external-identities/external-collaboration-settings-configure?azure-portal=true) to:
    
     -  Limit who can invite external users.
     -  Allow or block B2B specific domains.
     -  Set restrictions on guest user access to your directory.

### Easily invite guest users from the Azure AD portal

As an administrator, you can easily add guest users to your organization in the Azure portal.

1.  [Create a new guest user](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal?azure-portal=true) in Azure AD, similar to how you'd add a new user.
2.  Assign guest users to apps or groups.
3.  Send one of the following items:
    
     -  An invitation email that contains a redemption link.
     -  A direct link to an app you want to share.

:::image type="content" source="../media/add-a-b2b-user-to-azure-portal-05d3d59d.png" alt-text="Screenshot showing the invitation email that contains a redemption link or a direct link to an app you want to share.":::


4.  Guest users follow a few simple [redemption steps](/azure/active-directory/external-identities/redemption-experience?azure-portal=true) to sign in.

:::image type="content" source="../media/azure-ad-b2b-consent-screen-fc1f0881.png" alt-text="Screenshot showing the consent window that guest users must complete to access the shared resource.":::


### Allow self-service sign-up

With a self-service sign-up user flow, you can create a sign-up experience for external users who want to access your apps. As part of the sign-up flow, you can provide options for different social or enterprise identity providers. You can also collect information about the user. For more information, see [Self-service sign-up and how to set it up](/azure/active-directory/external-identities/self-service-sign-up-overview?azure-portal=true).

You can also use [API connectors](/azure/active-directory/external-identities/api-connectors-overview?azure-portal=true) to integrate your self-service sign-up user flows with external cloud systems. You can connect with custom approval workflows, perform identity verification, validate user-provided information, and more.

### Use policies to securely share your apps and services

You can use authentication and authorization policies to protect your corporate content. Conditional Access policies, such as multifactor authentication, can be enforced:

 -  At the tenant level.
 -  At the application level.
 -  For specific guest users to protect corporate apps and data.

### Let application and group owners manage their own guest users

You can delegate guest user management to application owners. By doing so, they can add guest users directly to any application they want to share, whether it's a Microsoft application or not.

 -  Administrators set up self-service app and group management.
 -  Non-administrators use their [Access Panel](https://myapps.microsoft.com/?azure-portal=true) to add guest users to applications or groups.

:::image type="content" source="../media/access-panel-manage-app-10892139.png" alt-text="Screenshot showing the access panel for the fictitious Contoso organization for non-administrators to add guest users to applications or groups.":::


### Customize the onboarding experience for B2B guest users

Bring your external partners on board in ways customized to your organization's needs.

 -  Use [Azure AD entitlement management](/azure/active-directory/governance/entitlement-management-overview?azure-portal=true) to configure policies that [manage access for external users](/azure/active-directory/governance/entitlement-management-external-users#how-access-works-for-external-users?azure-portal=true).
 -  Use the [B2B collaboration invitation APIs](/graph/api/resources/invitation?azure-portal=true) to customize your onboarding experiences.

### Integrate with Identity providers

Azure AD supports external identity providers like Facebook, Microsoft accounts, Google, or enterprise identity providers. You can set up federation with these identity providers. By doing so, your external users can sign in with their existing social or enterprise accounts. This process saves them from having to create a new account just for your application. For more information, see [Identity providers for External Identities](/azure/active-directory/external-identities/identity-providers?azure-portal=true).

:::image type="content" source="../media/identity-providers-3ae5713a.png" alt-text="Screenshot showing the All Identity Providers window in Azure Active Directory.":::


### Integrate with SharePoint and OneDrive

You can [enable integration with SharePoint and OneDrive](/sharepoint/sharepoint-azureb2b-integration?azure-portal=true) to share the following items with people outside your organization:

 -  files
 -  folders
 -  list items
 -  document libraries
 -  sites

At the same time, you can use Azure AD B2B for authentication and management.

The users you share resources with are typically added to your directory as guests. Permissions and groups work the same for these guests as they do for internal users. When enabling integration with SharePoint and OneDrive, you'll also enable the [email one-time passcode](/azure/active-directory/external-identities/one-time-passcode?azure-portal=true) feature in Azure AD B2B to serve as a fallback authentication method.

:::image type="content" source="../media/enable-email-one-time-passcode-options-4018c379.png" alt-text="Screenshot showing the email one-time passcode options for guest users.":::


## 

## Knowledge check

Choose the best response for the following question. Then select “Check your answers."