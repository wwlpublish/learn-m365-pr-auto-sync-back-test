In the following exercise, you'll enable Microsoft Viva Connections in your Microsoft 365 tenant.

To enable Viva Connections in your tenant, you'll need a SharePoint communication site with the global navigation enabled. You'll also need to enable this site as the home site in your tenant.

## Create a communication site

To start, go to the SharePoint admin center and create a new communication site.

> [!TIP]
> If you have an existing communication site that you want to use, you can skip these steps.

To go to the SharePoint admin center in your tenant:

1. In a web browser, go to the [Microsoft 365 admin center of your Microsoft 365 tenant](https://admin.microsoft.com) and sign in as an administrator.
1. From the side menu, select the **Show all** option.
1. From the list of admin centers, select **SharePoint**.

To create a new communication site:

1. In the SharePoint admin center, from the side menu, open the **Sites** section and select **Active sites**.
1. Select **Create**.
1. From the list of types of sites to create, select **Communication site**.
1. Provide the required information:
    1. **Site name**: Home site. (If the generated site address isn't available in your tenant, enter a different name.)
    1. **Site owner**: Your user account.
    1. **Select a language**: English for this module.
1. Select **Finish** to confirm your changes.

Wait for the site to be created. After it's created, you'll see it in the list of active sites. In the next section, you'll need the URL of the newly created site. To copy it, open the shortcut menu on the site's URL and select **Copy Link**.

## Configure the home site

The next step is to configure the newly created communication site as the home site in your tenant. Viva Connections will use this site to drive its experiences. This site will be opened as the default site when users go to the root of your Microsoft 365 tenant, such as https://contoso.sharepoint.com.

1. In the SharePoint admin center, from the menu, select **Settings**.
1. In the list of settings, select **Home site**.
1. In the **URL of site you want to use** box, paste the URL of the newly created communication site URL that you previously copied.
1. To confirm the changes, select **Save**.

## Enable global navigation

The last piece of configuration is to enable the global navigation. This procedure will allow you to show links to different resources from your Microsoft 365 tenant in Viva Connections.

1. In a web browser, go to the newly created communication site.
1. From the top bar, select the **Settings** (gear) icon.
1. On the **Settings** panel, select **Global navigation**.
1. Switch the **Enable global navigation** toggle to **On**.
1. To confirm the changes, select **Save**.

## Create the Viva Connections dashboard

An important part of Viva Connections is the dashboard, where employees can find useful resources and actionable tasks. This dashboard is driven by a special dashboard page that you create on the home site in your Microsoft 365 tenant.

To create the Viva Connection dashboard:

1. In a web browser, go to the home site that you configured previously.
1. From the suite bar, select the **Settings** (gear) button.
1. On the **Settings** panel, from the **SharePoint** section, select **Set up Viva Connections**.
1. On the **Set up Viva Connections** panel, select **Create Dashboard**.
1. On the dashboard page, select **Add a card**.
1. From the list of available cards, select **Web link**.

   :::image type="content" source="../media/3-add-card.png" alt-text="Screenshot that shows the Web link button in the web part toolbox.":::

   For now, let's leave the web link card as is. You'll use it to confirm that the Viva Connections dashboard is properly working on desktop and mobile.

1. To save your changes and publish the dashboard, from the toolbar, select **Publish**.

   :::image type="content" source="../media/3-publish-dashboard.png" alt-text="Screenshot that shows the Publish button on the Page menu in SharePoint.":::

By default, the dashboard is visible only in the Viva Connections mobile experience. To also show it in the desktop experience, you can edit the home page and add the dashboard web part:

1. In a web browser, go to the home site that you configured previously.
1. To ensure that you're on the home page of the site, on the top menu, select **Home**.

   :::image type="content" source="../media/3-site-menu-home.png" alt-text="Screenshot that shows the Home link on the SharePoint site navigation.":::

1. From the page's toolbar, select **Edit**.

   :::image type="content" source="../media/3-page-edit.png" alt-text="Screenshot that shows the Edit button on the page's toolbar.":::

1. In edit mode, select the **Add a new section** button. From the list of sections, select **Vertical section**.

   :::image type="content" source="../media/3-add-section.png" alt-text="Screenshot that shows the button for adding a vertical section in the section layout options.":::
   
   > [!TIP]
   > If you don't see the section, expand your browser window. SharePoint pages use responsive layout. If the browser window is too narrow, some elements on the page will be displayed differently.

1. To add the dashboard to the page, open the web part toolbox by using the **+** (plus) icon.
1. In the toolbox, to filter the list of available web parts, search for **dashboard**.`
1. From the list of web parts, select **Dashboard for Viva Connections**.

   :::image type="content" source="../media/3-dashboard-web-part.png" alt-text="Screenshot that shows the Dashboard for Viva Connections web part in the web part toolbox.":::

1. To save the changes, from the page's toolbar, select **Republish**.

   :::image type="content" source="../media/3-republish-home-page.png" alt-text="Screenshot that shows the Republish button on the page's toolbar.":::

## Install the Viva Connections Teams app

After you create and configure the home site in your Microsoft 365 tenant, you can enable Viva Connections. The following steps show you how to enable the Viva Connections desktop and mobile experience for all users in your tenant. Enabling the app for all users is a convenient way for you and your team to test your Viva Connections extensions in a shared Microsoft 365 tenant.

To enable the Viva Connections app in your tenant, go to the Microsoft Teams admin center:

1. In a web browser, go to the [Microsoft 365 admin center](https://admin.microsoft.com).
1. From the side menu, select the **Show all** option.
1. From the list of admin centers, select **Teams**.

Before you enable the Viva Connections app in your Microsoft 365 tenant, you can change its name and branding to match your organization's requirements. To customize the Viva Connection app:

1. From the side menu, expand the **Teams apps** section and select **Manage apps**.
1. In the list of apps, search for **Viva Connections**.

   :::image type="content" source="../media/3-teams-manage-apps.png" alt-text="Screenshot of the the Viva Connections app on the Teams Admin center screen for managing apps.":::

1. Select the **Viva Connections** app.
1. Next to the information about the app, select **Actions** > **Customize**.
1. Customize the app's information:
   1. **Short name:** Enter **Contoso**.
   1. **Short description:** Enter **Stay engaged with Contoso**.

   > [!NOTE]
   > Although you've just changed the display name of the Viva Connections app to *Contoso* to match your organization's branding, in this module we'll keep referring to the app as *Viva Connections*.

1. To confirm the changes, select **Apply**.
1. To confirm that you want to publish the changes to the app, select **Publish**.
1. Verify that the app status is set to **Allowed**. If it's not, select the **Allow** button.

   :::image type="content" source="../media/3-viva-connections-app-status.png" alt-text="Screenshot of the Viva Connections app summary in the Microsoft Teams admin center.":::

The easiest way to enable Viva Connections in your Microsoft 365 tenant is to install it for all users:

1. In the Teams admin center, from the side menu, expand the **Teams apps** section and select **Setup policies**.
1. From the list of policies, select **Global (Org-wide default)**.
1. In the **Installed apps** section, select **Add apps**.
1. On the **Add installed apps** pane, search for **Contoso**.
1. To select **Viva Connections**, select **Add**.
1. To confirm the installation, select **Add** at the bottom of the pane.

   :::image type="content" source="../media/3-installed-apps.png" alt-text="Screenshot that shows the Viva Connections app listed in the overview of installed Microsoft Teams apps.":::

Users can install many different apps in Microsoft Teams. To help them quickly access Viva Connections, you can add it to the list of pinned apps so it will appear on the menu bar in Microsoft Teams:

1. In the **Pinned apps** section, from the toolbar, select **Add apps**.
1. On the **Add pinned apps** pane, search for **Contoso**.
1. To choose the app, select **Add**.
1. To confirm pinning the app, select **Add** at the bottom of the pane.
1. In the list of pinned apps, select **Viva Connections**. From the toolbar, select **Move up** to move the app to the top of the list.

   :::image type="content" source="../media/3-pinned-apps.png" alt-text="Screenshot that shows the Viva Connections apps listed under pinned Microsoft Teams apps.":::

1. To confirm your changes, select **Save**.

Let's verify that Viva Connections desktop is correctly configured:

1. In a web browser, open [Microsoft Teams](https://teams.microsoft.com).
1. On the left rail, you should see the **Contoso** app pinned on top.
1. Open the **Contoso** app. You should see the home site open in Microsoft Teams.

   :::image type="content" source="../media/3-viva-connections-pinned.png" alt-text="Screenshot that shows the Viva Connections app pinned in Microsoft Teams.":::

   > [!TIP]
   > If you don't see the Contoso app pinned, it's likely because the changes that you just applied are still being propagated. You can try to refresh the changes by signing out from Microsoft Teams and signing in again. If you still don't see the Contoso app, wait a few hours for the changes to be applied.

To complete the configuration, let's verify that Viva Connections mobile is working correctly:

1. On your mobile device, open Microsoft Teams and sign in as a user in your Microsoft 365 tenant.
1. On the bottom, from the list of apps, select **Contoso**. You should see the Viva Connections dashboard that you configured previously.

   :::image type="content" source="../media/3-viva-connections-mobile.png" alt-text="Screenshot that shows the Viva Connections dashboard displayed on a mobile device.":::
