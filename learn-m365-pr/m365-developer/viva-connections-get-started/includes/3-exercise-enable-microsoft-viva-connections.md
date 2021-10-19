In the following exercise, you'll enable Microsoft Viva Connections in your Microsoft 365 tenant.

To enable Viva Connections in your tenant, you'll need a SharePoint Communication site with the global navigation enabled. You'll also need to enable this site as the Home site in your tenant.

## Create a communication site

To start, go to the SharePoint admin center and create a new communication site.

> [!TIP]
> If you have an existing communication site that you want to use, you can skip these steps.

**Go to the SharePoint admin center in your tenant**

1. In a web browser, navigate to the **Microsoft 365 admin center** of your Microsoft 365 tenant located at [https://admin.microsoft.com](https://admin.microsoft.com) and sign in as an administrator
1. From the side menu, select the **Show all** option
1. From the list of Admin centers, select **SharePoint**

**Create a new communication site**

1. In the **SharePoint admin center**, from the side menu, open the **Sites** section and choose **Active sites**
1. Choose the **Create** button
1. From the list of types of sites to create, choose **Communication site**
1. Provide the required information
    1. **Site name:** Home site (if the generated site address isn't available in your tenant, enter a different name)
    1. **Site owner:** your user account
    1. **Select a language:** English
1. Select the **Finish** button to confirm your changes

Wait for the site to be created. After it's created, you'll see it in the list of active sites. In the next step, you'll need the URL of the newly created site. To copy it, open the context menu on the site's URL and choose **Copy Link**.

## Configure the Home site

The next step is to configure the newly created communication site as the Home site in your tenant. Viva Connections will use this site to drive its experiences. Additionally, this site will be opened as the default site when users navigate to the root of your Microsoft 365 tenant, for example: https://contoso.sharepoint.com.

1. In the **SharePoint admin center**, from the menu, choose **Settings**
1. In the list of settings, select **Home site**
1. In the **URL of site you want to use** field, paste the URL of the newly created communication site you previously copied
1. To confirm the changes, choose the **Save** button

## Enable global navigation

The last piece of configuration is to enable the global navigation. This will allow you to show links to different resources from your Microsoft 365 tenant in Viva Connections.

1. In a web browser, navigate to the newly created communication site
1. From the top bar, select the **Settings** (gear) icon
1. In the **Settings** panel, select **Global navigation**
1. Switch the **Enable global navigation** toggle to **On**
1. To confirm the changes, choose the **Save** button

## Create Viva Connections dashboard

An important part of Viva Connections is the dashboard, where employees can find useful resources and actionable tasks. This dashboard is driven by a special dashboard page that you create in the Home site in your Microsoft 365 tenant.

**Create the Viva Connection dashboard**

The first step is to create a new dashboard. This dashboard will be used by the Viva Connections mobile experience.

1. In a web browser, navigate to the Home site that you've configured previously
1. From the suite bar, choose the **Settings** (gear) button
1. In the **Settings** panel, from the **SharePoint** section, choose **Set up Viva Connections**
1. In the **Set up Viva Connections** panel, choose the **Create Dashboard** button
1. On the dashboard page, choose **Add a card**
1. From the list of available cards, choose **Web link**
   :::image type="content" source="../media/3-add-card.png" alt-text="The Web link button highlighted in web part toolbox":::
   For now, let's leave the web link card as-is. You'll use it to confirm that the Viva Connections dashboard is properly working on desktop and mobile.
1. To save your changes and publish the dashboard, from the toolbar choose **Publish**
   :::image type="content" source="../media/3-publish-dashboard.png" alt-text="The Publish button highlighted in the Page menu in SharePoint":::

**Show the dashboard in Viva Connections desktop**

By default, the dashboard is visible only in the Viva Connections mobile experience. To show it in the desktop experience as well, you can edit the home page and add the dashboard web part.

1. In a web browser, navigate to the Home site that you've configured previously
1. To ensure that you're on the home page of the site, in the top navigation choose **Home**
   :::image type="content" source="../media/3-site-menu-home.png" alt-text="The Home link highlighted in the SharePoint site navigation":::
1. From the page toolbar, choose **Edit**
   :::image type="content" source="../media/3-page-edit.png" alt-text="The Edit button highlighted in page toolbar":::
1. In edit mode, choose the first **Add a new section button** and from the list of sections, select **Vertical section**
   :::image type="content" source="../media/3-add-section.png" alt-text="The Add vertical section button highlighted in the section layout option":::
   > [!TIP]
   > Tip: If you don't see the section, expand your browser window. SharePoint pages use responsive layout and if the browser window is too narrow, some elements on the page will be displayed differently.
1. To add the dashboard to the page, open the web part toolbox using the **+** (plus) icon
1. In the toolbox, to filter the list of available web parts, search for `dashboard`
1. From the list of web parts, select **Dashboard for Viva Connections**
   :::image type="content" source="../media/3-dashboard-web-part.png" alt-text="The Dashboard for Viva Connections web part highlighted in the web part toolbox":::
1. To save the changes, from the page toolbar choose **Republish**
   :::image type="content" source="../media/3-republish-home-page.png" alt-text="The Republish button highlighted in the page toolbar":::

## Install the Viva Connections Teams app

After you created and configured the Home site in your Microsoft 365 tenant, you can enable Viva Connections. The following steps show you how to enable Viva Connections desktop and mobile experience for all users in your tenant. Enabling the app for all users is a convenient way for you and your team to test your Viva Connections extensions in a shared Microsoft 365 tenant.

Viva Connections is a Microsoft Teams app provided by Microsoft that you can customize to your needs. You can change its logo, display name, and description to match your organization's branding requirements.

**Go to the Microsoft Teams admin center in your Microsoft 365 tenant**

To enable the Viva Connections app on your tenant, go to the Microsoft Teams admin center:

1. In a web browser, navigate to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com)
1. From the side menu, select the **Show all** option
1. From the list of Admin centers, select **Teams**

**Customize the Viva Connections app**

Before you enable the Viva Connections app in your Microsoft 365 tenant, you can change its name and branding to match your organization's requirements. To customize the Viva Connection app:

1. From the side navigation, expand the **Teams apps** section, and select **Manage apps**
1. In the list of apps, search for `Viva Connections`
   :::image type="content" source="../media/3-teams-manage-apps.png" alt-text="Screenshot of the Teams Admin center manage apps screen with the Viva Connections app highlighted":::
1. Select the **Viva Connections** app
1. Next to the information about the app, select **Actions > Customize**
1. Customize the app's information:
   1. **Short name:** Contoso
   1. **Short description:** Stay engaged with Contoso
   > [!NOTE]
   > While you've just changed the display name of the Viva Connections app to *Contoso* to match your organization's branding, in this module we'll keep referring to the app as *Viva Connections*.
1. To confirm the changes, choose **Apply**
1. To confirm that you want to publish the changes to the app, choose **Publish**
1. Verify that the app status is set to **Allowed**. If it's not, select the **Allow** button
   :::image type="content" source="../media/3-viva-connections-app-status.png" alt-text="Screenshot of the Viva Connections app summary in Microsoft Teams admin center":::

**Install Viva Connections for all users**

The easiest way to enable Viva Connections in your Microsoft 365 tenant is to install it for all users.

1. In the Teams admin center, from the side navigation, expand the **Teams apps** section and select **Setup policies**
1. From the list of policies, choose **Global (Org-wide default)**
1. In the **Installed apps** section, choose **Add apps**
1. In the **Add installed apps** pane, search for `Contoso`
1. To select **Viva Connections**, choose **Add**
1. To confirm the installation, choose **Add** at the bottom of the pane
   :::image type="content" source="../media/3-installed-apps.png" alt-text="The Viva Connections app listed in the overview of installed Microsoft Teams apps":::

**Pin Viva Connections**

Users can install many different apps in Microsoft Teams. To help them quickly access Viva Connections, you can add it to the list of pinned apps so it will appear in the navigation bar in Microsoft Teams.

1. In the **Pinned apps** section, from the toolbar choose **Add apps**
1. In the **Add pinned apps** pane, search for `Contoso`
1. To select the app, choose **Add**
1. To confirm pinning the app, choose **Add** at the bottom of the pane
1. In the list of pinned apps, select **Viva Connections**, and from the toolbar choose **Move up** to move the app to the top of the list
   :::image type="content" source="../media/3-pinned-apps.png" alt-text="The Viva Connections apps listed under pinned Microsoft Teams apps":::
1. To confirm your changes, choose **Save**

**Preview Viva Connections desktop**

Let's verify that Viva Connections desktop is correctly configured.

1. In a web browser, to open Microsoft Teams navigate to [https://teams.microsoft.com](https://teams.microsoft.com)
1. In the left rail, you should see the **Contoso** app pinned on top
1. Open the **Contoso** app. You should see the Home site open in Microsoft Teams
   :::image type="content" source="../media/3-viva-connections-pinned.png" alt-text="Viva Connections app pinned in Microsoft Teams":::
   > [!TIP]
   > If you don't see the Contoso app pinned, it's likely because the changes you've just applied are still being propagated. You can try to refresh the changes by signing out from Microsoft Teams and signing in again. If you still won't see the Contoso app, wait a few hours for the changes to be applied.

**Preview Viva Connections mobile**

To complete the configuration, let's verify that Viva Connections mobile is working correctly.

1. On your mobile device, open Microsoft Teams and sign in as a user in your Microsoft 365 tenant
1. On the bottom, from the list of apps, choose **Contoso**. You should see the Viva Connections dashboard that you've configured previously.
   :::image type="content" source="../media/3-viva-connections-mobile.png" alt-text="Viva Connections dashboard displayed on a mobile device":::
