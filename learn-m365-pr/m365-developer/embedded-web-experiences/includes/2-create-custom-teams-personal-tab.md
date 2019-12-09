In this unit, you'll learn how to create tabs in Microsoft Teams apps.

## Microsoft Teams-extensibility options

Microsoft Teams enables developers to create custom experiences for users. For the best and most extensible option for adding your service into Teams, create a Microsoft Teams app.

![Screenshot of a Microsoft Teams app](../media/02-01.png)

A Microsoft Teams app is a package of services that you host, that can be distributed through the Microsoft Teams product or uploaded by owners. These apps can consist of custom tabs, bots, messaging extensions, or webhooks and connectors.

![Screenshot of a custom bot](../media/02-02.png)

For quick one-off integration of your existing webhook, you can take advantage of our Custom Bot feature. This ad-hoc extensibility option allows you to set up webhooks / notifications in a specific team, with no additional coding required.

### What is a Microsoft Teams app?

Apps in Microsoft Teams allow you to make your service available to users in the contexts, or "scopes", that make the most sense.

You declare precisely which capabilities you support, in which scopes, via your app package's manifest file. Microsoft Teams app capabilities (such as bots, tabs, and so on) are available in most scopes. These capabilities are offered via a single Microsoft Teams app package that users can acquire through the Microsoft Teams in-product app gallery, the Office Store, or uploaded directly by your organization.

### How to create a Microsoft Teams App

How do you create a custom Microsoft Teams app?

![Diagram of three pillars to create an app](../media/02-03.png)

You'll first development the components that support your Microsoft Teams app. Microsoft Teams apps are web applications that can be created using HTML, TypeScript, or JavaScript, client-side web frameworks such as React, and/or any server-side framework such as .NET.

Microsoft Teams apps can be stand alone or they can integrate with Microsoft Teams. Microsoft provides a JavaScript SDK for interactive with the Microsoft teams client and a Bot Builder SDK for building bots.

Once you're finished creating the application, the final step is to package and deploy the application. Every Microsoft Teams app contains a manifest file that describes all aspects of your app. The manifest includes the URLs and unique identifiers for the components you've created to implement the application. After creating the manifest, create a package that includes the manifest and associated images used by the app. This package is just a ZIP file. Prior to uploading and publishing the package, you need to deploy all resources that implement the app. These resources include web pages and services used within tabs, bots, and webhooks.

## Microsoft Teams Tabs

This module focuses on creating custom tabs for Microsoft Teams.

### What is a Microsoft Teams tab?

A Microsoft Teams tab enables developers to display rich interactive web content within the Microsoft Teams clients. There are two approaches to create a custom tab. You can either take an existing web-app experience and adapt it to a custom tab. You can also build a custom tab from scratch.

Microsoft Teams tabs are simply web applications that are hosted by the provider or developer of the application. A tab in Microsoft Teams displays the specified web app within an `<iframe>` in the Microsoft Teams client.

### Tabs differ from web applications when browsing the same content

While Microsoft Teams tabs are `<iframe>` that display web pages, there are some differences between interacting with the web app within the Microsoft Teams client compared to just browsing the same content.

Microsoft Teams tabs always display web content in an `<iframe>` where a web page is loaded in any browser. This allows you to create unique experiences with the web app for only Microsoft Teams by limiting where the application is hosted. For instance, you can limit a web page to only be displayed within an `<iframe>` from a specific domain such as teams.microsoft.com.

Authentication is handled differently in a Microsoft Teams tab compared ot a web app, either via a popup or calling Azure AD to fetch tokens. Most websites simply redirect to a login provider that typically breaks for custom tabs that are hosted inside of an `<iframe>`. Tabs break in this experience because the sign in pages typically do not load within an `<iframe>` to prevent click-jacking.

Cross-domain navigation is handled differently in tabs from a web app. The Teams client needs to validate the origin against a static validDomains list in the app manifest when loading or communicating with the tab.

Microsoft Team tabs can be styled to match the current Microsoft Teams client's theme such as default, dark or high contrast.

Developers of Microsoft Teams tabs can also communicate with the hosting Microsoft Teams client using the JavaScript SDK (`microsoftTeams.initialize()`). The SDK gives Teams a communication channel with the hosted page and more visibility into its operations.

### Tab Scope: Where can a tab exist in Microsoft Teams?

Teams determines where a tab can be used based on its scope. Scope is set in the app manifest, and can be one of three (3) values:

![Screenshot showing difference placement of apps in tab navigation or app bar](../media/02-04.png)

The first is the Team scope. Tabs in channels allow teams to interact with your shared experience. These tabs are referred to as channel tabs, previously known as configurable tabs. When these tabs are added to team, a user configures the content of your tab experience when the tab is first added to a channel.

The next option for a tab scope is a group chat. Channel tabs can also be used in group chats. These are conversations between two (2) or more users.

The final option is the personal scope. Personal tabs allow users to interact with your experience privately. The content in a personal tab is only relevant to individual users.

## Developing Custom Microsoft Teams Tabs

This section will address the process of creating custom tabs for Microsoft Teams.

### Overview of building a Microsoft Teams Tab

Let’s look at what is involved in building a Microsoft Teams tab.

![Diagram of three steps to building an app](../media/02-05.png)

Microsoft has design guidelines for creating custom tabs that include the following:

#### Focus on functionality

Tabs work best when they’re built to address a specific need. Focus on a small set of tasks or a subset of data that’s relevant to the channel the tab is in.

#### Reduced chrome

Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab. In other words, try not to have tabs in your tab.

#### Integration

Find ways to notify users about tab activity. For example, post message card to a conversation about tab activity.

#### Conversational

Find a way to facilitate conversation around a tab. This ensures that conversations center on the content, data, or process at hand.

#### Streamlined access

Make sure you're granting access to the right people at the right time. Keeping your sign in process simple will avoid creating barriers to contribution and collaboration.

Once you've designed a great Microsoft Teams tab, the next step is to develop it. Tabs are just web apps hosted in an `<iframe>` within the Microsoft Teams client. Developers are free to use any web technologies and frameworks they are most comfortable with to implement the custom tab experience, such as HTML, JavaScript, TypeScript, web frameworks such as React or Angular, and server-side technologies.

The last step is to deploy the custom tab. Unlike other Microsoft Teams extensibility options such as bots and message extensions, developers can upload custom tabs directly to a team. Microsoft Teams apps can also be uploaded your tenant’s app gallery for other users to install in their teams.

### Custom Microsoft Teams Tabs: key points

When creating a Microsoft Teams tab, there are some key points to keep in mind.

A Microsoft Teams tab is just a web page hosted by the tab provider or developer. No data related to the tab is stored in Microsoft Teams; the developer of the tab is responsible for all aspects of the tab including data storage, configuration settings and authentication. Microsoft Teams saves only minimal configuration details on the tab, such as the URLs where the content and website of the tab, the name and IDs of the tab.

One thing you may want to consider when building your tab is to implement the user experience more like an application and less like a web page. Many web sites implement the traditional page-to-page and postback style of submitting and presenting information. The users of your tabs are interacting with your application from the Microsoft Teams client. This can be from a desktop, mobile or web experience, but all facilitate a rich client experience. Using web frameworks, such as React, Angular, and Vue.js, you can implement a rich client experience without continuously reloading the page.

### Developer tooling options

Microsoft provides developers with multiple tools for creating custom Microsoft Teams apps, including custom tabs.

App Studio makes it easy to start creating or integrating your own Microsoft Teams apps, whether you develop custom apps for your enterprise or SaaS applications for teams around the world by streamlining the creation of the manifest and package for your app and providing useful tools like the Card Editor and a React control library. App Studio is a Teams app that can be found in the Teams store. App Studio helps developers preview the rendering of cards and visually edit the manifest file for a Teams app.

![Screenshot of App Studio](../media/02-06.png)

Developers have two options for creating the project and resources necessary to implement Microsoft Teams tabs: Node.js or .NET.

![Screenshot of a console and creating a custom Microsoft Teams app](../media/02-07.png)

Developers who want to create a Node.js based project can use the Microsoft Teams Yeoman Generator. After answering multiple questions related to the project you want to create, the generator will create the scaffolding for your project. This option requires git, Node.js, NPM, and a text editor such as Visual Studio Code.

![Screenshot of Visual Studio and creating a custom Microsoft Teams app](../media/02-08.png)

Developers who want to create a .NET based project can use tooling provided in Visual Studio 2017 or later. Similar to the Node.js option, after selecting the project type and answering multiple questions, Visual Studio will generate the scaffolding for your project. This option only requires git and Visual Studio.

### Getting Context within Teams tabs

Your Microsoft Teams tab might require contextual information to display relevant content, or need basic information about the user, team, or company. The tab may need locale and theme information or need to read the `entityId` or `subEntityId` that identifies what is in this tab for additional context.

Microsoft Teams offers two ways to obtain context on the current user or from within Microsoft Teams. When loading the content page for a tab, Microsoft Teams can include placeholder values on the URL that the web application can use to obtain context. The web app, once loaded within Microsoft Teams, can use the Microsoft Teams JavaScript SDK.

### Accessing context - URL placeholder values

Use placeholders in your configuration or content URLs. Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL to navigate to. The available placeholders include all fields on the Microsoft Teams Context object available within the JavaScript SDK.

Some of the values available as URL placeholders are set when the tab was configured while others are set when generating a deep link to the tab. Deep links are used to facilitate tab-to-tab communication.

The URL placeholder values include the following properties:

|      Properties       |                                   Description                                    |
| --------------------- | -------------------------------------------------------------------------------- |
| `{entityId}`          | The ID you supplied on the tab’s config page                                     |
| `{subEntityId}`       | The ID you supplied when generating a deep link for specific item within the tab |
| `{loginHint}`         | Value suitable as login hint for Azure AD                                        |
| `{locale}`            | Lowercase lang-locale                                                            |
| `{theme}`             | `default` / `dark` / `contrast`                                                  |
| `{userPrincipalName}` | The user identifier of the current user in the current tenant in email format    |
| `{userObjectId}`      | The Azure AD object ID of the current user in the current tenant                 |
| `{tid}`               | GUID ID of the current Azure Tenant ID                                           |
| `{groupId}`           | GUID ID of the current Office 365 Group ID                                       |

### Accessing context - Microsoft Teams JavaScript client SDK

You can also retrieve the information listed above using the Microsoft Teams JavaScript client SDK by calling `microsoftTeams.getContext(function(teamsContext) { … })`.

The context values include the following properties:

| Noteworthy Properties |                     Description                     |
| --------------------- | --------------------------------------------------- |
| `teamId`              | The team ID in the format `19:[id]@thread.skype`    |
| `teamName`            | Name of the current team                            |
| `channelId`           | The channel ID in the format `19:[id]@thread.skype` |
| `channelName`         | Name of the current channel                         |
| `chatId`              | The chat ID in the format  `19:[id]@thread.skype`   |
| `locale`              | Lowercase lang-locale                               |
| `theme`               | `default` / `dark` / `contrast`                     |
| `entityId`            | The entity ID you set up on your config page        |
| `subEntityId`         | The sub entity ID you set up on your config page    |
| `userPrincipalName`   | The user identifier in email format                 |
| `tid`                 | GUID identifying the current Tenant ID              |
| `groupId`             | GUID identifying the current Office 365 Group ID    |
| `tenantSKU`           | SKU of the current tenant (for example: EDU)        |

### Personal Tabs - Manifest

Developers can create two different types of tabs for Microsoft Teams. One type of tab is a personal tab, previously referred to as static tabs. Personal tabs allow users to interact with your experience privately. The content in a personal tab is only relevant to individual users.

A personal tab is defined within the static tabs collection of the Microsoft Teams app manifest. These are a set of tabs that can be "pinned" by default, without the user adding them manually. Personal tabs declared in personal scope are always pinned to the app's personal experience.

```json
"staticTabs":
[
  {
    "entityId": "candidatesTab",
    "name": "Candidates",
    "contentUrl": "https://.../Tabs/candidates.html",
    "websiteUrl": "https://.../Tabs/candidates.html?web=1",
    "scopes": ["personal"]
  }
],
"validDomains": [
  "token.botframework.com"
]
```

The `entityId` is a unique identifier for the entity that the tab displays. This property is required.

The `name` is the display name of the tab in the channel interface. This property is required.

The `contentUrl` is the HTTPS URL that points to the entity URL to be displayed in the Microsoft Teams canvas. This property is required.

The `websiteUrl` is the HTTPS URL used if a user opts to view a tab in the browser. This property is not required.

The `scopes` is an array of scopes supported. This property is required and only supports the personal scope.

If your Microsoft Teams tab will load or redirect to other URLs, those must be listed in the `validDomains` collection.
