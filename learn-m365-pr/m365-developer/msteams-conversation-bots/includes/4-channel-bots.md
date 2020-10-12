Conversation bots can do many things within the Microsoft Teams client. They can subscribe to channel or group chat events, listen for and act on Microsoft Teams specific events and even update their own messages.

In this unit, you’ll learn how to expand on your existing bot to add some of this functionality.

## Conversation bots in Microsoft Teams

Microsoft Teams sends notifications to your bot for events that happen in scopes where your bot is active. You can capture these events in your code and take action on them, such as the following:

- trigger a welcome message when your bot is added to a team
- trigger a welcome message when a new team member is added or removed
- trigger a notification when a channel is created, renamed, or deleted
- when a bot message is liked by a user

### Conversation update events

A bot receives a `conversationUpdate` event when it has been added to a conversation, other members have been added to or removed from a conversation, or conversation metadata has changed.

The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added. It also receives an update when it has been added for the first time specifically for personal conversations.

### Channel events

Microsoft Teams will notify your bot of many different events that occur within Microsoft Teams. For example, the channel created event is sent to your bot whenever a new channel is created in a team your bot is installed in. You can handle this event within your bot with the following code:

```typescript
export class MyBot extends TeamsActivityHandler {
  constructor() {
    super();

    this.onTeamsChannelCreatedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
      const card = CardFactory.adaptiveCard(adaptiveCard);
      const message = MessageFactory.attachment(card);
      await turnContext.sendActivity(message);
      await next();
    });
  }
}
```

Your conversational bot can subscribe to any of the following events related to channels, channel members and teams unique to Microsoft Teams:

- **Team Member Events**
  - `teamMemberAdded`
  - `teamMemberRemoved`
- **Channel Events**
  - `channelCreated`
  - `channelRenamed`
  - `channelDeleted`
- **Team Events**
  - `teamRenamed`

### Message Reaction Events

Your bot can also handle instances where a user has reacted to one of your bot's messages. This is done by monitoring the events `reactionsAdded` or `reactionsRemoved`:

```typescript
export class ConvoBot extends TeamsActivityHandler {
  constructor() {
    super();

    this.onReactionsAdded(async (context: TurnContext, next: () => Promise<void>) => {
      if (context.activity.reactionsAdded) {
        context.activity.reactionsAdded.forEach(async (reaction) => {
          if (reaction.type === 'like') {
            await context.sendActivity(`Thank you!`);
          }
        });
      }
      await next();
    });
  }
}
```

## Channel and Group chat conversations with a Microsoft Teams bot

By adding the teams or group chat scope to your bot, it can be available to be installed in a team or group chat. This allows all members of the conversation to interact with your bot. Once installed, it will also have access to metadata about the conversation like the list of conversation members, and when installed in a team details about that team and the full list of channels.

Bots in a group or channel only receive messages when they're mentioned ("@botname"), they don't receive any other messages sent to the conversation.

> [!NOTE]
> The bot must be @mentioned directly. Your bot won't receive a message when the team or channel is mentioned, or when someone replies to a message from your bot without @mentioning it.

### Work with @Mentions

Every message to your bot from a group or channel will contain an @mention with its own name in the message text, so you'll need to ensure your message parsing handles that. Your bot can also retrieve other users mentioned in a message, and add mentions to any messages it sends.

### Strip mentions from message text

You may find it necessary to strip out the @mentions from the text of the message your bot receives.

### Retrieving mentions

Mentions are returned in the entities object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned. The text of the message will also include the mention like `<at>@John Smith<at>`.

However, you shouldn't rely on the text in the message to retrieve any information about the user; it's possible for the person sending the message to alter it. Instead, use the entities object.

### Updating and deleting existing messages

Your bot can update existing messages that the bot created, but it can't another person's messages. The following code demonstrates how to update an existing message. The `replyToId` property on the activity that initiated the turn, use the `updateActivity()` method to update an existing message.

```typescript
export class ConvoBot extends TeamsActivityHandler {
  private async updateCardActivity(context): Promise<void> {
    const data = context.activity.value;
    data.count += 1;

    const card = CardFactory.adaptiveCard(adaptiveCard);

    await context.updateActivity({
      attachments: [card],
      id: context.activity.replyToId,
      type: 'message' }
    );
  }
}
```

Your bot can also delete its own messages as the following code demonstrates:

```typescript
export class ConvoBot extends TeamsActivityHandler {
  private async deleteCardActivity(context): Promise<void> {
    await context.deleteActivity(context.activity.replyToId);
  }
}
```

## Summary

In this unit, you’ll learn how to expand on your existing bot to add some of this functionality.
