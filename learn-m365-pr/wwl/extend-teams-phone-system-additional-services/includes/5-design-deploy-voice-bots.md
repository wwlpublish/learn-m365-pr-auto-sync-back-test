Voice bots, or calling and meeting bots, can interact with Teams calls and meetings using real-time voice, video, and screen sharing. Calls can be from a person to a bot, or a bot can join a meeting.

> [!NOTE]
> These bots are different to the chatbot or conversational bots that allow chat-based interaction with users or automated sending of chat messages.

Third-party Teams solutions like compliance recording and contact center use bots. In the previous units, you have seen us granting access to bots for call recording solution and contact centers. This is the most common scenario that a Teams voice administrator will interact with voice bots.

However, if you are developing your own solution involving voice bots or need to support a development team by deploying a custom voice bot, this unit will show you how.

> [!NOTE]
> In scenarios where you are deploying a third-party certified SaaS solution you will not need to design or deploy the voice bot and just approve access to it.

## Design voice bot

When using voice bots, you need to decide which type of bot you need. There are two types of bots that can deal with real-time media:

- Service-hosted media bots you can hand off the audio and video processing to Microsoft services.

- Application-hosted media bots allow your solution to have direct access to the media.

### Service-hosted media bots

Service-hosted media bots are focused on application workflows like call routing. You can play audio files, record audio clips, and receive dual-tone multiple frequency (DTMF) tones from the user, that is, listen for the tone when they are asked to “Press 1 for sales.”

Dealing with real-time media streams is very complex. The service hosted media bots allow you to create workflows and engage with users on a call or meeting without having to directly deal with the media steam. This is great for building basic interactive voice response (IVR) scenarios, such as a main number welcome message and menu of departments to select from.

### Application-hosted media bots

These bots get direct access to the audio and video media stream. This is needed for scenarios like compliance call recording. The bot must be deployed on a Windows Server machine or Windows Server guest Operating System (OS) in Azure. The VM instance hosting the real-time media bot must have at least 2 CPU cores.

> [!TIP]
> The bots require more compute and network bandwidth capacity than messaging bots and incur significantly higher operational costs. A real-time media bot developer must carefully measure the bot's scalability and ensure the bot does not accept more simultaneous calls than it can manage.

Work with the development team to confirm their scenario and which type of bot is appropriate. They can then create the bot with the Azure Bot Framework SDK and deploy it into Azure.

## Registering a calling bot in the Azure Bot Service

Once the development team have created the bot and deployed it in Azure, you need to register it so that it can be deployed to Teams.

1. Go to the Microsoft Azure portal at [https://portal.azure.com](https://portal.azure.com/).
1. Below Azure services, select **Create a resource**.
1. In the search box enter *bot*, then press **Enter**.
1. Select the **Azure Bot**
1. Select **Create**
1. Enter the required values.
    - Bot Handle is a unique identifier for your bot. You can choose a different Display Name for your bot in the Settings blade after bot creation.
    - Choose an Azure subscription and resource group
    - Choose to crate a new Microsoft App ID
1. Select **Review + create**.
1. If the validation passes, select **Create**.
1. Select **Go to resource group**. You should see the bot and the related **Azure Key Vault** resources listed in the resource group you selected.

From here, the development team can upload the app to Microsoft Teams as a custom app to side load or publish to the organization or the wider Teams app store.
