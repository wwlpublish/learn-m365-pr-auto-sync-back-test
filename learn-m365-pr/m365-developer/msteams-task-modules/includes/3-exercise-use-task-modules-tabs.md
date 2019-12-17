In this exercise, you’ll learn the basics of task modules in Microsoft Teams and how to collect input from users in a custom Teams tab. After creating a new Microsoft Teams personal tab, you'll add two task modules to it.

One is a standard HTML page that accepts the ID of a video on YouTube. When the task module is invoked, it will display the video using the YouTube embedded player. This task module will get the video ID from the query string, but it will not need to return any information back to the tab.

![Screenshot of the YouTube Player task module](../media/03-yo-teams-10.png)

The other task module is implemented using React, the same way custom tabs are implemented using the Yeoman Generator for Microsoft Teams. This task module enables the user to specify the ID of the YouTube video to display. Once changed, when the user saves their changes, it will use the callback to close submit the new ID back to the tab.

![Screenshot of the YouTube Selector task module](../media/03-yo-teams-11.png)

## Prerequisites

Developing Microsoft Teams apps requires an Office 365 tenant, Microsoft Teams configured for development, and the necessary tools installed on your workstation.

For the Office 365 tenant, follow the instructions on [Microsoft Teams: Prepare your Office 365 tenant](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-tenant) for obtaining a developer tenant if you don't currently have an Office 365 account. Make sure you have also enabled Microsoft Teams for your organization.

Microsoft Teams must be configured to enable custom apps and allow custom apps to be uploaded to your tenant to build custom apps for Microsoft Teams. Follow the instructions on the same **Prepare your Office 365 tenant** page mentioned above.

You'll use Node.js to create custom Microsoft Teams tabs in this module. The exercises in this module assume you have the following tools installed on your developer workstation.

> [!IMPORTANT]
> In most cases, installing the latest version of the following tools is the best option. The versions listed here were used when this module was published and last tested.

- [Node.js](https://nodejs.org/) - v10.\* (or higher)
- NPM (installed with Node.js) - v6.\* (or higher)
- [Gulp](https://gulpjs.com/) - v4.\* (or higher)
- [Yeoman](https://yeoman.io/) - v3.\* (or higher)
- [Yeoman Generator for Microsoft Teams](https://github.com/OfficeDev/generator-teams) - v2.\* (or higher)
- [Visual Studio Code](https://code.visualstudio.com)

You must have the minimum versions of these prerequisites installed on your workstation.

## Create Microsoft Teams app

Open your command prompt, navigate to a directory where you want to save your work, create a new folder **learn-msteams-taskmodules**, and change directory into that folder.

Run the Yeoman Generator for Microsoft Teams by running the following command:

```shell
yo teams
```

![Screenshot of the Yeoman Generator for Microsoft Teams](../media/03-yo-teams-01.png)

Yeoman will launch and ask you a series of questions. Answer the questions with the following values:

- **What is your solution name?**: YouTubePlayer
- **Where do you want to place the files?**: Use the current folder
- **Title of your Microsoft Teams App project?**: YouTube Player
- **Your (company) name? (max 32 characters)**: Contoso
- **Which manifest version would you like to use?**: 1.5
- **Enter your Microsoft Partner Id, if you have one?**: (Leave blank to skip)
- **What features do you want to add to your project?**: A Tab
- **The URL where you will host this solution?**: https://youtubeplayer.azurewebsites.net
- **Would you like to include Test framework and initial tests?**: No
- **Would you like to use Azure Applications Insights for telemetry?**: No
- **Default Tab name? (max 16 characters)**: YouTube Player 1
- **Do you want to create a configurable or static tab?**: Static

> [!NOTE]
> Most of the answers to these questions can be changed after creating the project. For example, the URL where the project will be hosted isn't important at the time of creating or testing the project.

After answering the generator's questions, the generator will create the scaffolding for the project and then execute `npm install` that downloads all the dependencies required by the project.

### Test the personal tab

Before customizing the tab, let's test the tab to see the initial developer experience for testing.

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

This gulp task will run many other tasks all displayed within the command-line console. The **ngrok-serve** task builds your project and starts a local web server (http://localhost:3007). It then starts ngrok with a random subdomain that creates a secure URL to your local webserver.

> [!NOTE]
> Microsoft Teams requires all content displayed within a tab be loaded from an HTTPS request. In development, can be done using the tool [ngrok](https://www.ngrok.com) that creates a secure rotatable URL to your local HTTP webserver. Ngrok is included as a dependency within the project so there is nothing to setup or configure.

![Screenshot of gulp ngrok-serve](../media/03-yo-teams-02.png)

Open a browser and navigate to the ngrok URL displayed in the console:

![Screenshot of the local web app hosting the Teams tab project](../media/03-yo-teams-03.png)

Update the URL in the browser to load the tab created by the scaffolding process. Here you can see the page can determine that it isn't running within the Microsoft Teams client.

![Screenshot of the local web app hosting the Teams tab project](../media/03-yo-teams-04.png)

Now let's load the tab in Microsoft Teams. In the browser, navigate to **https://teams.microsoft.com** and sign in with the credentials of a Work and School account.

> [!NOTE]
> Microsoft Teams is available for use as a web client, desktop client and a mobile client. In this module, we will use the web client but any of the clients can be used.

Using the app bar navigation menu, select the **Mode added apps** button. Then select **Browse all apps** followed by **Upload for me or my teams**.

![Screenshot of More added apps dialog in Microsoft Teams](../media/03-yo-teams-05.png)

In the file dialog that appears, select the Microsoft Teams package in your project. This app package is a ZIP file that can be found in the project's **./package** folder.

Once the package is uploaded, Microsoft Teams will display a summary of the app. Here you can see some "todo" items to address. *None of these "todo" items are important to this exercise, so you will leave them as is.*

![Screenshot of Microsoft Teams app](../media/03-yo-teams-06.png)

Select the **Add** button to install the app, adding a new personal tab to your **More added apps** dialog:

![Screenshot of the installed Microsoft Teams app in the More added apps dialog](../media/03-yo-teams-07.png)

Select the app to navigate to the new tab:

![Screenshot of the installed Microsoft Teams app personal tab](../media/03-yo-teams-08.png)

Notice that when the content page is loaded in a tab within the Microsoft teams client, it's displaying the value of the `entityId` property of the tab, not the message "This isn't hosted in Microsoft Teams" as you saw when viewing the content page in the browser. The tab can detect if it's loaded within the Microsoft Teams client using the Microsoft Teams JavaScript SDK.

The next step is to make some changes to the project.

Next, stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console to stop the running process.

### Update the project to use the Stardust UI library

Microsoft Teams recommends your custom apps use React and the themable React component library [Stardust UI React](https://stardust-ui.github.io/react/). To use Stardust in the Microsoft Teams app, we need to make some changes to the project.

> [!IMPORTANT]
> At the time of publication of this module, there are plans to update the Yeoman generator for Microsoft Teams to include Stardust in the default project. However, at the time of publication of this module, the default project uses the older Microsoft Teams control library that Stardust is replacing.
>
> Therefore, the steps in this section may or may not be necessary as the Yeoman generator for Microsoft Teams may have been updated. Review each of the instructions in this section and compare the results with your project to determine if they are necessary.

The first step is to uninstall the existing control library and install the Stardust library. Execute the following two commands in the command line from the root folder of the project:

```shell
npm uninstall msteams-ui-components-react
npm install @stardust-ui/react
```

Locate and open the file that contains the React component used in the project: **./src/app/scripts/youTubePlayer1Tab/YouTubePlayer1Tab.tsx**.

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

Replace the above statement with the following import statement:

```ts
import {
  Flex, Provider, themes, ThemePrepared,
  Header, Button, Input, Text
} from "@stardust-ui/react";
```

The default project contains additional user interface style code that used the previous control library. This code is no longer necessary

Locate the following code in the `componentWillMount()` method in the `YouTubePlayer1Tab` class and delete it:

```ts
this.setState({
  fontSize: this.pageFontSize()
});
```

Locate the following code in the `render()` method in the `YouTubePlayer1Tab` class and delete it:

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

Locate the `return ()` statement in the `render()` method in the `YouTubePlayer1Tab` class and delete the contents. This code used the UI library that you replaced with Stardust. At this point, the `render()` method should look like the following code:

```ts
public render() {
  return (
  );
}
```

### Implement the personal tab's user interface

Now you can implement the user interface for the tab. The simple tab will have a basic interface.

First, update the state of the component to contain a list of items and a property for a new item. Locate the `IYouTubePlayer1TabState` interface in the **YouTubePlayer1Tab.tsx** file and add the following properties to it:

```ts
teamsTheme: ThemePrepared;
todoItems: string[];
newTodoValue: string;
```

Add the following method to the `YouTubePlayer1Tab` class that will update the component state to the Stardust theme that matches the currently selected Microsoft Teams client theme:

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

This code registers an event handler to update the component's theme to match the theme of the current Microsoft Teams client when this page is loaded as a tab. Update this line to call the new handler the following line to register another handler to update the Stardust library theme:

```ts
microsoftTeams.registerOnThemeChangeHandler(this.updateStardustTheme);
```

With the theme management and state initialized, we can now implement the user interface.

Locate the `render()` method and update the return statement to the following code. The `render()` method will now display the list of items in our state out with a brief copyright statement:

```tsx
public render() {
  return (
    <Provider theme={this.state.teamsTheme}>
      <Flex column gap="gap.smaller">
        <Header>Task Module Demo</Header>
        <Text>YouTube Video ID:</Text>
        <Input value={this.state.youTubeVideoId} disabled></Input>
        <Button content="Change Video ID" onClick={this.onChangeVideo}></Button>
        <Button content="Show Video" primary onClick={this.onShowVideo}></Button>
        <Text content="(C) Copyright Contoso" size="smallest"></Text>
      </Flex>
    </Provider>
  );
}
```

The next step is to add some interactivity to the tab. Add the following methods to the `YouTubePlayer1Tab` class. These methods will handle updating the state when specific events happen on the form you'll add to the component:

```ts
private onShowVideo = (event: React.MouseEvent<HTMLButtonElement>): void => {
}

private onChangeVideo = (event: React.MouseEvent<HTMLButtonElement>): void => {
}
```

Finally, initialize the state of the tab by setting it to a default video to display.

Within the `componentWillMount()` method, add the following statement to the top of the method:

```ts
this.setState(Object.assign({}, this.state, {
  youTubeVideoId: "X8krAMdGvCQ"
}));
```

### Test the personal tab

At this point, our Microsoft Teams app, implemented as a custom person tab is set up and working. Verify this by starting ngrok again and refreshing the Microsoft Teams interface.

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

Refresh the Microsoft Teams interface and notice the new UI you've implemented for the tab:

![Screenshot of the updated YouTube Player tab](../media/03-yo-teams-09.png)

Now you can update the project and add task modules to the custom Microsoft Teams app.

Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console to stop the running process.

## Add video player task module

A task module can be a web page implemented with HTML and JavaScript. Create the video player task module by creating a new file, **player.html** in the **./src/app/web/youTubePlayer1Tab** folder in your project.

Add the following HTML to the **player.html** file:

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <title>YouTube Player Task Module</title>
  <style>
    #embed-container iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 95%;
      height: 95%;
      padding-left: 20px;
      padding-right: 20px;
      padding-top: 10px;
      padding-bottom: 10px;
      border-style: none;
    }
  </style>
</head>

<body>
  <div id="embed-container"></div>
</body>

</html>
```

The video player task module will use the YouTube embedded player to show the specified video. The video will be defined in the query string when the **player.html** file is loaded.

Implement the `<iframe>` embedded video player by adding the following JavaScript before the closing `</body>` tag in the **player.html** file:

```html
<script>
  function getUrlParameter(name) {
    name = name.replace(/[\[]/, '\\[').replace(/[\]]/, '\\]');
    var regex = new RegExp('[\\?&]' + name + '=([^&#]*)');
    var results = regex.exec(location.search);
    return results === null ? '' : decodeURIComponent(results[1].replace(/\+/g, ' '));
  };

  var element = document.createElement("iframe");
  element.src = "https://www.youtube.com/embed/" + getUrlParameter("vid");
  element.width = "1000";
  element.height = "700";
  element.frameborder = "0";
  element.allow = "autoplay; encrypted-media";
  element.allowfullscreen = "";

  document.getElementById("embed-container").appendChild(element);
</script>
```

Now, implement the task module in the personal tab.

Locate and open the **./src/app/scripts/YouTubePlayer1Tab.tsx** file.

First, add the following utility method to the `YouTubePlayer1Tab` class:

```js
private appRoot(): string {
  if (typeof window === "undefined") {
    return "https://{{HOSTNAME}}";
  } else {
    return window.location.protocol + "//" + window.location.host;
  }
}
```

Next, add the following code to the `onShowVideo` method:

```ts
private onShowVideo = (event: React.MouseEvent<HTMLButtonElement>): void => {
  const taskModuleInfo = {
    title: "YouTube Player",
    url: this.appRoot() + `/youTubePlayer1Tab/player.html?vid=${this.state.youTubeVideoId}`,
    width: 1000,
    height: 700
  };
  microsoftTeams.tasks.startTask(taskModuleInfo);
}
```

This code will create a new `taskInfo` object with the details of the task module. It will then launch the task module. This task module does nothing but display information, so we don't need to implement the callback.

### Test the video player task module

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

Refresh the Microsoft Teams interface. Select the **Show video** button. Microsoft Teams will load the video player task module with the specified video loaded in the embedded player:

![Screenshot of the YouTube Player task module](../media/03-yo-teams-10.png)

Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console to stop the running process.

## Add video selector task module

Now let's update the project to include a task module that will enable the user to change the video loaded in the player task module. For this task module, you'll implement it similar to how the custom tab is implemented: as a React app.

### Create the task module's React app web page host

Create a new file, **selector.html**, in the **./src/app/web/youTubePlayer1Tab** folder.

Add the following HTML to it:

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>YouTube Video Selector</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- inject:css -->
  <!-- endinject -->
  <style>
    #app {
      margin-left: 20px;
      margin-right: 20px;
      margin-top: 10px;
      margin-bottom: 10px;
    }
  </style>
</head>

<body>
  <div id='app'>
    Loading...
  </div>
  <!-- inject:js -->
  <!-- endinject -->
  <script type='text/javascript'>
    youTubePlayer.VideoSelectorTaskModule.render(document.getElementById('app'), {});
  </script>
</body>

</html>
```

### Register the new page

Next, register the page you created in the last step with the project's hosting infrastructure. This will also add the necessary HTTP headers to the page's response to ensure it can be loaded within an IFRAME, but only within a Microsoft Teams client.

Create a new file, **VideoSelectorTaskModule.ts**, in the **./src/app/youTubePlayer1Tab** folder.

Add the following code to the file:

```ts
import { PreventIframe } from "express-msteams-host";

@PreventIframe("/youTubePlayer1Tab/selector.html")

export class VideoSelectorTaskModule { }
```

Now register the page by adding the following line to the end of the **./src/app/TeamsAppsComponents.ts** file:

```ts
export * from "./youTubePlayer1Tab/VideoSelectorTaskModule";
```

### Implement the React app for the selector task module

With the selector's page created and registered, the next step is to implement the React app that is loaded in the page.

Create a new file, **VideoSelectorTaskModule.tsx**, in the folder **./src/app/scripts/youTubePlayer1Tab**.

Add the following code to the page. Most of this code mirrors what you would see if you created a new tab.

```ts
import * as React from "react";
import {
  Flex, Provider, themes, ThemePrepared,
  Button, Input, Text
} from "@stardust-ui/react";
import TeamsBaseComponent, { ITeamsBaseComponentProps, ITeamsBaseComponentState } from "msteams-react-base-component";
import * as microsoftTeams from "@microsoft/teams-js";

export interface IVideoSelectorTaskModuleState extends ITeamsBaseComponentState {
  teamsTheme: ThemePrepared;
  youTubeVideoId?: string;
}

export interface IVideoSelectorTaskModuleProps extends ITeamsBaseComponentProps {
}

export class VideoSelectorTaskModule extends TeamsBaseComponent<IVideoSelectorTaskModuleProps, IVideoSelectorTaskModuleState> {
  public componentWillMount(): void {
    this.updateStardustTheme(this.getQueryVariable("theme"));
    this.setState(Object.assign({}, this.state, {
      youTubeVideoId: this.getQueryVariable("vid")
    }));

    if (this.inTeams()) {
      microsoftTeams.initialize();
      microsoftTeams.registerOnThemeChangeHandler(this.updateStardustTheme);
    }
  }

  public render() {
    return (
    );
  }

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
}
```

Implement the user interface of the task module by adding the following code to the `render()` method:

```tsx
<Provider theme={this.state.teamsTheme}>
  <Flex column gap="gap.smaller">
    <Text size="medium">
      Enter the ID of a YouTube video to show in the task module player.
    </Text>
    <Input value={this.state.youTubeVideoId} onChange={this.handleOnChanged}></Input>
    <Button content="Update" primary onClick={this.handleOnClick}></Button>
  </Flex>
</Provider>
```

Next, implement the two handlers referenced in the `render()` method. Add these two functions to the `VideoSelectorTaskModule` class:

```ts
private handleOnChanged = (event): void => {
  this.setState(Object.assign({}, this.state, {
    youTubeVideoId: event.target.value
  }));
}

private handleOnClick = (event: React.MouseEvent<HTMLButtonElement>): void => {
  microsoftTeams.tasks.submitTask(this.state.youTubeVideoId, undefined);
}
```

The `handleOnChanged()` method updates the state with the value specified in the input control, while the `handleOnClick()` method uses the Microsoft Teams SDK to pass the ID of the video back to the personal tab.

Make this React class available to the rest of the application by adding the following line to the **./src/app/scripts/client.ts** file:

```ts
export * from "./youTubePlayer1Tab/VideoSelectorTaskModule";
```

The last step is to wire this task module up to the tab. Within the **./src/app/scripts/youTubePlayer1Tab/YouTubePlayer1Tab.tsx** file, locate the method `onChangeVideo()`. Add the following code to the method:

```ts
const taskModuleInfo = {
  title: "YouTube Video Selector",
  url: this.appRoot() + `/youTubePlayer1Tab/selector.html?theme={theme}&vid=${this.state.youTubeVideoId}`,
  width: 350,
  height: 150
};

const submitHandler = (err: string, result: string): void => {
  this.setState(Object.assign({}, this.state, {
    youTubeVideoId: result
  }));
};

microsoftTeams.tasks.startTask(taskModuleInfo, submitHandler);
```

This code will first create the `taskInfo` object that defines the task module. It also creates a callback that will take the result from the task module and use it to update the state of the React app.

### Test the video selector task module

From the command line, navigate to the root folder for the project and execute the following command:

```shell
gulp ngrok-serve
```

Refresh the Microsoft Teams interface. Select the **update video** button. Microsoft Teams will load the video selector task module with the ID of the currently selected video in the text control.

![Screenshot of the YouTube Selector task module](../media/03-yo-teams-11.png)

Enter the ID of another YouTube video and select the **Update** button. Notice the ID of the video has changed. Now when you select the **Show video** button, the player task module loads with the new video.

![Screenshot of the YouTube Player task module](../media/03-yo-teams-12.png)

Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console to stop the running process.

## Summary

In this exercise, you learned the basics of task modules in Microsoft Teams and how to collect input from users in a custom Teams tab. After creating a new Microsoft Teams personal tab, you added two task modules to it.
