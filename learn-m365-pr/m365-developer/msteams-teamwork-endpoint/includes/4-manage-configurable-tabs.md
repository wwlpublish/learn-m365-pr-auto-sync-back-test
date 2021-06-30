> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OIwQ]

Built-in Microsoft Teams tabs for websites, Office documents, SharePoint document libraries, and other tabs can be configured using Microsoft Graph.

In this unit, you'll learn how to configure an existing built-in tab with Microsoft Graph.

Microsoft Teams supports the following built-in tabs:

- Website tabs
- Office clients (Word, Excel, PowerPoint, OneNote) tabs
- PDF tabs
- SharePoint (document libraries & pages) tabs
- Planner tabs
- Microsoft Stream tabs
- Microsoft Forms tabs
- Power BI tabs

## Create custom tabs

To create or configure a Microsoft Teams tab using Microsoft Graph APIs, you need to know the `teamsAppId` of the app, and the `entityId`, `contentUrl`, `removeUrl`, and `websiteUrl` to provide for that kind of app. Some of these properties are required while others aren't depending on the tab you're creating.

The `teamsAppId` is also the `id` property in the app's manifest.

To create or configure a tab, submit an HTTP POST to the `/tabs` endpoint on a channel with a payload that contains the settings to configure the tab:

```http
HTTP POST https://graph.microsoft.com/v1.0/teams/{groupId}/channels/{channelId}/tabs
Content-Type: application/json
{
  "displayName": "Word",
  "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}",
  "configuration": {
    "entityId": "CA2E9D19-3FE7-4E60-82DF-F73BD3B8D302",
    "contentUrl": "https://{tenant}.sharepoint.com/sites/TestTeam/Shared Documents/General/sample.docx",
    "removeUrl": null,
    "websiteUrl": null
  }
}
```

> [!NOTE]
> In the previous code listing is an example Microsoft Word tab that loads the **sample.docx** document from a SharePoint document library, the `{groupId}` and `{channelId}` should be replaced with the ID values of the team and channel the tab will be created/updated in.
>
> The `{teamsAppId}` is the ID of the application as defined in it's manifest.

The `teamsApp@odata.bind` property is what defines the Microsoft Teams app the tab is defined in.

The `configuration` object contains multiple properties, some that are required, that the tab uses to load the specified content.

Let's look at some different examples for the built-in tabs in Microsoft Teams.

## Website tabs

For website tabs, the `teamsAppId` should be set to `com.microsoft.teamspace.tab.web`. This means the `teamsApp@odata.bind` should be set to:

```http
https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/com.microsoft.teamspace.tab.web
```

Then, set the `contentUrl` and `websiteUrl` properties to the URL of the page to load in the tab. The other two properties, `entityId` and `removeUrl` should be set to `null`.

## Word, Excel, PowerPoint, and PDF tabs

For website tabs, the `teamsAppId` should be set to one of the following values depending on the file type:

|    App     |                       `teamsAppId`                       |
| ---------- | -------------------------------------------------------- |
| Word       | com.microsoft.teamspace.tab.file.staticviewer.word       |
| Excel      | com.microsoft.teamspace.tab.file.staticviewer.excel      |
| PowerPoint | com.microsoft.teamspace.tab.file.staticviewer.powerpoint |
| PDF        | com.microsoft.teamspace.tab.file.staticviewer.pdf        |

The `contentUrl` property should be set to the URL of the document in the SharePoint library in the site that supports the current team. This should be in the format `{folder-webUrl}/{filename}`

The `entityId` property should be set to the document's ID in the SharePoint library. This is displayed in the URL parameter `sourcedoc` when viewing a file in a SharePoint library.

The other two properties, `websiteUrl` and `removeUrl` should be set to `null`.

## SharePoint document library, list, and page tabs

When creating a tab to show content within a SharePoint site, such as a document library, list, or page, the configuration options are simpler than the other tabs covered.

First, the `teamsAppId` should be set to one of the following values depending on the tab:

| SharePoint Type  |                 `teamsAppId`                 |
| ---------------- | -------------------------------------------- |
| Document library | com.microsoft.teamspace.tab.files.sharepoint |
| List             | 2a527703-1f6f-4559-a332-d8a7d288cd88         |
| Page             | 2a527703-1f6f-4559-a332-d8a7d288cd88         |

The list & page types don't support configuration, so you can omit the `configuration` element from the request.

However, for a document library, the `entityId` should be set to an empty string. The `contentUrl` should be set to the URL of the root folder of the document library, while the `websiteUrl` and `removeUrl` properties should be set to `null`.

## All other tabs

The remaining built-in tabs don't support configuration so you only need to set the `teamsAppId` value when setting them:

|       App        |              `teamsAppId`               |
| ---------------- | --------------------------------------- |
| Microsoft Stream | com.microsoftstream.embed.skypeteamstab |
| Microsoft Forms  | 81fef3a6-72aa-4648-a763-de824aeafb7d    |
| OneNote          | 0d820ecd-def2-4297-adad-78056cde7c78    |
| Planner          | com.microsoft.teamspace.tab.planner     |
| Power BI         | com.microsoft.teamspace.tab.powerbi     |
