> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OIzv]

In this exercise, you’ll learn how to create an Office 365 Connector and add it to Microsoft Teams.

The first step will be to create a new Microsoft Teams app that contains a web service and the necessary details to associate the Office 365 Connector to connect it to Microsoft Teams. Then you'll register a new Office 365 Connector with the **Connectors Developer Dashboard**.

## Create Microsoft Teams app

Open your command prompt, navigate to a directory where you want to save your work, create a new folder **learn-msteams-connectors**, and change directory into that folder.

Run the Yeoman Generator for Microsoft Teams by running the following command:

```console
yo teams
```

Yeoman will launch and ask you a series of questions. Answer the questions with the following values:

- **What is your solution name?**: MyFirstTeamsConnector
- **Where do you want to place the files?**: Use the current folder
- **Title of your Microsoft Teams App project?**: My First Teams Connector
- **Your (company) name? (max 32 characters)**: Contoso
- **Which manifest version would you like to use?**: 1.11
- **Quick scaffolding**: Yes
- **What features do you want to add to your project?**: A Connector
- **The URL where you will host this solution?**: (Accept the default option)
- **Would you like show a loading indicator when your app/tab loads?**: No
- **What type of Connector would you like to include?**: A new Connector hosted in this solution
- **What is the Id of your Connector (found in the Connector Developer Portal)?**:  (Accept the default option)
- **What is the name of your Connector?** My First Teams Connector

> [!NOTE]
> Most of the answers to these questions can be changed after creating the project. For example, the URL where the project will be hosted isn't important at the time of creating or testing the project.

After answering the generator's questions, the generator will create the scaffolding for the project and then execute `npm install` that downloads all the dependencies required by the project.

### Examine and update the app manifest file

After creating the project, you'll need to make a few edits to the default app manifest file. Locate and open the file **./src/manifest/manifest.json**.

Within this file, locate the `connectors` array. Notice a single Connector is listed:

```json
"connectors": [
  {
    "connectorId": "{{CONNECTOR_ID}}",
    "configurationUrl": "https://{{PUBLIC_HOSTNAME}}/myFirstTeamsConnector/config.html",
    "scopes": [
      "team"
    ]
  }
]
```

> [!IMPORTANT]
> Notice the value of the Connector ID will be replaced by the build process. This ID can be found in the `./.env` file that's used for development.

A default manifest has a few empty array properties that must be removed to add the Connector to a team. Locate the following properties and delete them from the **manifest.json** file:

```json
"configurableTabs": []
"staticTabs": []
"bots": []
"composeExtensions": []
```

Finally, let's explore the code in the default project to see how it works. The default project contains two elements that support the Connector:

1. The web service that Microsoft Teams & the Office 365 Connector infrastructure will call which implements the Connector logic.
1. A configuration page that's displayed when the Connector is added to a team.

### Examine the configuration page

The configuration page is an HTML page that contains a React control. Locate and open the React control file **./src/client/myFirstTeamsConnector/MyFirstTeamsConnectorConfig.tsx**.

You need to make one edit to this file before building the project. Within the `useEffect()` React hooks method, locate the following code:

```typescript
setColor(availableColors.find(c => c.code === context.entityId));
```

The `find()` method needs to be replaced with a `filter()` method. Update this to the following:

```typescript
setColor(availableColors.filter(c => c.code === context.entityId)[0]);
```

The important part of this component to take note of is in the call to the `microsoftTeams.settings.registerOnSaveHandler()` handler that is called when the user selects the **Save**  button on the config page. Selecting **Save** will save the configuration of the Connector in Microsoft Teams and notify the Connector's web service that it has been added to a team.

The code does the following things:

- Update the settings for the Connector in Microsoft Teams
- Submit an HTTP POST to the Connector's `/api/connector/connect` endpoint with a payload that contains necessary information the Connector web service needs to store

Notice before the HTTP POST is executed, the code calls the `getSettings()` method to retrieve the settings from Microsoft Teams:

```typescript
microsoftTeams.settings.getSettings((setting: any) => { ... });
```

This method passes in a settings object that contains a few important properties:

- **webhookUrl**: this is the endpoint, the incoming webhook, the Connector will submit to
- **userObjectId**: the ID of the user who is registering the Connector
- **appType**: this is the value `team` when associating the Connector with a team

When the HTTP POST request succeeds, the `notifySuccess()` method is called on the `SaveEvent` passed into this `registerOnSaveHandler()` handler; otherwise the `notifyFailure()` method is called.

### Examine the web service

The Connector is implemented as a web service that is hosted within the Microsoft Teams project. Locate and open the file **./src/server/myFirstTeamsConnector/MyFirstTeamsConnector.ts**.

The web service exposes two endpoints, both represented by methods with the endpoint's respective names. The endpoints are:

- **/connect**: This is called, as we covered in the previous section, when the **Save** button is selected on the config page. The default code in the handler, `Connect()`, simply saves the Connector registration in a local JSON file.

    > [!NOTE]
    > The sample web service in the default project uses a JSON file to store the registration. It does not contain any logic to update an existing Connector when it's changed, or remove a Connector. In a real world Connector, you'll likely implement a system that saves this registration to a persistent data store that handles the scenarios of updating and removing a Connector from a team.

- **/ping**: This endpoint can be called by anyone and is used to test the Connector. When called, it will create a card and send it to all the registered Connectors.

### Start the project to get the web service endpoint

Before registering the Connector in the next step, you need to obtain the URL where your Connector's web service will be hosted.

> [!NOTE]
> Microsoft Teams requires all content displayed within a tab to be loaded from an HTTPS request. In development, this can be done by using the tool [ngrok](https://www.ngrok.com) that creates a secure rotatable URL to your local HTTP web server. Ngrok is included as a dependency within the project, so there's nothing to set up or configure.

Because we're using ngrok to test our project, and because every time you start ngrok it creates a new dynamic subdomain, we need to start the project. From the command line, navigate to the root folder for the project and execute the following command:

```console
gulp ngrok-serve
```

Locate and copy the dynamic URL created by ngrok from the command prompt as it was displayed when you started the `gulp ngrok-serve` task:

![Screenshot of the ngrok URL](../media/07-test-setup-app-08.png)

Copy this URL as you'll need it in the next step.

> [!IMPORTANT]
> Make sure to leave the web server running and don't terminate the process. If the web server stops for any reason, you'll have to update the Connector's registration details with the new endpoint created by ngrok.

## Register an Office 365 Connector

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OARc]

Open a browser and navigate to the **Connectors Developer Dashboard**: https://aka.ms/ConnectorsDashboard

![Screenshot of the Connectors Developer Dashboard](../media/07-connector-dashboard-01.png)

Select **New Connector**.

On the **Register Connector** page, complete the required fields in the form with anything you like and accept any default options presented, with the following exceptions:

- **Connector name**: My First Teams Connector
- **Configuration page for your Connector**: `https://REPLACE.ngrok.io/MyFirstTeamsConnector/config.html`
- **Valid domains**: `REPLACE.ngrok.io`

> [!IMPORTANT]
> Make sure to use the ngrok subdomain you copied from the previous step.

Select the **I accept the terms and conditions...** checkbox and select **Save** to register the Connector.

After successfully registering your Connector, the **Connectors Developer Dashboard** page will display some additional sections. While there's a button to **Download Manifest** for a custom Microsoft Teams app, we'll use the manifest created by the Yeoman Generator for Microsoft Teams.

You'll need the ID of your new Connector later in the exercise. This ID, a GUID, can be found in the URL of the updated page. Copy this ID for later use.

![Screenshot of the created Connector](../media/07-connector-dashboard-02.png)

### Update the project with the Connector ID

Within your project, locate and open the **./.env** file. Set the `CONNECTOR_ID` to the ID of the Connector you just created.

### Update the Microsoft Teams app package

When you started the project in a previous step, the build process generated the Microsoft Teams app package using the ngrok URL. The process also set the Connector's ID in the **manifest.json** file with the value in the **./.env** file. However, at that time we didn't know the Connector's ID.

To address this, you can start & stop the **ngrok-serve** task, but that'll generate a new ngrok subdomain which would require you to update the Connector's registration details. Changes to an existing Connector registration can take some time to propagate which can delay testing the app.

The other option is to unzip the generated package found in the **./package** folder in your project update the `connectors[0].connectorId` property, and create a new app package ZIP with the updated **manifest.json** file and the two images.

Feel free to chose either of these options.

## Test the Office 365 Connector in Microsoft Teams

At this point, our Microsoft Teams app and Office 365 Connector is set up and working. Let's load the Connector in Microsoft Teams. In the browser, navigate to **https://teams.microsoft.com** and sign in with the credentials of a Work and School account.

Once you're signed in, the first step is to install the Microsoft Teams app.

Select a team, select the action menu on the team and select **Manage team**:

![Screenshot of the team's action menu](../media/07-test-setup-app-01.png)

Select the **Apps** tab and then **Upload a custom app** button:

![Screenshot of the Manage team page](../media/07-test-setup-app-02.png)

Select the Microsoft Teams app package, the **MyFirstTeamsConnector.zip** file in the **./package** folder of your project.

> [!NOTE]
> If the **./package** folder is not present, this means you are affected by a bug in the yoteams-deploy package. To resolve the issue:
> - Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console.
> - Install the preview version of the **yoteams-deploy** package using the command `npm install yoteams-deploy@preview`
> - Restart the server process: `gulp ngrok-serve`

After uploading the app, select the **Add** button and enter the team...

![Screenshot of the app details](../media/07-test-setup-app-04.png)

![Screenshot of the Add to a team dialog](../media/07-test-setup-app-05.png)

This will display the configuration page from our project:

![Screenshot of the Connector configuration page](../media/07-test-setup-app-07.png)

Select a color and then select the **Save** button.

This will trigger the configuration page to call the web service's `/connect` endpoint to save the Connector.

With the Connector saved, the next step is to see it post to a channel. Do this by submitting an HTTPS request to the web service's `/ping` endpoint.

Using the free tool [Postman](https://www.postman.com/), create a new request to the point endpoint:

- set the `Content-Type` header to `application/json` on the **Headers** tab:

    ![Screenshot of the Headers tab in Postman](../media/07-test-setup-app-09.png)

Select the **Send** button in Postman. When you go back to the channel, you'll see a card displayed as a message in the team:

![Screenshot of the rendered card in the team](../media/07-test-setup-app-11.png)

## Summary

In this unit, you learned how to create an Office 365 Connector and add it to Microsoft Teams.
