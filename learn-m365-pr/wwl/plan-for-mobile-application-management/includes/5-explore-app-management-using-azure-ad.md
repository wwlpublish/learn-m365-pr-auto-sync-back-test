Organizations often have hundreds of applications that users depend on to get their work done. Users access these applications from many devices and locations. New applications are added, developed, and retired all the time. With so many apps and access points, it's important to use an identity solution that works with them all.

A centralized identity system provides a single place to store user information that can then be used by all applications. These systems have come to be known as Identity and Access Management (IAM) systems. Azure Active Directory is the IAM system for the Microsoft cloud.

Azure AD provides a single place to store information about digital identities. You can configure your software applications to use Azure AD as the place where user information is stored. Azure AD must be configured to integrate with an application. In other words, it needs to know what apps are using it for identities. Making Azure AD aware of these apps, and how it should handle them, is known as application management.

You manage applications on the **Enterprise applications** page located in the **Manage** section of the Azure Active Directory portal.

:::image type="content" source="../media/enterprise-applications-in-azure-ad-d009f19b.png" alt-text="screenshot of the Azure AD portal and the Enterprise Applications page":::


Azure AD can provide organizations with identity and access control. Apps are registered with Azure AD either by selecting one of the available apps from the gallery or by adding your custom app, which can run in the cloud or on-premises. Access to an app is provided by assigning it to a user or group. It doesn't matter whether the group has static or dynamic membership. You can also use Azure AD for ongoing access management, usage evaluation, and reporting.

Azure AD provides several benefits for application management, including:

 -  Application authentication and authorization.
 -  User authentication and authorization.
 -  SSO using password hash synchronization.
 -  User provisioning and synchronization.
 -  Role-based access control. The directory can be used to define application roles to complete role-based authorization checks in an application.
 -  Application publishing and proxy. An application can be published from a private network to the Internet.

Azure AD supports extensive access management for configured applications, enabling companies to easily achieve the right access policies. Policies can range from automatic, attribute-based assignment through delegation to administrator management. With Azure AD, you can easily achieve complex policies that combine multiple management models for a single application. Management rules can even be reused across applications with the same audiences.

Azure AD sits in the middle between cloud and on-premises apps and provides identity management to each.

:::image type="content" source="../media/app-management-in-azure-ad-overview-d614d97b.png" alt-text="diagram showing how Azure AD sits in the middle between cloud and on-premises apps and provides identity management to each":::


After an app is assigned to a user, they can access it on the access panel. The access panel is a web-based portal, available on the Microsoft Apps site. Employees can also use self-service group and app management capabilities through the access panel. On Android and iOS devices, users can also access the apps by using the My Apps mobile app.

You can use Azure AD as your identity system for just about any app. Many apps are already pre-configured and can be set up with minimal effort. These pre-configured apps are published in the [Azure AD App Gallery](/azure/active-directory/saas-apps/).

> [!TIP]
> The Azure AD app gallery contains many popular applications that are already pre-configured to work with Azure AD as an identity provider.

### Improve productivity with single sign-on

Single sign-on (SSO) provides a unified user experience between Microsoft 365 and all the other apps you use. The purpose of SSO is to eliminate the need to constantly enter your username and password. You can manually configure most apps for single sign-on if they aren't already in the gallery. When building your own line-of-business applications, you can also integrate them with Azure AD to support single sign-on.

Azure AD provides several SSO options. Some of the most popular are SAML-based SSO and OIDC-based SSO. To learn more about integrating apps to enable SSO, see [single sign-on options](/azure/active-directory/manage-apps/sso-options).

### Manage risk with Conditional Access policies

Coupling Azure AD single sign-on (SSO) with [Conditional access](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps) provides high levels of security for accessing applications. Conditional access policies provide granular control to apps based on conditions you set. Azure AD Conditional Access can also be used to set access policies for specific users or groups. Conditional access policies enable organizations to implement automated access control for accessing their cloud apps. Automated access control is based on conditions. For example, Conditional Access policies can specify whether:

 -  application access is permitted outside the company network.
 -  access is allowed only from devices that are compliant.
 -  users must be authenticated by using MFA.

**Additional reading.** For more information, see [Application Management in Azure Active Directory](/azure/active-directory/active-directory-apps-index).

### What is Azure Active Directory B2C?

Azure Active Directory B2C provides business-to-customer identity as a service. Your customers use their preferred social, enterprise, or local account identities to get single sign-on access to your applications and APIs.

:::image type="content" source="../media/azure-ad-b2c-overview-81a29502.png" alt-text="diagram showing overview of customer and business features in Azure AD B2C":::


Azure Active Directory B2C is a customer identity access management solution. It's capable of supporting millions of users and billions of authentications per day. It takes care of the scaling and safety of the authentication platform. It does so by monitoring the platform and automatically handling threats like denial-of-service, password spray, or brute force attacks.

**Additional reading.** For more information, see [What is Azure Active Directory B2C?](/azure/active-directory-b2c/overview)

### 
