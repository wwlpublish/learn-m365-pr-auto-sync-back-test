In this exercise, you will build a SharePoint Framework web part that retrieves data from a SharePoint list and add the web part to Viva Connections desktop.

## Create a new solution

To start, create a new solution using the SharePoint Framework Yeoman generator.

1. Create a folder for your project named **spfx-company-announcements-webpart**
1. In a terminal, change the working directory to **spfx-company-announcements-webpart**
1. Next, run the `yo @microsoft/sharepoint` command to start scaffolding a new solution
1. Answer generator's prompts:
   1. What is your solution name? **spfx-company-announcements-webpart**
   1. Only SharePoint Online (latest) is supported. For earlier versions of SharePoint (2016 and 2019) please use the 1.12.1 version of the generator. **SharePoint Online only (latest)**
   1. Where do you want to place the files? **Use the current folder**
   1. Do you want to allow the tenant admin the choice of being able to deploy the solution to all sites immediately without running any feature deployment or adding apps in sites? **No**
   1. Will the components in the solution require permissions to access web APIs that are unique and not shared with other components in the tenant? **No**
   1. Which type of client-side component to create? **WebPart**
   1. What is your Web part name? **Company announcements**
   1. What is your Web part description? **Shows company announcements**
   1. Which framework would you like to use? **No JavaScript framework**
1. Wait for the project creation to complete. It may take a few minutes.
   > [!TIP]
   > While creating the project, you will likely see some warnings. You can safely ignore them.

## Install the development certificate

SharePoint Framework uses a workbench hosted in SharePoint Online to let you test your code before deploying it to Viva Connections. When you test your code, you start a local web server using Gulp. SharePoint Framework workbench then loads files from your local server and lets you test them. To let the workbench load files from your local dev server, you need to trust the development certificate provided by SharePoint Framework.

> [!IMPORTANT]
> You need to install the development certificate only once on your machine. When you create a new project, SharePoint Framework will use the previously installed certificate. If you've done this already, you can skip these steps.

1. Open a terminal
1. Change the working directory to your project folder
1. Run the `gulp trust-dev-cert` command
1. Follow the instructions on the screen to complete the installation of the certificate

## Edit the web part

After you created the project, the next step is to extend the web part so that it loads company announcements from the list and shows them on the page.

1. Open the project in your code editor
1. In the code editor, open the **./src/webparts/companyAnnouncements/CompanyAnnouncementsWebPart.ts** file
1. In the top section of the file, add `import { SPHttpClient } from '@microsoft/sp-http';`
1. Clear the contents of the **render** method
1. In the **render** method, add the following code block:

   ```typescript
   this.context.spHttpClient
     .get(`${this.context.pageContext.web.absoluteUrl}/_api/web/lists/getByTitle('Announcements')/items?$select=Title,Description,Important`,
       SPHttpClient.configurations.v1,
       {
         headers: {
           'accept': 'application/json;odata.metadata=none'
         }
       })
     .then(response => response.json())
     .then(announcements => {
       // todo: display results
     })
     .catch(error => this.context.statusRenderer.renderError(this.domElement, error));
   ```

   You use the `spHttpClient` to retrieve the list of announcements from the previously created **Announcements** list. `spHttpClient` wraps the standard `fetch` API and is authenticated to call SharePoint APIs.
   In the API URL, you use the OData `$select` parameter to specify the list of properties to retrieve. These properties match the columns from the **Announcements** list. While calling the SharePoint API, you also set the `accept` header to suppress metadata in the response. It allows you to minimize the amount of data sent over the network.
   After you receive the response from the API, you retrieve its JSON response. If an error occurs while calling the API, it will be displayed in the web part's content area using the helper method exposed by the web part.
1. After retrieving announcements from the list, the next step is to display them in the web part. In the last `then` clause, replace the `// todo: display results` comment with the following block:

   ```typescript
   const announcementsHtml = announcements.value.map(announcement =>
     `<dt${announcement.Important ?
       ` class="${styles.important}"` : ''}>${announcement.Title}</dt>
     <dd>${announcement.Description}</dd>`);
   
   this.domElement.innerHTML = `
   <div class="${styles.companyAnnouncements} ${this._hasTeamsContext ? styles.teams : ''}">
     <div class="${styles.container}">
       <div class="${styles.title}">Announcements</div>
       <dl>
         ${announcementsHtml.join('')}
       </dl>
     </div>
   </div>
   `;
   ```

   The `announcement` variable contains the `value` property holding an array of announcements from the list. For each announcement, you create an HTML string with the `dt` and `dd` elements holding the announcement's contents. Next, you combine the announcements into a single HTML string and display it in the web part's DOM element.
   > [!TIP]
   > When possible, you should always use semantic HTML rather than the generic `div` and `span` elements. Using semantic HTML, like a heading (`h1`-`h6`) or a definition list (`dl`) allows people who use screen readers and other accessibility tools to follow the page's contents more easily.
1. To save your changes, from the **File** menu choose **Save** or press on the keyboard `CTRL+S` (`CMD+S` on macOS).

## Style the web part contents

To show announcements in the web part, you used the standard `dl`, `dt`, and `dd` HTML elements. You also included a custom CSS class named `important` to highlight important announcements. Let's add CSS styles to format how announcements and important announcements are displayed.

1. In the code editor, open the **./src/webparts/companyAnnouncements/CompanyAnnouncementsWebPart.module.scss** file
1. Replace the contents of the file with the following code:

   ```css
   @import '~@microsoft/sp-office-ui-fabric-core/dist/sass/SPFabricCore.scss';
   
   .companyAnnouncements {
     &.teams {
       font-family: $ms-font-family-fallbacks;
     }
   
     .container {
       @include ms-Grid;
       color: var(--primaryText, #323130);
     }
   
     .title {
       @include ms-fontSize-18;
       @include ms-fontWeight-semibold;
     }
   
     dt {
       @include ms-fontWeight-bold;
       @include ms-fontSize-14;
       margin-top: 1rem;
   
       &.important {
         color: $ms-color-red;
       }
     }
   
     dd {
       margin-left: 0;
     }
   }
   ```

   You start with importing Fluent UI to ensure consistent styling with Microsoft 365. Next, you add a CSS class for the web part's title. In the class, you refer to the font definitions from Fluent UI. Then, you define styling for the `dt` and `dd` elements that you used to display announcements. Like you did for the web part's title, you refer to Fluent UI styles to ensure consistency. To highlight important announcements, you define an extra class named `important`, which uses red text as defined in Fluent UI.
1. To save your changes, from the **File** menu choose **Save** or press on the keyboard `CTRL+S` (`CMD+S` on macOS).

## Test the web part

To build and preview the Company announcements web part:

1. In a terminal, run the `gulp serve --nobrowser` command. This command will start a local webserver on `https://localhost:4321`
   :::image type="content" source="../media/4-terminal-serve.png" alt-text="Screenshot of a terminal window with the output of the gulp serve command":::
   > [!WARNING]
   > If you see in the terminal the following warning:
   > :::image type="content" source="../media/4-terminal-serve-warning.png" alt-text="Screenshot of a terminal window showing a warning after running the gulp serve command":::
   >
   > _Warning - [spfx-serve] When serving in HTTPS mode, a PFX cert path or a cert path and a key path must be provided, or a dev certificate must be generated and trusted. If a SSL certificate isn't provided, a default, self-signed certificate will be used. Expect browser security warnings._
   >
   > it means that the local web server couldn't load your development certificate. To fix this issue, stop the web server by pressing `CTRL+C` and execute the `gulp trust-dev-cert` command.
1. In a web browser, go to the workbench at `<Home site url>/_layouts/workbench.aspx`. The Home site URL is where you have created the **Announcements** list in the previous exercise.
   > [!WARNING]
   > After you open the workbench, if you see the following error:
   > :::image type="content" source="../media/4-workbench-warning.png" alt-text="SharePoint workbench showing a warning message about being unable to load the local manifest":::
   >
   > _Your web part will not appear in the toolbox. Please make sure “gulp serve” is running in a web part project. Please refresh the page once “gulp serve” is running._
   >
   > it means that the local web server couldn't load your development certificate. To fix this issue, stop the web server by pressing `CTRL+C` and execute the `gulp trust-dev-cert` command.
1. To add the newly created web part to the canvas, select the **+** button to launch the toolbox.
   :::image type="content" source="../media/4-open-toolbox.png" alt-text="Arrow pointing to the + button to open the toolbox in the SharePoint workbench":::
1. In the search bar, type `Company announcements` and select the web part.
   :::image type="content" source="../media/4-toolbox-company-announcements-web-part.png" alt-text="Arrow pointing to the Company announcements web part in the web part toolbox":::
   If you followed all steps successfully, you'll see your announcements from the Announcements list displayed in the workbench.
   :::image type="content" source="../media/4-company-announcements-web-part.png" alt-text="Company announcements web part showing announcements in the SharePoint workbench":::
   The titles of announcements selected as important are shown in red.
1. To stop the dev web server, go back to the terminal and press `CTRL+C`.

You have successfully built a SharePoint Framework web part. Now let's see how we can deploy this web part to Viva Connections.

## Deploy the web part to Viva Connections

You've built the **Company announcements** web part using the SharePoint Framework. Now let's see how we can deploy it to Viva Connections.

**Package the app**

To package the web part into an app using Gulp:

1. Go to the terminal where the working directory is the root folder of the project
1. To build the solution in release mode, run the `gulp bundle --ship` command
1. To make a release mode package of the solution, run the `gulp package-solution --ship` command
1. The `package-solution` task created an app package file named **spfx-company-announcements-webpart.sppkg** in the **./sharepoint/solution** folder.

This file is your app package. Next, you'll deploy this package into the SharePoint app catalog, which contains all Viva Connections extensions.

**Create an app catalog**

If you do not have an app catalog in your tenant, you'll need to create it before you continue this exercise.

1. In a web browser, go to the **Microsoft 365 admin center** located at [https://admin.microsoft.com](https://admin.microsoft.com).
1. From the side menu, select the **Show all** option
1. From the list of **Admin centers**, select **SharePoint**
1. In the **SharePoint admin center**, from the side navigation, select **More features**
1. From the **Apps** section, select the **Open** button to go to the **Apps** admin page
1. Under **Apps**, select **App Catalog**
1. If the site opens up, you already have an app catalog and you can skip further steps
1. If the app catalog doesn't exist, you'll be prompted to create one.
1. From the list of options, choose **Automatically create a new app catalog site** and select **OK**.

**Deploy the app to the app catalog**

To deploy your application to the catalog:

1. In a web browser, go to the **SharePoint app catalog**
1. In the SharePoint app catalog, from the side navigation choose **Apps for SharePoint**
1. Upload/drag and drop the **spfx-company-announcements-webpart.sppkg** file into the list
1. SharePoint will ask you to confirm and deploy the package. It will make the package available to install in SharePoint sites.
   :::image type="content" source="../media/4-sharepoint-app-catalog-prompt.png" alt-text="SharePoint app catalog prompt to confirm deploying the uploaded solution package":::
1. Select **Deploy**

**Install the app in your Home site**

Once the app is successfully deployed in the app catalog, you'll need to install it on your Home site.

To install the app:

1. In a web browser, go to the **Home site**
1. From the top navigation, select the **Settings** (gear) icon
1. From the **SharePoint** section, select the **Add an app** link. You'll be taken to the **My Apps** page
1. In the search box on the page, type `Company` and locate the **spfx-company-announcements-webpart-client-side-solution** app
1. To install the app, select the **Add** button

The web part in the app will now be available to be added on all SharePoint pages in the site.

**Add the web part on a SharePoint page**

You can now add the `Company announcements` web part into any SharePoint page. To the web part in the home page of the Home site:

1. In a web browser, go to the **Home site**
1. To ensure that you're on the home page, from the top navigation choose **Home**
1. To edit the page, from the page menu, choose **Edit**
1. Choose an area inside the page where you'll place the web part
1. Select the **+** button to open the web part toolbox
1. Search for the `Company announcements` web part
1. Select the web part, which will then add the web part into the page
1. From the page menu, choose **Republish**

**Test the app in Viva Connections**

The **Company announcements** web part is now on the home page of your Home site. Let's now see how this web part looks in Viva Connections in Microsoft Teams

1. Open the **Microsoft Teams** desktop client or in a web browser navigate to [https://teams.microsoft.com](https://teams.microsoft.com).
1. Open the Viva connection app and you'll see the Home site's home page where the **Company announcements** web part displays all announcements.
   :::image type="content" source="../media/4-company-announcements-web-part-viva-connections-desktop.png" alt-text="Company announcements web part showing announcements in Viva Connections desktop":::
