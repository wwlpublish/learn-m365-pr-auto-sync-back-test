Organizations must address the following requirements before they can begin setting up Workplace Analytics:

 -  **Microsoft 365 tenant requirements.** Workplace Analytics requires a Microsoft 365 tenant with Exchange Online. Mailboxes must have [Exchange Online Plan 1 or Plan 2 licenses assigned](https://products.office.com/exchange/compare-microsoft-exchange-online-plans?azure-portal=true). Workplace Analytics currently supports multi-tenant and vNext environments. Each mailbox that you want to license must have its data stored in Exchange Online.
 -  **Workplace Analytics licenses.** Workplace Analytics is licensed as an add-on to existing Microsoft 365 subscriptions and doesn't change the end-user experience in Microsoft 365. Workplace Analytics licenses are applied to the mailboxes that you want to analyze, which can be all the employees in your organization or a specific subset. The population of employees that you license are referred to in Workplace Analytics as measured employees.
 -  **Supported browsers.** Workplace Analytics works with the latest or immediately previous versions of Microsoft Edge and Internet Explorer, Google Chrome, Apple Safari, and Mozilla Firefox.

Once the preliminary requirements have been addressed, Workplace Analytics can be configured by completing the steps outlined in the following sections.

### Step 1 - Determine key personas and roles for implementation

The metrics of this step include:

 -  **Owner.** The Workplace Analytics sponsor, who's the initial point-person for the engagement.
 -  **Task.** Identify people in the organization to participate in setting up Workplace Analytics.
 -  **Outcome.** A list of people in your organization with key roles identified.

Use the following personas to identify the people who will help gather data, make decisions, and complete the tasks required to set up Workplace Analytics:

 -  Workplace Analytics sponsor (the initial point person for the engagement).
 -  Workplace Analytics administrator role, which has access to Admin and Data Sources features, and will set system defaults, privacy settings, and upload and verify organizational data.
 -  Microsoft 365 Global administrator.
 -  Exchange administrator.
 -  Human resources (HR) information system administrator.
 -  Line of business (LOB) system administrators, or data analyst.

### Step 2 - Assign licenses to population in scope for analysis

The metrics of this step include:

 -  **Owner.** The Workplace Analytics sponsor, Workplace Analytics administrator, Microsoft 365 Global administrator, and Exchange administrator.
 -  **Task.** Determine population in scope for analysis and assign licenses through Microsoft 365.
 -  **Outcome.** Microsoft 365 licenses are assigned for the population that will be analyzed.

The Workplace Analytics sponsor will work with the Workplace Analytics administrator and Microsoft 365 Global administrator to identify the population (the people in your company) whose Microsoft 365 collaboration activity you'll analyze. These people are referred to as measured employees within Workplace Analytics. Employees in your organization that aren't licensed for analysis but may have meeting and email collaboration with measured employees are called other internal collaborators.

Some organizations will analyze the entire population, while others will use subpopulations for specific analysis scenarios and sections of the organization. Once you've identified the population in scope, the Microsoft 365 Global administrator will assign Workplace Analytics licenses to users in this population.

If an organization hasn't fully migrated to Microsoft 365 Exchange Online, it may come across mailboxes that are hosted using Exchange on-premises. The Microsoft 365 Global administrator or Exchange administrator can help to determine if the organization will experience this scenario and assist with the following options:

 -  Options for mailboxes hosted using Exchange on-premises.
 -  Migrate these mailboxes to Microsoft 365 Exchange Online.
 -  Contact the FastTrack team to understand the process for analyzing these mailboxes (this step requires other work streams within your organization).

### Step 3 - Assign roles to Workplace Analytics admins and analysts

The metrics of this step include:

 -  **Owner.** The Microsoft 365 Global administrator.
 -  **Task.** Assign users for administrators and data analysts to Workplace Analytics service.
 -  **Outcome.** Workplace Analytics roles are assigned so that administrators can use Workplace Analytics to set system defaults, privacy settings, and upload and verify organizational data. And, data analysts can log into and use Workplace Analytics once data is provisioned.

Assigning users to the Workplace Analytics service enables administrators to set system defaults and privacy settings, upload and verify organizational data, and enable data analysts to use Workplace Analytics.

Workplace Analytics roles and their corresponding level of access include:

 -  **Analyst.** Has full access to all service features except Admin. This role is used for the analyst who requires the most complete access to the data.
 -  **Analyst (Limited Access).** Has access to the Home and Explore the metrics pages, and to flexible queries. This role is used for the analyst who only needs access to insights generated from our curated set of Explore-the-metrics dashboards.
 -  **Administrator.** Has access to the Administrator and Data-sources features. The Workplace Analytics administrator has responsibilities to configure privacy settings and system defaults and to prepare, upload, and verify organizational data.
 -  **Program manager.** Has access to the Home and Explore the metrics pages. They also have access to the Solutions tab and its Manage page, on which they can set up programs, and to its Track page, on which they can track the progress of active or ended programs.

### Step 4 - Configure Workplace Analytics settings

The metrics of this step include:

 -  **Owner.** The Workplace Analytics administrator.
 -  **Task.** Provide default time zone values the system will use in metric calculations if the data isn't available for a measured employee or other internal collaborator.
 -  **Outcome.** Default time zone values are defined in Workplace Analytics.

#### Time zone

The default time zone is used to compute after-hours metrics when a time zone has not been configured by the user or provided as part of the organizational data. The default time zone is typically the time zone of the corporate headquarters or the time zone in which most employees are located. If a measured employee or other internal collaborator doesn't have a time zone defined as part of the organizational data, the metric will be computed using the default time zone.

The default time zone for Workplace Analytics is Pacific Standard Time. For a complete list of valid times zones, see Time zones in Workplace Analytics.

Complete the following steps to change the default time zone:

1.  On the **Settings** page, select **Settings**.
2.  Under **System defaults**, select the time zone you want from the **Default time zone** list.
3.  Select **Save**.

#### Working days and working hours

Users can set their own working days and working hours in their [Outlook settings](https://outlook.office.com/owa/?path=/options/calendarappearance?azure-portal=true). While there's no option to upload working days or working hours in organizational data, a Workplace Analysis administrator can set default working days and working hours for the organization on the System defaults area of the Settings page.

These admin-configured default settings are used for a particular user only if the user hasn't already configured their working days and hours.

#### Privacy settings

 -  **Owner.** Workplace Analytics sponsor, Workplace Analytics administrator.
 -  **Task.** Use company-specific legal and privacy guidelines to define settings to use in Workplace Analytics.
 -  **Outcome.** Privacy settings are defined in Workplace Analytics and you've confirmed that you're ready to provision the service using these rules.

Being aware of employees’ rights is a key component to ensuring a successful program using Workplace Analytics. Before using Workplace Analytics, it's important to consider ever-changing laws and regulations concerning employer-employee relationships, privacy, personal data, and company policies.

Workplace Analytics doesn't encode any specific policy. Instead, it provides controls that administrators can use to configure the product to be consistent with applicable laws, regulations, and company policies. Organizations choose what data they want to use in Workplace Analytics.

Once an organization has examined its privacy needs, it will use the **Settings** area in Workplace Analytics to define the following privacy settings for its data:

 -  Detail display
    
     -  Minimum Aggregation Size. Set the minimum group size required to display data in Explore Metrics. By default, the minimum group size is set to five.
     -  Decide to show or hide subject lines in meeting reports.
 -  User data exclusion:
    
     -  Exclude emails/meetings to, or from, specific users, or all users from a domain using “;” as the delimiter.
     -  Exclude emails/meetings with specific terms in the subject line using “;” as the delimiter. Terms can be any combination of letters, numbers and special characters, such as client attorney privilege and D&amp;I.

Complete the following steps to set privacy settings:

1.  On the **Settings** page, select **Settings**.
2.  Under **Privacy settings**, configure the settings to meet your company's needs.
3.  Select **Save**.
4.  To begin the processing of Office 365 data, select **I confirm that all privacy settings are complete**, and then select **Save**.

### Step 5 - Prepare and upload organizational data

The metrics of this step include:

 -  **Owner.** The Workplace Analytics administrator, HR information system administrator, LOB system administrators, or data analyst.
 -  **Task.** Obtain organizational data needed for analysis from other information systems.
 -  **Outcome.** CSV file of organizational data is generated and uploaded to Workplace Analytics for final provisioning.

Organizational data is the information about employees that a company provides to use in Workplace Analytics. Workplace Analytics combines organizational data with Microsoft 365 to provide rich, actionable insights into a company’s communication and collaboration trends to help it make more effective business decisions.

#### What is organizational data?

 -  Individual-level metadata that provides descriptive information of a company’s employees.
 -  Sourced from multiple sources:
    
     -  Human Resources Information Systems (HRIS) Ex: Workday, PeopleSoft
     -  Payroll Systems
     -  Employee Surveys (Engagement, Manager Feedback, Culture)
     -  Performance Management Systems or Quota Attainment Systems
     -  CRM Systems
 -  Workplace Analytics organizational data is structured as a flat file with each row representing one person with columns representing attribute fields.

#### How is it used?

 -  Provides context for the mailboxes that enables Workplace Analytics to calculate metrics based on the relationship of the Org Data attributes.
 -  Enables the user to filter and group data in meaningful ways and generate custom metrics.

#### How often should it be refreshed?

To account for organization changes, it's recommended that data be refreshed monthly. When loading an organization's data the first time, Workplace Analytics loads 13 months of data. Ideally, an organization would load 13 dated rows of organizational data would for each employee.

#### Who should be included in the org data file?

 -  Human Resource Data:
    
     -  It's recommended that HR data be collected for all employees in the company, even if they're not part of the measured population.
     -  At a minimum, an organization must have data for all employees in its measured population.
 -  Line of Business Data:
    
     -  An organization should have line-of-business data for all employees of interest in the scenario it's analyzing.

#### What are common pitfalls to avoid?

 -  Too many or too few unique values.
 -  Redundant values.
 -  Attributes that only exist for a subset of your employees.
 -  Dirty data.

#### Preparing organizational data for upload to Workplace Analytics

Complete the following steps to start working with organizational data:

1.  **Identify trends that you want to analyze.** An organization should decide what trends it wants to learn about to improve workplace efficiency. Based on this information, it can better choose what organizational data to use.
2.  **Know what data to include.** A few data attributes are required, and many are optional. Among the optional ones, an organization should choose those attributes that best serve its analytical purposes.
3.  **Get an export of organizational data.** An organization should have an admin export the HR data from the HR system. Line-of-business data should be included if the organization's analysis requires it.
4.  **Structure the organizational data.** For data to validate successfully, it must be structured correctly in the.csv file that's uploaded.
5.  **Upload the data to Workplace Analytics.** After the .csv file is ready, upload it to Workplace Analytics where, after validation and processing, it becomes available for analysis.

Once the .csv file has been created, the Workplace Analytics administrator can upload it into the service. Once the upload has been submitted successfully, the data must be further validated and processed to complete provisioning. Microsoft 365 meeting and email data is refreshed monthly. If any problems arise, the Workplace Analytics team will contact the Workplace Analytics administrator.<br>

Once the provisioning of data is complete, Workplace Analytics users can access full product features. The Workplace Analytics administrator can also generate and upload updated organizational data.

**Additional reading.** For more information, see the following links on preparing organizational data for upload to Workplace Analytics:

 -  [Data sources in Workplace Analytics](/workplace-analytics/use/data-sourcesv2).
 -  [Prepare organizational data](/workplace-analytics/setup/prepare-organizational-data).
 -  [Upload organizational data](/workplace-analytics/setup/upload-organizational-data).<br>

### Step 6 - Validate and verify data

The metrics of this step include:

 -  **Owner.** The Workplace Analytics administrator, or data analysts with full access.
 -  **Task.** Set meeting exclusion rules to reflect the company's meeting norms and exclude meetings that aren't relevant for analysis.
 -  **Outcome.** Workplace Analytics administrators and analysts are satisfied that meeting query results are focused on the data relevant for analysis.

Workplace Analytics uses activities stored in a person’s Microsoft 365 email and calendar to reveal internal and external collaboration trends. However, a person’s calendar and email can contain a diverse set of activities (such as personal meetings, work-related social activities, all-day training meetings, and so forth) that aren't relevant to work-related collaboration, and if included in the metrics, can skew query results.

Analysts can use the Meeting exclusions feature to create custom meeting exclusions that help ensure query results accurately represent relevant meeting norms within their company. Or, analysts may choose to use the default meeting exclusions that exclude a set of meetings that would commonly fall outside relevant collaboration for analysis.

### Step 7 - Set up meeting exclusions

The metrics of this step include:

 -  **Owner.** The Workplace Analytics administrator, or data analysts with full access.
 -  **Task.** Set meeting exclusion rules to reflect your company's meeting norms and exclude meetings that aren't relevant for analysis.
 -  **Outcome.** Workplace Analytics administrators and analysts are satisfied that meeting query results are focused on the data relevant for analysis.

Workplace Analytics uses activities stored in a person’s Microsoft 365 email and calendar to reveal internal and external collaboration trends. However, a person’s calendar and email can contain a diverse set of activities (such as personal meetings, work-related social activities, all-day training meetings, and so forth) that aren't relevant to work-related collaboration, and if included in the metrics, can skew query results.

Analysts can use the Meeting exclusions feature to create custom meeting exclusions that help ensure query results accurately represent relevant meeting norms within their company. Or, analysts may choose to use the default meeting exclusions that exclude a set of meetings that would commonly fall outside relevant collaboration for analysis.
