An app built on the Microsoft Teams Platform extends the Microsoft Teams client (web, mobile, and desktop) with web services you host. The Teams Platform provides a rich and flexible set of extensibility points, UI constructs, and APIs for you to take advantage of while building your app. Your app can be as simple as embedding your existing website within a tab for your team, or a fully featured, multi-faceted app engaging your users across the entire breadth of the Teams client. You may choose to integrate an existing app, or create a new experience built entirely for Teams.

With the Microsoft Teams Platform, you can augment your services with context-specific information available from the various Microsoft Teams APIs like information about the team or channel your app is installed in, or messages your app was triggered from. You can create apps for an individual user, a team, your entire organization, or publish your app to the public app store for everyone to use.

## What makes up a Microsoft Teams app?

Apps built on the Microsoft Teams Platform consist of three primary pieces.

- **The Microsoft Teams client** provides the extensions points and UI elements your app will use to engage your users.
- **Your Teams App Package** is the package that is installed in Microsoft Teams. It contains a small icon, a large icon, and a manifest JSON file. The manifest file contains the metadata for your app (like the name of the app, the developer's name, and so on), which extensibility points your app uses (like tabs and messaging extensions), and pointers to your web services that power your app (like the ID for your bot, or your tab's URL).
- **Your web services** hosted by you providing the APIs and logic that power your app.

It's important to keep in mind that the Microsoft Teams Platform isn't a hosting service; the web services powering your app must be hosted by you and accessible by HTTPS over the internet.

## Where can the Teams client be extended?

There are multiple places where the Microsoft Teams client can be extended to allow users to interact with your app. Depending on your scenario, you may choose to focus on a single extension point (like a personal conversational bot), or combine multiple extension points.

### Teams, channels, and group chats

Teams, channels, and group chats allow multiple people to collaborate. Apps that extend context make themselves available to all members of the group or conversation, typically focusing on enabling other collaborative workflows or unlocking new social interactions. Your app will have access to APIs allowing it to get information about the members in the conversation, the channels in a team, and metadata about the team or conversation.

They can be expanded with:

- **Conversational bots** interacting with members of the conversation through chat, and responding to events (like a new member being added, or a channel being renamed). All conversations with a bot in this context are visible to all members of the channel or group, so you'll need to ensure the conversation is relevant to everyone.
- **Channel & Group Chat Tabs** providing a full-screen embedded web experience configured for the channel or group chat it's installed in. All members will interact on the same shared web-app, so a stateless single page app experience is typical.
- **Webhooks & Connectors** enabling external services to post messages to the conversation. You can take advantage of cards and card actions to create rich, actionable messages. Webhooks provide a simple, unauthenticated, one-way method to post messages to a channel, while Connectors provide a slightly more robust back-and-forth experience.

### Personal apps

Personal apps are the portion of your Teams app focusing on interactions with a single user. The experience is unique to each individual user. This portion of your app can be pinned to the left-navigation rail - enabling one-click access for your users.

They can contain:

- **Conversational bots** having a one-to-one conversation with the user. Because this is a private conversation, if your app needs to have a multi-turn conversation with a user, or provide a notification relevant only to a single user, it's typically best to have that interaction in a personal app.
- **Personal Tabs** providing a full-screen embedded web experience.

### Messages

Messages are the heart of collaboration in Teams. With a **messaging extension action command**, your app can allow users to invoke your app's API from a message, sending the contents of the message to your app for processing or action. Your app can respond by presenting a form (a task module) to the user to collect more information, sending a reply to the original message, or sending a message directly to the user.

### Writing messages

Your app can help users craft more effective messages by enabling them to search, or take action, in an external system, and insert the results in a rich, structured format complete with actionable buttons.

There are three ways your app can help users create better messages:

- **Messaging Extension - action commands** present your user with a modal form (a task module), submit the results of the form to your app, then either insert a message into the conversation directly, or create part of a message the user can edit before sending to the conversation.
- **Messaging Extension - search commands** allowing them to quickly search an external system, preview the results of that search, then insert the result into the chat as a rich card.
- **Messaging Extension - link unfurling** allows your app to monitor web domains you're interested in. When a URL containing that domain is pasted into the compose message box, your app's API will be invoked, allowing you to add a rich card to the message with additional information about the item being linked to.

## User interface (UI) elements

Also, to extensibility points, the Microsoft Teams Platform provides flexible UI elements for apps to take advantage of. These elements allow you to create rich experiences that feel native to the Teams client.

### Cards & card actions

Cards are user-interface containers defined by schematized JSON, that can contain multiple properties and attachments. They can contain formatted text, media, controls (like drop-down boxes and radio buttons), and buttons that trigger card actions. Card actions can send payloads to your app's API, open a link, start authentication flows, or send messages to conversations. The Microsoft Teams Platform supports multiple types of cards including Adaptive Cards, Hero Cards, Thumbnail Cards and more. They can be combined into Card Collections and displayed in a list or carousel.

### Task modules

Task modules allow you to create modal popup experiences in your Teams application. Inside the popup you can run your own custom HTML/JavaScript code, show an `<iframe>` such as a YouTube or Microsoft Stream video or display an Adaptive card. They're especially useful for starting and completing tasks or displaying rich information like videos or Power BI dashboards. A popup experience is often more natural for users starting and completing tasks compared to a tab or a conversation-based bot experience.

### Deep links

Your app can create URL deep links to help navigate your user through your app, and the Teams client. You can create a deep link for most entities within Teams, and some (like a new meeting request) allow you to pre-populate information using query strings in the URL. For example, your conversational bot could send a message to a channel with a deep link to a task module that results in a card being sent as a one-to-one message to a user, that in turn contains a deep link to create a new meeting with a specific user at a certain date/time. Use deep links to connect across the various extension points available to your app, keeping your user in the correct context.

### Web content pages

A web content page is a webpage you host that can be embedded in a tab or a task module. To enable your webpage to be embedded in a Microsoft Teams client, it must:

- Be hosted on an HTTPS.
- Be embeddable in an `<iframe>` by the Teams client.
- Include the Microsoft Teams JavaScript client SDK, and invoke the SDK's `initialize()` method on page load.

## Summary

A Microsoft Teams app then is a collection of web services, hosted externally to Microsoft Teams, that take advantage of the extensibility points and UI elements made available through the Microsoft Teams Platform.
