> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OIwP]

In this exercise, you'll add a few built-in tabs to a channel in a Microsoft Teams team with the Microsoft Graph's teamwork endpoint.

> [!IMPORTANT]
> This exercise assumes you have created the Microsoft Teams app project from the previous exercise in this module. You'll update the project to add buttons ot the tab that add new pre-configured tabs to the current channel.

## Add the TeamsTab.ReadWriteForTeam permission to the Azure AD application

The Microsoft Graph teamwork endpoint supports modifying the tabs in an existing channel. The user that executes the code that calls the tabs endpoint must consent to one of the **TeamsTab.\*** permissions. In this exercise, you'll create tabs using this endpoint, so you need to consent to the permission that enables reading and writing tabs: **TeamsTab.ReadWriteForTeam**.

Let's start by adding and pre-consenting this permission for our existing Azure AD application.

Open a browser and navigate to the [Azure Active Directory admin center (https://aad.portal.azure.com)](https://aad.portal.azure.com). Sign in using a **Work or School Account** that has global administrator rights to the tenancy.

Select **Azure Active Directory** in the left-hand navigation.

Select **Manage > App registrations** in the left-hand navigation.

On the **App registrations** page, select the app **My Teams SSO App**.

In the left-hand navigation, select **Manage > API permissions**.

Select **Add a permission**, then select **Microsoft Graph > Delegated permissions**.

Search for, and select the permission **TeamsTab.ReadWriteForTeam**, then select the **Add permissions** button:

![Screenshot adding a new permission to the app](../media/05-azure-ad-add-api-permissions.png)

To simplify the testing process, select **Grant admin consent for Contoso** to consent this new permission for all users in your tenant.

### Update the list of permissions requested by the tab

With the permission added to the Azure AD app, you now need to update the list of permissions the server-side API will include in the request for the access token.

Locate and open the **./.env**. At the end of the file, locate the environment variable that contains the space-delimited permissions and add the following permission you just added so it now looks like the following:

```txt
TAB_APP_SCOPES=https://graph.microsoft.com/User.Read https://graph.microsoft.com/Team.ReadBasic.All https://graph.microsoft.com/TeamsTab.ReadWriteForTeam email openid profile offline_access
```

## Add documents to the channel

Before adding the tabs that will load the Word and Excel files, you need a Word document and Excel workbook first!

In the browser, navigate back the channel where you installed the team in the previous exercise. Select the **Files** tab and then use the **New** button to add a new Word and Excel file to the library:

![Screenshot adding Office files to the library](../media/05-add-office-files.png)

Keep track of the names of these files. For the purposes of this exercise, we'll assume they're called **document.docx** and **workbook.xlsx**.

### Get document IDs and URLs

When creating a new tab as one of the Office built-in tabs, you'll need to know two important things about each of the files you want to display in the tabs:

- document ID
- document URL

Both of these values can be retrieved via the Microsoft Graph API, but you can also get them from the URL. Select one of the files, such as **document.docx**, in the **Files** tab and select **Open in SharePoint**.

![Screenshot opening the Word document in SharePoint](../media/05-open-office-files.png)

This file is located in the **Documents** library that's named **Shared Documents** inside SharePoint. Its also located in the **General** subfolder within the library that matches the name of the Microsoft Teams channel you were just in. Look at the URL of the **General** folder in the **Documents library**... it should look similar to the following:

```text
https://m365x285179.sharepoint.com/sites/TestTeam/Shared%20Documents/Forms/AllItems.aspx
    ?RootFolder=%2Fsites%2FTestTeam%2FShared%20Documents%2FGeneral
    &FolderCTID=0x012000A794675CEBE1A542BFB9E3500689BAEE
```

> [!NOTE]
> Line breaks have been added for readability.

From this, you get the URL of the document library: `https://m365x285179.sharepoint.com/sites/TestTeam/Shared%20Documents`. You can also see the folder is **General**, so the URL to this folder is: `https://m365x285179.sharepoint.com/sites/TestTeam/Shared%20Documents/General`.

Now, select the Word document to load it in the Microsoft Office Word web client. If you look at the URL in the browser's address bar, it should look similar to the following:

```text
https://m365x285179.sharepoint.com/:w:/r/sites/TestTeam/_layouts/15/Doc.aspx
    ?sourcedoc=%7B5E12B0DE-AD44-43D3-BD00-53C9BDD5609D%7D
    &file=document.docx
    &action=default
    &mobileredirect=true
```

> [!NOTE]
> Line breaks have been added for readability.

From this, you can get the ID of the document from the `sourcedoc` URL parameter. In this case that's `5E12B0DE-AD44-43D3-BD00-53C9BDD5609D` after you remove the escaped `{` and `}` characters (*respectively: `%7B` and `%7D`*).

Now you have what you need to create the Word tab:

- **document ID:** `5E12B0DE-AD44-43D3-BD00-53C9BDD5609D`
- **document URL:** `https://m365x285179.sharepoint.com/sites/TestTeam/Shared%20Documents/General/document.docx`

Repeat this process to get the same values for the Excel file.

## Update the tab to add a Word tab

Now, let's update the project's existing tab. This button will create a new tab that will load a Microsoft Word document from the team in the tab.

In Visual Studio Code, locate and open the **./src/client/msGraphTeamworkTab/MsGraphTeamworkTab.tsx** file.

At the top of the file, add the following code immediately after the existing `import` statements to import the icons for Word and Excel:

```typescript
import { WordIcon, ExcelIcon } from "@fluentui/react-icons-northstar";
```

Next, let's add two event handlers with the `useCallback()` hooks. These will get executed when the user selects a button that you'll add to the user interface of the tab in a moment. Each one submits a request to Microsoft Graph's **tab** endpoint to create a new tab.

Notice each one uses a specific `teamsApp@odata.bind` string for each tab type.

Also notice how each one's `configuration` property sets the file's document ID to the `entityId` property of the tab, and the `contentUrl` property is set to the document's fully qualified URL.

Next, add the following `useCallback()` hook that will be used to submit a request to Microsoft Graph for all the teams the current user has joined:

Locate the `return` statement and add the following code immediately before it:

```typescript
const handleWordOnClick = useCallback(async() => {
  if (!msGraphOboToken || !context) { return; }

  const endpoint = `https://graph.microsoft.com/v1.0/teams/${context.groupId}/channels/${context.channelId}/tabs`;
  const requestObject = {
    method: "POST",
    headers: {
      authorization: `bearer ${msGraphOboToken}`,
      "content-type": "application/json"
    },
    body: JSON.stringify({
      displayName: "Word",
      "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/com.microsoft.teamspace.tab.file.staticviewer.word",
      configuration: {
        entityId: "{{WORD_DOCUMENT_ID}}",
        contentUrl: "{{WORD_DOCUMENT_URL}}",
        removeUrl: null,
        websiteUrl: null
      }
    })
  };

  await fetch(endpoint, requestObject);
}, [context, msGraphOboToken]);

const handleExcelOnClick = useCallback(async() => {
  if (!msGraphOboToken || !context) { return; }

  const endpoint = `https://graph.microsoft.com/v1.0/teams/${context.groupId}/channels/${context.channelId}/tabs`;
  const requestObject = {
    method: "POST",
    headers: {
      authorization: `bearer ${msGraphOboToken}`,
      "content-type": "application/json"
    },
    body: JSON.stringify({
      displayName: "Excel",
      "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/com.microsoft.teamspace.tab.file.staticviewer.excel",
      configuration: {
        entityId: "{{EXCEL_DOCUMENT_ID}}",
        contentUrl: "{{EXCEL_DOCUMENT_URL}}",
        removeUrl: null,
        websiteUrl: null
      }
    })
  };

  await fetch(endpoint, requestObject);
}, [context, msGraphOboToken]);
```

Now add the buttons to the user interface that will execute these methods. Locate the following line in the `return` statement:

```tsx
{joinedTeams && <div><h3>You belong to the following teams:</h3><List items={joinedTeams} /></div>}
```

Add the following lines to add two buttons after the list of teams the current user has joined:

```tsx
<Button icon={<WordIcon />} content="Add Word tab" onClick={handleWordOnClick} />
<Button icon={<ExcelIcon />} content="Add Excel tab" onClick={handleExcelOnClick} />
```

Finally, save all your edits to the **MsGraphTeamworkTab.tsx** file.

## Build and test the application

Now let's test the new functionality added in this exercise.

> [!IMPORTANT]
> If the **ngrok-serve** stopped for any reason, remember when you start/restart the **gulp ngrok-serve** task, the dynamic ngrok URL will change.
>
> You'll need to update all the locations where you set the URL in your project as well as in the Azure AD app registration as previously explained.
>
> In addition, you'll need to reinstall your app package because the Microsoft Teams app manifest contains the URL. To do this, you'll first need to increment the `version` property in the app's **./manifest/manifest.json** file. This value is dynamically set using the `version` property from the **./package.json** file. When you repeat the installation process of the app, it will update the existing installation.

Once the app starts, go back to the browser and navigate back to your tab that you previously installed. You'll now see the two buttons appear below the list of joined teams:

![Screenshot of the two Office tab buttons](../media/05-test-01.png)

Select each of the two tabs and wait a few seconds. After a few seconds, you should see two new tabs appear in the channel:

![Screenshot of the two new Office tabs](../media/05-test-02.png)

Select each of the tabs to see them load the specified Office file in each one respectively.
