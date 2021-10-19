Once an organization has published an on-premises app for remote access, it must verify the app functions properly by adding a test user and then testing the published app.

### Publish an on-premises app for remote access

Complete the following steps to publish an on-premises app for remote access:

1.  Sign in as an administrator in the [Azure portal](https://portal.azure.com/?azure-portal=true).
2.  Select **Azure Active Directory** &gt; **Enterprise applications** &gt; **New application**.
3.  Select **All**, then select **On-premises application**.
4.  Provide the following information about your application:
    
     -  **Name.** The name of the application that will appear on the access panel and in the Azure portal.
     -  **Internal URL.** The URL that accesses the application from inside the organization's private network. A specific path can be provided on the backend server to publish, while the rest of the server is unpublished. In this way, different sites can be published on the same server as different apps, and each one can be given its own name and access rules.
     -  **External URL.** The address that users will enter to access the app from outside the organization's network. If the organization doesn't want to use the default Application Proxy domain, read about [custom domains in Azure AD Application Proxy](/azure/active-directory/manage-apps/application-proxy-configure-custom-domain).
     -  **Pre-Authentication.** This setting indicates how Application Proxy verifies users before giving them access to the application.
     -  **Azure Active Directory.** Application Proxy redirects users to sign in with Azure AD, which authenticates their permissions for the directory and application. It's recommended that the organization keep this option as the default so that it can take advantage of Azure AD security features like Conditional Access and multifactor authentication.
     -  **Passthrough.** Users don't have to authenticate against Azure Active Directory to access the application. Authentication requirements can still be set up on the backend.
     -  **Connector group.** Connectors process the remote access to the application, and connector groups help organize connectors and apps by region, network, or purpose. If no connector groups have been created, the app is assigned to **Default**.
5.  If necessary, configure any other required settings. For most applications, these settings should be kept in their default states.
    
     -  **Backend Application Timeout.** Set this value to **Long** only if the application is slow to authenticate and connect.
     -  **Translate URLs in Headers.** Keep this value as **Yes** unless the application required the original host header in the authentication request.
     -  **Translate URLs in Application Body.** Keep this value as **No** unless the organization has hardcoded HTML links to other on-premises applications, and don't use custom domains. For more information, see [Link translation with Application Proxy](/azure/active-directory/manage-apps/application-proxy-configure-hard-coded-link-translation).
6.  Select **Add**.

### Add a test user

An organization should test whether its new app was published correctly by adding a test user account. Verify that this account already has permissions to access the app from inside the corporate network.

1.  Back on the **Quick start** page, select **Assign a user for testing (required)**.
2.  On the **Users and groups** page, select **Add user**.
3.  On the **Add assignment** view, select **Users and groups** and then select the desired user account.
4.  Select **Assign**.

### Test your published app

In your browser, navigate to the external URL that was configured during the publish step. From the start screen, sign in with the test account that was set up.
