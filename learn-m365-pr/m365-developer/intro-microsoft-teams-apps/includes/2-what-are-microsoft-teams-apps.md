An app built on the Microsoft Teams Platform  extends the Microsoft Teams client (web, mobile, and desktop) with web services you host. The Teams Platform provides a rich and flexible set of extensibility points, UI constructs, and APIs for you to take advantage of while building your app. Your app can be as simple as embedding your existing website within a tab for your team, or a fully featured, multi-faceted app engaging your users across the entire breadth of the Teams client. You may chose to integrate an existing app, or create a new experience built entirely for Teams.

With the Microsoft Teams Platform, you can augment your services with context-specific information available from the various Microsoft Teams APIs like information about the team or channel your app is installed in, or messages your app was triggered from. You can create apps for an individual user, a team, your entire organization, or publish your app to the public app store for everyone to use.

## Where can the Teams client be extended?

There are multiple places where the Microsoft Teams client can be extended to allow users to interact with your app. Depending on your scenario you may choose to focus on a single extension point (like a personal conversational bot), or combine multiple extension points.

### Teams, channels and group chats

Teams, channels and group chats allow multiple people to collaborate. Apps that extend context make themselves available to all members of the group or conversation, typically focusing on enabling additional collaborative workflows or unlocking new social interactions. Your app will have access to APIs allowing it to get information about the members in the converation, the channels in a team, and metadata about the team or conversation.

They can be expanded with:

* **Conversational bots** interacting with members of the converation through chat, and responding to events (like a new member being added, or a channel being renamed). All conversations with a bot in this context are visible to all members of the channel or group, so you'll need to ensure the conversation is relevant to everyone.
  
* **Configurable Tabs** providing a full-screen embedded web experience configured for the channel or group chat it is installed in. All members will interact on the same shared web-app, so a stateless single page app experience is typical.

* **Webhooks and connectors** enabling external services to post messages to the conversation. You can take advantage of cards and card actions to to create rich, actionable messages.

### Personal apps

Personal apps are the portion of your Teams app focusing on interactions with a single user. The experience is unique to each individual user. This portion of your app can be pinned to the left-navigation rail - enabling one-click access for your users.

They can be extended with:

**Conversational bots** having a one-to-one conversation with the user.

**Personal Tabs** providing a full-screen embedded web experience.

### Messages

Messages are the heart of collaboration in Teams. Your app can 

* message actions

### Writing messages

* search extensions
* link unfurling

## UI constructs

### Cards & card actions

### Task modules

### Deep links

### Web content pages



## Teams app building blocks

Conversational Bots

Tabs

Messaging Extensions

Webhooks & Connectors