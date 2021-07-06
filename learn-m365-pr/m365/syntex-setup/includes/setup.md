You have decided to set up and activate SharePoint Syntex for a single department within the company. The Human Resources department has several large libraries of documents and forms. It has become harder and harder to find specific documents. You begin setting up SharePoint Syntex by navigating to Contoso Electronics' Microsoft 365 admin center. You follow the steps listed below:

- Select Setup.
- Navigate to the Files and content section.  
- Select Automate content and understanding.
- Click Get started.

> [!NOTE]
> Available AI Builder credits, if you have them, are listed under **At a glance**.

![A screenshot of the Automate content understanding page with Get started and the AI Builder credits highlighted for reference.](../media/automate-content-understanding.png)

## Configure form processing

- On the Configure Form Processing page, you choose whether the users in Human Resources can create form processing models in their SharePoint document libraries.  
  - Enabling this feature puts a menu option on the document library ribbon called Create a form processing model. It must be enabled for each SharePoint document library where Contoso Electronics' HR staff want to create form processing models.
  - Options for Which SharePoint libraries should show option to create a form processing model:
    - Libraries in all SharePoint sites – this option makes form processing available to all SharePoint libraries.
    - Libraries in selected SharePoint sites – this option allows you to select which sites you want to use to create forms processing models. Accommodates up to 50 sites
    - No SharePoint libraries – used if you prefer not to create form processing models right away. This setting can be changes after setup is complete.

![A screenshot of the configure form processing page with Libraries in all SharePoint sites selected.](../media/configure-form-processing.png)

> [!NOTE]
> Removing a site after it has been included does not affect existing models applied to the libraries in that site or the ability to apply document understanding models to a library.

### Power Platform

If your organization has more than one Power Platform environment configured, you can choose which one to use for form processing. The option does not appear if you have only one environment.

For Power Platform, you can select:

- Use the default environment.
- Use a custom environment to use a custom environment.  

Click Next.

## Create the content center

In this step, the Content Center is created. A content center is the model creation interface. It also contains information about which document libraries have published models applied to them.

A SharePoint admin can choose to create additional centers as needed. While a single content center may be fine for environments for which you want a roll-up of all model activity, you may want to have additional centers for multiple departments within your organization, which may have different needs and permission requirements for their models.

If you previously created a content center from the SharePoint admin center, that information will appear here, and you can click Next.

- In the Create Content Center page, you create a SharePoint content center site where users can create and manage document understanding models.
  - For Site name, the IT lead types in Content Center as the name of your content center site.
  - The Site address shows the URL for the site, based on what was selected for the site name.
  - To change the name, you click Edit.

![A screenshot of the Create a content center window with the Content center name box highlighted.](../media/create-content-center.png)

Select Next.

## Review and finish

- On the Review and finish page, look over the selected settings.
- Make any necessary changes.
- Select Activate.
- Click Done on the confirmation page.
- The form returns to the Automate content understanding page.
- Select Manage to make configuration changes if necessary.

## Assign licenses

Finally, you will assign licenses to everyone who will use any SharePoint Syntex features.

To assign licenses, return to the Microsoft 365 admin center.

- Under Users, click Active users.
- Choose the users to license.
- Select Manage product licenses.
- Choose Apps from the drop-down menu.
- Select Show apps for SharePoint Syntex.
  - Under Apps, select all three license types: Common Data Service for SharePoint Syntex, SharePoint Syntex, and SharePoint Syntex - SPO type.

![A screenshot of the licensing window with all options selected.](../media/licenses.png)

Click Save changes.

You have successfully set up and activated your first SharePoint Syntex environment in the Human Resources libraries.

Congratulations! You now know how to set up SharePoint Syntex. To add more sites, return to your M365 Admin Center.
