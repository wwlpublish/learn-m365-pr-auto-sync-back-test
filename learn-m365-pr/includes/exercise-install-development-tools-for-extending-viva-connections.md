In this exercise, you'll install the necessary tools to build Viva Connections extensions. You'll also create a SharePoint list with sample data that will be used in other exercises in this module.

> [!TIP]
> If you completed these steps while following another module about Viva Connections extensibility, you can skip this unit.

## Install the SharePoint Framework Yeoman generator and its prerequisites

To build applications by using the SharePoint Framework, you need to install the SharePoint Framework Yeoman generator. The generator scaffolds SharePoint Framework projects for you, giving you a starting point to build applications.

> [!IMPORTANT]
> If you've used the SharePoint Framework before, verify that you have version 1.13 or newer of the SharePoint Framework Yeoman generator installed on your computer. The SharePoint Framework supports extending Viva Connections starting from version 1.13. 
>
> To verify the installed version, run `npm list --global --depth=0` in a terminal and check the version of the **@microsoft/generator-sharepoint** package. If it's lower than 1.13, uninstall it by running `npm uninstall --global @microsoft/generator-sharepoint`.

If you don't have the SharePoint Framework Yeoman generator installed, or if you uninstalled it, follow these steps to set it up on your computer:

1. Open a terminal.
1. Run the `node -v` command to verify that you have Node.js v14 installed. If you have a different version installed, uninstall it, and then install v14.
1. In the terminal, run `npm install --global yo gulp @microsoft/generator-sharepoint`. This command installs the SharePoint Framework Yeoman generator along with Yeoman and Gulp, which are required to work with the SharePoint Framework.
1. Wait for the installation to finish.

## Create a SharePoint list with sample data

In the following exercises in this learn module, you'll build Viva Connections extensions that show announcements stored in a SharePoint list. The following procedures show you how to create the list and add sample data to it.

To create a new SharePoint list:

1. In a web browser, go to the home site in your Microsoft 365 tenant.
   
   > [!TIP]
   > To see which site is configured as the home site in your Microsoft 365 tenant, go to the SharePoint admin center. From the **Settings** menu, select **Home site**.
1. On the home site, select **New** > **List** from the top menu.
1. From the types of lists to create, select **Blank list**.
1. In the **Name** field, enter **Announcements**.
1. Select **Create**.

Next, extend the newly created list with an extra column to store the announcements' contents:

1. From the list heading, select **Add column** > **Multiple lines of text**.
1. In the **Name** field, enter **Description**.
1. Select **Save**.

Extend the list with another column to track which announcements are important:

1. From the list heading, select **Add column** > **Yes/No**.
1. In the **Name** field, enter **Important**.
1. In the **Default value** dropdown list, change the value to **No**.
1. Select **Save**.

Create a few test announcements by using the **New** button on the list's toolbar. Mark one of them as important by selecting the **Important** column.
