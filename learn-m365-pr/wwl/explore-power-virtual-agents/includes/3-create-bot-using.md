Creating a bot from start to finish is a five-step process.

### Step 1 - Create the bot

A bot is the overlying structure to which you'll assign your conversation.

Complete the following steps to create a bot:

1.  Go to [Power Virtual Agents](https://aka.ms/TryPVA?azure-portal=true) in your browser. Supported browsers include Microsoft Edge, Chrome, and Firefox. On the website, select **Start free**, and then sign in with your work email address. Microsoft accounts (@microsoft.com) aren't currently supported.
2.  Next, you must choose a name for your bot. The name can be something generic to your company or specific to the scenario you're tailoring your bot to.
3.  Your bot is created in the default Power Apps environment that was created for you when you signed up. This environment should be sufficient for most users. However, if you want to specify a custom Power Apps environment for your Power Virtual Agents, you can do so by expanding the **More options** menu and selecting a different environment.
4.  Once you select **Create**, the process of creating the first bot within a new environment can take up to 15 minutes. Later will be created much faster.
5.  After a few minutes, you'll land on the home page. From this page, you can play around with the bot in read-only mode. You can't save any edits during this time, but you can:
    
     *  explore the overall user interface.
     *  look at the topics.
     *  experiment with the preloaded User Topics and System Topics.
     *  interact with your bot using the Test Canvas.
6.  The banner changes when the bot creation process completes. You now have full functionality in the bot and can modify any User or System topic, test out your content changes, or deploy your bot.

**Additional reading.** For more information on creating bots using Power BI Virtual Agents, see [Authoring key concepts](https://docs.microsoft.com/power-virtual-agents/authoring-fundamentals?azure-portal=true).

### Step 2 - Create a topic for a bot

A topic is basically a conversation. Once you create the bot, you'll create the topic for that bot. A topic is the dialog tree that specifies how your bot responds to a user's question. For each topic, you can assign trigger phrases, which are used by the system to select the appropriate bots that may apply to a user's question.

Complete the following steps to create a topic for your bot:

1.  Start by selecting **Topics** in the side navigation pane, and then select **New topic** at the top of the page.
2.  You can now name your topic and include some trigger phrases for this topic. Trigger phrases are examples of the type of user questions or utterances that help select this bot to respond to user queries. For example, assume you want to create a topic called **Personal Hello World** and add **hello world** as a trigger phrase. Select **Save topic** to add the topic to the topics list.
3.  After saving your topic, select **Go to authoring canvas**. This page is the graphical dialog tree editor that enables you to define bot responses and the overall bot conversation. In the **Personal Hello World** example, you could start by entering **Hello! I’ll create a personalized greeting for you.** into the first **Message** node.
4.  Select the plus sign (+) below the node and add an **Ask a question** node by selecting it in the menu. Enter the question text "**Where do you live?"** in the **Ask a question** box. To give the customer a choice between different responses, select **Multiple choice** options under **Identify**.
5.  Add two options for the user by selecting **+ New option**. Enter **Seattle** and **Bellevue** in the **Options for user** text boxes. Each option is presented as a multiple choice button to the user. The authoring canvas creates separate paths in the conversation, depending on the customer's response. The conversation path leads the customer to the appropriate resolution for each user response.
6.  In the forked conversation path, each node has automatically checked for **Seattle** in one path, and **Bellevue** in the other path to take the appropriate next step.
7.  Select the plus sign (+) below each of the **Condition** nodes to add a **Message** node in each branch. Add a message like **Hello Seattle!** in the Seattle branch, and **Hello Bellevue!** in the Bellevue branch. Select **Save** at the top.

After completing these steps, you can create a basic branching dialog tree. You can create more complex versions of this tree by incorporating [variables](https://docs.microsoft.com/power-virtual-agents/authoring-variables?azure-portal=true), [entities](https://docs.microsoft.com/power-virtual-agents/advanced-entities-slot-filling?azure-portal=true), and [Power Automate flows](https://docs.microsoft.com/power-virtual-agents/advanced-flow?azure-portal=true).

### Step 3 - Test the bot

Once you've created a topic for your bot, you can test it in real time to see if it’s working as you expected. To do so, you’ll use the test bot panel.

Complete the following step to test the bot in real time:

1.  You can test your dialog tree by typing into the test bot window. Turn on **Track between topics** at the top, which enables you to follow along with the bot as it executes your dialog. You’ll start to see parts of your dialog tree highlighted as the bot gets to that portion of the dialog.
2.  Let's continue with the **Personal Hello World** example that we used when explaining how to create a topic. To test this topic, type **hello world** in the chat window, and send the message to the bot. You’ll see the top portion of your dialog tree highlighted in green. You’ll also see **Seattle** and **Bellevue** presented as user options in the test bot window.
3.  The bot is now waiting for you to respond and has provided suggestions on how to respond. These suggestion buttons reflect what you authored within your dialog tree in the **Ask a question** node. In the test bot, you can either select these suggestion buttons to continue, or you can enter your response in the chat window.
4.  You can continue the dialog by selecting the **Seattle** branch. The chat will stop once you've reached the bottom of this branch. If you author more content, the dialog will continue. Since this example is a small dialog tree, it will quickly reach the end of the content.

This test experience enables you to quickly create and test a conversation to ensure it flows as expected. If the dialog doesn't reflect your intention, you can change and save it. The latest content will be pushed into the test bot, and you can try it out again. None of the changes that you make here will affect the published version of the bot. This design enables you to play around with your content and make as many changes as you would like until you're satisfied with the bot.

### Step 4 - Publish the bot

Once you're satisfied with the content authored in your bot, you can publish your bot to a website.

Complete the following step to publish a bot:

1.  Start by selecting the **Publish** tab in the side navigation pane.
2.  Select **Publish** to activate your bot with a single click. If the publish is successful, a green banner on the top of the page will indicate the bot was successfully published.
3.  Select the demo website link under **Share your bot** to see it in action on a demo website.
4.  A new window should open in your browser. This webpage demonstrates what your bot looks like to an end user who comes to your webpage. The bot canvas is at the bottom. You can interact with it by typing into the window or by selecting a starter phrase from the provided options. This webpage demonstrates your bot in action.

### Step 5 - Analyze the performance of your bot

Statistics are generated every time a bot is run. Once your bot has completed interactions with users, you can analyze the statistics to determine how well the bot is doing.

Complete the following step to analyze the statistics:

1.  Select the **Analytics** tab in the side navigation pane. On this tab, you'll find key performance indicators (KPIs) that show:
    
     *  the volume of sessions your bot has handled.
     *  how effectively your bot engaged end users and resolved issues.
     *  escalation rates to human agents.
     *  abandonment rates during conversations.
2.  Select **Sessions** from the **Analytics** tab to view detailed session history and transcripts. This page enables you to download a CSV file with the full session transcript. Reviewing the transcript will be a helpful way to fine-tune the performance of your bot and change the content in your topics to improve the bot’s efficiency.
3.  Select the **Customer Satisfaction** tab to analyze customer satisfaction information at the KPI level.

**Additional reading.** For more information, see [Analytics key concepts](https://docs.microsoft.com/power-virtual-agents/analytics-overview?azure-portal=true).
