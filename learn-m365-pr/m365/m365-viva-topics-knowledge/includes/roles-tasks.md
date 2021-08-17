Once the Topic Center is set up and configured, Global, Tenant, or Knowledge administrators can start assigning users or groups to roles.

Knowledge managers must be licensed for Viva Topics. If not, admins will need to apply the Viva Topics license to their Knowledge managers. Allow up to an hour for license activations to complete. Then admins can designate who should have the Knowledge manager role in the Microsoft 365 admin center.  

|Knowledge administrator (Tenant administrator)|Knowledge manager|Topic contributor (SME)|
|-|-|-|
|- Sets up Topic experiences <br>- Ensures security and compliance standards are enforced <br>- Understands licensing agreement|- Owns quality of Topics and curation <br>- Performs topic management tasks such as create, edit, delete, and reject topics|- Contributes to topics, curating pinned people and resources.|

The following table outlines the tasks the knowledge manager can perform by using the **Manage Topics** feature.

|Task|Description|
|-|-|
|Manage Knowledge|The Knowledge manager maintains the quality of the knowledge network by confirming/rejecting AI-indexed topics, publishing topics mature enough to be viewed by a broader audience and performing other triage tasks.|
|Pinpoint topics|Powerful filtering capabilities empower Knowledge managers to locate topics that meet specific criteria.|
|Gain insights|The Knowledge manager can track ongoing topic activity and the health of the knowledge network.|

## Manage topics in the Topics center

In the Topic Center, a Knowledge manager can review topics that have been identified in the SharePoint source locations you specified and can either confirm or reject them. A Knowledge manager can also create and publish new topic pages if they are not found in topic discovery or edit existing ones if they need to be updated.

>[!NOTE]
> To access the Topics center, you need both a Viva Topics license and to be assigned the **Who can manage topics** permission. A knowledge admin can grant you this permission from the Viva Topics permissions settings.

Knowledge managers can access the management tools on the **Manage Topics** tab in the Topic Center view. (Only users who have been assigned the Knowledge manager role will have access to this view.)

Admins can control the quality threshold when topics start to become broadly visible to the org. When a topic becomes discoverable, topic highlights will start appearing wherever the topic name appears in SharePoint and the topic will also appear in Search results.

:::image type="content" source="../media/viva-suggested.png" alt-text="A screenshot shows Suggested topics view in the Manage topics section of the Topics Center.":::

## Sort metadata columns

You'll see helpful metadata columns for sorting. These sorting options enable Knowledge managers to focus on the topics in the knowledge network that are most critical to triage. For example, the Knowledge manager might sort this list by impressions. Impressions reflect how often users in the organization mention a given topic and how often these mentions are seen by other users. Knowledge managers would want to spend their time reviewing topics with the highest usage first. Knowledge managers can review the topics most recently discovered by the AI by sorting this list with the Discovered date column.  

## Review quality score

Each topic that appears in your Manage topics page has a quality score assigned to it. The quality score ranges from 1 to 100. A newly discovered topic will have a quality score of 0 until two or more users have viewed it. Each user's quality score is determined by several factors, amount of content displayed for the specific user, controlled by the user's permissions as each topic page has security trimming in place for AI-generated content. The quality score on the Manage topics tab is an average of each user's individual score.

The quality score can help give insights on which topics may need to be manually augmented. For example, a topic with a lower quality score may be the result of some users not having SharePoint permissions to pertinent files or sites that AI has included in the topic. A Topic contributor could then edit the topic to include the information (when appropriate), to be viewable to all users who can view the topic.

## Review impressions

The impressions column displays the number of times a topic has been shown to users. This includes views through topic cards in Search, topic highlights, and the Topic Center. It does not reflect the click-through on these topics, but just that the topic has been displayed. The impressions column will show for topics in the suggested, confirmed, published, and removed tabs in the Manage topics page.

Knowledge managers help to guide discovered topics through various topic lifecycle stages:

:::image type="content" source="../media/viva-flow.png" alt-text="A workflow diagram that shows four phases of the topic lifecycle: Suggested, Confirmed, Published, and Rejected.":::

- **Suggested**: A topic has been identified by AI and has enough supporting resources, connections, and properties to be included in this list.
- **Confirmed**: A topic that has been suggested by AI is validated. Validation is done by confirmation from a Knowledge manager. If there are net two positive votes (upvotes) from users, the topic is automatically confirmed. A net two negative votes (downvotes) from users means that the topic is rejected.
- **Published**: A confirmed topic has been curated; manual edits have been made to improve its quality.
- **Rejected**: A topic is rejected by a Knowledge manager and will no longer be visible to viewers. The topic can be in any stage when it is removed (suggested, confirmed, or published). When a published topic is removed, the page with the curated details will need to be deleted manually from the Pages Library of Topic Center.

On the **Manage Topics** page, each Knowledge manager will only be able to see the topics related to files and pages that they have access to, sorted into **Suggested**, **Confirmed**, **Removed**, and **Published** columns. However, the topic counts show the total counts in the organization regardless of permissions.
