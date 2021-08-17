Enterprise developers and software-as-a-service (SaaS) providers can develop commercial cloud services or line-of-business applications that can be integrated with Azure Active Directory (Azure AD) to provide secure sign-in and authorization for their services. To integrate an application or service with Azure AD, a developer must first register the application with Azure AD.

> [!NOTE]
> Sometimes the meaning of the term "application" can be misunderstood when used in the context of Azure AD. An application that has been integrated with Azure AD has implications that go beyond the software aspect. "Application" is frequently used as a conceptual term, referring to not only the application software, but also its Azure AD registration and its role in authentication/authorization "conversations" at runtime. By definition, an application can function in a [client](/azure/active-directory/develop/active-directory-dev-glossary) role (consuming a resource), a [resource server](/azure/active-directory/develop/active-directory-dev-glossary) role (exposing APIs to clients), or even both.

As previously mentioned, any application that wants to use the capabilities of Azure AD must first be registered in an Azure AD tenant. This registration process involves giving Azure AD details about your application, such as the URL where it’s located, the URL to send replies after a user is authenticated, the URL that identifies the app, and so on.

The following graphic shows that application registration enables access to a Line of Business (LoB) app by using Azure AD as the authentication provider. If a user connects to an app and the user doesn't have a valid token, they're redirected to Azure AD for authentication. At that point, they're redirected and granted access to the app.

:::image type="content" source="../media/app-registration-uses-aad-as-auth-provider-3ada1307.jpg" alt-text="graphic shows that application registration allows access to a LoB app by using Azure AD as the authentication provider":::


### To register a new application using the Azure portal

Complete the following steps to register a new application in the Azure portal:

1.  Sign in to the [Azure portal](https://portal.azure.com/?azure-portal=true).
2.  If your account gives you access to more than one Azure AD tenant, select your account in the top-right corner and set your portal session to the appropriate Azure AD tenant.
3.  In the left-hand navigation pane, select the **Azure Active Directory service**, select **App registrations**, and then select **New application registration**.
4.  When the **Create page** appears, enter the application's registration information:
    
     -  **Name:** Enter a meaningful application name
     -  **Application type:**
        
         -  Select **Native** for [client applications](/azure/active-directory/develop/active-directory-dev-glossary) that are installed locally on a device. This setting is used for OAuth public [native clients](/azure/active-directory/develop/active-directory-dev-glossary).
         -  Select **Web app / API** for client applications and [resource/API applications](/azure/active-directory/develop/active-directory-dev-glossary) that are installed on a secure server. This setting is used for OAuth confidential [web clients](/azure/active-directory/develop/active-directory-dev-glossary) and public [user-agent-based clients](/azure/active-directory/develop/active-directory-dev-glossary). The same application can also expose both a client and resource/API.
     -  **Sign-On URL:** For Web app / API applications, provide the base URL of your app. For example, **http://localhost:31544** may be the URL for a web app running on your local machine. Users would use this URL to sign in to a web client application.
     -  **Redirect URL:** For Native applications, provide the URL used by Azure AD to return token responses. Enter a value specific to your application, such as **http://MyFirstAADApp**.
5.  When finished, select **Create**.

After selecting **Create** in the final step, Azure AD assigns a unique Application ID to the application and navigates to the application's main registration page. Depending on whether the application is a web or native application, different options are provided to add extra capabilities to the application. The next unit continues this discussion by providing an overview of consent and details on enabling more configuration features in the application registration.

**Additional reading.** For specific examples of web applications and native applications, see the [Get Started section of the Azure Active Directory for developers](/azure/active-directory/develop/active-directory-developers-guide) site.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”