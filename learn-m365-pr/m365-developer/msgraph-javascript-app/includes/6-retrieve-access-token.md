At this point, you have a basic understanding of what an access token is. You've also seen how to register your application with the Microsoft identity platform by using Azure Active Directory. Now you'll learn how to retrieve an access token so your team can use it to build the customer application.

Token interaction can be challenging if you don't use a library to abstract away the protocol details, validation, token caching, and security. Fortunately, you can use a library called *Microsoft Authentication Library (MSAL) 2.0* to simplify this process.

MSAL enables developers to acquire tokens from the Microsoft identity platform to authenticate users and access secured web APIs like Microsoft Graph. MSAL is also available in other platforms such as .NET, iOS, and Android.

## Authentication flow

One of the authentication flows for the application that uses MSAL, which we'll use in our exercise, is as follows:

1. The application redirects the user to sign in.
1. The user signs in successfully and requests an authorization code.
1. The authorization code is returned to the application.
1. The application requests the token by using the authorization code.
1. The access token and other information are returned after successful validation.
1. The application can call Microsoft Graph services with an access token in the authorization header.
1. Microsoft Graph validates the token.
1. Microsoft Graph sends back the response.

The following diagram shows the authentication flow:

:::image type="content" source="../media/6-auth-flow.png" alt-text="Diagram of the authentication flow.":::
