# Sign in your app using Microsoft Graph Toolkit components

The Microsoft Graph Toolkit providers simplifies signing in your application to access Microsoft Graph. Upon completing this module, you will learn about Microsoft Graph Toolkit providers and how they work with or without other components of the Toolkit to authenticate and access Microsoft Graph.

## What are providers in Microsoft Graph Toolkit

Providers simplify implementing authentication for your application and make calls to Microsoft Graph using the JavaScript client SDK.

## Why do we need providers

Providers are required and needs to be initialized before using any web components in the Toolkit.However, providers can be used on their own, without components to implement authentication for your application

## Different type of providers in Microsoft Graph Toolkit

The Toolkit includes the following providers which vary depending on the platform in which you are using the Toolkit components in your application. They are as listed as below:

- MSAL
- SharePoint
- Teams
- Proxy
- Custom

### What is MSAL provider

MSAL provider is used in web applications to sign in users to access and use Microsoft Graph.

### What is SharePoint provider

SharePoint provider is used by the components in SharePoint web parts to access and use Microsoft Graph.

### What is Teams provider

Teams provider is used by the components in Microsoft teams tabs to access and use Microsoft Graph.

### What is Proxy provider

Proxy provide can use your own backend authentication service which in turn makes a call to Microsoft Graph on behalf of the user, to enable access to Graph for Toolkit components.

### What is Custom provider

If you have an existing authentication mechanism in your application to access Microsoft Graph, you can use Custom providers to enable access to Graph for Toolkit components.

## What is the purpose of adding Login component in your application

Once the right provider is initialized in your application, you can add Login component of the Toolkit to implement login and logout functionality and all the authentication logic associated with it using one line of code in the application.
