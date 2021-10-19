In this exercise, you will install the necessary tools to build Viva Connections extensions. Additionally, you'll create a SharePoint list with sample data that will be used in other exercises in this module.

> [!TIP]
> If you've completed these steps while following another module about Viva Connections extensibility, you can skip this unit.

## Install the SharePoint Framework Yeoman generator and its prerequisites

To build applications using the SharePoint Framework, you need to install the SharePoint Framework Yeoman generator. The generator scaffolds SharePoint Framework projects for you, giving you a starting point to build applications.

> [!IMPORTANT]
> If you've used SharePoint Framework before, verify that you have version 1.13 or newer of the SharePoint Framework Yeoman generator installed on your computer. SharePoint Framework supports extending Viva Connections starting from version 1.13. To verify the installed version, run `npm list --global --depth=0` in a terminal and check the version of the **@microsoft/generator-sharepoint** package. If it's lower than 1.13, uninstall it by running `npm uninstall --global @microsoft/generator-sharepoint`.

If you don't have the SharePoint Framework Yeoman Generator installed, or if you uninstalled it, follow these steps to set it up on your computer:

1. Open a terminal
1. Run the `node -v` command to verify that you have Node.js v14 installed. If you have a different version installed, uninstall it, and install v14.
1. In the terminal, execute `npm install --global yo gulp @microsoft/generator-sharepoint` to install the SharePoint Framework Yeoman generator along with Yeoman and Gulp, which are required to work with SharePoint Framework
1. Wait for the installation to complete

## Create a SharePoint list with sample data

In the following exercises in this learn module, you will build Viva Connections extensions that show announcements stored in a SharePoint list. The following steps show you how to create the list and add sample data to it.

**Create a new SharePoint list**

To start, go to the home site of your Microsoft 365 tenant and create a new SharePoint list.

1. In a web browser, navigate to the home site in your Microsoft 365 tenant
   > [!TIP]
   > To see which site is configured as the home site in your Microsoft 365 tenant, navigate to the **SharePoint admin center** and from the **Settings** menu, choose **Home site**.
1. On the home site, choose **New > List** from the top menu
1. From the types of lists to create, choose **Blank list**
1. In the Name field, enter `Announcements`
1. To create the list, choose **Create**

**Add the Description column**

Next, extend the newly created list with an extra column to store the announcements' contents.

1. From the list heading, choose **Add column > Multiple lines of text**
1. In the Name field, enter `Description`
1. To create the column, choose **Save**

**Add the Important column**

Extend the list with another column to track which announcements are important.

1. From the list heading, choose **Add column > Yes/No**
1. In the Name field, enter `Important`
1. In the **Default value** drop-down, change the value to **No**
1. To create the column, choose **Save**

Create a few test announcements using the **New** button in the list's toolbar. Mark one of them as important by selecting the **Important** column.
