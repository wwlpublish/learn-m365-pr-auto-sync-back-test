When you build a web app and want to connect it to Microsoft 365, you need to implement authorization and call Microsoft Graph to retrieve data stored in Microsoft 365.

To simplify this process, Microsoft Graph Toolkit provides a set of web components and authentication providers for connecting web apps to Microsoft 365.

In this unit, you'll learn what Microsoft Graph Toolkit is and why you would want to use it. You'll also learn about different kinds of apps that can use the toolkit.

## Microsoft Graph Toolkit overview

Microsoft Graph Toolkit is a set of web components that you can use with any JavaScript framework to connect your app to Microsoft 365. After loading the toolkit in your app, you get access to a set of custom HTML tags. These tags allow you to load data from Microsoft 365.

For example, to show the list of upcoming meetings for the current user, you would include in your app the following code snippet:

```html
<mgt-agenda></mgt-agenda>
```

Your app would then render:

:::image type="content" source="../media/02-agenda.png" alt-text="Screenshot of the list of upcoming meetings rendered by the Microsoft Graph Toolkit Agenda component.":::

Microsoft Graph Toolkit is updated regularly with new components and features.

## Why would you use Microsoft Graph Toolkit?

In the previous example, did you notice that you didn’t need to issue a single web request? This is exactly why you should consider using Microsoft Graph Toolkit.

- **Focus on building your own web app:** Microsoft Graph Toolkit abstracts away authorizing and connecting to Microsoft Graph. You don't need to worry about authorization, building web requests, handling responses, and dealing with exceptions.
- **Customize rendering to match your web app:** All Microsoft Graph Toolkit components are ready-to-use. By default, they show data by using Fluent UI, the Microsoft 365 design language. Each component also exposes a template, which allows you to customize the data rendered.

## When would you use Microsoft Graph Toolkit?

You can use Microsoft Graph Toolkit when you're building web apps and extensions for Microsoft 365.

- **Use Microsoft Graph Toolkit in web apps:** Microsoft Graph Toolkit is best suited for use in web applications. With minimal configuration, it enables people to sign in to your app with their Microsoft 365 account. Using the different components, you can load data directly from Microsoft 365, increasing the value of your app.
- **Build Microsoft 365 extensions with Microsoft Graph Toolkit:** You can also use Microsoft Graph Toolkit when you're building extensions for Microsoft 365, such as Teams tabs or SharePoint Framework web parts. For building these extensions, the toolkit comes with providers to use the existing authentication information exposed by Microsoft 365.
- **Use Microsoft Graph Toolkit in any JavaScript framework:** Microsoft Graph Toolkit web components work with any JavaScript framework. If you build web apps by using React, there's a specific toolkit package made for React. This package wraps the toolkit's components in React components, making it easier to pass complex data into components, and to configure event handlers.

## Load Microsoft Graph Toolkit in your web app

If you build web apps without using a bundler, you can load Microsoft Graph Toolkit directly from the content delivery network. To load the toolkit from the content delivery network, add the following code snippet to your web app:

```html
<script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
```

If you work on projects that use a package manager like npm, add Microsoft Graph Toolkit to your web app by installing the **@microsoft/mgt** package:

```console
npm install @microsoft/mgt
```

If you build React apps, install the **@microsoft/mgt-react** package instead:

```console
npm install @microsoft/mgt-react
```
