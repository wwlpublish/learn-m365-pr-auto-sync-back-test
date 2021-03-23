At this point, you have a basic understanding of what an **Access token** is, and you've seen how to register your application with the Microsoft Identity platform using the Azure AD application registration. Now let’s learn how to retrieve an access token so it can be used by your team to build the customer application. 

Token interaction can be challenging if you don’t use a library to abstract away the protocol details, validation, token caching, and security. Fortunately, you can use a library called **Microsoft Authentication Library 2.0 (MSAL)** to simplify this process.  

The Microsoft Authentication Library (MSAL) enables developers to acquire tokens from the Microsoft identity platform to authenticate users and access secured web APIs like Microsoft Graph.
MSAL is also available in other platforms such as .NET, iOS, and Android.

## Authentication flow

One of the authentication flows for the application that uses MSAL, which we'll use in our exercise, is as follows:

1. The application redirects the user to sign in.
1. The user signs in successfully, requesting an authorization code.
1. The authorization code is returned to the application.
1. The application then requests the tokens using the authorization code.
1. The access token and other information are returned after successful validation.
1. The application can now call Graph services with an access token in the authorization header.
1. Graph validates the token and sends the response back.

The authentication flow is shown in the following diagram:

:::image type="content" source="../media/6-auth-flow.png" alt-text="The diagram of the authentication flow."::: 
