In this exercise, you'll create a SharePoint Framework client-side web part.

> [!IMPORTANT]
> The instructions below assume you are using v1.11.0 of the SharePoint Framework Yeoman generator.

Open a command prompt and change to the folder where you want to create the project.

Run the SharePoint Yeoman generator by executing the following command:

```shell
yo @microsoft/sharepoint
```

Use the following to complete the prompt that is displayed:

- **What is your solution name?**: HelloWorld
- **Which baseline packages do you want to target for your component(s)?**: SharePoint Online only (latest)
- **Where do you want to place the files?**: Use the current folder
- **Do you want to allow the tenant admin the choice of being able to deploy the solution to all sites immediately without running any feature deployment or adding apps in sites?**: No
- **Will the components in the solution require permissions to access web APIs that are unique and not shared with other components in the tenant?** No
- **Which type of client-side component to create?**: WebPart
- **What is your Web part name?**: HelloWorld
- **What is your Web part description?**: HelloWorld description
- **Which framework would you like to use?**: No JavaScript framework

After provisioning the folders required for the project, the generator will install all the dependency packages using NPM.

When NPM completes downloading all dependencies, install the developer certificate by executing the following command:

```shell
gulp trust-dev-cert
```

Run the project by executing the following command:

```shell
gulp serve
```

The SharePoint Framework's gulp **serve** task will build the project, start a local web server, and launch a browser open to the SharePoint Workbench:

![Screenshot of the SharePoint Workbench](../media/03-testing-01.png)

Select the web part icon button to open the list of available web parts:

![Screenshot of adding the HelloWorld web part](../media/03-testing-02.png)

Select the **HelloWorld** web part:

![Screenshot of the HelloWorld web part](../media/03-testing-03.png)

Edit the web part's properties by selecting the pencil (edit) icon in the toolbar to the left of the web part:

![Screenshot of the web part edit toolbar](../media/03-testing-04.png)

In the property pane that opens, change the value of the **Description Field**. Notice how the web part updates as you make changes to the text:

![Screenshot of editing the web part property pane](../media/03-testing-05.png)1

## Update the web part code

Next, update the code in the `render()` method to add a button that responds to an event.

If the local dev webserver isn't running, start it by running `gulp serve` on the command line from the root folder of the project, and add the **HelloWorld** web part to the SharePoint Workbench.

Open the project folder in **Visual Studio Code**.

Locate and open the file **src/webparts/helloWorld/HelloWorldWebPart.ts**.

Within this file, locate the `render()` method. Locate the following line:

```html
<a href="https://aka.ms/spfx" class="${ styles.button }">
```

...and replace the URL with a simple hash symbol:

```html
<a href="#" class="${ styles.button }">
```

Next, add the following code to the end of the `render()` method. This will wire up some code to the **click** event on the anchor tag and display an alert on the page.

```typescript
this.domElement.getElementsByClassName(`${ styles.button }`)[0]
  .addEventListener('click', (event: any) => {
    event.preventDefault();
    alert('Welcome to the SharePoint Framework!');
  });
```

Save your changes. In a second or two, the SharePoint Workbench should automatically refresh so that you can test them.

Select the **Learn More** button.

Notice the button triggers a JavaScript alert displaying the message you added in the above code.

Close the browser and stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the command prompt.

## Update the web part's properties

Now change the properties of the web part to give it a new name, description, and icon.

The web part's metadata is found in its manifest file.

Locate and open the file **src/webparts/helloWorld/HelloWorldWebPart.manifest.json**.

In the section **preconfiguredEntries**, locate the following lines:

```json
"preconfiguredEntries": [{
  ...
  "title": { "default": "HelloWorld" },
  "description": { "default": "HelloWorld description" },
  "officeFabricIconFontName": "Page",
  ...
}]
```

Change the web part's title and description to something different.

The web part's icon is the name of one of the icons listed in the Office UI Fabric, located here: [https://developer.microsoft.com/fabric#/styles/icons](https://developer.microsoft.com/fabric#/styles/icons). Pick one and update the `officeFabricIconFontName` property:

```json
"preconfiguredEntries": [{
  ...
  "title": { "default": "Hello SPFx" },
  "description": { "default": "My first SPFx web part" },
  "officeFabricIconFontName": "BirthdayCake",
  ...
}]
```

Start the local web server using the provided gulp **serve** task:

```shell
gulp serve
```

The SharePoint Framework's gulp **serve** task will build the project, start a local web server, and launch a browser open to the SharePoint Workbench. This time, when you hover the mouse over the web part in the toolbox, you'll see the changes you applied to your web part:

![Screenshot of editing the web part property pane](../media/03-testing-06.png)

Close the browser and stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the command prompt.

## Summary

In this exercise, you created a SharePoint Framework client-side web part.
