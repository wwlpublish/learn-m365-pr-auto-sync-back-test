You've familiarized yourself with the concepts of the toolkit. Now you must be ready to see how to put something together.
Let's say you want to load any data from Microsoft 365. You'll need to sign in your application to access Microsoft Graph.

Let's walk through this unit and figure out how toolkit will make authentication to your application simple, so you can focus on just building the experience.

## What is the purpose of adding Login component in your application

Imagine how easy app development will be, if the most time consuming aspect like authentication logic is just an HTML tag you can add.
You can use the login component of the toolkit to your app and forget writing or maintaining code for authentication. The login and logout functionality is pre-baked into the component.

## What are providers in Microsoft Graph Toolkit

Providers simplify implementing authentication for your application and make calls to Microsoft Graph using the JavaScript client SDK.
Initialize a provider before you use any other toolkit component, like the login component we saw earlier. However, they can also be used on their own, to implement authentication for your application.
There are different providers, depending on the platform in which you're using the toolkit components in your application.

In the next exercise, you'll figure out how to use login component with MSAL provider, which is the widely used provider in the toolkit.
