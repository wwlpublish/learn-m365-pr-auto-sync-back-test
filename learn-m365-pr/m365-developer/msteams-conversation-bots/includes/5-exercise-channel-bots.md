Conversation bots can do many things within the Microsoft Teams client. They can proactively send a message to a channel or group chat, listen for and act on Microsoft Teams specific events and even update their own messages.

In this exercise, you’ll modify the existing Microsoft Teams app to update your bot to respond to message reactions, and update or delete messages capabilities.

> [!IMPORTANT]
> This exercise assumes you have created the Microsoft Teams app project with the Yeoman generator that contains a personal tab from the previous exercise in this module. You'll update the project to add a new task module that uses an Adaptive Card.

## Add channel support to a conversation bot

In a previous exercise, you created a bot that could be used in the personal scope that enabled one:one chat. When a bot is used in a channel, you must @mention it to receive messages.

In this section, you'll modify the existing Microsoft Teams app to support being added to a team and respond to messages from the **Conversations** tab.

### Update the app's configuration

First, update app's manifest to add channel support. Locate and open the **./src/manifest/manifest.json** file.

You must increment the version of the app to upgrade an existing installed version. Locate the property `version` and increment the version to something greater than the default value `0.0.1`.

Next, locate the `bots.scopes` property. Add an addition value `teams` to the array so it looks like the following code:

```json
"bots": [
  {
    ...
    "scopes": [
      "personal",
      "team"
    ],
    ...
  }
]
```

### Update the bot code

The next step is to update the bot's code.

In the previous exercise, our code was looking for the specific message `MentionMe` in order to respond. This works in a 1:1 personal chat because the bot isn't mentioned in the conversation.

However, in a channel conversation, a user must @mention the bot to trigger it. This results in a message containing a reference to the bot, not just the message submitted.

While there are multiple ways to address this, let's handle it in a simple way: look for `MentionMe` at the end of the message.

Locate and open the bot in the file **./src/app/convoBot/convoBot.ts**. Locate the existing `onMessage()` handler in the class constructor. Add the following `else if` statement to find these new messages sent from a channel conversation:

```typescript
} else if (botMessageText.endsWith("</at> mentionme")) {
  await this.handleMessageMentionMeChannelConversation(context);
```

The complete `onMessage()` handler should now look like the following:

```typescript
this.onMessage(async (context: TurnContext, next: () => Promise<void>) => {
  const botMessageText: string = context.activity.text.trim().toLowerCase();

  if (botMessageText === "mentionme") {
    await this.handleMessageMentionMeOneOnOne(context);
  } else if (botMessageText.endsWith("</at> mentionme")) {
    await this.handleMessageMentionMeChannelConversation(context);
  }
  await next();
});
```

Finally, add the following method to the `ConvoBot` class to implement the handler for our new scenario:

```typescript
private async handleMessageMentionMeChannelConversation(context: TurnContext): Promise<void> {
  const mention = {
    mentioned: context.activity.from,
    text: `<at>${new TextEncoder().encode(context.activity.from.name)}</at>`,
    type: "mention"
  };

  const replyActivity = MessageFactory.text(`Hi ${mention.text}!`);
  replyActivity.entities = [mention];
  const followupActivity = MessageFactory.text(`*We are in a channel conversation group chat in the !*`);
  await context.sendActivities([replyActivity, followupActivity]);
}
```

Save your changes, update, and test the installed app.

### Test the conversation bot in a channel

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

> [!IMPORTANT]
> Recall from a previous exercise, Ngrok will create a new subdomain. You need to update your bot registration's **Messaging endpoint** in the Azure portal (*shown in a previous exercise*) with this new domain before testing it.

First, update the existing installed version of the bot.

In the browser, navigate to **https://teams.microsoft.com** and sign in with the credentials of a Work and School account.

Using the app bar navigation menu, select the **Mode added apps** button. Then select **Browse all apps**, select the menu in the top-right corner of the **Conversation bot** and select **Update**.

![Screenshot of updating an installed Microsoft Teams app](../media/05-test-01.png)

When prompted, select the updated package of the Microsoft Teams app. Microsoft Teams will update the app to the new version.

Navigate to an existing channel in a team.

From the channel's **Conversations** tab, @mention the bot. The first time you @mention the bot, you'll be prompted to install it into the team.

![Screenshot installing bot into a channel](../media/05-test-02.png)

After installing the bot, when you @mention it and include the message `mentionme`, the bot will reply to your message:

![Screenshot of the bot replying to a channel conversation](../media/05-test-03.png)

## Reply to messages with Adaptive cards

In this section, you'll update the bot to respond to unknown messages using an Adaptive card. The card's single action will trigger the bot to update the existing message with a new Adaptive card. The updated message will include an additional action that will trigger the bot to delete the message.

Locate and open the bot in the file **./src/app/convoBot/convoBot.ts**. 

Add the `CardFactory` and `ActionTypes` objects to the existing `import {...} from "botbuilder";` statement to import two more objects you'll need:

```typescript
import {
  TeamsActivityHandler,
  TurnContext,
  MessageFactory,
  MemoryStorage,
  ActionTypes, CardFactory
} from "botbuilder";
```

Locate the existing `onMessage()` handler in the class constructor. Add the following `else` statement to the existing `if` statement to respond with an adaptive card if the bot receives an unknown command:

```typescript
} else {
  const value = { cardAction: "update", count: 0 };
  const card = CardFactory.adaptiveCard({
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Adaptive card response",
            "weight": "bolder",
            "size": "large"
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Demonstrates how to respond with a card, update the card & ultimately delete the response.",
            "wrap": true
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.Submit",
        "title": "Update card",
        "data": value
      }
    ]
  });
  await context.sendActivity({ attachments: [card] });
}
```

The `onMessage()` handler should now look like the following:

```typescript
this.onMessage(async (context: TurnContext, next: () => Promise<void>) => {
  const botMessageText: string = context.activity.text.trim().toLowerCase();

  if (botMessageText === "mentionme") {
    await this.handleMessageMentionMeOneOnOne(context);
  } else if (botMessageText.endsWith("</at> mentionme")) {
    await this.handleMessageMentionMeChannelConversation(context);
  } else {
    const value = { cardAction: "update", count: 0 };
    const card = CardFactory.adaptiveCard({..});
    await context.sendActivity({ attachments: [card] });
  }
  await next();
});
```

Notice the `else` statement will send a card to the conversation that contains a `data` object in the single `actions`. This object has a `count` property & `cardAction` property. When a user triggers the action, this object will be sent to the bot.

Add the following methods to implement the `updateCardActivity()` & the `deleteCardActivity()` handlers:

```typescript
private async updateCardActivity(context): Promise<void> {
  const value = {
    cardAction: "update",
    count: context.activity.value.count + 1
  };
  const card = CardFactory.adaptiveCard({
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Adaptive card response",
            "weight": "bolder",
            "size": "large"
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": `Updated count: ${ value.count }`,
            "wrap": true
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.Submit",
        "title": "Update card",
        "data": value
      },
      {
        "type": "Action.Submit",
        "title": "Delete card",
        "data": { cardAction: "delete"}
      }
    ]
  });

  await context.updateActivity({ attachments: [card], id: context.activity.replyToId, type: 'message' });
}

private async deleteCardActivity(context): Promise<void> {
  await context.deleteActivity(context.activity.replyToId);
}
```

In the code you've added, notice the `updateCardActivity()` retrieves and increments the `count` property it received. It then creates a new card with the same data, but with an additional action to delete the card. Finally, the method uses the `updateActivity()` method to update an existing message.

The `deleteCardActivity()` deletes the card using the `deleteActivity()` method.

The last step is to handle messages that are sent from the adaptive card correctly.

Within the `onMessage()` method, add the following code at the very start of the method, before the existing code:

```typescript
// if a value property exists = adaptive card submit action
if (context.activity.value) {
  switch (context.activity.value.cardAction) {
    case "update":
      await this.updateCardActivity(context);
      break;
    case "delete":
      await this.deleteCardActivity(context);
      break;
  }
} else {
```

Close the `else` statement before the last line `await next();`. The final `onMessage()` method should look like the following code:

```typescript
this.onMessage(async (context: TurnContext, next: () => Promise<void>) => {
  // if a value property exists = adaptive card submit action
  if (context.activity.value) {
    switch (context.activity.value.cardAction) {
      case "update":
        await this.updateCardActivity(context);
        break;
      case "delete":
        await this.deleteCardActivity(context);
        break;
    }
  } else {
    const botMessageText: string = context.activity.text.trim().toLowerCase();

    if (botMessageText === "mentionme") {
      await this.handleMessageMentionMeOneOnOne(context);
    } else if (botMessageText.endsWith("</at> mentionme")) {
      await this.handleMessageMentionMeChannelConversation(context);
    } else {
      const value = { cardAction: "update", count: 0 };
      const card = CardFactory.adaptiveCard({
        /* card omitted for readability */
      });
      await context.sendActivity({ attachments: [card] });
    }
  }
  await next();
});
```

### Test the bot updating existing messages

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

> [!IMPORTANT]
> Recall from a previous exercise, Ngrok will create a new subdomain. You need to update your bot registration's **Messaging endpoint** in the Azure portal (*shown in a previous exercise*) with this new domain before testing it.

In the Microsoft Teams client, go to the channel you installed the bot in the previous section. From the **Conversations** tab, @mention the bot with a random string to trigger the `else` condition.

The bot will reply to the message with a card:

![Screenshot of a message from the bot using cards](../media/05-test-04.png)

Notice the value in the card is set to **0**.

Select the button **Update card**. After a few seconds, the card should be updated with a new card containing an incremented counter value and a new button:

![Screenshot of an updated message from the bot using cards](../media/05-test-05.png)

Select the **Update card** button a few more times to see the counter get updated.

Finally, select the **Delete card** button. After a few seconds, the card will be removed by the bot.

## Reply to message reactions

In this section, you'll update the bot to respond when someone likes a message from the bot.

Locate and open the bot in the file **./src/app/convoBot/convoBot.ts**.

Add the following handler to the existing class constructor method:

```typescript
this.onReactionsAdded(async (context: TurnContext, next: () => Promise<void>) => {
  if (context.activity.reactionsAdded) {
    context.activity.reactionsAdded.forEach(async (reaction) => {
      if (reaction.type === "like") {
        await context.sendActivity("Thank you!");
      }
    });
  }
  await next();
});
```

This code will execute when a user adds a reaction to a message from the bot. If the reaction is a *like*, the bot will reply with a *"Thank you!"* message

### Test the bot reacting to message reactions

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

> [!IMPORTANT]
> Recall from a previous exercise, Ngrok will create a new subdomain. You need to update your bot registration's **Messaging endpoint** in the Azure portal (*shown in a previous exercise*) with this new domain before testing it.

In the Microsoft Teams client, go to the channel you installed the bot in the previous section. From the **Conversations** tab, find a message from the bot and apply a *like* reaction to it:

![Screenshot of a user reacting to a bot's message](../media/05-test-06.png)

After a few seconds, the bot will reply with a message, thanking them for liking the reaction:

![Screenshot of a bot replying to a reaction](../media/05-test-07.png)

## Summary

In this exercise, you modified the existing Microsoft Teams app to update your bot to respond to message reactions, and update or delete messages capabilities.
