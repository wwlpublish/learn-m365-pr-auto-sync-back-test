The volume and complexity of organizations' data is increasing daily—email, documents, instant messages, and more. 

By default, Teams chat, channel, and files data are retained indefinitely, unless there is an attempt to delete the content via retention policies, user deletes, admin deletes and so on.

Retention policies and retention labels from Microsoft 365 help you to more effectively manage the information in your organization. Teams supports **retention policies** for chat and channel messages so that as an admin, you can decide proactively whether to retain this data, delete it, or retain it for a specific period of time and then delete it.

## Retention locations

Retention policies can be applied to the following locations:

* Exchange email

* SharePoint site

* OneDrive accounts

* Microsoft 365 Groups

* Skype for Business

* Exchange public folders

* Teams channel messages

* Teams chats

* Yammer community messages

* Yammer user messages

    :::image type="content" source="../media/retention-policy-locations.png" alt-text="Retention policy Choose locations page" lightbox="../media/retention-policy-locations.png":::

Although a retention policy can support multiple locations, you can't create a single retention policy that includes all the supported locations.

Teams requires a retention policy that's separate from other workloads. In other words, you have to create specific retention policies for Teams chats or channel messages.

* You can apply a Teams retention policy to your entire organization.

* You can configure unique policies that apply to specific users or teams in your organization.

* You can also set up separate retention policies for private chats (1:1 or 1: many chats) and channel messages.

The followings are retention policy locations associated with Teams:

* **Teams channel messages**: Message from standard channels or channel meeting messages. For Teams channel messages, you can select which teams the policy applies to.

* **Teams private channel messages**: Messages from private channel chats and private channel meetings.

* **Teams chats**: Private chats (1:1 chats) or group chats or impromptu meeting messages. For Teams chats, you can select which users the policy applies to.

* **Microsoft 365 groups**: Teams is more than just chats and channel messages. If you have teams that were created from a Microsoft 365 group, you should additionally configure a retention policy to include that Microsoft 365 group. This retention policy applies to content in the group's mailbox, site, and files.

* **Skype for Business**: If conversation history is turned on for Skype for Business and from the Skype for Business client side that history is being saved into a mailbox, that chat data isn't handled by a Teams retention policy. For this content, use a retention policy that's configured for Skype for Business.

* **SharePoint site**: Files shared in channels are stored in the SharePoint site for the team.

* **OneDrive accounts**: Files that are shared in chat are stored in the OneDrive account of the user who shared the file.

A retention policy applied to Microsoft 365 groups, SharePoint sites, or OneDrive accounts can delete files referenced in a Teams chat or channel message.

In this scenario, the file still displays in the Teams message, but they get a "File not found" error when users select the file. This behavior isn't specific to retention policies. It could also happen if a user manually deletes a file from SharePoint or OneDrive.

The retention policies applied to the user or group mailboxes in the Exchange or Microsoft 365 Groups locations don't affect Teams chat and channel messages. Even though Teams chat and channel messages are stored in Exchange, they're affected only by a retention policy applied to the Teams location.

## Retention settings

Use retention policies to keep data that's needed to follow your organization's internal policies, industry regulations, or legal needs, and to delete data that's considered a liability, that you're no longer required to keep, or has no legal or business value. Managing content commonly requires two actions:

* **Retaining content** so that it can't be permanently deleted before the end of the retention period.

    If you configure a Teams retention policy to **retain chats or channel messages**, users can still edit and delete their messages in their Teams app. Although users no longer see their pre-edited or deleted messages in Teams, data from these messages is stored in a secured location that's designed for eDiscovery searches by compliance administrators. Permanent deletion of this data doesn't happen before the end of the configured retention period, or if another retention policy is configured to retain this data, or it is subject to an eDiscovery hold.

* **Deleting content** permanently at the end of the retention period.

    When a retention policy is configured to **delete chats and channel messages**, these messages become eligible for automatic deletion. If the messages are still displayed in the Teams app, they will disappear from there and users are informed that a retention policy has deleted these messages. If the messages were previously subject to a retain action and have been edited or deleted by users, these messages will now be deleted from the secured location and no longer returned in eDiscovery searches.

With these two retention actions, you can configure retention settings for the following outcomes:

* **Retain and then delete**: Retain content for a specified period of time and then delete it. For this configuration, choose **Retain items for a specific period** and **At end of the retention period: Delete items automatically**.

* **Retain-only**: Retain content forever or for a specified period of time. For this configuration, choose **Retain items for a specific period** and **At end of the retention period: Do nothing**. Or, select **Retain items forever**.

* **Delete-only**: Delete content after a specified period of time. For this configuration, choose **Only delete items when they reach a certain age**.

    :::image type="content" source="../media/retention-policy-settings.png" alt-text="Retention policy settings page" lightbox="../media/retention-policy-settings.png":::

## The principles of retention

You can apply more than one retention policy to the same content. Each retention policy can result in a retain action and a delete action. If you set up multiple Teams retention policies with different retention settings, the principles of retention resolve any conflicts.

1. **Retention wins over deletion**: Content won't be permanently deleted when it also has retention settings to retain it.

2. **The longest retention period wins**: If content is subject to multiple retention settings that retain content for different periods of time, the content will be retained until the end of the longest retention period.

3. **Explicit wins over implicit for deletions**: If a retention policy includes a specific location, such as a specific user’s mailbox or OneDrive for Business account, that policy takes precedence over another retention policy that applies to all users’ mailboxes or OneDrive for Business accounts but doesn’t specifically include that user’s mailbox.

4. **The shortest deletion period wins**: Similarly, if content is subject to multiple policies that delete content (with no retention), it will be deleted at the end of the shortest retention period.

    :::image type="content" source="../media/principles-of-retention.png" alt-text="Diagram of the principles of retention":::

## Create a retention policy for Teams locations

To create and manage Teams retention policies, you can use the Microsoft 365 compliance center or PowerShell. To create a retention policy for Teams chats and channel messages, use the following steps:

1. From the [Microsoft 365 compliance center](https://compliance.microsoft.com/?azure-portal=true), select **Policies** > **Retention**.

2. Select **New retention policy** to start the Create retention policy wizard, and name your new retention policy.

3. For the **Choose locations to apply the policy** page, select any or all of the locations for Teams. By default, all teams and all users are selected, but you can refine this setting by selecting the **Choose** and **Exclude** options.

    * **Teams channel message**: Messages from standard channel chats and standard channel meetings.

    * **Teams chats**: Messages from private 1:1 chats, group chats, and meeting chats.

    * **Teams private channel messages**: Messages from private channel chats and private channel meetings.  

4. For **Decide if you want to retain content, delete it, or both** page of the wizard, specify the configuration options for retaining and deleting content. You can create a retention policy with the following options:

   * Retains content without deleting.

   * Retains and then deletes after a specified period of time.

   * Deletes content after a specified period of time.

5. Complete the wizard to save your settings.

## Create a retention policy using PowerShell

To create and manage retention policies via PowerShell, you need to use the Security & Compliance Center PowerShell module. The following cmdlets are available for managing retention policies:

* [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy?azure-portal=true)

For more information, see:

* [Manage retention policies for Microsoft Teams](/microsoftteams/retention-policies?azure-portal=true)

* [Principles of retention policies](https://docs.microsoft.com/microsoft-365/compliance/retention?azure-portal=true#the-principles-of-retention-or-what-takes-precedence)
