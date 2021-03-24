In the following exercise, you'll get a hands-on look at Graph Explorer and see key Microsoft Graph APIs that can be called. 
 

## Get started with Graph Explorer 

Let’s say a salesperson would like to see profile information including name, job title, mail, and mobile phone. You can complete the following steps to get a user's profile in Graph Explorer: 

1. Visit the Graph Explorer website using the following URL: https://developer.microsoft.com/graph/graph-explorer. 
2. Under the **Sample queries** on the left, select any Microsoft Graph API. 
3. The selected query will automatically run in Graph Explorer. Notice the URL for the Microsoft Graph API you chose to test. 
4. When your query runs successfully, you'll get an **OK – 200** notification. 
5. The request result will appear under the **Response preview**. 
:::image type="content" source="../media/5-get-started-graph-explorer.png" alt-text="Screenshot showing Microsoft Graph get started with user profile.":::

## Test queries with your own account in Graph Explorer 

For this exercise, let’s assume a salesperson is looking for documents shared in meetings, Teams chat, or e-mail. The sales company would also like to have an easier way to view trending documents around users. As a developer, you can test getting trending items around you using the Microsoft Graph API for Insights in Graph Explorer.  

Microsoft Graph Explorer uses sample account data by default. However, to test queries that get your own data you can sign in with your account. It can be accomplished by using the **Authentication** feature available in the Graph Explorer: 

1. Make sure to create **Microsoft 365 Developer Program tenant**, check the prerequisites of the module.  
1. Select the **Sign in to Graph Explorer** button on the left, sign in with your **Microsoft 365 developer tenant** account, provide consent for requested permissions by Graph Explorer and **Accept**. After you've signed in, your profile information will appear on the left. 
1. Select **GET items trending around me** from the Sample queries.  
1. You'll receive a warning that means Microsoft Graph Insights API requires some permissions to run the query. 
1. Select **Modify permissions**, you'll see the required permissions for the selected query. 
1. Select **Consent** to provide consent for each permission. 
:::image type="content" source="../media/5-test-queries.png" alt-text="Screenshot showing how to test queries with your own account in Graph Explorer.":::

6. After you give the consent for requested permissions, select **Run query**.
7. After the Insights API runs, you'll receive an **OK – 200** message.
8.	You'll see your own trending items around you as a result in the **Response query**.
:::image type="content" source="../media/5-test-queries-result.png" alt-text="Screenshot showing how to get query result with your own account in Graph Explorer.":::

<!-- ## Try a POST request in Graph Explorer

Every time a new salesperson is added in the sales team channel on Teams, you can automate sending a message to the channel to welcome the new salesperson. To send a message to a channel on Microsoft Teams, you can use a POST request in Graph Explorer: 

1.	Select **POST** from the HTTP verb drop-down list.
2.	Search for “teams” under Sample queries.
3.	Select **POST send channel message** under the **Microsoft Teams** dropdown list.
4.	You'll see a tip popping up, letting you know that you'll need the team ID and channel ID for this query. It also recommends running **GET my joined teams** and **GET channel of a team which I am member of** to get the required team ID and channel ID.
:::image type="content" source="../media/5-post-request.png" alt-text="Screenshot showing post request in Microsoft Graph Explorer.":::

5.	After you get the team ID and channel ID, edit the query using the query editor. Make sure to replace {team-id} and {channel-id} with your IDs.
6.	Provide consent for required permissions from the **Modify permissions** tab.
7.	In the **Request body**, there's default content such as "Hello world".  This is the message you'll send to your channel on Microsoft Teams. Feel free to change the content in the request body with any sentence you prefer to send.
8.	Select **Run query** to run the request.
9.	When the request is successfully completed, you'll see a message **Created – 201**.
:::image type="content" source="../media/5-post-request-result.png" alt-text="Screenshot showing post request result in Microsoft Graph Explorer.":::

10.	To see the results, go to https://teams.microsoft.com and select **Teams** on the left-hand side menu. Find the team and channel you picked to send a message and select on the channel name. You should see the "Hello world” message sent by you under the channel **Posts**:
:::image type="content" source="../media/5-post-request-result-teams.png" alt-text="Screenshot showing post request result in Microsoft Teams."::: -->

## Consume Microsoft Graph in your apps with the help of Graph Explorer

Microsoft Graph Explorer has many other features that can help you connect your apps with Microsoft Graph.

1.	**Access token:** Used by Microsoft Graph APIs to establish the user's identity to perform authentication and authorization. From the Access token tab, you can copy your own access/authentication token.
2.	**Code snippets:** If you test any Graph query in Graph Explorer and you would like to consume the same query in your app, you can go to the Code snippets section to get the related code to add in your app. Code snippets are available in C#, JavaScript, Java, and Objective-C   for all sample queries. 
3.	**Toolkit component:** Microsoft Graph Toolkit components are framework-agnostic web components that help you access Microsoft Graph. You can use the Toolkit component tab to test these HTML components and consume them in your web apps for retrieving Microsoft 365 data through Microsoft Graph. When you run a query and a Toolkit component is available for the query, a blue dot appears on the right side of the tab.
4.	**Adaptive cards:** Adaptive cards are platform-agnostic UI components that are usually used in bots. If you wish to consume Microsoft Graph in your chatbots such as the calendar bot example given earlier, you can use the Adaptive cards tab to get the UI snippet. If you run a query and an adaptive card is available for the query, a blue dot appears on the right side of the tab. 
:::image type="content" source="../media/5-consuming-graph.png" alt-text="Screenshot showing how to consume Microsoft Graph in your apps with the help of Graph Explorer.":::

Microsoft Graph Explorer is a continuously evolving tool with many features that aim to make learning and practicing easy for people discovering Microsoft Graph features.