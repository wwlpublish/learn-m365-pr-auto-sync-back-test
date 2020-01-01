In this exercise, you'll learn how to create a channel tab with a configuration page in a Microsoft Teams app.

> [!IMPORTANT]
> This exercise assumes that you created the Microsoft Teams app project with the Yeoman generator that contains a personal tab from the previous unit in this module. You'll update the project and add a channel tab in this exercise.

## Add a channel app to the Microsoft Teams app project

The Yeoman generator for Microsoft Teams can be used to add new components to an existing project. In this section, you'll add a channel tab to the existing project.

Execute the following command in the console from the root folder of the project:

```shell
yo teams
```

Yeoman starts and asks you a series of questions. Answer the questions with the following values:

- **You are running the generator on an already existing project... are you sure you want to continue?**: Yes
- **Do you want to change the current manifest version (1.5)?**: No
- **What features do you want to add to your project?**: learnMsTeamsTabs
- **Default tab name? (max 16 characters)**: ConfigMathTab
- **Do you want to create a configurable or static tab?**: Configurable
- **What scopes do you intend to use for your tab?**: In a Team
- **Do you want this tab to be available in SharePoint Online?**: Yes
- **How do you want your tab to be available in SharePoint?**: As a full-page application, as a web part

After you answer the generator's questions, the generator adds the additional files for a new component. Then it runs `npm install` to ensure that any new dependencies are downloaded for the project.

## Test the channel tab

Before you customize the tab, let's test the tab to see the experience for testing.

From the command line, go to the root folder for the project and run the following command:

```shell
gulp ngrok-serve
```

Open a browser, and go to [Microsoft Teams](https://teams.microsoft.com). Sign in with the credentials of a Work and School account.

Using the app bar navigation menu, select the **Mode added apps** button. Then select **Browse all apps** > **Upload for me or my teams**.

![Screenshot of More added apps dialog box in Microsoft Teams](../media/03-yo-teams-05.png)

In the file dialog box that appears, select the Microsoft Teams package in your project. This app package is a zip file in the project's ./package folder.

After the package is uploaded, Microsoft Teams displays a summary of the app. Select the arrow next to the **Add** button, and select **Add to a team** to install the app.

![Screenshot adding a channel tab](../media/05-channel-tab-01.png)

In the **Select a channel to start using** dialog box, select an existing team. Then select **Set up a tab**.

![Screenshot selecting a team to add the channel tab to](../media/05-channel-tab-02.png)

Before the tab is added to the team, Microsoft Teams displays the tab's configuration page.

![Screenshot of the tab configuration page](../media/05-channel-tab-03.png)

Enter anything in the text box, and select **Save**.

Microsoft Teams adds the tab to the channel and displays it for you. You should see the text you entered on the configuration page displayed in the tab.

## Update the configuration tab

On the tab you'll create in this exercise, the user can select a math operation to do on the configuration page. This value is saved with the tab so that users of the tab can do this operation on two values to see the results.

The first step is to modify the configuration page.

Locate and open the file ./src/app/scripts/configMathTab/ConfigMathTabConfig.tsx.

### Update the configuration tab to use the Stardust UI library

Before you create the configuration tab, first update it to use the Stardust UI library.

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
  Header,
  Dropdown, DropdownProps, Text
} from "@stardust-ui/react";
```

Locate the `IConfigMathTabConfigState` interface, and replace its contents with the following two members:

```ts
teamsTheme: ThemePrepared;
mathOperator: string;
```

Locate the following code in the `render()` method in the `ConfigMathTabConfig` class and delete it:

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

Locate the `return ()` statement in the `render()` method in the `ConfigMathTabConfig` class, and delete the contents. This code used the UI library that you replaced with Stardust. At this point, the `render()` method should look like the following code:

```ts
public render() {
    return (
    );
}
```

Add the following method to the `ConfigMathTabConfig` class that will update the component state to the Stardust theme that matches the currently selected Microsoft Teams client theme:

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
```

Locate the following code in the `componentWillMount()` method and delete it:

```ts
this.setState({
  fontSize: this.pageFontSize()
});
```

### Implement the configuration page logic

The configuration page displays a drop-down list of four math operators to select from. After an operator is selected, it's saved to the tab's `entityId` property with the string **MathPage** appended to it. This value is used by the tab page to determine what operation to perform in the tab.

Locate the following line in the `componentWillMount()` method: `microsoftTeams.getContext()`. The function passed into this method sets the state of the React component. Replace the `this.setState()` method with the following code. This new code takes the value of the `entityId` property on the tab, removes the **MathPage** string, and leaves only the operator:

```ts
this.setState(Object.assign({}, this.state, {
  mathOperator: context.entityId.replace("MathPage", "")
}));
```

Next, locate the following line in the `componentWillMount()` method: `microsoftTeams.settings.registerOnSaveHandler()`. This method lets you provide the function to execute when the user selects the **Save** button on the configuration page. This code should save any settings you need to save and notify Microsoft Teams that the configuration page saved the settings successfully.

Update this code to save the selected math operation and change the name of the tab:

```ts
microsoftTeams.settings.registerOnSaveHandler((saveEvent: microsoftTeams.settings.SaveEvent) => {
  // Calculate host dynamically to enable local debugging
  const host = "https://" + window.location.host;
  microsoftTeams.settings.setSettings({
    contentUrl: host + "/configMathTab/?data=",
    suggestedDisplayName: "Config Math Tab",
    removeUrl: host + "/configMathTab/remove.html",
    entityId: `${this.state.mathOperator}MathPage`
  });
  saveEvent.notifySuccess();
});
```

Add the following event handler to the `ConfigMathTabConfig` class, which updates the component state to be the value of the selected operator:

```ts
private handleOnSelectedChange = (event, props: DropdownProps): void => {
  this.setState(Object.assign({}, this.state, {
    mathOperator: (props.value) ? props.value.toString() : "add"
  }));
}
```

### Implement the configuration page user interface

Locate the `render()` method. Replace it with the following code, which adds a drop-down list for the user to select the operator they want to use:

```tsx
public render() {
  return (
    <Provider theme={this.state.teamsTheme}>
      <Flex gap="gap.smaller" style={{ height: "300px" }}>
        <Dropdown placeholder="Select the math operator"
          items={[
            "add",
            "subtract",
            "multiply",
            "divide"
          ]}
          onSelectedChange={this.handleOnSelectedChange}></Dropdown>
      </Flex>
    </Provider>
  );
}
```

### Test the configuration page

At this point, the configuration page is complete. If you removed the tab in the last step, repeat the process to upload and add it again.

If you didn't remove the tab, select the menu from the tab and then select **Settings**:

![Screenshot selecting the tab settings menu](../media/05-channel-tab-05.png)

The configuration page opens with our updated component:

![Screenshot selecting the tab settings menu](../media/05-channel-tab-04.png)

Select one of the math operators, and save your changes by selecting **Save**. The tab should display the selected operator with the **MathPage** suffix.

## Implement the channel tab

The last step is to implement the channel tab.

Locate and open the file ./src/app/scripts/configMathTab/ConfigMathTab.tsx.

### Update the channel tab to use the Stardust UI library

Before you create the configuration tab, first update it to use the Stardust UI library.

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
  Header,
  Button, Input, Text
} from "@stardust-ui/react";
```

Locate the `IConfigMathTabState` interface, and replace its contents with the following two members:

```ts
teamsTheme: ThemePrepared;
teamsTheme: ThemePrepared;
mathOperator?: string;
operandA: number;
operandB: number;
result: string;
```

Locate the following code in the `render()` method in the `ConfigMathTab` class and delete it:

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

Locate the `return ()` statement in the `render()` method in the `ConfigMathTab` class, and delete the contents. This code used the UI library that you replaced with Stardust. At this point, the `render()` method should look like the following code:

```ts
public render() {
  return (
  );
}
```

Add the following method to the `ConfigMathTab` class that will update the component state to the Stardust theme that matches the currently selected Microsoft Teams client theme:

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
```

Within the `componentWillMount()` method, locate the following line:

```ts
microsoftTeams.registerOnThemeChangeHandler(this.updateTheme);
```

This code registers an event handler to update the component's theme to match the theme of the current Microsoft Teams client when this page is loaded as a tab. Update this line to call the new handler in the following line to register another handler to update the Stardust library theme:

```ts
microsoftTeams.registerOnThemeChangeHandler(this.updateStardustTheme);
```

Locate the following code in the `componentWillMount()` method and delete it:

```ts
this.setState({
  fontSize: this.pageFontSize()
});
```

### Implement the channel page logic

Locate the following line in the `componentWillMount()` method: `microsoftTeams.getContext()`. The function passed into this method sets the state of the React component. Replace the `this.setState()` method with the following code. This new code takes the value of the `entityId` property on the tab, removes the **MathPage** string, and leaves only the operator:

```ts
this.setState(Object.assign({}, this.state, {
  mathOperator: context.entityId.replace("MathPage", "")
}));
```

Locate the following code in the `componetWillMount()` method:

```ts
this.setState({
  entityId: "This is not hosted in Microsoft Teams"
});
```

Replace this code with the following code. This new code will cause the math operator to add two numbers by default in case this page is loaded outside of a Microsoft Teams client:

```ts
this.setState(Object.assign({}, this.state, {
  mathOperator: "add"
}));
```

Add the following event handlers to the `ConfigMathTab` class. These event handlers will update the state with the values from the controls and perform the calculation of the two numbers by using the operator specified on the configuration page:

```ts
private handleOnChangedOperandA = (event): void => {
  this.setState(Object.assign({}, this.state, { operandA: event.target.value }));
}

private handleOnChangedOperandB = (event): void => {
  this.setState(Object.assign({}, this.state, { operandB: event.target.value }));
}

private handleOperandChange = (): void => {
  let stringResult: string = "n/a";

  if (!isNaN(Number(this.state.operandA)) && !isNaN(Number(this.state.operandB))) {
    switch (this.state.mathOperator) {
      case "add":
        stringResult = (Number(this.state.operandA) + Number(this.state.operandB)).toString();
        break;
      case "subtract":
        stringResult = (Number(this.state.operandA) - Number(this.state.operandB)).toString();
        break;
      case "multiply":
        stringResult = (Number(this.state.operandA) * Number(this.state.operandB)).toString();
        break;
      case "divide":
        stringResult = (Number(this.state.operandA) / Number(this.state.operandB)).toString();
        break;
      default:
        stringResult = "n/a";
        break;
    }
  }

  this.setState(Object.assign({}, this.state, {
    result: stringResult
  }));
}
```

### Implement the channel page user interface

Locate the `render()` method in the `ConfigMathTab` class. Replace the existing method implementation with the following code. This new code adds two input boxes and a button to the page. When the button is selected, it performs the math operation selected on the configuration page to the two values and displays the results.

```ts
public render() {
  return (
    <Provider theme={this.state.teamsTheme}>
      <Flex column gap="gap.smaller">
        <Header>This is your tab</Header>
        <Text content="Enter the values to calculate" size="medium"></Text>

        <Flex gap="gap.smaller">
          <Flex.Item>
            <Flex gap="gap.smaller">
              <Flex.Item>
                <Input autoFocus
                        value={this.state.operandA}
                        onChange={this.handleOnChangedOperandA}></Input>
              </Flex.Item>
              <Text content={this.state.mathOperator}></Text>
              <Flex.Item>
                <Input value={this.state.operandB}
                        onChange={this.handleOnChangedOperandB}></Input>
              </Flex.Item>
            </Flex>
          </Flex.Item>
          <Button content="Calculate" primary
                  onClick={this.handleOperandChange}></Button>
          <Text content={this.state.result}></Text>
        </Flex>
        <Text content="(C) Copyright Contoso" size="smallest"></Text>
      </Flex>
    </Provider>
  );
}
```

### Test the channel tab page

At this point, the channel tab page is complete. If the web server isn't still running, rebuild the project and start the web server by running **gulp ngrok-server**.

Open a browser, and go to [Microsoft Teams](https://teams.microsoft.com). Sign in with the credentials of a Work and School account.

Go to the team where the tab is installed, and select the channel tab. Enter two values, and select the **Calculate** button. The results of the calculation appear next to the button.

![Screenshot of the working channel button](../media/05-channel-tab-06.png)

Use the **Settings** link on the tab to open the configuration tab, and change the math operation.

Stop the local web server by selecting <kbd>Ctrl</kbd>+<kbd>C</kbd> in the console to stop the running process.

## Summary

In this exercise, you created a channel tab with a configuration page in a Microsoft Teams app.
