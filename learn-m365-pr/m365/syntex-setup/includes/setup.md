You have decided to set up and activate SharePoint Syntex for the Human Resources department at Contoso, which has has several large libraries of documents and forms that have become harder and harder to locate. You begin setting up SharePoint Syntex by navigating to Contoso Electronics' Microsoft 365 admin center. You follow the steps listed below:

- Select **Setup**.
- Navigate to the **Files and content** section.  
- Select **Automate content and understanding**.
- Click **Get started**.

![A screenshot of the Automate content understanding page with Get started and the AI Builder credits highlighted for reference.](../media/automate-content-understanding.png)

> [!NOTE]
> Available AI Builder credits, if you have them, are listed under **At a glance** in the Automate content understanding section.

## Configure form processing

- On the **Configure form processing** page, you choose whether the users in Human Resources can create form processing models in their SharePoint document libraries.  
  - Enabling this feature puts a menu option on the document library ribbon called **Create a form processing model**. It must be enabled for _each_ SharePoint document library where Contoso Electronics' Human Resources staff want to create form processing models.
  - For **Which SharePoint libraries should show option to create a form processing model**, you have the following options:
    - **Libraries in all SharePoint sites** – this option makes form processing available in all SharePoint libraries.
    - **Libraries in selected SharePoint sites** – this option allows you to select which sites you want to use to create forms processing models. Accommodates up to 50 sites
    - **No SharePoint libraries** – used if you prefer not to create form processing models right away. This setting can be changes after setup is complete.

![A screenshot of the configure form processing page with Libraries in all SharePoint sites selected.](../media/configure-form-processing.png)

> [!NOTE]
> Removing a site after it has been included does not affect existing models applied to the libraries in that site or the ability to apply document understanding models to a library.

### Power Platform

If you have more than one Power Platform environment configured, you can pick which one you want to use for form processing. _This option does not appear if you have a single environment configured._

For **Power Platform**, you can select:

- **Use the default environment**.
- **Use a custom environment** to use a custom environment.

![A screenshot of the Power Platform environment window showing the options that exist if more than one Power Platform environment exists.](../media/powerplatform.png)

- Click **Next**.

## Create the content center

In this step, the _default_ content center is created. A content center is the model creation interface. It also contains information about which document libraries have published models applied to them.

- In the **Create a content center** page, you create a SharePoint content center site where users can create and manage document understanding models.
  - For **Site name**, type in the name of your _default_ content center.
  - The **Site address** shows the URL for the site, based on what was selected for the site name.
  - To change the name, click **Edit**.

![A screenshot of the Create a content center window with the Content center name box highlighted.](../media/create-content-center.png)

- Select **Next**.

> [!Important]
> A SharePoint admin can choose to create additional centers as needed. While a single content center may be fine for environments for which you want a roll-up of all model activity, you may want to have additional centers for multiple departments within your organization, which may have different needs and permission requirements for their models.

## Review and finish

- On the **Review and finish** page, look over the selected settings.
- Make any necessary changes.
- Select **Activate**.
- Click **Done** on the confirmation page.
- The form returns to the **Automate content understanding** page.
- Select **Manage** to make configuration changes if necessary.

## Assign licenses

Finally, you will assign licenses to everyone who will use any SharePoint Syntex features.

To assign licenses, return to the Microsoft 365 admin center.

- Under **Users**, click **Active users**.
- Choose the users to license.
- Select **Manage product licenses**.
- Choose **Apps** from the drop-down menu.
- Select **Show apps for SharePoint Syntex**.
  - Under **Apps**, select _all three_ license types: **Common Data Service for SharePoint Syntex**, **SharePoint Syntex**, and **SharePoint Syntex - SPO type**.

![A screenshot of the licensing window with all options selected.](../media/licenses.png)

- Click **Save changes**.

You have successfully set up and activated your first SharePoint Syntex environment. To create a content center dedicated to the Human Resources deparment, or when Contoso decides to rollout SharePoint Syntex to other departments, you'll need return to the SharePoint admin center to add more sites:

- Navigate to the **Active sites** page
- Click **Create**
- Select **Other options**
- Create a new content center following the same steps as the default content center.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4CPSF]

## Learn more

- [Create a content center](/microsoft-365/contentunderstanding/create-a-content-center)
