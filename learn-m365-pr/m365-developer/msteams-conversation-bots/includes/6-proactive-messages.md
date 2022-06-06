> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzEr]

Proactive messages are sent by a bot to start a conversation. Welcome message and poll responses or for external event notifications are common scenarios to use proactive messages.

In this unit, you’ll learn how to send proactive messages from your bot.

## Creating proactive messages

You may want your bot to start a conversation for many reasons, including:

- Welcome messages for personal bot conversations
- Poll responses
- External event notifications

A bot that sends a message to start a new conversation thread is different than sending a message in response to an existing conversation. When your bot starts a new conversation, there's no pre-existing conversation to post the message to.

### Consider when to use proactive messages

Sending proactive messages to users can be an effective way to communicate with your users. However, from their perspective, this message can appear to come to them completely unprompted. Welcome messages will be the first time they've interacted with your app.

It's important to use this functionality sparingly. Provide them with enough information to let them understand why they're being messaged.

Proactive messages generally fall into one of two categories: welcome messages or notifications.

### Welcome messages

When you use proactive messages to send a welcome message to users, you must keep in mind that for most people receiving the message they'll have no context for why they're receiving it. Welcome messages are also the first time they'll have interacted with your app; it's your opportunity to create a good first impression.

### Notification messages

When you use proactive messages to send notifications, you need to make sure your users have a clear path to take common actions based on your notification, and a clear understanding of why the notification occurred.

## Creating a channel conversation

Your team-added bot can post into a channel to create a new reply chain. The following code demonstrates how to create a new message in the channel when the message **newconversation** is received by the bot:

```typescript
export class ConvoBot extends TeamsActivityHandler {
  constructor() {
    super();

    this.onMessage(async (context: TurnContext, next: () => Promise<void>) => {
      const botMessageText: string = context.activity.text.trim().toLowerCase();
      if (botMessageText.endsWith("newconversation")) {
        const channelId = teamsGetChannelId(context.activity);
        const message = MessageFactory.text("This will be the first message in a new thread");
        const newConversation = await this.createConversationInChannel(context, channelId, message);
        await context.sendActivity({ attachments: [card] });
      }
      await next();
    });
  }

  private async createConversationInChannel(context: TurnContext, teamsChannelId: string, message: Partial<Activity>): Promise<[ConversationReference, string]> {
    // create parameters for the new conversation
    const conversationParameters = <ConversationParameters>{
      isGroup: true,
      channelData: <TeamsChannelData>{
        channel: <ChannelInfo>{
          id: teamsChannelId
        }
      },
      activity: message
    };

    // get a reference to the bot adapter & create a connection to the Teams API
    const adapter = <BotFrameworkAdapter>context.adapter;
    const connectorClient = adapter.createConnectorClient(context.activity.serviceUrl);

    // create a new conversation and get a reference to it
    const conversationResourceResponse: ConversationResourceResponse = await connectorClient.conversations.createConversation(conversationParameters);
    const conversationReference = <ConversationReference>TurnContext.getConversationReference(context.activity);
    conversationReference.conversation.id = conversationResourceResponse.id;

    return [conversationReference, conversationResourceResponse.activityId];
  }
}
```

## Summary

In this unit, you’ll learn how to send proactive messages from your bot.
