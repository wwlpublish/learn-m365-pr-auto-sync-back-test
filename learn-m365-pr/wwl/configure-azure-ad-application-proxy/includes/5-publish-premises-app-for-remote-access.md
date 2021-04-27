At this point, you're now ready to publish an on-premises app for remote access. Once the app is published, you must verify the app functions properly by adding a test user and then testing your published app.

### Publish an on-premises app for remote access

Complete the following steps to publish an on-premises app for remote access:

1.  Sign in as an administrator in the [Azure portal](https://portal.azure.com/?azure-portal=true).
2.  Select **Azure Active Directory** &gt; **Enterprise applications** &gt; **New application**.
3.  Select **All**, then select **On-premises application**.
4.  Provide the following information about your application:
    
     *  **Name.** The name of the application that will appear on the access panel and in the Azure portal.
     *  **Internal URL.** The URL that you use to access the application from inside your private network. You can provide a specific path on the backend server to publish, while the rest of the server is unpublished. In this way, you can publish different sites on the same server as different apps and give each one its own name and access rules.
     *  **External URL.** The address your users will enter to access the app from outside your network. If you don't want to use the default Application Proxy domain, read about [custom domains in Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-custom-domain?azure-portal=true).
     *  **Pre-Authentication.** This setting indicates how Application Proxy verifies users before giving them access to your application.
     *  **Azure Active Directory.** Application Proxy redirects users to sign in with Azure AD, which authenticates their permissions for the directory and application. It's recommended that you keep this option as the default, so that you can take advantage of Azure AD security features like conditional access and Multi-Factor Authentication.
     *  **Passthrough.** Users don't have to authenticate against Azure Active Directory to access the application. You can still set up authentication requirements on the backend.
     *  **Connector group.** Connectors process the remote access to your application, and connector groups help you organize connectors and apps by region, network, or purpose. If you don't have any connector groups created yet, your app is assigned to **Default**.
5.  If necessary, configure any other required settings. For most applications, you should keep these settings in their default states.
    
     *  **Backend Application Timeout.** Set this value to **Long** only if your application is slow to authenticate and connect.
     *  **Translate URLs in Headers.** Keep this value as **Yes** unless your application required the original host header in the authentication request.
     *  **Translate URLs in Application Body.** Keep this value as **No** unless you have hardcoded HTML links to other on-premises applications, and don't use custom domains. For more information, see [Link translation with Application Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-hard-coded-link-translation?azure-portal=true).
6.  Select **Add**.

### Add a test user

To test that your app was published correctly, add a test user account. Verify that this account already has permissions to access the app from inside the corporate network.

1.  Back on the **Quick start** blade, select **Assign a user for testing (required)**.
2.  On the **Users and groups** blade, select **Add user**.
3.  On the **Add assignment** blade, select **Users and groups** and then choose the account you want to add.
4.  Select **Assign**.

### Test your published app

In your browser, navigate to the external URL that you configured during the publish step. From the start screen, sign in with the test account you set up.
