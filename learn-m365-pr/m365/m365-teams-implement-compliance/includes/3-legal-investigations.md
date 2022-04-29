Large corporations are sometimes required to submit all electronically stored information (ESI) as part of legal proceedings. The process by which you identify and locate information that pertains to a case is called eDiscovery. eDiscovery investigations in Microsoft 365 can include content generated in Microsoft Teams.

Suppose that Contoso has been taken to court by a disgruntled employee who claims harassment. You suspect that the content of Teams chats and meeting recordings can exonerate the company. You want to find out how to locate this data and place a hold on it to prevent any tampering.
Here, you will learn how to execute eDiscovery searches and holds on Teams content.

## eDiscovery in Teams

The discovery of ESI in Teams is accomplished in the following ways:

- Teams journals chat messages to each user's mailboxes.
- Teams journals standard channel messages to the group mailbox representing the team.
- Files uploaded in standard channels are covered for eDiscovery by SharePoint Online and OneDrive for Business.

Not all Teams content is eDiscoverable. The following table shows the content types that can be located through eDiscovery.

| Content type | eDiscoverable | Notes |
| --- | --- | --- |
| Teams chat messages | Yes |
| Audio recordings | No | |
| Private channel messages | Yes | |
| Emojis, GIFs, stickers | Yes | |
| Code snippets | No | |
| Chat links | Yes | |
| Reactions (likes, hearts, and so on) | No | |
| Edited messages | Yes | If the user is on hold, previous versions of edited messages are preserved. |
| Inline images | Yes | |
| Tables | Yes  | |
| Subject | Yes | |
| Quotes | Yes | Quoted content is searchable. However, search results don't indicate that the content was quoted. |
| Name of channel | No | |

## Audit log and content search

 Audit logs record specific activities in Teams, including:

- Team creation
- Team deletion
- Added channel
- Changed setting

These logs can help during an investigation and can be located during eDiscovery. To be able to look at audit data, you must turn on auditing in the Microsoft 365 Defender portal. For help with this action, read Turn audit log search on or off in the Learn more section below.

### Retrieve Teams data from the audit log

To locate information from audit logs during eDiscovery, follow these steps:

1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com).
1. Under **Search**, select **Audit log search**.
1. Use **Search** to filter by the activities, dates, and users you want to audit.
1. Export your results to Excel for further analysis.

### Content Search

Content Search is an eDiscovery tool in Microsoft 365 that you can use to locate information, relevant to a legal action, in:

- Microsoft Teams
- Exchange Online mailboxes
- Exchange Online public folders
- SharePoint Online sites
- OneDrive for Business
- Skype for Business conversations
- Microsoft 365 groups
- Yammer groups

Using this tool, you can run single queries that locate information in multiple Microsoft 365 systems in one action. For example, you could search for "New Factory specifications" and retrieve results from:

- A Teams channel conversation
- A file uploaded to a SharePoint site
- A user's OneDrive for Business account
- A conversation in Yammer

You have a large degree of control over the queries you use, which enables you to narrow the range of results you discover and to drill down into only those items that relate to the legal action you are investigating.

## Place a Microsoft Teams user or team on legal hold

If there is a chance of litigation, you must preserve electronically stored information (ESI) and protect it from tampering. This includes Teams messages and other items that are relevant to the case.

To put a user or a team on legal hold:

1. To create a case, in the Microsoft 365 Defender portal go to **eDiscovery** and select **+ Create a case**. When the case is created, open it.

   :::image type="content" source="../media/3-legal-hold-1.png" alt-text="Create a case":::

1. To create a hold, select the **Holds** tab, and then select **+ Create** to create a hold.

    :::image type="content" source="../media/3-legal-hold-2.png" alt-text="Holds section":::

1. In the **Name** textbox, type a descriptive name for your hold. If you need to provide extra information, use the **Description** textbox.

    :::image type="content" source="../media/3-legal-hold-3.png" alt-text="Name your hold":::

1. Choose a **Location** for the hold.

    :::image type="content" source="../media/3-legal-hold-4.png" alt-text="Choose location":::

1. Create the query to target specific content.

> [!NOTE]
> If a user is on hold, all their messages are also on hold, including whatever they sent in a one-on-one, one-to-many, or group chats, or channel conversations, including private channels.

## Learn more

- [eDiscovery of private channels](/microsoftteams/ediscovery-investigation#ediscovery-of-private-channels)
- [Use Content Search in Microsoft Teams](/microsoftteams/content-search))
- [Turn audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off)
- [Place a Microsoft Teams user or team on legal hold](/microsoftteams/legal-hold)
