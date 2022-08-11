After completing your data review for a subject rights request, the next stage is to generate the reports necessary to fulfill the request. Priva will create reports and collect the files marked as **Include** during the data review process. Selected files from these data packages can be submitted to your data subject to complete their request.

## Understanding reports

After you select **Complete review** in the **Review data** stage of the subject rights request, the final reports for the request will start generating automatically. On the **Reports** tab of the subject rights requests details page, the **Status** column indicates when report generation is **In progress** and when a report is **Ready to download**. It can take up to 30 minutes to finish creating the reports.

Reports are divided into two sections:
* **Reports for the data subject**: These reports contain information that can be returned to the data subject as part of request fulfillment. This is where you'll find the **data package** containing files for you to send to the data subject.
* **Reports for internal use**: These reports are for your organization's internal records related to the subject rights request. They include an audit log and a list of all the files you applied tags to during the data review in order to follow up or take further action on.

## Data package

:::image type="content" source="../media/get-report-priva-rights-request.png" alt-text="Screenshot showing creating a report from a Subject Rights Request." lightbox="../media/get-report-priva-rights-request.png":::

The subject rights request data package contains items marked as **Include** during the data review stage of the process. The data package is generated as a zip file. When it's ready for download, select the report's row on the **Reports** tab of the subject rights request details page. A flyout panel will open with a button to **Download** the report. The **What do do next** instructions on the flyout panel provide a quick reference for how to work with the contents.

When you're ready to download the data package, select **Download**, find your download, and then open the downloaded zip file.

### Contents of the data package

The data package zip file contains the following items:

- A folder named **Azure**: This folder contains the key materials for your data subject. See the detailed explanation below.
- Files outside of the **Azure** folder: these may include two spreadsheets named **Results** and **Summary**. These files outside of the Azure folder are provided for reference and should be used primarily by your organization's administrators.

When Priva identifies and retrieves files for a subject rights request, the files it exports in this process are renamed using unique identifiers to help protect personal data. You can cross-reference the unique names with the original file names using the **Export_load_file.csv** file. Because the original file names may include sensitive information, you should follow your policies that apply to such information.

> [!NOTE]
> We recommend reviewing the contents of this folder carefully and submitting only the necessary files to your data subject. You should evaluate your response to make sure it's tailored to meet the requirements of applicable law.

### Azure folder contents

Open the **Azure** folder, then open the **AEDExport.zip** file, which contains another file folder with a long name comprised of numbers and letters. Open the folder with the long name to reveal the contents described below:

- **Extracted_text_files** folder: Contains text extracted from the native files (where supported).
- **NativeFiles** folder: Contains all the items marked during data review as **Included**, in their native file format. Each item in this folder is given a unique file name to protect personal data. You can cross-reference these unique names with their original file name using the Export_load_file.csv file, explained below.
  - Files that were redacted using the **Annotate** function during the data review process are in the **NativeFiles** folder and have the suffix "_burn.pdf".
- **Export_load_file.csv** file: Contains the original file names so you can cross-reference them with the unique file names provided in the NativeFiles folder.
- **Summary** text file: Provides a summary of the types of files in the data package, the number of files and their size.

#### What to do with the folder contents

Open the **Azure** folder and the zip files as explained above. Your next task is to review the items, determine what to send to the data subject, and modify zip file contents if necessary.

For example, for an export request where the data subject wants to receive a copy of all the items containing their personal data held by the organization, you'll want to closely review items in the **NativeFiles** folder and remove any item you don't want to send back to the data subject.

For an access request where the data subject wants to receive a summary of all their personal information held by the organization, you'll want to focus on the **Summary** text file.

Modify the zip file to remove any content you don't want to include in the final package. Once complete, send the zip file in a secure manner to the data subject who made the subject rights request.

## Audit log

The audit log is a CSV file providing a record of the progression of stages for each subject rights request. It lists each stage of the process along with the date and time completed, and the user name of the individual who completed the step.

## Tagged files reports

The reports labeled as **Files tagged as...** are CSV files which list the content items to which tags were applied during the data review process. Tags are used to flag content items for further attention or action by the organization. Learn more about [settings for tags](/privacy/priva/priva-settings#data-review-tags).

## Retention periods for reports and data

Reports generated by Subject Rights Requests and associated data, such as annotated files saved in Azure, are stored for a specified length of time. The default retention period is 30 days from the date on which a subject rights request is closed.

The data retention period is defined in Priva **Settings** and applies to all subject rights requests. To view or change your data retention period, follow the steps below:

1. From anywhere in Priva Subject Rights Requests, select **Settings** (the gear icon) in the top right corner of your screen.
2. Select **Data retention periods** on the left navigation.
3. From the **Data collected and reports** dropdown menu, select either 30 days or 90 days as the retention period.
4. Select **Save** to save your settings.

Be sure to verify that your chosen data retention periods comply with your organization's policies and legal obligations.

## Close the request

When you've performed all the necessary actions related to the subject rights request, mark the request as closed by selecting **Close the request** in the upper right of the request details page. A closed request means it's no longer active and indicates that no further work is needed in order to fulfill the data subject's original request to your organization.

Closed requests can't be re-opened, but you can return to the request to view request details and notes. Reports for the request are retained according to the established [retention period](#retention-periods-for-reports-and-data).