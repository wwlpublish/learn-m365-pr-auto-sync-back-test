In this exercise, you will build a SharePoint Framework application customizer that retrieves data from a SharePoint list and shows it in the Viva Connections desktop experience.

## Create a new solution

To start, create a new solution using the SharePoint Framework Yeoman generator.

1. Create a folder for your project named **spfx-company-announcements-appcustomizer**
1. In a terminal, change the working directory to **spfx-company-announcements-appcustomizer**
1. Next, run the `yo @microsoft/sharepoint` command to start scaffolding a new solution
1. Answer generator's prompts:
   1. What is your solution name? **spfx-company-announcements-appcustomizer**
   1. Only SharePoint Online (latest) is supported. For earlier versions of SharePoint (2016 and 2019) please use the 1.12.1 version of the generator. **SharePoint Online only (latest)**
   1. Where do you want to place the files? **Use the current folder**
   1. Do you want to allow the tenant admin the choice of being able to deploy the solution to all sites immediately without running any feature deployment or adding apps in sites? **No**
   1. Will the components in the solution require permissions to access web APIs that are unique and not shared with other components in the tenant? **No**
   1. Which type of client-side component to create? **Extension**
   1. Which type of client-side extension to create? **Application Customizer**
   1. What is your Web part name? **Important company announcements**
   1. What is your Web part description? **Shows important company announcements**
1. Wait for the project creation to complete. It may take a few minutes
   > [!TIP]
   > While creating the project, you will likely see some warnings. You can safely ignore them.
1. Run the `npm install @microsoft/sp-office-ui-fabric-core` command to install the Office UI Fabric package. You'll need it to style the application customizer.

## Install the development certificate

SharePoint Framework uses a workbench hosted in SharePoint Online to let you test your code before deploying it to Viva Connections. When you test your code, you start a local web server using Gulp. SharePoint Framework workbench then loads files from your local server and lets you test them. To let the workbench load files from your local dev server, you need to trust the development certificate provided by SharePoint Framework.

> [!IMPORTANT]
> You need to install the development certificate only once on your machine. When you create a new project, SharePoint Framework will use the previously installed certificate. If you've done this already, you can skip these steps.

1. Open a terminal
1. Change the working directory to your project folder
1. Run the `gulp trust-dev-cert` command
1. Follow the instructions on the screen to complete the installation of the certificate

## Edit the application customizer code

After you created the project, the next step is to extend the application customizer so that it loads important announcements from the list and shows them in the page's top placeholder.

1. Open the project in your code editor
1. In the code editor, open the **./src/extensions/importantCompanyAnnouncements/ ImportantCompanyAnnouncementsApplicationCustomizer.ts** file.
1. Extend the `@microsoft/sp-application-base` import statement to include `PlaceholderContent` and `PlaceholderName`:

   ```typescript
   import {
     BaseApplicationCustomizer,
     PlaceholderContent,
     PlaceholderName
   } from '@microsoft/sp-application-base';
   ```

1. Add `import { SPHttpClient } from '@microsoft/sp-http';`
1. In the `ImportantCompanyAnnouncementsApplicationCustomizer` class, add the private `_topPlaceholder` variable.

   ```typescript
   private _topPlaceholder: PlaceholderContent | undefined;
   ```

1. Extend the `onInit()` method with an event handler to render the placeholder.

   ```typescript
   @override
   public onInit(): Promise<void> {
     this.context.placeholderProvider.changedEvent.add(this, this._renderPlaceHolders);
   
     return Promise.resolve();
   }
   ```

1. Create a new `_renderPlaceHolders` private method with the following code:

   ```typescript
   private _renderPlaceHolders(): void {
     if (!this._topPlaceholder) {
       this._topPlaceholder = this.context.placeholderProvider.tryCreateContent(
         PlaceholderName.Top
       );
 
       if (!this._topPlaceholder) {
         console.error('The expected placeholder (Top) was not found.');
         return;
       }    
       this.context.spHttpClient
         .get(`${this.context.pageContext.web.absoluteUrl}/_api/web/lists/getByTitle('Announcements')/items?$filter=Important eq 1&$select=Title`,
           SPHttpClient.configurations.v1,
           {
             headers: {
               'accept': 'application/json;odata.metadata=none'
             }
           })
         .then(response => response.json())         
         .then(announcements => {          
            const announcementsHtml = announcements.value.map(announcement =>
              `<li>${announcement.Title}</li>`);              
            this._topPlaceholder.domElement.innerHTML=`<div class="${styles.app}">
              <ul>${announcementsHtml.join('')}</ul></div>`;
         }).catch(error => console.log(error));
     }
   }
   
   ```

   The above code will instantiate the placeholder. It will check if the placeholder is available or not and then retrieve important announcements from the **Announcements** list. Finally, it will render retrieved announcements in the placeholder's DOM element.
1. In the **/src/extensions/importantCompanyAnnouncements** folder, add a new file named **ImportantCompanyAnnouncementsApplicationCustomizer.module.scss** with the following contents:

   ```css
   @import '~@microsoft/sp-office-ui-fabric-core/dist/sass/SPFabricCore.scss';
   .app {
     background-color: $ms-color-themePrimary;
     color: $ms-color-white;
     display: flex;
     font-size: 1.5em;   
     justify-content: center;
   
     ul {
       list-style: none;    
     }
   }
   ```

   You start with importing Fluent UI to ensure consistent styling with Microsoft 365. Next, you add CSS classes needed to style the application customizer.
1. In the **ImportantCompanyAnnouncementsApplicationCustomizer.ts** file, add an import statement for the style file **ImportantCompanyAnnouncementsApplicationCustomizer.module.scss** you created, after the strings import at the top of the file:

   ```typescript
   import styles from './ImportantCompanyAnnouncementsApplicationCustomizer.module.scss';
   import * as strings from 'ImportantCompanyAnnouncementsApplicationCustomizerStrings';
   ```

## Test the application customizer on a page

To build and preview our important announcement application customizer:

1. In a terminal, run the `gulp serve --nobrowser` command. It starts a local webserver on `https://localhost:4321`.
   > [!WARNING]
   > If you see in the terminal the following warning:
   > :::image type="content" source="../media/4-terminal-serve-warning.png" alt-text="Screenshot of a terminal window showing a warning after running the gulp serve command":::
   >
   > _Warning - [spfx-serve] When serving in HTTPS mode, a PFX cert path or a cert path and a key path must be provided, or a dev certificate must be generated and trusted. If a SSL certificate isn't provided, a default, self-signed certificate will be used. Expect browser security warnings._
   >
   > it means that the local web server couldn't load your development certificate. To fix this issue, stop the web server by pressing `CTRL+C` and execute the `gulp trust-dev-cert` command.
1. In the code editor, open the **src/extensions/importantCompanyAnnouncements/ImportantCompanyAnnouncementsApplicationCustomizer.manifest.json** file and copy the **id** which you'll need to create the page debug URL to test the local version of the application customizer.
1. In a web browser, go to the page debug URL at `<Home site URL>/SitePages/home.aspx?debugManifestsFile=https://localhost:4321/temp/manifests.js&loadSPFX=true&customActions={"<id>":{"location":"ClientSideExtension.ApplicationCustomizer","properties":{ }}}`. Replace the `id` with the value you copied from the application customizer's manifest.
   > [!TIP]
   > The Home site URL is the URL of the SharePoint site where you have created the **Announcements** list in the previous exercise.
1. When prompted, select the **Load debug scripts** button to continue loading the application customizer.
   :::image type="content" source="../media/4-allow-debug-scripts-prompt.png" alt-text="SharePoint prompt to confirm loading debug scripts":::
   You'll now see important announcement on top of the page.
   :::image type="content" source="../media/4-application-customizer-sharepoint-page.png" alt-text="Custom application customizer showing company announcements displayed on a SharePoint page":::

To stop testing:

- To disable the page debug mode, navigate to `<Home site URL>/SitePages/home.aspx?reset=true`.
  > [!IMPORTANT]
  > If you don't disable the debug mode and only stop the local web server, the next time you navigate to the Home site, you will see an error stating that the page can't load manifests from the local web server. To fix that issue add `?reset=true` to the page URL, which will disable the debug mode.
- To stop the dev web server, go back to the terminal and press `CTRL+C`.

You have successfully built a SharePoint Framework application customizer. Now, let's deploy it to Viva Connections.

## Deploy the application customizer to Viva Connections

You've built the **Important announcements** application customizer using the SharePoint Framework. Now let's deploy it to Viva Connections.

## Package the app

To package the web part into an app using Gulp:

1. Go to a terminal where the working directory is the root folder of the project
1. To build the solution in release mode, run the `gulp bundle --ship` command
1. To make a release mode package of the solution, run the `gulp package-solution --ship` command. It will create the **./sharepoint/solution/spfx-company-announcements-appcustomizer.sppkg** app package file.

Next, you'll deploy this package into the SharePoint app catalog.

**Create an app catalog**

If you don't have an app catalog in your tenant, you'll need to create it before you continue this exercise.

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

To deploy your application to the app catalog:

1. In a web browser, go to the **SharePoint app catalog**
1. In the SharePoint app catalog, from the side navigation choose **Apps for SharePoint**
1. Upload/drag and drop the **spfx-company-announcements-appcustomizer.sppkg** file into the list
1. SharePoint will ask you to confirm and deploy the package. It will make the package available to install in SharePoint sites.
   :::image type="content" source="../media/4-deploy-package-prompt.png" alt-text="SharePoint app catalog prompt to confirm deploying the solution package":::
1. Select **Deploy**

**Install the app in your Home site**

Once the app is successfully deployed in the app catalog, you'll need to install it on your Home site.

To install the app:

1. In a web browser, go to the **Home site**
1. From the top navigation, select the **Settings** (gear) icon
1. From the **SharePoint** section, select the **Add an app** link. You'll be taken to the **My Apps** page
1. In the search box on the page, type `Company` and locate the **spfx-company-announcements-appcustomizer-client-side-solution** app
1. To install the app, select the **Add** button

The application customizer will now be visible on all SharePoint pages in the site.

**Test the app in Viva Connections**

The **Important company announcements** application customizer is now visible on pages in the Home site. Let's now see how it looks in Viva Connections.

1. Open the **Microsoft Teams** desktop client or in a web browser navigate to [https://teams.microsoft.com](https://teams.microsoft.com).
1. Open on the Viva Connections app and you'll see the Home site's home page with the **Important company announcements** banner displayed on top.
   :::image type="content" source="../media/4-application-customizer-viva-connections.png" alt-text="Custom banner showing important company announcements displayed on top of the page in Viva Connections desktop":::