In this exercise, you’ll learn how to use task modules with bots in Microsoft Teams.

The first step will be to create a bot and add it to our existing Microsoft Teams app. You'll then extend the bot to support the existing task modules to display a video and change the selected video.

> [!NOTE]
> This exercise requires a valid Azure subscription in order to create a bot using Bot Framework. However, if you do not have an Azure subscription, you can use the legacy Bot Framework Registration Portal. Refer to the following docs for more information: [Create a bot for Microsoft Teams](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/create-a-bot-for-teams)

> [!IMPORTANT]
> This exercise assumes you have created the Microsoft Teams app project with the Yeoman generator that contains a personal tab from the previous exercise in this module. You'll update the project to add a new task module that uses an Adaptive Card.

## Register a new bot in Microsoft Azure

The first step is to create a new Microsoft Teams bot. Adding a bot to the Teams app involves two steps:

1. Register the bot with Microsoft Azure's Bot Framework
1. Add a bot to the project codebase

### Register the bot with Microsoft Azure's Bot Framework

Open a browser and navigate to the [Azure portal](https://portal.azure.com). Sign in using a **Work or School Account** that has rights to create resources in your Azure subscription.

Select **Create a resource** in the left-hand navigation:

![Screenshot of the primary Azure navigation](../media/07-azure-portal-01.png)

Enter **resource group** in the **Search the marketplace** input box, and select **Resource group**.

![Screenshot of creating a resource group](../media/07-azure-portal-02.png)

On the **Resource Group** page, select the **Create** button to create a new resource group.

Select a valid subscription, enter a name for the resource group, and select the wanted region. *None of these choices will impact the bot registration and are up to you.*

![Screenshot of creating a resource group](../media/07-azure-portal-03.png)

Complete the wizard to create the resource group. Once Azure has completed the resource group creation process, navigate to the resource group.

From the resource group, select the **Add** or **Create resources** button.

![Screenshot of creating a new resource](../media/07-azure-bot-registration-01.png)

Enter **bot** in the **Search the marketplace** input box, and select **Bot Channels Registration** from the list of resources returned. Then select **Create** on the next page to start the process of registering a new bot resource:

![Screenshot of searching for the bot registration resource](../media/07-azure-bot-registration-02.png)

In the **Bot Channels Registration** blade, enter the following values and then select **Create**:

- **Bot handle**: *Enter a globally unique name for the bot*
- **Subscription**: *Select the subscription you selected previously when creating the resource group*
- **Resource group**: *Select the resource group you created previously*
- **Location**: *Select your preferred Azure region*
- **Pricing tier**: *Select a preferred pricing tier; the F0 tier is free*
- **Messaging endpoint**: https://REPLACE_THIS.ngrok.io/api/messages

    > The bot registration needs to know the endpoint of the web service where the bot is implemented. This will change each time you start the ngrok utility used in previous exercises.

- **Application Insights**: Off
- **Microsoft App ID and password**: Auto create App ID and password

Azure will start to provision the new resource. This will take a moment or two. Once its finished, navigate to the bot resource in the resource group.

![Screenshot of searching for the bot registration resource](../media/07-azure-bot-registration-03.png)

### Enable the Microsoft Teams channel for the bot

In order for the bot to interact with Microsoft Teams, you must enable the Teams channel.

From the bot resource in Azure, select **Channels** in the left-hand navigation.

On the **Connect to channels** pane, select the Microsoft Teams channel, then select **Save** to confirm the action.

![Screenshot enabling the Microsoft Teams channel](../media/07-azure-bot-registration-04.png)

Once this process is complete, you should see both the **Web Chat** and **Microsoft Teams** listed in your enabled channels:

![Screenshot of the enabled bot channels](../media/07-azure-bot-registration-05.png)

### Retrieve the bot app id and password

When Azure created the bot, it also registered a new Azure AD app for the bot. You need to generate this new bot app a secret and copy the app's credentials.

Select **Settings** from the left-hand navigation. Scroll down to the **Microsoft App ID** section.

Copy the ID of the bot as you'll need it later.

Select **Manage** to navigate to the Azure AD app blade:

![Screenshot of the bot's settings page](../media/07-azure-bot-registration-06.png)

### Create a client secret for the app

In order for the daemon app to run without user involvement, it will sign in to Azure AD with an application ID and either a certificate or secret. In this exercise, you'll use a secret.

Select **Certificates & secrets** from the left-hand navigation panel.

Select the **New client secret** button:

![Screenshot of the Certificates & Secrets page in the Azure AD admin center](../media/07-azure-bot-registration-07.png)

When prompted, give the secret a description and select one of the expiration duration options provided and select **Add**. *What you enter and select doesn't matter for the exercise.*

The **Certificate & Secrets** page will display the new secret. It's important you copy this value as it's only shown this one time; if you leave the page and come back, it will only show as a masked value.

![Screenshot showing the new secret](../media/07-azure-bot-registration-08.png)

Copy the value of the secret as you'll need it later.

### Update the Microsoft Teams app project with the app details

Open the project you created in previous exercises in Visual Studio Code.

Locate the **./.env** file. This is an environment variable helper file used during development.

Locate the properties **MICROSOFT_APP_ID** and **MICROSOFT_APP_PASSWORD** and copy the values of the bot's application ID and secret to these values.

At this point, the bot has been registered with the Azure Bot service. The next step is to implement the bot and add it to Microsoft Teams.

## Add a bot to the project

The first step is to add the bot to the app's manifest file. Locate and open the file **./src/manifest/manifest.json**.

Locate the `id` property and change its value to the same ID as the Azure AD application created for the bot.

Locate the section `"bots": [],` in the **manifest.json** file. Replace this empty collection with the following. Ensure you use the same Azure AD app ID for the `botId` in the following code:

```json
"bots": [
  {
    "botId": "618ddfa7-7990-4bba-ab95-fc6e76d2c019",
    "scopes": [
      "personal"
    ],
    "supportsFiles": false,
    "isNotificationOnly": false,
    "commandLists": [
      {
        "scopes": [ "personal" ],
        "commands": [
          {
            "title": "MentionMe",
            "description": "Sends message with @mention of the sender"
          }
        ]
      }
    ]
  }
],
```

This registers a new bot that only exists in the personal scope and has a single command **MentionMe**. You'll use this to ensure the bot is working.

The next step is to add the code to implement the bot.

### Code the bot

> [!IMPORTANT]
> At the time of publication of this module, there are plans to update the Yeoman generator for Microsoft Teams to use the Bot Framework v4 SDK. However, at the time of publication of this module, the default project uses an older SDK.
>
> Therefore, the following steps that remove & upgrade the **botbuilder** package may or may not be necessary as the Yeoman generator for Microsoft Teams may have been updated. Review each of the instructions in this section and compare the results with your project to determine if they are necessary.

Remove the older bot SDK and related packages. Then, upgrade the bot builder project, execute the following two commands in the command line from the root folder of the project:

```shell
npm uninstall botbuilder-dialogs botbuilder-teams botframework-config
npm install botbuilder@4.6.2
```

Create a new folder **learningTeamsBot** in the **./src/app** folder.

Create a new file **teamsLearningBot.ts** in this new folder **./src/app/learningTeamsBot/teamsLearningBot.ts**

Add the following code to the **teamsLearningBot.ts** file:

```ts
import {
  ActionTypes,
  CardFactory, MessageFactory,
  TeamsActivityHandler, TaskModuleTaskInfo,
  TurnContext, TaskModuleRequest, TaskModuleResponse
} from "botbuilder";
import * as Util from "util";

const TextEncoder = Util.TextEncoder;

export class TeamsLearningBot extends TeamsActivityHandler {
  constructor() {
    super();

    // create handlers
    this.onMessage(async (context, next) => {
      switch (context.activity.text.trim().toLowerCase()) {
        case "mentionme":
          await this.mentionActivity(context);
          break;
        default:
          const card = CardFactory.heroCard("Learn Microsoft Teams", undefined, [ ]);
          await context.sendActivity({ attachments: [card] });
          break;
      }
      await next();
    });
  }

  private async mentionActivity(context: TurnContext) {
    const mention = {
      mentioned: context.activity.from,
      text: `<at>${new TextEncoder().encode(context.activity.from.name)}</at>`,
      type: 'mention'
    };

    const replyActivity = MessageFactory.text(`Hi ${mention.text}`);
    replyActivity.entities = [mention];
    await context.sendActivity(replyActivity);
  }
}
```

### Update the webserver to load the bot

The next step is to get the bot working in the project.

Locate and open the file **./src/app/server.ts**.

Add the following `import` statements to the end of the existing `import` statements:

```ts
import { BotFrameworkAdapter } from "botbuilder";
import { TeamsLearningBot } from "./learningTeamsBot/teamsLearningBot";
```

Locate the following code at the end of the file:

```ts
http.createServer(express).listen(port, () => {
  log(`Server running on ${port}`);
});
```

This code creates the server and starts listening on a port. You need access to the server to load the bot. Update the above code to separate the creation of the web server and listening on a specific port to the following:

```ts
const server = http.createServer(express);
server.listen(port, () => {
  log(`Server running on ${port}`);
});
```

Add the following code to the end of the **server.ts** to create a bot framework adapter. This code uses the environment variables defined in the **./.env** file to set the Azure AD app ID and secret of the bot:

```ts
const botAdapter = new BotFrameworkAdapter({
  appId: process.env.MICROSOFT_APP_ID,
  appPassword: process.env.MICROSOFT_APP_PASSWORD
});
```

Add the following error handler to the end of the **server.ts** file.

```ts
botAdapter.onTurnError = async (context, error) => {
  console.error(`\n [bot.onTurnError] unhandled error: ${error}`);
  await context.sendTraceActivity("OnTurnError Trace", `${error}`, "https://www.botframework.com/schemas/error", "TurnError");
  await context.sendActivity("bot error");
};
```

Load the bot and register a new endpoint, **/api/messages**. When HTTP POSTS are received on this endpoint, they're routed into the bot adapter:

```ts
const bot = new TeamsLearningBot();
express.post("/api/messages", (request, response) => {
  botAdapter.processActivity(request, response, async (context) => {
    await bot.run(context);
  });
});
```

### Test the bot in Microsoft Teams

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

In the console, locate the dynamic URL created by ngrok:

![Screenshot of the console with ngrok URL](../media/07-test-bot-01.png)

Go back to the bot registration in the Azure portal.

Select **Settings** from the left-hand navigation. Update the **Messaging endpoint** of the bot to match the ngrok URL. The resulting URL should be **https://{{REPLACE_THIS}}.ngrok.io/api/messages**.

![Screenshot of the console with ngrok URL](../media/07-test-bot-02.png)

Locate the **./.env** file in the project. Update the property **HOSTNAME** to point to the same ngrok URL: **{{REPLACE_THIS}}.ngrok.io**.

Now you're ready to add the bot to Microsoft Teams. In the browser, navigate to **https://teams.microsoft.com** and sign in with the credentials of a Work and School account.

> [!NOTE]
> Microsoft Teams is available for use as a web client, desktop client and a mobile client. In this module, we will use the web client but any of the clients can be used.

Using the app bar navigation menu, select the **Mode added apps** button. Then select **Browse all apps** followed by **Upload for me or my teams**.

![Screenshot of More added apps dialog in Microsoft Teams](../media/03-yo-teams-05.png)

In the file dialog that appears, select the Microsoft Teams package in your project. This app package is a ZIP file that can be found in the project's **./package** folder.

Once the package is uploaded, Microsoft Teams will display a summary of the app. Here you can see some "todo" items to address. *None of these "todo" items are important to this exercise, so you'll leave them as is.*

![Screenshot of Microsoft Teams app](../media/07-yo-teams-06.png)

Notice Microsoft Teams recognizes there's a bot associated with the app.

Select the **Add** button to install the app, adding a new personal tab to your **More added apps** dialog:

![Screenshot of the installed Microsoft Teams app in the More added apps dialog](../media/03-yo-teams-07.png)

Select the app to navigate to the tab:

![Screenshot of the installed Microsoft Teams app personal tab](../media/07-test-bot-03.png)

Notice there's a new **Conversation** tab. Focus on the message box at the bottom of the user interface. Microsoft Teams is displaying the things this bot can do, including the **MentionMe** action. Let's try that out.

Enter `MentionMe` following in the message box and press <kbd>enter</kbd>.

![Screenshot of the MentionMe bot action](../media/07-test-bot-04.png)

Next, enter some random text. Because the bot is looking for specific text, it will display the default message:

![Screenshot of the default message](../media/07-test-bot-05.png)

At this point, the bot is working. Move onto the next section to add task module support.

## Add the video player task module

In this section, you'll add a task module to the bot. First, let's update the Hero card to add a button the user can select.

In the bot file, **./src/app/learningTeamsBot/teamsLearningBot.ts**, locate the class constructor. Locate Hero card statement in the `switch` statement's `default` path in the `onMessage()` handler:

```ts
const card = CardFactory.heroCard("Learn Microsoft Teams", undefined, [ ]);
```

Update this statement to add a new action to the card. The type of this action is special: `invoke`.

```ts
const card = CardFactory.heroCard("Learn Microsoft Teams", undefined, [
  {
    type: "invoke",
    title: "Watch 'Overview of Microsoft Teams'",
    value: { type: "task/fetch", taskModule: "player", videoId: "X8krAMdGvCQ" }
  }
]);
```

The project's **ngrok-serve** task will detect the code change, rebuild & restart the web server. After a moment, enter another random string in the **Conversations** tab for the bot and notice the new card:

![Screenshot of the updated default Hero card response](../media/07-task-module-01.png)

The bot framework is looking for messages of type `invoke` with their `value.type` property set to `task/fetch`. For each one it finds, it passes it into a handler `handleTeamsTaskModuleFetch()`. To handle what happens when you select the action, implement the method.

Add the following code to the `TeamsLearningBot` class:

```ts
protected handleTeamsTaskModuleFetch(context: TurnContext, request: TaskModuleRequest): Promise<TaskModuleResponse> {
  let response: TaskModuleResponse;

  switch (request.data.taskModule) {
    case "player":
      response = <TaskModuleResponse>{
        task: {
          type: "continue",
          value: <TaskModuleTaskInfo>{
            title: "YouTube Player",
            url: `https://${process.env.HOSTNAME}/youTubePlayer1Tab/player.html?vid=${request.data.videoId}`,
            width: 1000,
            height: 700
          }
        }
      };
      break;
    default:
      response = <TaskModuleResponse>{
        task: {
          type: "continue",
          value: <TaskModuleTaskInfo>{
            title: "YouTube Player",
            url: `https://${process.env.HOSTNAME}/youTubePlayer1Tab/player.html?vid=X8krAMdGvCQ&default=1`,
            width: 1000,
            height: 700
          }
        }
      };
      break;
  };

  console.log("handleTeamsTaskModuleFetch() response", response);
  return Promise.resolve(response);
}
```

### Test the video player task module

After saving the page, let the project rebuild itself and restart the web server. Once that's happened, select the **Watch `Overview of Microsoft Teams`** button in the Hero card. Notice the task module from the previous exercise is displayed:

![Screenshot of the player task module](../media/07-task-module-02.png)

Create a few more buttons to the Hero card that reference different videos by duplicating the existing button. Make sure to create one that has the `value.taskModule` property set to something other than `player` so the handler takes the default path:

```ts
const card = CardFactory.heroCard("Learn Microsoft Teams", undefined, [
  {
    type: "invoke",
    title: "Watch 'Overview of Microsoft Teams'",
    value: { type: "task/fetch", taskModule: "player", videoId: "X8krAMdGvCQ" }
  },
  {
    type: "invoke",
    title: "Watch 'Go-to guide for team owners'",
    value: { type: "task/fetch", taskModule: "player", videoId: "7XcDSuw6NR4" }
  },
  {
    type: "invoke",
    title: "Watch a invalid action...",
    value: { type: "task/fetch", taskModule: "something", videoId: "helloworld" }
  }
]);
```

![Screenshot of additional actions](../media/07-task-module-03.png)

The next step is to add a task module that submits data.

## Add the video selector Adaptive Card task module

In this section, you'll add an action to the Hero card that displays a task module using an Adaptive Card. This task module will submit data back to the bot that will use the value to display the specified video in the player task module.

In the bot file, **./src/app/learningTeamsBot/teamsLearningBot.ts**, locate the code in the `teamsLearningBot` class constructor that created the Hero card. Add another action to the end, but notice this action specifies a different `value.taskModule` property:

```ts
{
  type: "invoke",
  title: "Watch Specific Video",
  value: { type: "task/fetch", taskModule: "selector", videoId: "QHPBw7F4OL4" }
}
```

You'll chain two task modules together. The first will display the Adaptive Card selector. Within the `handleTaskModuleFetch()` method, add the following `case` statement to the existing `switch` statement:

```ts
case "selector":
  response = <TaskModuleResponse>{
    task: {
      type: "continue",
      value: <TaskModuleTaskInfo>{
        title: "YouTube Video Selector",
        card: this.getSelectorAdaptiveCard(request.data.videoId),
        width: 350,
        height: 250
      }
    }
  };
  break;
```

Add the following method to the `TeamsLearningBot` class. This will create an Adaptive Card with an input control. This is the programmatic way of creating the same adaptive card from a previous exercise.

```ts
private getSelectorAdaptiveCard(defaultVideoId: string = "") {
  return CardFactory.adaptiveCard({
    type: "AdaptiveCard",
    version: "1.0",
    body: [
      {
        type: "Container",
        items: [
          {
            type: "TextBlock",
            text: "YouTube Video Selector",
            weight: "bolder",
            size: "extraLarge"
          }
        ]
      },
      {
        type: "Container",
        items: [
          {
            type: "TextBlock",
            text: "Enter the ID of a YouTube video to show in the task module player.",
            wrap: true
          },
          {
            type: "Input.Text",
            id: "youTubeVideoId",
            value: defaultVideoId
          }
        ]
      }
    ],
    actions: [
      {
        type: "Action.Submit",
        title: "Update"
      }
    ]
  });
}
```

Next, add the handler for the Adaptive Card handler method. Similar to the `task/fetch`, we need to handle a submit, or `task/submit`. Do this by adding the following method to the `TeamsLearningBot` class:

```ts
protected handleTeamsTaskModuleSubmit(context: TurnContext, request: TaskModuleRequest): Promise<TaskModuleResponse> {
  const response: TaskModuleResponse = <TaskModuleResponse>{
    task: {
      type: "continue",
      value: <TaskModuleTaskInfo>{
        title: "YouTube Player",
        url: `https://${process.env.HOSTNAME}/youTubePlayer1Tab/player.html?vid=${request.data.youTubeVideoId}`,
        width: 1000,
        height: 700
      }
    }
  };
  return Promise.resolve(response);
}
```

This handler will fetch the submitted video ID from the Adaptive Card and use it to present the player task module.

### Test the video selector Adaptive Card task module

After saving your changes and giving the project a moment to rebuild and restart the webserver, enter another message into the bot **Conversation** tab:

![Screenshot of the Specific Video button in the Hero card](../media/07-adaptive-card-01.png)

Select the **Watch Specific Video** button. When the Adaptive Card task module loads, either accept the default value or enter the ID of a video on YouTube.

![Screenshot of the player task module with the specified video](../media/07-adaptive-card-02.png)

Select the **Update** button. Notice the Adaptive Card task module disappears and the player task module loads with the specified video.

Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console to stop the running process.

## Summary

In this exercise, you learned how to use task modules with bots in Microsoft Teams. After creating and adding it to our existing Microsoft Teams app, then extend the bot to support the existing task modules to display a video and change the selected video.
