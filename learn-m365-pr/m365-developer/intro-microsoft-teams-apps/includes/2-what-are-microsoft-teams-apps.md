An app built on the Microsoft Teams Platform  extends the Microsoft Teams client (web, mobile, and desktop) with web services you host. The Teams Platform provides a rich and flexible set of extensibility points, UI constructs, and APIs for you to take advantage of while building your app. Your app can be as simple as embedding your existing website within a tab for your team, or a fully featured, multi-faceted app engaging your users across the entire breadth of the Teams client. You may choose to integrate an existing app, or create a new experience built entirely for Teams.

With the Microsoft Teams Platform, you can augment your services with context-specific information available from the various Microsoft Teams APIs like information about the team or channel your app is installed in, or messages your app was triggered from. You can create apps for an individual user, a team, your entire organization, or publish your app to the public app store for everyone to use.

## Where can the Teams client be extended?

There are multiple places where the Microsoft Teams client can be extended to allow users to interact with your app. Depending on your scenario you may choose to focus on a single extension point (like a personal conversational bot), or combine multiple extension points.

### Teams, channels and group chats

Teams, channels and group chats allow multiple people to collaborate. Apps that extend context make themselves available to all members of the group or conversation, typically focusing on enabling additional collaborative workflows or unlocking new social interactions. Your app will have access to APIs allowing it to get information about the members in the conversation, the channels in a team, and metadata about the team or conversation.

They can be expanded with:

* **Conversational bots** interacting with members of the conversation through chat, and responding to events (like a new member being added, or a channel being renamed). All conversations with a bot in this context are visible to all members of the channel or group, so you'll need to ensure the conversation is relevant to everyone.
  
* **Configurable Tabs** providing a full-screen embedded web experience configured for the channel or group chat it is installed in. All members will interact on the same shared web-app, so a stateless single page app experience is typical.

* **Webhooks and connectors** enabling external services to post messages to the conversation. You can take advantage of cards and card actions to to create rich, actionable messages.

### Personal apps

Personal apps are the portion of your Teams app focusing on interactions with a single user. The experience is unique to each individual user. This portion of your app can be pinned to the left-navigation rail - enabling one-click access for your users.

They can contain:

* **Conversational bots** having a one-to-one conversation with the user. Because this is a private conversation, if your app needs to have a multi-turn conversation with a user, or provide a notification relevant only to a single user, it is typically best to have that interaction in a personal app.

* **Personal Tabs** providing a full-screen embedded web experience.

### Messages

Messages are the heart of collaboration in Teams. Your app can allow users to invoke your app's API from a message, sending the contents of the message to your app for processing or action. Your app can respond by presenting a form (a task todule) to the user to collect more information, sending a reply to the original message, or sending a message directly to the user.

### Writing messages

Your app can help users craft more effect messages by enabling them to search in an external system, and insert the results of that search in a rich, structured format complete with actionable buttons.

There are three ways your app can help users create better messages:

* **Search extensions** allowing them to quickly search an external system, preview the results of that search, then insert the result into the chat as a rich card.

* **Link unfurling** allows your app to monitor web domains you're interested in. When a URL containing that domain is pasted into the compose message box, your app's API will be invoked, allowing you to add a rich card to the message with additional information about the item being linked to.

* **Action extensions** present your user with a modal form (a task module), submit the results of the form to your app, then either insert a message into the conversation directly, or create part of a message the user can edit before sending to the conversation.

## User Interface (UI) elements

In addition to extensibility points, the Microsoft Teams Platform provides multiple flexible UI elements apps can take advantage of. These elements allow you to create rich experiences that feel native to the Teams client.

### Cards & card actions

Cards are user-interface containers defined by schematized JSON, that can contain multiple properties and attachments. They can contain formatted text, media, controls (like drop-down boxes and radio buttons), and buttons that trigger card actions. Card actions can send payloads to your app's API, open a link, initiate authentication flows, or send messages to conversations. The Microsoft Teams Platform supports multiple types of cards including Adaptive Cards, Hero Cards, Thumbnail Cards and more. They can be combined into Card Collections and displayed in a list or carousel.

### Task modules

Task modules allow you to create modal popup experiences in your Teams application. Inside the popup you can run your own custom HTML/JavaScript code, show an `<iframe>` widget such as a YouTube or Microsoft Stream video or display an Adaptive card. They are especially useful for initiating and completing tasks or displaying rich information like videos or Power BI dashboards. A popup experience is often more natural for users initiating and completing tasks compared to a tab or a conversation-based bot experience.

### Deep links

Your app can create URL deep links to help navigate your user through your app, and the Teams client. You can create a deepling for most entities within Teams, and some (like a new meeting request) allow you to prepopulate information using querystrings in the URL. For example, your conversational bot could send a message to a channel with a deeplink to a task module that results in a card being sent as a one-to-one message to a user, that in turn contains a deeplink to create a new meeting with a specific user at a certain date/time. Use deep links to connect across the various extension points available to your app, keeping your user in the correct context at all times.

### Web content pages

A web content page is a webpage you host that can be embedded in a tab or a task module. To enable your webpage to be embedable in a Microsoft Teams client it must:

* Be hosted on an HTTPS.
* Be able to be embedded in an `<iframe>` by the Teams client.
* Include the Microsoft Teams JavaScript client SDK, and invoke the SDK's `initialize()` method on page load.

## Summary

A Microsoft Teams app then is a collection of web services, hosted externally to Microsoft Teams, that take advantage of the extensibility points and UI elements made available through the Microsoft Teams Platform.
