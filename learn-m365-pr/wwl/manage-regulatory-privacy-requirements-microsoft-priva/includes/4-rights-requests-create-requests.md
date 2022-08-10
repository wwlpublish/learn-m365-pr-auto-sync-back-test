Users holding a role in the Subject Rights Request Administrators role group other than the view-only role can create a request. There are two ways you can create a request:

- From a [template](#quick-setup-use-a-template-with-default-settings), a quick "out-of-box" option that uses tailored default settings; or
- The [custom](#custom-setup-guided-process-to-choose-all-settings) option, which is a guided process to walk through all settings.

## Request types

Priva Subject Rights Requests supports three different types of requests:

1. **Access**: Provides a summary of the data subject’s personal information held by your organization in Microsoft 365.

2. **Export**: Provides a summary and an exported file of content items that contain the data subject’s personal information. These are the items reviewed and marked as **Included** during your review of the data collected by your search settings.

3. **Tagged list for follow up**: Generates a summary of any files that were tagged during data review that may require more action outside of Priva. For example, you may need to facilitate deletion of the data subject's personal information according to their request. You can view the included tags and set up custom tags for your organization in [Priva settings](priva-settings.md).

## Getting started with your first request

When you start a trial or subscription of Subject Rights Requests, we offer a simple, out-of-box setup for your first request that uses default settings. This setup can help you explore the subject rights request workflow and get familiar with its functionality.

The first time you arrive at the Subject Rights Requests page, you'll see a banner at the top with a **Get started** button. When a user selects this button, a flyout pane appears with that user's information pre-populated into the name and email fields, and shows all the default settings.

**Exploring request functionality with your information**: Trying out a subject rights request based on your own information can help you gain familiarity and comfort with moving through each stage of the process. You'll see what a default search will return, and can practice refining results by adjusting search settings. On the **Data collected** tab, you can review items in the preview area to the right and practice redacting text, applying tags, entering notes, and marking items to include or exclude for the final report (find details at [Review data for a subject rights request](subject-rights-requests-data-review.md)).

- You don't have to use your information to create your first request. If you're ready to start a request for a data subject, replace your name and email address with the data subject's information.

To accept all settings and create the request, select **Create**. The pane will close and you'll see your new request listed on your **Subject Rights Requests** page. To change any of the default settings before creating the request, select **Edit request details**, which puts you into the [subject rights request creation wizard](#custom-setup-guided-process-to-choose-all-settings).

> [!NOTE]
> Any request you create will count toward your trial or paid subscription allotment, regardless of which data subject's information is used for the request. The standard 30-day data retention period applies after the request is closed. Learn how to change [retention periods for subject rights requests](subject-rights-requests-reports.md#retention-periods-for-reports-and-data).

## Quick setup: Use a template with default settings

When creating a request directly from a template, the default settings are intended to help get you up and running quickly. The three templates correspond to the [three request types](#request-types): **Data access**, **Data export**, and **Data tagged for further action.**  You can view the default settings of a template and make changes during the request creation process.

##### Selecting the relationship

Each template allows you to select the type of relationship between the data subject and your organization, which in turn determines default settings. The points below explain how the relationship you choose affects search settings in templates:

- **Current employee**: Search results are tailored to avoid emails or Teams chats that the employee has participated in, or files that the employee authored. This setting streamlines search results, as current employees generally have access to content they authored or communication they participated in.

- **Former employee**: Search settings prioritize the former employee's mailbox (if available), and items authored by the employee. These settings aim to return content that former employees generated or participated in.

- **Customer**, **Prospective employee**, and **Other**: Search results for these relationships won't include content authored by the data subject, and will only include the most recent versions of SharePoint items (learn more at [advanced search options](#advanced-search-options)).

#### Steps for creating a request from a template

1. In the [Microsoft Purview compliance center](https://compliance.microsoft.com/), select **Priva Subject Rights Requests** in the left navigation.

2. In the top right corner of the screen, select **Create a request**.

3. Find the type of request you want to create—**Data access**, **Data export**, or **Data tagged for further action**— and select **Get started**. A flyout pane will appear.

4. At **Relationship to organization**, select the option that describes the [relationship](#selecting-the-relationship) between the data subject and your organization. If you select **Other**, an **Other relationship** text field appears in the flyout pane. Enter a term that makes sense for your organization; for example, "patient" or "student." 

5. If you want to review all the default settings and make changes to any of them, select the **View settings** button. The settings will appear on the flyout pane. To change any settings, select **Edit settings**, which takes you into the [guided process](#custom-setup-guided-process-to-choose-all-settings) outlined below.

6. Enter the data subject's details:
    - First and last name, and email address, are required fields. For current and former employees, typing the data subject's name into the **Search for a data subject** field will bring up a list of users to choose from. You can also select the link underneath that field to manually enter their name and email.
    - It's optional to enter the data subject's country of residence, the privacy regulation associated to their request, and a timeframe.
   
7. When you're done, select **Create**. You'll be taken back to your **Subject Rights Request** page with your new request listed at the top of the request list.

By default, your request is named with the data subject's name and type of request. To edit the request name, select the request from the list to open its details page and select the **Edit** command at the top of the screen. You'll arrive at the request creation wizard. Select **Next** until you advance to the **Request name** page, where you can edit the name and add a description.

None of the templates pause automatically at the data estimate stage. However, you can change this and other search settings by selecting **View Settings** on the template's flyout pane.

## Custom setup: Guided process to choose all settings

The custom request option is a guided process for creating a policy. You'll start by choosing a template, and then walk through each setting to customize your policy. The instructions below give details about basic settings that apply to each of the three policy types. Where the settings differ by policy type, we'll link to specific instructions.

Follow the steps below to create a request:

1. In the [Microsoft Purview compliance portal](https://compliance.microsoft.com/), select **Priva Subject Rights Requests** in the left navigation.

2. In the top right corner of the screen, select **Create a request**.

3. Under the **Custom** option, select **Get started**. You'll be taken into the request creation wizard.

4. On the **Data subject information** page, enter the data subject's first and last names and email address. Select **Add residency** to choose the data subject's country of residence. Select the option that identifies how the data subject is related to your organization. If you choose **Other**, enter a term to describe the relationship that makes sense for your organization; for example, "patient" or "student." Select **Next** to move to the next step.

5. On the **Locations** page, decide where you want to search for the data subject's information. Choose one or both of the following locations by moving the status toggle switch next to each option to the **On** position:

   - **Exchange**: look for data in Exchange mailboxes and in individual or group Teams chats. You can choose to search all Exchange accounts in your organization, or select **Choose accounts** to select individual users from the **Exchange mailboxes** flyout pane.

   - **SharePoint**: look for data in SharePoint sites, OneDrive for Business sites, and Teams channels. You can choose to search all SharePoint sites in your organization, or select **Choose sites** to select individual users from the **SharePoint sites** flyout pane.

6. On the **Define search settings** page, you can elect to make changes to the default search by choosing among various advanced search options. Here's where you can also choose to get an estimate first before data is automatically returned. If you choose any of these options, when you select **Next** you'll proceed to additional screens. Get details at **Define search settings** below. If you don't want to change your search, leave all options blank and select **Next** to advance to the next stage.

7. On the **Select the type of request** page, choose the request type: **Access**, **Export**, or **Tagged list for follow up**. Indicate whether the request pertains to a data privacy regulation. Review or make changes to completion deadline, which defaults to two weeks past the request creation date. Then select **Next**.

8. On the **Confirm or edit the name of this request** page, you can keep or edit the friendly name that's provided for the request, and enter an optional description. Then select **Next**.

9. On the **Review and finish** page, review the summary of what you've entered during the previous steps. Any field can be edited by selecting the **Edit link** in each section. When you're done, select **Create request**.

You'll see a confirmation screen once the request has been created. Select **Done** to return to the main Subject Rights Requests screen. The new request will be listed at the top of your list of requests. Select it from the list to start reviewing and working through the progress stages.

#### What happens after your request is created

We'll calculate an estimate of the amount of data it expects to find based on your search parameters begins immediately. Visit your request's details page in a few minutes to one hour to see the results of the estimate and whether the request has moved onto the next stage. Your request will automatically progress from **Data estimate** to **Data retrieval** except in the following circumstances:

 - If you selected to receive a data esimtae first in Step 5, **Define search settings**, you'll be able to view details about your search and make changes to your search before all the data is retrieved. You'll need to manually advance to the next stage of **Data retrieval** if you paused at **Data estimate**.
 
 - If you didn't choose to stop at data estimate, but we predict your search will yield a large volume of data, you'll see a message bar across the top of your request with a link to edit your search before proceeding to **Data retrieval**.

## Defining search settings

When you create a subject rights request, a default search will run based on your selections on the **Locations** page of the creation wizard. If you want to conduct a more targeted search, or if you want to choose to get an estimate of your data before content items are retrieved, you can make those selections on the **Search settings** page of the request creation wizard.

### Advanced search options

- **Refine your search**: This option allows you to specify extra properties to help identify the data subject among your organization's data. After choosing this option, you'll be prompted to add more search parameters, explained below in the **Refining your search** section.
- **Include content authored by the data subject**: This option will look for content that has been authored by the data subject. Examples include files created by, or uploaded to SharePoint by, the data subject. Selecting this option may significantly increase the amount of data returned.
- **Include all versions of items**: If you selected SharePoint as a search location, the default search query will return only the current version of SharePoint items. Checking this box will return the current and all previous versions of SharePoint items, yielding a significantly larger amount of data for you to review.

### Data estimate

The **Get an estimate first** option will present an estimate of how much data we expect to find before your data is automatically retrieved. When your estimate is displayed on the request's details page, you can choose to view the search results and preview a sampling of items that were discovered. If the items represent the expected results, you'll need to select **Retrieve data** in order to proceed with the actual retrieval of content items. 

## Refining your search

If you choose **Refine your search** on the **Search settings** page, or if you've paused at the **Data estimate** stage and choose to edit your search query, you'll be prompted to provide details for personal attributes and conditions to further target your search results. You can make additions in either or both categories. When you're done making selections in this section, the data retrieval for the request will be based on your search settings.

The details explained below are also what you'll be asked to provide if you've paused at the **Data estimate** stage and choose to edit your search query. 

#### Add personal attributes

Enter values in the text fields for the data subject's names, nicknames, email addresses, and address. You can add other identifiers such as birth date or phone number, and text fields support multiple entries separated by a semicolon. When you're done, select **Next** to continue to the **Conditions** page.

#### Conditions

Select the **Add condition** button to choose among a range of conditions to further target your search, including item name, sender and recipient names, personal data type, and whether the item was shared externally outside of your organization. The text fields support multiple entries separated by a semicolon. When you're done, select **Next** to save your search settings and progress to the request type setting.