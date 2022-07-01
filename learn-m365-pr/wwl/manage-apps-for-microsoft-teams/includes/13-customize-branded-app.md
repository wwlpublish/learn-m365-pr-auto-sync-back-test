Microsoft Teams lets admins customize Teams app to enhance store experience and adhere to their organization's branding. An app developer needs to allow their app to be customized by a Teams admin. 

As a Teams admin you can use **Manage apps** page in Teams admin center, customize an app to include a specific look and feel according to your organization needs. The details you can customize are:

* Short name
* Short description
* Full description
* Privacy policy URL
* Website URL
* Terms of use URL
* App icon
* Outline color of the icon
* Accent color

## Customize details of an app

You can customize an app to include a specific look and feel according to your organization needs. 

1. Sign in to the Teams admin center.

1. Expand **Teams apps** and select **Manage apps**.

1. Check the **Customizable** column of the apps list and sort by apps that are customizable.

    :::image type="content" source="../media/customizable-apps-in-tac.png" alt-text=" Screenshot of customizable app on Manage apps page.":::

4. Open **Customize** pane by the following options:

    * From the **Manage apps** page, select next to the app that you want to customize, and then select **Customize**.

        :::image type="content" source="../media/customize-app.png" alt-text=" Screenshot of customizing app.":::

    * Go to the app details page by selecting the app name and then **Customizable**.
        
        :::image type="content" source="../media/customizable-app.png" alt-text=" Screenshot of customizable from app details page.":::

    * Go to the app details page by selecting the app name, and select  **... > Actions** drop-down menu then select **Customize**.

        :::image type="content" source="../media/customize-app-actions.png" alt-text=" Screenshot of actions drop down menu.":::


5. Customize the visible fields that the developer allowed as customizable, including:

    * **Details** 
        * Short name
        * Short description
        * Full description
        * Website
        * Privacy policy URL
        * Terms of use URL

    * **Icons**
        * Color icon: 192 x 192 pixel in PNG format
        * Outline icon: 32x32 pixel in PNG format
        * Accent color 

    :::image type="content" source="../media/customize-app-pane.png" alt-text="Screenshot of customize app details page.":::


6.	After customizing the app, select Apply.

7.	Select Publish to publish the customized app.

The customized app is now listed in your Manage apps page. You'll have only one version of the app, since customizing the app features doesn't create a copy of the app.

There are several important points:

-   When you customize apps, and any description related to an app, ensure that you follow any customization guidelines if provided by the app publisher in their documentation or terms of use.
-   You are responsible to ensure that links to terms of use or privacy policy are valid.
-   In case the app publisher no longer allows a field to be customizable, a message appears on the app details page notifying the admin about the fields that can't be customized any longer.
-   Changes to the branding may require up to 24 hours to propagate to all the users.
-   It is recommended to test app customization changes in a Teams test tenant before making these changes in your production environment.
-   The app usage report in Teams admin center displays the original name of the app that is provided by the publisher.
-   The Microsoft Graph permission consent dialog displays the original name of the app that is provided by the publisher. It helps you to accurately identify an app while providing permissions to it.

## Review app details

To see the app details and review the information

1.  Sign in to the Teams admin center.
2.  Expand **Teams apps** and select **Manage apps**.
3.  Select the app name.
4.  View the app details, including the original app name **Short name from publisher**.

    The **Short name from publisher** field is only visible if you've changed the app's short name.

    :::image type="content" source="../media/custom-app-detail.png" alt-text="Screenshot of reset app details to default values.":::

## Reset app details to default values

You can reset the app details to the original values provided by the app developer only if you have customized it.

1.  In Teams admin center, access **Teams Apps** \> **Manage apps**.
2.  Select the app name.
3.  Select Reset to default from the Actions menu.

    :::image type="content" source="../media/reset-app.png" alt-text="Screenshot of reset app details to default values.":::


