In this exercise, you'll build an Adaptive Card Extension (ACE) to display the latest important company announcement. You'll add the ACE to the dashboard so that it's displayed in the Viva Connections desktop and mobile experience.

## Create a new solution

To start, create a new solution using the SharePoint Framework Yeoman generator.

1. Create a folder for your project named **spfx-company-announcements-ace**
1. In a terminal, change the working directory to **spfx-company-announcements-ace**
1. Next, run the `yo @microsoft/sharepoint` command to start scaffolding a new solution
1. Answer generator's prompts:
   1. What is your solution name? **spfx-company-announcements-ace**
   1. Only SharePoint Online (latest) is supported. For earlier versions of SharePoint (2016 and 2019) please use the 1.12.1 version of the generator. **SharePoint Online only (latest)**
   1. Where do you want to place the files? **Use the current folder**
   1. Do you want to allow the tenant admin the choice of being able to deploy the solution to all sites immediately without running any feature deployment or adding apps in sites? **No**
   1. Will the components in the solution require permissions to access web APIs that are unique and not shared with other components in the tenant? **No**
   1. Which type of client-side component to create? **Adaptive Card Extension**
   1. Which template do you want to use? **Basic Card Template**
   1. What is your Adaptive Card Extension name? **Important announcements**
   1. What is your Web part description? **Shows important company announcements**
1. Wait for the project creation to complete. It may take a few minutes
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

## Edit the Adaptive Card Extension's code

After you added an Adaptive Card Extension to your solution, the next step is to implement its code so that it shows the latest important announcement.

**Load the latest announcement**

To start, extend the ACE's code to load the latest announcement from the **Announcements** list.

1. In the code editor, open your project
1. Open the **./src/adaptiveCardExtensions/importantAnnouncements/ImportantAnnouncementsAdaptiveCardExtension.ts** file
1. To the list of imports add `import { SPHttpClient } from '@microsoft/sp-http';`
1. Add an interface to define the shape of the announcement data

   ```typescript
   export interface IAnnouncement {
     title: string;
     url: string;
   }
   ```

1. Update the `IImportantAnnouncementsAdaptiveCardExtensionState` interface to store information about the retrieved announcement

   ```typescript
   export interface IImportantAnnouncementsAdaptiveCardExtensionState {
     announcement: IAnnouncement | undefined;
   }
   ```

1. Update the `onInit` method to set the initial state for the card and initialize loading announcements.

   ```typescript
   public onInit(): Promise<void> {
     this.state = {
       announcement: undefined
     };
   
     this.cardNavigator.register(CARD_VIEW_REGISTRY_ID, () => new CardView());
     this.quickViewNavigator.register(QUICK_VIEW_REGISTRY_ID, () => new QuickView());
   
     return this._fetchAnnouncements();
   }
   ```

1. Implement the `_fetchAnnouncements` method that loads the company announcements from the list.

   ```typescript
   private _fetchAnnouncements(): Promise<void> {
     return this.context.spHttpClient
       .get(`${this.context.pageContext.web.absoluteUrl}/_api/web/lists/getByTitle('Announcements')/items?$filter=Important eq 1&$select=Title,ID`,
         SPHttpClient.configurations.v1,
         {
           headers: {
             'accept': 'application/json;odata.metadata=none'
           }
         })
       .then(response => response.json())
       .then(announcements => {
         const announcement = announcements.value.pop();
         this.setState({
           announcement: {
             title: announcement.Title,
             url: `${this.context.pageContext.web.absoluteUrl}/lists/Announcements/DispForm.aspx?ID=${announcement.ID}`
           }
         });
       })
       .catch(error => console.error(error));
   }
   ```

   The method uses the `spHttpClient` to retrieve important announcements from the **Announcements** list. `spHttpClient` wraps the standard `fetch` API and is authenticated to call SharePoint APIs.
   In the API URL, you use the OData `$select` parameter to specify the list of properties to retrieve. These properties match the columns from the **Announcements** list. While calling the SharePoint API, you also set the `accept` header to suppress metadata in the response. It allows you to minimize the amount of data sent over the network.
   After the method retrieved the data, it gets the latest announcement and assigns it to be displayed by the ACE.
1. The last step is to change the card's icon to a warning triangle in the `iconProperty` getter:

   ```typescript
   protected get iconProperty(): string {
     return 'warning';
   }
   ```

**Show the announcement title on the card**

After you implemented the code to retrieve the latest important announcement from the list, the next step is to show it on the card.

1. In the code editor, open the **./src/adaptiveCardExtensions/importantAnnouncements/cardView/CardView.ts** file
1. In the `CardView` class, update the `data` getter, to assign the announcement's title to the card's primary text.

   ```typescript
   public get data(): IBasicCardParameters {
     return {
       primaryText: this.state.announcement.title
     };
   }
   ```

1. Next, update the `cardButtons` getter to point to the announcement's URL:

   ```typescript
   public get cardButtons(): [ICardButton] | [ICardButton, ICardButton] | undefined {
     return [
       {
         title: 'View',
         action: {
           type: 'ExternalLink',
           parameters: {
             target: this.state.announcement.url
           }
         }
       }
     ];
   }
   ```

1. Finally, update the `onCardSelection` event handler to also point to the announcement's URL:

   ```typescript
   public get onCardSelection(): IQuickViewCardAction | IExternalLinkCardAction | undefined {
     return {
       type: 'ExternalLink',
       parameters: {
         target: this.state.announcement.url
       }
     };
   }
   ```

   With these changes, the card will show a button to view the details of the announcement in the SharePoint list, but also selecting the card itself will open the announcement.

## Test the Adaptive Card Extension in the workbench

To test Adaptive Card Extensions in the workbench:

1. Open terminal and change the working directory to your project folder
1. Run the `gulp serve --nobrowser` command to start the local web server
   > [!WARNING]
   > If you see in the terminal the following warning:
   > :::image type="content" source="../media/4-terminal-serve-warning.png" alt-text="Screenshot of a terminal window showing a warning after running the gulp serve command":::
   >
   > _Warning - [spfx-serve] When serving in HTTPS mode, a PFX cert path or a cert path and a key path must be provided, or a dev certificate must be generated and trusted. If a SSL certificate isn't provided, a default, self-signed certificate will be used. Expect browser security warnings._
   >
   > it means that the local web server couldn't load your development certificate. To fix this issue, stop the web server by pressing `CTRL+C` and execute the `gulp trust-dev-cert` command.
1. In a web browser, go to the workbench at `<Home site url>/_layouts/workbench.aspx`. The Home site URL is where you've created the **Announcements** list in the previous exercise.
   > [!WARNING]
   > After you open the workbench, if you see the following error:
   > :::image type="content" source="../media/4-workbench-warning.png" alt-text="SharePoint workbench showing a warning message about being unable to load the local manifest":::
   >
   > _Your web part will not appear in the toolbox. Please make sure “gulp serve” is running in a web part project. Please refresh the page once “gulp serve” is running._
   >
   > it means that the local web server couldn't load your development certificate. To fix this issue, stop the web server by pressing `CTRL+C` and execute the `gulp trust-dev-cert` command.
1. To add the newly created Adaptive Card Extension to the canvas, select the **+** button to launch the toolbox.
   :::image type="content" source="../media/4-open-toolbox.png" alt-text="Red arrow pointing to the + button with web part toolbox open in the SharePoint workbench.":::
1. In the search bar, type `Important announcements` and select the Adaptive Card Extension.
   :::image type="content" source="../media/4-important-announcements-adaptive-card-extension-toolbox.png" alt-text="The Important announcements Adaptive Card Extension highlighted in the toolbox in SharePoint workbench.":::
1. From the workbench view options, choose **Preview** to exit the edit mode and interact with the Adaptive Card Extension
   :::image type="content" source="../media/4-workbench-preview.png" alt-text="Red arrow pointing to the Preview option in the SharePoint workbench.":::
1. When you select the card or the **View** button, you'll be redirected to the SharePoint list to see the announcement.
   :::image type="content" source="../media/4-flow-adaptive-card-extension-to-announcement-list.png" alt-text="Red arrow pointing from the Adaptive Card Extension to the announcement list item displayed in a web browser.":::
1. To stop testing, go to the terminal and press `CTRL+C` to stop the local web server.

After you verified that the newly added Adaptive Card Extension works as intended, you'll deploy it to Viva Connections.

## Deploy the Adaptive Card Extension to Viva Connections

You've built the `Important announcements` Adaptive Card Extension using the SharePoint Framework. Now let's deploy it to Viva Connections.

**Package the app**

To package the Adaptive Card Extension into an app using Gulp:

1. Go to the terminal where the working directory is the root folder of the project
1. To build the solution in release mode, run the `gulp bundle --ship` command
1. To make a release mode package of the solution, run the `gulp package-solution --ship` command
1. The `package-solution` task created an app package file named **spfx-company-announcements-ace.sppkg** in the **./sharepoint/solution** folder.

This file is your app package. Next, you'll deploy this package into the SharePoint app catalog, which contains all Viva Connections extensions.

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

**Deploy the app to SharePoint app catalog**

To deploy your application to the app catalog:

1. In a web browser, go to the **SharePoint app catalog**
1. In the SharePoint app catalog, from the side navigation choose **Apps for SharePoint**
1. Upload/drag and drop the **spfx-company-announcements-ace.sppkg** file into the list
1. SharePoint will ask you to confirm and deploy the package. It makes the package available to be installed in SharePoint sites.
   :::image type="content" source="../media/4-sharepoint-app-catalog-deploy-prompt.png" alt-text="SharePoint app catalog prompt to confirm deploying the uploaded solution package.":::
1. Select **Deploy**

**Install the app in your Home site**

Once the app is successfully deployed in the app catalog, you'll need to install it on your Home site.

To install the app:

1. In a web browser, go to the **Home site**
1. From the top navigation, select the **Settings** (gear) icon
1. From the **SharePoint** section, select the **Add an app** link. You'll be taken to the **My Apps** page
1. In the search box on the page, type `Company` and locate the **spfx-company-announcements-ace-client-side-solution** app
1. To install the app, select the **Add** button

The Adaptive Card Extension in the app will now be available to add to the dashboard.

## Preview the Adaptive Card Extension in Viva Connections

After you deployed the new solution package with Adaptive Card Extension, the last thing left is to test it in Viva Connections desktop.

**Add Adaptive Card Extension to the Viva Connections dashboard**

To add the Important announcements Adaptive Card Extension to Viva Connections dashboard:

1. In a web browser, go to the **Home site** in your Microsoft 365 tenant
1. From the site menu, select **Pages**
1. From the list of pages, select **Dashboard.aspx**
1. From the page menu, choose **Edit**
1. In the canvas, choose the **Add a card** button
   :::image type="content" source="../media/4-add-a-card.png" alt-text="Mouse pointer hovering over the Add a card button on the dashboard page.":::
1. In the search box, type `Important announcements` and from the list of search results, select the **Important announcements** Adaptive Card Extension
1. To save the changes to the dashboard, from the page menu choose **Republish**

**Preview Adaptive Card Extension in Viva Connections desktop**

After you added the Adaptive Card Extension to the dashboard, you can preview it in Viva Connections desktop.

1. Open Microsoft Teams desktop client or in a web browser navigate to [https://teams.microsoft.com](https://teams.microsoft.com)
1. From the left rail, choose the **Viva Connections** app
1. See the **Important announcements** Adaptive Card Extension visible in the dashboard
   :::image type="content" source="../media/4-viva-connections-dashboard-desktop.png" alt-text="The dashboard highlighted in the Viva Connections desktop experience.":::

**Preview Adaptive Card Extension in Viva Connections mobile**

After you added the Adaptive Card Extension to the dashboard, it's also visible in the Viva Connections mobile experience. To preview it:

1. On your mobile device, open the **Microsoft Teams** app
1. From the list of apps, choose the **Viva Connections** app
1. See the **Important announcements** Adaptive Card Extension visible in the dashboard
   :::image type="content" source="../media/4-viva-connections-dashboard-mobile.png" alt-text="Dashboard displayed in the Viva Connections mobile app.":::
