In this exercise, you'll create a new Microsoft Teams personal tab by using the Microsoft Teams Yeoman generator, Visual Studio Code, and App Studio.

## Prerequisites

Developing Microsoft Teams apps requires an Office 365 tenant, Microsoft Teams configured for development, and the necessary tools installed on your workstation. 

For the Office 365 tenant, follow the instructions in [Microsoft Teams: Prepare your Office 365 tenant](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-tenant) to obtain a developer tenant if you don't currently have an Office 365 account. Make sure you've also enabled Microsoft Teams for your organization.

Microsoft Teams must be configured to enable custom apps and allow custom apps to be uploaded to your tenant to build custom apps for Microsoft Teams. Follow the instructions in "Prepare your Office 365 tenant" mentioned previously.

You'll use Node.js to create custom Microsoft Teams tabs in this module. The exercises in this module assume you have the following tools installed on your developer workstation.

> [!IMPORTANT]
> In most cases, installing the latest version of the following tools is the best option. The versions listed here were used when this module was published and last tested.

- [Node.js](https://nodejs.org/) - v10.\* (or higher)
- NPM (installed with Node.js) - v6.\* (or higher)
- [Gulp](https://gulpjs.com/) - v4.\* (or higher)
- [Yeoman](https://yeoman.io/) - v3.\* (or higher)
- [Yeoman generator for Microsoft Teams](https://github.com/OfficeDev/generator-teams) - v2.\* (or higher)
- [Visual Studio Code](https://code.visualstudio.com)

*You must have the minimum versions of these prerequisites installed on your workstation.

## Create Microsoft Teams app

Open your command prompt, and go to a directory where you want to save your work. Create a new folder named learn-msteams-tabs, and change the directory into that folder.

Run the Yeoman generator for Microsoft Teams by running the following command:

```shell
yo teams
```

![Screenshot of the Yeoman generator for Microsoft Teams](../media/03-yo-teams-01.png)

Yeoman starts and asks you a series of questions. Answer the questions with the following values:

- **What is your solution name?**: Learn MSTeams Tabs
- **Where do you want to place the files?**: Use the current folder
- **Title of your Microsoft Teams App project?**: Learn MSTeams Tabs
- **Your (company) name? (max 32 characters)**: Contoso
- **Which manifest version would you like to use?**: 1.5
- **Enter your Microsoft Partner Id, if you have one?**: (Leave blank to skip)
- **What features do you want to add to your project?**: A tab
- **The URL where you will host this solution?**: https://learnmsteamstabs.azurewebsites.net
- **Would you like to include Test framework and initial tests?**: No
- **Would you like to use Azure Applications Insights for telemetry?**: No
- **Default Tab name? (max 16 characters)**: LearnPersonalTab
- **Do you want to create a configurable or static tab?**: Static

> [!NOTE]
> Most of the answers to these questions can be changed after you create the project. For example, the URL where the project will be hosted isn't important at the time of creating or testing the project.

After you answer the generator's questions, the generator creates the scaffolding for the project. The generator then runs `npm install` that downloads all the dependencies required by the project.

## Test the personal tab

Before you customize the tab, let's test the tab to see the initial developer experience for testing.

From the command line, go to the root folder for the project and run the following command:

```shell
gulp ngrok-serve
```

This gulp task runs many other tasks all displayed within the command-line console. The **ngrok-serve** task builds your project and starts a local web server (http://localhost:3007). It then starts ngrok with a random subdomain that creates a secure URL to your local web server.

> [!NOTE]
> Microsoft Teams requires all content displayed within a tab to be loaded from an HTTPS request. In development, this can be done by using the tool [ngrok](https://www.ngrok.com) that creates a secure rotatable URL to your local HTTP web server. Ngrok is included as a dependency within the project, so there's nothing to set up or configure.

![Screenshot of gulp ngrok-serve](../media/03-yo-teams-02.png)

Open a browser, and go to the ngrok URL displayed in the console.

![Screenshot of the local web app hosting the Teams tab project](../media/03-yo-teams-03.png)

Update the URL in the browser to load the tab created by the scaffolding process. Here you can see the page can determine that it isn't running within the Microsoft Teams client.

![Screenshot of the local web app hosting the Teams tab project](../media/03-yo-teams-04.png)

Now let's load the tab in Microsoft Teams. In the browser, go to [Microsoft Teams](https://teams.microsoft.com). Sign in with the credentials of a Work and School account.

> [!NOTE]
> Microsoft Teams is available for use as a web client, a desktop client, and a mobile client. In this module, we use the web client, but any of the clients can be used.

On the app bar navigation menu, select the **Mode added apps** button. Then select **Browse all apps** > **Upload for me or my teams**.

![Screenshot of More added apps dialog box in Microsoft Teams](../media/03-yo-teams-05.png)

In the file dialog box that appears, select the Microsoft Teams package in your project. This app package is a zip file in the project's ./package folder.

After the package is uploaded, Microsoft Teams displays a summary of the app. Here you can see some "todo" items to address. You'll update the "todo" items later in the exercise.

![Screenshot of Microsoft Teams app](../media/03-yo-teams-06.png)

Select the **Add** button to install the app, which adds a new personal tab to your **More added apps** dialog box.

![Screenshot of the installed Microsoft Teams app in the More added apps dialog box](../media/03-yo-teams-07.png)

Select the app to go to the new tab.

![Screenshot of the installed Microsoft Teams app personal tab](../media/03-yo-teams-08.png)

Notice that when the content page is loaded in a tab within the Microsoft teams client, it displays the `entityId` property of the tab, not the message "This isn't hosted in Microsoft Teams" as you saw when you viewed the content page in the browser. The tab can detect if it's loaded within the Microsoft Teams client by using the Microsoft Teams JavaScript SDK.

The next step is to make some changes to the project.

Uninstall the app by right-clicking the app in the **More added apps** dialog box and select **Uninstall**. Then select **Uninstall** in the confirmation dialog box that appears.

![Screenshot uninstalling the Microsoft Teams app](../media/03-yo-teams-09.png)

![Screenshot of the Uninstall dialog box for the Microsoft Teams app](../media/03-yo-teams-10.png)

Next, stop the local web server by selecting <kbd>Ctrl</kbd>+<kbd>C</kbd> in the console to stop the running process.

## Update the project to use the Stardust UI library

Microsoft Teams recommends that your custom apps use React and the themable React component library [Stardust UI React](https://stardust-ui.github.io/react/). To use Stardust in the Microsoft Teams app, we need to make some changes to the project.

> [!IMPORTANT]
> At the time of publication of this module, there are plans to update the Yeoman generator for Microsoft Teams to include Stardust in the default project. At the time of publication of this module, the default project uses the older Microsoft Teams control library that Stardust is replacing.
>
> The steps in this section might not be necessary because the Yeoman generator for Microsoft Teams might have been updated. Review each of the instructions in this section and compare the results with your project to determine if they're necessary.

The first step is to uninstall the existing control library and install the Stardust library. Run the following two commands in the command line from the root folder of the project:

```shell
npm uninstall msteams-ui-components-react
npm install @stardust-ui/react
```

Locate and open the file that contains the React component used in the project: ./src/app/scripts/learnPersonalTab/LearnPersonalTab.tsx.

Update the `import` statements in this file to replace the component library used. Find the following `import` statement that imports the legacy Microsoft Teams UI Components - React library:

```ts
import {
  PrimaryButton,
  TeamsThemeContext,
  Panel,
  PanelBody,
  PanelHeader,
  PanelFooter,
  Surface,
  getContext
} from "msteams-ui-components-react";
```

Replace the previous statement with the following import statement:

```ts
import { 
  Flex, Provider, themes, ThemePrepared,
  Alert, Header,
  Button, Icon, Input, Label, List, Text
} from "@stardust-ui/react";
```

The default project contains additional user interface style code that used the previous control library. This code is no longer necessary.

Locate the following code in the `componentWillMount()` method in the `LearnPersonalTab` class and delete it.

```ts
this.setState({
  fontSize: this.pageFontSize()
});
```

Locate the following code in the `render()` method in the `LearnPersonalTab` class and delete it.

```ts
const context = getContext({
  baseFontSize: this.state.fontSize,
  style: this.state.theme
});
const { rem, font } = context;
const { sizes, weights } = font;
const styles = {
  header: { ...sizes.title, ...weights.semibold },
  section: { ...sizes.base, marginTop: rem(1.4), marginBottom: rem(1.4) },
  footer: { ...sizes.xsmall }
};
```

Locate the `return ()` statement in the `render()` method in the `LearnPersonalTab` class and delete the contents. This code used the UI library that you replaced with Stardust. At this point, the `render()` method should look like the following code:

```ts
public render() {
  return (
  );
}
```

## Implement the personal tab's user interface

Now you can implement the user interface for the tab. The simple tab has a basic interface. It presents a list of items, and users can add items to the list.

First, update the state of the component to contain a list of items and a property for a new item. Locate the `ILearnPersonalTabState` interface in the LearnPersonalTab.tsx file, and add the following properties to it:

```ts
teamsTheme: ThemePrepared;
todoItems: string[];
newTodoValue: string;
```

Add the following method to the `LearnPersonalTab` class that updates the component state to the Stardust theme that matches the currently selected Microsoft Teams client theme:

```ts
private updateStardustTheme = (teamsTheme: string = "default"): void => {
  let stardustTheme: ThemePrepared;

  switch (teamsTheme) {
    case "default":
      stardustTheme = themes.teams;
      break;
    case "dark":
      stardustTheme = themes.teamsDark;
      break;
    case "contrast":
      stardustTheme = themes.teamsHighContrast;
      break;
    default:
      stardustTheme = themes.teams;
      break;
  }
  // update the state
  this.setState(Object.assign({}, this.state, {
    teamsTheme: stardustTheme
  }));
}
```

Initialize the current theme and state of the component. Locate the line `this.updateTheme(this.getQueryVariable("theme"));` and replace it with the following code in the `componentWillMount()` method:

```ts
this.updateStardustTheme(this.getQueryVariable("theme"));
this.setState(Object.assign({}, this.state, {
  todoItems: ["Submit time sheet", "Submit expense report"],
  newTodoValue: ""
}));
```

Within the `componentWillMount()` method, locate the following line:

```ts
microsoftTeams.registerOnThemeChangeHandler(this.updateTheme);
```

This code registers an event handler to update the component's theme to match the theme of the current Microsoft Teams client when this page is loaded as a tab. Update this line to call the new handler in the following line to register another handler to update the Stardust library theme:

```ts
microsoftTeams.registerOnThemeChangeHandler(this.updateStardustTheme);
```

With the theme management and state initialized, we can now implement the user interface.

Locate the `render()` method, and update the return statement to the following code. The `render()` method now displays the list of items in our state output with a brief copyright statement.

```tsx
public render() {
  return (
    <Provider theme={ this.state.teamsTheme }>
      <Flex column gap="gap.smaller">
        <Header>This is your tab</Header>
        <Alert icon="exclamation-triangle" content={ this.state.entityId } dismissible></Alert>
        <Text content="These are your to-do items:" size="medium"></Text>
        <List selectable>
          { this.state.todoItems.map(todoItem => (
            <List.Item media={<Icon name="window-maximize outline"></Icon> }
                       content={ todoItem }>
            </List.Item> ))
          }
        </List>

        TODO: add new list item form here

        <Text content="(C) Copyright Contoso" size="smallest"></Text>
      </Flex>
    </Provider>
  );
}
```

> [!TIP]
> At this point, you can test your tab without loading it in Microsoft Teams. Run the command **gulp ngrok-serve** from the command line, and go to https://`{your-ngrok-subdomain}`.ngrok.io/learnPersonalTab/index.html in the browser.
>
> ![Screenshot of the update tab page in the default theme](../media/03-yo-teams-11.png)
>
> Add the query string value `?theme=dark` to the URL to see the theme change:
>
> ![Screenshot of the update tab page in the dark theme](../media/03-yo-teams-12.png)

The next step is to add some interactivity to the tab. Add the following methods to the `LearnPersonalTab` class. These methods handle updating the state when specific events happen on the form that you'll add to the component.

```ts
private handleOnChanged = (event): void => {
  this.setState(Object.assign({}, this.state, { newTodoValue: event.target.value }));
}

private handleOnClick = (event: React.MouseEvent<HTMLButtonElement>): void  => {
  const newTodoItems = this.state.todoItems;
  newTodoItems.push(this.state.newTodoValue);

  this.setState(Object.assign({}, this.state, {
    todoItems: newTodoItems,
    newTodoValue: ""
  }));
}
```

Finally, locate the string `TODO: add new list item form here` in the `render()` method, and replace it with the following code. This code displays a form that the user can use to add items to the list.

```tsx
<Flex gap="gap.medium">
  <Flex.Item grow>
    <Flex>
      <Label icon="to-do-list"
             styles={{
               background: "darkgray",
               height: "auto",
               padding: "0 15px"
             }}></Label>
      <Flex.Item grow>
        <Input placeholder="New todo item" fluid
               value={this.state.newTodoValue}
               onChange={this.handleOnChanged}></Input>
      </Flex.Item>
    </Flex>
  </Flex.Item>
  <Button content="Add Todo" primary
          onClick={this.handleOnClick}></Button>
</Flex>
```

## Use App Studio to update the Microsoft Teams app manifest

At this point, the app is complete. Recall from our initial test that when the app was added to Microsoft Teams, it had a few "TODO" strings for the description of the app. While you could change these values in the project's ./src/manifest/manifest.json file, you use App Studio to make these changes.

First, build and run the project by running the command **gulp ngrok-serve** in the command line like you did previously. This step also creates the Microsoft Teams app package.

In the browser, go to [Microsoft Teams](https://teams.microsoft.com) and sign in with the credentials of a Work and School account.

Using the **More added apps** link on the app bar navigation menu, select **App Studio**.

![Screenshot of the More added apps dialog box with App Studio highlighted](../media/03-yo-teams-13.png)

Select the **Manifest editor** tab in App Studio, and then select **Import an existing app**. Locate the zip file that can be found in the project's ../package folder and open it.

![Screenshot of the Microsoft Teams app in App Studio](../media/03-yo-teams-14.png)

Edit the app by selecting its tile, or use the menu for more options in the upper-right corner and select **Edit**.

On the **App details** page, change the **Long name** of the app to **Learn Microsoft Teams Tabs**.

On the **App details** page, scroll down to the **Descriptions** section and enter the following values:

- **Short description**: My first custom Teams app
- **Long description**: *enter a long description*

![Screenshot of app details App Studio](../media/03-yo-teams-15.png)

Update the name of the tab by selecting **Capabilities** > **Tabs** in the App Studio navigation pane on the left.

Locate the only personal tab in the project. Select the menu for more options on the tab, and select **Edit**. Change the name of the tab to **My First Tab**. Add `?theme={theme}` to the end of the **Content URL** property. Select **Save** to save your changes.

The changes made to the app within App Studio aren't saved to your project. If you want to update the project, download the app package from App Studio.

To download the project, select **Finish** > **Test and distribute** in the App Studio navigation pane on the left. Then select **Download**.

> [!CAUTION]
> Be careful if you chose to update the manifest.json file in your project with the one in the package downloaded from App Studio.
>
> The manifest file in your project contains placeholder strings that are updated by the build and debugging process that's replaced when you test the project. This simplifies the development and debugging process.
>
> For instance, the placeholder `{{HOSTNAME}}` is replaced with the hosting URL of the app each time the package is re-created.
>
> So you might not want to completely replace the existing manifest.json file with the file generated by App Studio.

## Install and test the Microsoft Teams app

In App Studio, select **Finish** > **Test and distribute** in the App Studio navigation pane on the left. Then select **Install**. Notice that the new names and descriptions are shown prior to installing the app.

![Screenshot of installing the updated app](../media/03-yo-teams-16.png)

Select **Add** to install the app. This action adds a new personal tab to your **More added apps** dialog box. Select the app to see the updated working version.

![Screenshot of the updated and working tab](../media/03-yo-teams-17.png)

## Summary

In this exercise, you created a new Microsoft Teams personal tab by using the Microsoft Teams Yeoman generator, Visual Studio Code, and App Studio.
