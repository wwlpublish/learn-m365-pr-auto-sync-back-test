Multi-tenant applications allow sign-ins by user accounts from Azure AD tenants other than the tenant in which the app was initially registered. The Azure AD consent framework enables a tenant administrator or user in these other tenants to consent to (or deny) an application's request for permission to access their resources.

For example, perhaps a web application requires read-only access to a user's calendar in Microsoft 365. It's the identity platform's consent framework that enables the prompt asking the user to consent to the app's request for permission to read their calendar. If the user consents, the application is able to call the Microsoft Graph API on their behalf and get their calendar data.

Consent is the process of a user granting authorization to an application to access protected resources on their behalf. An admin or user can be asked for consent to allow access to their organization/individual data.

Consent can be initiated in various ways. For example:

 -  Users can be prompted for consent when they attempt to sign-in to an application for the first time.
 -  Depending on the permissions they require, some applications may require an administrator to be the one who grants consent.

### User consent

A user can authorize an application to access some data at the protected resource, while acting as that user. The permissions that allow this type of access are called "delegated permissions."

User consent is initiated when a user signs in to an application. After the user has provided sign-in credentials, they're checked to determine whether consent has already been granted. If no previous record of user or admin consent for the required permissions exists, the user is directed to the consent prompt window to grant the application the requested permissions.

User consent by non-administrators is possible only in organizations where user consent is allowed for the application and for the set of permissions the application requires. If user consent is disabled, or if users aren't allowed to consent for the requested permissions, they won't be prompted for consent. If users are allowed to consent and they accept the requested permissions, the consent is recorded and they usually don't have to consent again on future sign-ins to the same application.

#### User consent settings

Users are in control of their data. A Privileged Administrator can configure whether non-administrator users are allowed to grant user consent to an application. This setting can take into account aspects of the application and the application's publisher, and the permissions being requested.

As an administrator, you can choose whether user consent is allowed. If you choose to allow user consent, you can also choose what conditions must be met before an application can be consented to by a user.

By choosing which application consent policies apply for all users, you can set limits on when users are allowed to grant consent to applications and on when they’ll be required to request administrator review and approval. The Azure portal provides the following built-in options:

 -  **You can disable user consent**. Users can't grant permissions to applications. Users continue to sign in to applications they've previously consented to or to applications that administrators have granted consent to on their behalf, but they won't be allowed to consent to new permissions to applications on their own. Only users who have been granted a directory role that includes the permission to grant consent can consent to new applications.
 -  **Users can consent to applications from verified publishers or your organization, but only for permissions you select.** All users can consent only to applications that were published by a [verified publisher](/azure/active-directory/develop/publisher-verification-overview?azure-portal=true) and applications that are registered in your tenant. Users can consent only to the permissions that you've classified as low impact. You must [classify permissions](/azure/active-directory/manage-apps/configure-permission-classifications?azure-portal=true) to select which permissions users are allowed to consent to.
 -  **Users can consent to all applications**. This option allows all users to consent to any permissions that don't require admin consent, for any application.

For most organizations, one of the built-in options will be appropriate. Some advanced customers may want more control over the conditions that govern when users are allowed to consent. These customers can [create a custom app consent policy](/azure/active-directory/manage-apps/manage-app-consent-policies#create-a-custom-app-consent-policy?azure-portal=true) and configure those policies to apply to user consent.

### Admin consent

During admin consent, a Privileged Administrator may grant an application access on behalf of other users (usually, on behalf of the entire organization). Also during admin consent, applications or services provide direct access to an API, which can be used by the application if there's no signed-in user.

When your organization purchases a license or subscription for a new application, you may proactively want to set up the application so that all users in the organization can use it. To avoid the need for user consent, an administrator can grant consent for the application on behalf of all users in the organization.

After an administrator grants admin consent on behalf of the organization, users usually aren't prompted for consent for that application. In certain cases, a user may be prompted for consent even after consent was granted by an administrator. For example, an application requests another permission that the administrator hasn't already granted.

Granting admin consent on behalf of an organization is a sensitive operation. It can potentially allow the application's publisher access to significant portions of the organization's data, or the permission to do highly privileged operations. Examples of such operations may include role management, full access to all mailboxes or all sites, and full user impersonation.

Before you grant tenant-wide admin consent, ensure that you trust the application and the application publisher for the level of access you're granting. If you aren't confident that you understand who controls the application and why the application is requesting the permissions, you should NOT grant consent.

For step-by-step guidance on whether to grant an application admin consent, see [Evaluating a request for tenant-wide admin consent](/azure/active-directory/manage-apps/manage-consent-requests#evaluate-a-request-for-tenant-wide-admin-consent?azure-portal=true).

For step-by-step instructions for granting tenant-wide admin consent from the Azure portal, see [Grant tenant-wide admin consent to an application](/azure/active-directory/manage-apps/grant-admin-consent?azure-portal=true).

#### Grant consent on behalf of a specific user

Instead of granting consent for an entire organization, an admin can also use the Microsoft Graph API to grant consent to delegated permissions on behalf of a single user. For a detailed example that uses Microsoft Graph PowerShell, see [Grant consent on behalf of a single user by using PowerShell](/azure/active-directory/manage-apps/manage-consent-requests?azure-portal=true).

#### Limit user access to an application

User access to applications can still be limited, even when tenant-wide admin consent has been granted. Configure the application’s properties to require user assignment to limit user access to the application. For more information, see [Methods for assigning users and groups](/azure/active-directory/manage-apps/assign-user-or-group-access-portal?azure-portal=true).

For a broader overview, including how to handle other complex scenarios, see [Use Azure AD for application access management](/azure/active-directory/manage-apps/what-is-access-management?azure-portal=true).

#### Admin consent workflow

The admin consent workflow gives users a way to request admin consent for applications when they aren't allowed to consent themselves. When the admin consent workflow is enabled, users are presented with an "Approval required" window. This window requests admin approval for access to the application.

After users submit the admin consent request, the admins who have been designated as reviewers receive a notification. The users are notified after a reviewer has acted on their request. For step-by-step instructions for configuring the admin consent workflow by using the Azure portal, see the article titled: [Configure the admin consent workflow](/azure/active-directory/manage-apps/configure-admin-consent-workflow?azure-portal=true).

#### How users request admin consent

After the admin consent workflow is enabled, users can request admin approval for an application that they're unauthorized to consent to. Here are the steps in the process:

1.  A user attempts to sign in to the application.
2.  An "Approval required" message appears. The user types a justification for needing access to the application and then selects "Request approval."
3.  A "Request sent" message confirms that the request was submitted to the admin. If the user sends several requests, only the first request is submitted to the admin.
4.  The user receives an email notification when the request is approved, denied, or blocked.

### Example of the consent experience

The following steps describe how the consent experience works for both application developers and users.

1.  Assume you have a web client application that needs to request specific permissions to access a resource/API. The Azure portal is used to declare permission requests at configuration time. Like other configuration settings, they become part of the application's Azure AD registration.
2.  Consider that your application’s permissions have been updated, the application is running, and a user is about to use it for the first time. First the application needs to obtain an authorization code from Azure AD’s /authorize endpoint. The authorization code can then be used to acquire a new access and refresh token.
3.  If the user isn't already authenticated, Azure AD's **`/authorize`** endpoint prompts for sign-in.
4.  After the user has signed in, Azure AD determines if the user needs to be shown a consent page. This determination is based on whether the user (or the organization’s administrator) has already granted the application consent. If consent hasn't already been granted, Azure AD prompts the user for consent and displays the required permissions it needs to function. The permissions that are displayed in the consent dialog match the ones selected in the Delegated Permissions in the Azure portal.
5.  After the user grants consent, an authorization code is returned to your application, which is redeemed to acquire an access token and refresh token. For more information about this flow, see the [Oauth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow?azure-portal=true).
6.  An administrator can also consent to an application's delegated permissions for all the users in the company's tenant. Administrative consent prevents the consent dialog from appearing for every user in the tenant, and can be done in the Azure portal by users with the administrator role. Complete the following steps to consent to an app's delegated permissions:
    
    1.  Go to the **API permissions** page for your application.
    2.  Select the **Grant admin consent** button.
