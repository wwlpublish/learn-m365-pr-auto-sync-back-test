Teams apps let you do more in Teams. Think about the tools, files, and dashboards your org already uses. Many of them can be added right into Teams. Teams apps provide out-of-the-box tools that enable your organization to maximize its Teams experience in the context of a **channel in a team**, a **group chat**, or an individual **user** alone (personal app).   

You can use apps functionality within Microsoft Teams to help you find content from your favorite services and then share it in Teams. Apps can assist you with things such as pinning services at the top of a channel, chatting with bots, and sharing and assigning tasks. For example, you can add the Microsoft Planner app to your initial Teams rollout to drive Teams adoption.

:::image type="content" source="../media/teams-apps.png" alt-text=" Teams app":::

These apps combine the functionality of tabs, messaging extensions, connectors, and bots provided by **Microsoft**, built by a **third-party**, or by **developers** in your organization. In the collaborative social framework of Teams, there's a wide variety of user needs that you can solve with a Teams app.

The app user and their app's requirements are the basic guidelines that determine all app choices you'll make. Building app design, selecting capabilities, determining build and test environment, and app distribution follow the user's requirement from the app.

## Microsoft Teams app capabilities

The Microsoft Teams platform offers a large variety of features. Each feature is a way of interacting with your users that makes the Teams app capability relevant to the user need.

Capabilities are the core functionalities that you can build in your app. They're also called entry or extension points because they enable integration and interaction. Your Teams apps can have one or all of the following core capabilities:

-   **Personal apps:** A [personal app](/microsoftteams/platform/concepts/design/personal-apps?azure-portal=true) is a dedicated space or bot to help users focus on their own tasks or view relevant activities.
-   **Tabs:** Display your web-based content in a [tab](/microsoftteams/platform/tabs/what-are-tabs?azure-portal=true) where people can discuss and work on it together.
-   **Bots:** Conversations often result in the need to do something (generate an order, review code, check ticket status, and so on). A [bot](/microsoftteams/platform/bots/what-are-bots?azure-portal=true) can kick off these kinds of workflows right inside Teams.
-   **Message extensions:** With [message extensions](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions?azure-portal=true), you can search and share external information. You also can act on a message, such as creating a help ticket based on the content of a channel post.
-   **Meeting extensions:** There are a few options for [incorporating your app into the Teams calling experience](/microsoftteams/platform/apps-in-teams-meetings/design/designing-apps-in-meetings?azure-portal=true).
-   **Webhooks and connectors :** [Incoming webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors?azure-portal=true) are a simple way to automatically send notifications from another app to a Teams channel. With [outgoing webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors?azure-portal=true), you can message your web service with an @mention.
-   **Microsoft Graph for Teams:** The [Microsoft Graph API for Teams](/graph/teams-concept-overview?azure-portal=true) provides access to information about teams, channels, users, and messages that helps you to create or enhance features for your app.


There are several ways you can interact with apps and services in Teams:

* **Share content on a tab**

    When you work with different people, you want different information and different tools on hand. You can add relevant files and apps as tabs to any Teams conversation. Tabs help you share content and functionality from your favorite services in a channel. They can connect you to Microsoft services (like Excel, SharePoint, Power Apps), other services (like Asana, YouTube, and Zendesk), or to a website of your choice. 

* **Get updates from a connector**

    Connectors keep your team current by delivering content and updates directly to a channel from services you frequently use. With connectors, Teams users can receive updates from popular services such as Twitter, Trello, Wunderlist, GitHub, and Azure DevOps Services in their Teams chats.

* **Add rich content to your messages**

    These apps find content from different services and send it straight to a message. You can share things like weather reports, daily news, images, and videos with anyone you're talking to. Messages sometimes include buttons for interacting with the app. For example, a daily weather report could include an option to download the forecast for the entire week.

    :::image type="content" source="../media/search-extension.png" alt-text=" Screenshot of Search extension in Teams client":::

* **Chat with a bot**
    
    Bots provide answers, updates, and assistance in private chats or channels. You can chat with them one-on-one or in a channel. Bots allow you to interact with cloud services such as task management, scheduling, and polling in a Teams chat.
  
    :::image type="content" source="../media/chat-bot.gif" alt-text=" Screenshot of Bots in Teams client":::

## Teams and Microsoft Power Platform

Microsoft Power Platform is the innovative gateway to rapidly build Teams compatible apps using low code attributes. You can use Microsoft Power Platform to build solutions, automate processes, analyze data, and create virtual agents within a unified and integrated environment:
 
-   **Power BI**: You can create packaged Power BI app content from scratch and distribute it as an app or create a template app in Power BI. Additionally, you can use the Power BI app in Teams to bring your entire basic Power BI service experience into Teams.
-   **Power Apps**: You can export the pre-built app from the Power Apps maker portal and embed in Microsoft Teams.
-   **Power Automate**: You can create flows to automate repetitive work tasks directly within the Teams environment with the Power Automate app in Teams. You can trigger a flow from any message in Microsoft Teams and use Adaptive Cards within Power Automate.
-   **Power Virtual Agents**: You can use the Power Virtual Agents app in Teams, to create, manage, and publish conversational chatbots easily from within Teams. You can also integrate your Power Virtual Agents chatbot to Teams.
-   **Virtual Assistant for Teams**: Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data. You can configure your virtual assistant for integration into the Teams.

:::image type="content" source="../media/power-platform.png" alt-text="The graph illustrates Microsoft Teams can combine capabilities from a wide spectrum of tools to create a fully integrated experience":::

> [!NOTE]
> You must not use Microsoft Power Platform to create apps that are to be published to the Teams app store. Microsoft Power Platform apps can be published to an organization’s app store only.