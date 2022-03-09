In this exercise, you'll create a SharePoint Framework client-side web part.

> [!IMPORTANT]
> The instructions below assume you are using v1.13.1 of the SharePoint Framework Yeoman generator.

Open a command prompt and change to the folder where you want to create the project.

Run the SharePoint Yeoman generator by executing the following command:

```console
yo @microsoft/sharepoint
```

Use the following to complete the prompt that is displayed:

- **What is your solution name?**: HelloWorld
- **Only SharePoint Online (latest) is supported.  For earlier versions of SharePoint (2016 and 2019) please use the 1.4.1 version of the generator.**: SharePoint Online only (latest)
- **Do you want to allow the tenant admin the choice of being able to deploy the solution to all sites immediately without running any feature deployment or adding apps in sites?**: No
- **Will the components in the solution require permissions to access web APIs that are unique and not shared with other components in the tenant?** No
- **Which type of client-side component to create?**: WebPart
- **What is your Web part name?**: HelloWorld
- **What is your Web part description?**: HelloWorld description
- **Which framework would you like to use?**: No JavaScript framework

After provisioning the folders required for the project, the generator will install all the dependency packages using NPM.

When NPM completes downloading all dependencies, ensure the developer certificate is installed by executing the following command:

```console
gulp trust-dev-cert
```

Run the project by executing the following command:

```console
gulp serve --nobrowser
```

The SharePoint Framework's gulp **serve** task with the **nobrowser** switch will build the project and start a local web server.

Wait for the **reload** subtask to finish executing. At this point, the web part will be ready for testing.

![Screenshot of the gulp serve output](../media/03-testing-01.png)

Open a browser and navigate to the developer site you created in the first exercise. If prompted, log in using your Work or School credentials. Append the following to the end of the site's URL: **/_layouts/workbench.aspx**. This is the SharePoint-hosted workbench.

![Screenshot of the SharePoint Workbench](../media/03-testing-02.png)

Select the web part icon button to open the list of available web parts, scroll down to the **Advanced** section, and select the **HelloWorld** web part:

![Screenshot of adding the HelloWorld web part](../media/03-testing-03.png)

Edit the web part's properties by selecting the pencil (edit) icon in the toolbar to the left of the web part:

![Screenshot of the web part edit toolbar](../media/03-testing-04.png)

In the property pane that opens, change the value of the **Description Field**. Notice how the web part updates as you make changes to the text:

![Screenshot of editing the web part property pane](../media/03-testing-05.png)

## Update the web part code

Open the project folder in **Visual Studio Code**.

If the local web server isn't running, start it by running **gulp serve --nobrowser** on the command line from the root folder of the project, and add the **HelloWorld** web part to the SharePoint Workbench.

Next, update the code in the `render()` method to add a button that responds to an event.

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

Save your changes. Wait a few seconds for the gulp **serve** task to rebuild your project, and then refresh the SharePoint Workbench so that you can test them.

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

Start the local web server using the provided gulp **serve** task with the **nobrowser** switch:

```console
gulp serve --nobrowser
```

Wait for the **reload** subtask to finish executing, then open or refresh the SharePoint Workbench. This time, when you hover the mouse over the web part in the toolbox, you'll see the changes you applied to your web part:

![Screenshot of the web part gallery](../media/03-testing-06.png)

Close the browser and stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the command prompt.

## Summary

In this exercise, you created a SharePoint Framework client-side web part.
