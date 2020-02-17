This unit will cover the different topology options available to developers that are supported by the Microsoft identity platform. These topologies include consumers, enterprises, Business to Business and Business to Customer.

## Consumer

Consumers refer to Microsoft Accounts that are created by users for personal use. The Microsoft Account is the combination of an email address and a password that a user uses to sign in to all consumer-oriented Microsoft products and cloud services such as Outlook, OneDrive, MSN, or Xbox LIVE.​

The Microsoft identity platform enables developers to create applications that allow users to sign-in using either a Microsoft Account (Personal Account) or a Work or School Account (an Azure AD identity).​

While there are many similarities between Microsoft Accounts and Azure AD accounts, Microsoft Accounts are primarily for personal or consumer services. Some small business will also use consumer accounts and consumer services like email and OneDrive. Some similarities between the topologies include account and password management, support multi-factor authentication, and password less authentication. Unlike Microsoft Accounts, Azure AD accounts have additional security-related features that are available in enterprise scenarios.​

As an app developer, you can use Microsoft Account as a standards-based approach for adding single sign-on (SSO) to your app, allowing it to work with a user's pre-existing credentials. Microsoft identity also provides APIs that can help you build personalized app experiences using the users personal Office 365 resources.​

## Enterprises

Enterprises refer to Azure Active Directory (Azure AD), Microsoft's cloud-based identity and access management service. Azure AD helps your employees sign in and access internal resources such as apps in your corporate network or intranet and cloud apps that are developed by your organization. In additional to internal resources, your employees can access external resources such as Microsoft Office 365 and many other software-as-a-service (SaaS) applications.

As previously stated, Azure AD provides organizations and developers two important capabilities when it comes to building custom applications. Employee user accounts and groups are securely stored within an Azure AD directory. Employees can use these identities to sign in to internal and external resources.

IT administrators can also register applications with Azure AD that can be used in conjunction with software applications to control access and permissions to protected resources.

As an app developer, you can use Azure AD as a standards-based approach for adding single sign-on (SSO) to your app, allowing it to work with a user's pre-existing credentials. Azure AD also provides APIs that can help you build personalized app experiences using existing organizational data.

## Business to Business (B2B)

Azure Active Directory (Azure AD) business-to-business (B2B) collaboration lets you securely share your company's applications and services with guest users from any other organization, while maintaining control over your own corporate data. Work safely and securely with external partners, large, or small, even if they don't have Azure AD or an IT department. A simple invitation and redemption process lets partners use their own credentials to access your company's resources. Developers can use Azure AD business-to-business APIs to customize the invitation process or write applications like self-service sign-up portals.

With Azure AD B2B, the partner uses their own identity management solution, so there is no external administrative overhead for your organization. The partner uses their own identities and credentials; Azure AD isn't required. In addition, you don't need to manage external accounts or passwords, nor do you need to sync accounts or manage the lifecycle of accounts.

Let's look at how an external user will access your resources in a B2B scenario.

In this scenario, you are in the Contoso organization and Fabrikam is a partner of yours. You have configured Azure AD B2B with Fabrikam. A user from Fabrikam needs to access content within the Contoso organization. Because the content is protected by Azure AD, the user will be redirected to Contoso to sign in for authentication and authorization to obtain an access token from Contoso that is required to access the content.

Consoto's Azure AD recognizes the user is a guest from Fabrikam and that Fabrikam is configured for B2B with Contoso, so Azure AD redirects the user to Fabrikam for authentication. After the user signs in with Fabrikam, they're redirected back to Contoso's Azure AD that validates the Fabrikam generated token and creates a new token for the user to access the content. Because the new token was created by Contoso's Azure AD directory, it can be used to access the content because it only trusts the Contoso Azure AD directory.

### Grant guest users access and securing corporate resources

Azure AD B2B provides IT administrators and developers multiple ways to grant guest users from another organization access to your corporate content. An administrator can create a new guest user in the Azure AD portal, similar to how you'd add a new user, they can be sent email invitation or added in bulk using PowerShell. Administrators can also delegate group owners and application owners manage their own guest user so they can add guests directly to any application they want to share.

Once a guest user has been added to your directory, you can use Azure AD's Conditional Access policies, such as multi-factor authentication, to further protect your content at the tenant level, application level or for specific guest users.

## Business to Customer (B2C)

Azure Active Directory B2C (Azure AD B2C) is a customer identity access management (CIAM) solution capable of supporting millions of users and billions of authentications per day. It takes care of the scaling and safety of the authentication platform, monitoring, and automatically handling threats like denial-of-service, password spray, or brute force attacks. Azure AD B2C uses standards-based authentication protocols including OpenID Connect and OAuth 2.0.

With Azure AD B2C, users will authenticate with their preferred identity provider that has been configured and by your IT administrator. The user signs in using a customized sign-in page hosted by Azure AD B2C.

Azure AD B2C is a white-label authentication solution. This means you can customize the entire user experience with your brand so that it blends seamlessly with your web and mobile applications.

Customize every page displayed by Azure AD B2C when your users sign up, sign in, and modify their profile information. Customize the HTML, CSS, and JavaScript in your user journeys so that the Azure AD B2C experience looks and feels like it's a native part of your application.

After the user signs in, you can implement progressive polling. Progressive polling allows your customers to quickly complete their first transaction by supplying only the minimum required information necessary. Over time, you can gradually collect more profile data from the customer each time they sign in. You can store up to 100 custom attributes per user in Azure AD B2C or integrate with external systems to store even more details on your users.

### Comparing Azure AD B2B and B2C

Both Azure Active Directory (Azure AD) B2B collaboration and Azure AD B2C allow you to work with external users in Azure AD. But how do they compare?

Azure AD B2B is for businesses that want to securely share files and resources with external users so they can collaborate. An Azure admin sets up B2B in the Azure portal, and Azure AD takes care of federation between your business and your external partner. Users sign in to the shared resources using a simple invitation and redemption process with their work or school account, or any email account.

Azure AD B2C is primarily for businesses and developers that create customer-facing apps. With Azure AD B2C, developers can use Azure AD as the full-featured identity system for their application, while letting customers sign in with an identity they already have established (like Facebook or Gmail).
