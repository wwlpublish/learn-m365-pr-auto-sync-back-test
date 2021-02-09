# Sign in your app using Microsoft Graph Toolkit components

Upon completing this module, you will learn how to authenticate your application to access Microsoft Graph using the Login component of the Toolkit.

## What is the purpose of adding Login component in your application

You can add Login component of the Toolkit to implement login and logout functionality and all the authentication logic associated with it using one line of code in the application.
A Toolkit provider needs to be initialized to use the login component to work.

## What are providers in Microsoft Graph Toolkit

Providers simplify implementing authentication for your application and make calls to Microsoft Graph using the JavaScript client SDK.
Providers are required and needs to be initialized before using any web components in the Toolkit.However, providers can be used on their own, without components to implement authentication for your application.
Providers vary depending on the platform in which you are using the Toolkit components in your application, here we use the widely used MSAL provider.
