Creating a bot from start to finish is a five-step process.

### Step 1 - Create the bot

A bot is the overlying structure to which the bot creator will assign their conversation. Complete the following steps to create a bot:

1.  Go to [Power Virtual Agents](https://aka.ms/TryPVA?azure-portal=true) in your browser. Supported browsers include Microsoft Edge, Chrome, and Firefox. On the website, select **Start free**. The bot creator must then sign in with their work email address. Microsoft accounts (@microsoft.com) aren't currently supported.
2.  Choose a name for the bot. The name can be something generic to the bot creator's company or specific to the scenario the bot creator is tailoring the bot to.
3.  The bot is created in the default Power Apps environment that was created when the bot creator signed up. This environment should be sufficient for most users. However, if the bot creator wants to specify a custom Power Apps environment for their Power Virtual Agents, they can do so by expanding the **More options** menu and selecting a different environment.
4.  After selecting **Create**, the process of creating the first bot within a new environment can take up to 15 minutes. Later bots will be created much faster.
5.  After a few minutes, the home page will be displayed. From this page, the bot creator can play around with the bot in read-only mode. No edits can be saved during this time, but the bot creator can:
    
     -  explore the overall user interface.
     -  look at the topics.
     -  experiment with the preloaded User Topics and System Topics.
     -  interact with the bot using the Test Canvas.
6.  The banner changes when the bot creation process completes. The bot creator now has full functionality in the bot. They can modify any User or System topic, test out content changes, or deploy the bot.

**Additional reading.** For more information on creating bots using Power BI Virtual Agents, see [Authoring key concepts](/power-virtual-agents/authoring-fundamentals?azure-portal=true).

### Step 2 - Create a topic for a bot

A topic is basically a conversation. Once the bot is created, the bot creator must create the topic for that bot. A topic is the dialog tree that specifies how the bot responds to a user's question. For each topic, the bot creator can assign trigger phrases, which are used by the system to select the appropriate bots that may apply to a user's question.

Complete the following steps to create a topic for the bot:

1.  Start by selecting **Topics** in the side navigation pane, and then select **New topic** at the top of the page.
2.  Name the topic and include some trigger phrases for this topic. Trigger phrases are examples of the type of user questions or utterances that help select this bot to respond to user queries. For example, assume bot creator wants to create a topic called **Personal Hello World** and add **hello world** as a trigger phrase. Select **Save topic** to add the topic to the topics list.
3.  After saving the topic, select **Go to authoring canvas**. This page is the graphical dialog tree editor that enables bot creator to define bot responses and the overall bot conversation. In the **Personal Hello World** example, bot creator could start by entering **Hello! I’ll create a personalized greeting for you.** into the first **Message** node.
4.  Select the plus sign (+) below the node and add an **Ask a question** node by selecting it in the menu. Enter the question text "**Where do you live?"** in the **Ask a question** box. To give the customer a choice between different responses, select **Multiple Choice** options under **Identify**.
5.  Add two options for the user by selecting **+ New option**. Enter **Seattle** and **Bellevue** in the **Options for user** text boxes. Each option is presented as a Multiple Choice button to the user. The authoring canvas creates separate paths in the conversation, depending on the customer's response. The conversation path leads the customer to the appropriate resolution for each user response.
6.  In the forked conversation path, each node has automatically checked for **Seattle** in one path, and **Bellevue** in the other path to take the appropriate next step.
7.  Select the plus sign (+) below each of the **Condition** nodes to add a **Message** node in each branch. Add a message like **Hello Seattle!** in the Seattle branch, and **Hello Bellevue!** in the Bellevue branch. Select **Save** at the top.

After the bot creator completes these steps, they can create a basic branching dialog tree. More complex versions of this tree can be created by incorporating [variables](/power-virtual-agents/authoring-variables?azure-portal=true), [entities](/power-virtual-agents/advanced-entities-slot-filling?azure-portal=true), and [Power Automate flows](/power-virtual-agents/advanced-flow?azure-portal=true).

### Step 3 - Test the bot

Once a topic is created for the bot, the bot creator can test it in real time to see if it’s working as expected. To do so, the bot creator must complete the following steps in the test bot panel:

1.  Test the dialog tree by typing into the test bot window. Turn on **Track between topics** at the top, which enables the bot creator to follow along with the bot as it executes the bot's dialog. Parts of the dialog tree will be highlighted as the bot gets to that portion of the dialog.
2.  Let's continue with the **Personal Hello World** example that we used when explaining how to create a topic. To test this topic, type **hello world** in the chat window, and send the message to the bot. The top portion of the dialog tree will be highlighted in green. **Seattle** and **Bellevue** will be presented as user options in the test bot window.
3.  The bot is now waiting for a response and has provided suggestions on how to respond. These suggestion buttons reflect what the bot author created in the dialog tree in the **Ask a question** node. In the test bot, either select these suggestion buttons to continue, or enter a response in the chat window.
4.  Continue the dialog by selecting the **Seattle** branch. The chat will stop once the bottom of this branch is reached. If more content was authored, the dialog will continue. Since this example is a small dialog tree, it will quickly reach the end of the content.

This test experience enables the bot author to quickly create and test a conversation to ensure it flows as expected. If the dialog doesn't reflect your intention, you can change and save it. The latest content will be pushed into the test bot, and it can be tested again later. None of the changes that are made here will affect the published version of the bot. This design enables the bot author experiment with the content. They can make as many changes as they want until they're satisfied with the bot.

### Step 4 - Publish the bot

Once a bot author satisfied with the content authored in the bot, they can publish the bot to a website.

Complete the following steps to publish a bot:

1.  Select the **Publish** tab in the side navigation pane.
2.  Select **Publish** to activate the bot with a single selection. If the publish is successful, a green banner on the top of the page will indicate the bot was successfully published.
3.  Select the demo website link under **Share your bot** to see it in action on a demo website.
4.  A new window should open in the browser. This webpage demonstrates what the bot looks like to an end user who comes to this webpage. The bot canvas is at the bottom. The bot author can interact with it by typing into the window or by selecting a starter phrase from the provided options. This webpage demonstrates the bot in action.

    > [!NOTE]
    > If the new window fails to happen automatically, check whether a pop-up blocker has been activated. If so, allow the window to be opened. Pop-ups can usually be allowed directly from the URL field.

### Step 5 - Analyze the performance of your bot

Statistics are generated every time a bot is run. Once a bot has completed interactions with users, the bot author can analyze the statistics to determine how well it's doing.

Complete the following step to analyze the statistics:

1.  Select the **Analytics** tab in the side navigation pane. On this tab, key performance indicators (KPIs) are displayed that show:
    
     -  the volume of sessions the bot has handled.
     -  how effectively the bot engaged end users and resolved issues.
     -  escalation rates to human agents.
     -  abandonment rates during conversations.
2.  Select **Sessions** from the **Analytics** tab to view detailed session history and transcripts. This page enables the bot author to download a CSV file with the full session transcript. Reviewing the transcript is a helpful way to fine-tune the bot's performance and change the content in the topics to improve the bot’s efficiency.
3.  Select the **Customer Satisfaction** tab to analyze customer satisfaction information at the KPI level.

**Additional reading.** For more information, see [Analytics key concepts](/power-virtual-agents/analytics-overview?azure-portal=true).
