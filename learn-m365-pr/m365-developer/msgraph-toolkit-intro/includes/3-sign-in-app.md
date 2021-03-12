Now that you've seen an overview of the toolkit, let's learn how you can use it to load data from Microsoft 365 services. You'll first need to provide a way for users to sign in to your application. Fortunately, the toolkit greatly simplifies the authentication process so that you can focus on building the overall user experience.

## What is the purpose of adding the Login component in your application?

Imagine how simple and secure your app development process will be if one of the most time-consuming aspects is handled for you. By using the toolkit, authentication logic and access token retrieval is handled by adding a simple HTML tag.

```html
<mgt-login></mgt-login>
```

You can use the toolkit login component in your app and forget about writing and maintaining authentication code. The login and logout functionality is pre-baked into the component!

## What are providers in Microsoft Graph Toolkit?

Providers simplify implementing authentication in your application and handle making calls to Microsoft Graph using the JavaScript client SDK. You'll initialize a provider before using any toolkit components such as the login component. It's also possible to use providers on their own, in an application to handle authentication. There are several different providers that can be used depending on the platform you're targeting with the toolkit components:

- Microsoft Authentication Library (MSAL) provider – For general use by single-page applications that will authenticate from the browser.

- Electron provider – For use in Electron apps.

- Proxy provider – For use by web applications that will authenticate on the backend server.

- SharePoint provider – For use in the SharePoint Framework.

- Microsoft Teams provider – For use by single-page applications that will run as Teams tabs.

- Custom provider – Allows you to build your own authentication.

In the next exercise, you'll learn how to use the toolkit's login component with the Microsoft Authentication Library (MSAL) provider, which is the most widely used provider in the toolkit.
