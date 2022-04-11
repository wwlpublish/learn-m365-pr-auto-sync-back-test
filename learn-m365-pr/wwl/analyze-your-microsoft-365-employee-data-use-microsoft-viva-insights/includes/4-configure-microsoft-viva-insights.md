Setting up workplace analytics in Microsoft Viva Insights is a straightforward process. Here's an overview of the primary steps:

1.  Your Microsoft 365 or Azure Active Directory admin assigns the licenses and roles.
2.  The designated Viva Insights admin sets up the system defaults and privacy settings.
3.  The Viva Insights admin then prepares and uploads the organizational data.
4.  Microsoft Viva Insights validates the upload and then processes the data.

After these steps are complete, your organization has full access to all service features. The only exceptions are for admin-only settings, such as for uploading HR data, and the privacy and system default settings.

Organizational data contains effective dates that map to the Microsoft 365 data. This data should be uploaded on a regular (monthly) schedule to reflect changes in your organization. The Microsoft 365 collaboration data updates weekly.

### Microsoft Viva Insights and data privacy

Microsoft Viva Insights resides within the Microsoft 365 trust boundaries. These boundareis are defined by organizations for privacy safeguards and protections of individual employees. By default, only metadata is processed for generating metrics that don't include personal information. Your organization has full control over how Viva Insights is used, deployed, and the visibility it has in your organization.

User-specific controls in Viva Insights include:

 -  Scope of population (with the option to exclude sensitive groups).
 -  Analyst (role-based) access to workplace analysis and to specific population scopes.
 -  Visibility to meeting subject lines.
 -  Exclusions set for all meetings and emails based on keywords (in subject lines) that you deem sensitive.
 -  Specific individuals or domains.
 -  Organizational attributes loaded.

The objective of Viva Insights isn't to examine individual activity. Rather, its goal is to recognize group-level trends occurring in an organization. It uses header level metadata and not content, such as body of emails or email attachments.

Viva Insights features default to non-personal information. It also includes a minimum aggregate threshold of five employees, which you can set higher if necessary.

### Roles and responsibilities for setting up Microsoft Viva Insights

Companies that are onboarding Microsoft Viva Insights will typically set up a working group that includes:

 -  an executive sponsor
 -  a project leader
 -  a proposed Microsoft Viva Insights admin
 -  analysts (such as from HR, IT, or a related People analytics team)
 -  the Microsoft 365 Enterprise Admin

This group will:

 -  Determine which employees are assigned Viva Insights licenses.
 -  Determine which team members are assigned roles in Viva Insights.
 -  Provide input to the Viva Insights admin on appropriate privacy and configuration settings.
 -  Identify necessary data fields to include in the org data file, based on the scope of analyses.

The following diagram shows how the Microsoft 365 Enterprise Admin assigns licenses and user roles (steps 1 and 2). The Microsoft Viva Insights admin confirms the workplace analytics settings and uploads the organizational data file (steps 3 and 4).

:::image type="content" source="../media/setup-onboarding-microsoft-viva-insights-de23c11f.png" alt-text="diagram shows Microsoft Viva Insights setup responsibilities for two roles, the Enterprise admin and the Microsoft Viva Insights admin":::


### Assign licenses

An organization's Microsoft 365 Enterprise Admin should work with the company's business leaders to determine which users to include in the analysis population. This group consistgs of the employees whose digital collaboration patterns the company wants to evaluate.

The enterprise admin can use Azure Active Directory or Windows PowerShell to assign users or group-based licenses. It's important to note that assigning a Viva Insights license to a mailbox doesn't change the employee's day-to-day experience.

### Assign Microsoft Viva Insights roles

The following user roles are required to implement Microsoft Viva Insights:

 -  **Microsoft 365 Enterprise Admin**. Assigns Viva Insights licenses to user mailboxes and an applicable Viva Insights role to these users. This role doesn't have access to the Viva Insights (unless they assign themselves an applicable role, such as an analyst role).
 -  **Viva Insights admin**. Sets system defaults and privacy settings for your company's Viva Insights environment. This role is also responsible for uploading and verifying the organizational (HR) data. This role can access Data sources, Leader and manager settings, and Analyst settings.
 -  **Viva Insights analyst**. Has full access to all Viva Insights features (except Upload in Data sources and other admin-only settings) and can directly query the full dataset. This role is typically assigned to analysts who need complete data access to perform their analyses.
 -  **Viva Insights analyst (limited)**. Has similar access as analysts with the following exceptions:
    
     -  No access to Query designer
     -  Read-only access to Analyst settings

To get started with Viva Insights, your Microsoft 365 Enterprise Admin must assign one or more users the roles of Viva Insights admin and analyst.

> [!NOTE]
> Only people with an assigned Viva Insights role can access and use the web app and its features.

### Microsoft Viva Insights settings

The Viva Insights admin must set up the System defaults and Privacy settings before their organization can start using the application. This admin can also assign the analyst role to other people in the organization. These analysts can help set up the applicable Analyst settings. They can also confirm whether the analysis population and collaboration data are accurate.

#### System defaults

The following system default settings apply to the employees who are included in the analysis population:

 -  **Default time zone, Working days, and Working hours**. These settings are used to calculate employees' collaboration hours within work hours and during after hours. The system defaults are applied only if the user hasn't previously personalized their settings in Outlook.
 -  **Hourly Rate.** This setting is used to calculate the cost of employee time (for example, the cost of time spent in "low-quality" meetings). You can customize this value at aggregate levels in the organizational data file, or the Viva Insights admin can set a single number as a default.
 -  **Reclassify external domains**. Viva Insights provides insights on how employees use domain information to collaborate with other employees in the company (not included in the analysis population) or with external individuals. The **Reclassify external domains** setting can be used to include external domains as internal collaborators.
    
    For example, if your company has contractors or consultants as part of their internal teams, you'll want to include interactions with those people as internal as compared to external collaboration in your analysis. You can reclassify the consulting company's domain as internal with this setting. This setting for reclassifying a domain will be available after the first Microsoft 365 data extraction.

> [!IMPORTANT]
> You can change the system default settings at any time. Changes are applied after the next data refresh of the organizational data or Microsoft 365 collaboration data. These changes apply to data retroactively and can affect previous calculations that use historical metrics.

#### Privacy settings

You can set the following privacy settings for the employees in the analysis population:

 -  **Minimum group size**. This setting suppresses data for groups that are smaller than the specified value (the smallest value permitted is five). This setting is applied to your application immediately and also applies retroactively.
 -  **Hash subject lines**. This setting determines whether subject lines are excluded from meeting-query results. This setting also has a word-cloud feature in the Meeting Exclusion wizard. Like minimum group size, this setting applies immediately and also retroactively.
 -  **Processing exclusions (domains, email addresses, and subject lines)**. Any activity that involves the excluded criteria isn't processed or measured as part of your data. These settings reduce the amount of collaboration data that's processed from employees. By doing so, it results in a reduced dataset available for analysis.
    
    For example, if you exclude sarah@contoso.com, any collaboration with this email address (either as the sender, receiver, or meeting attendee) won't be processed or measured.
    
    These exclusions apply to new data processed during the next data refresh and don't affect historical data.

### Example scenario - Configuring settings for Microsoft Viva Insights

Contoso's Enterprise Admin has created a project team responsible for deploying Microsoft Viva Insights. The project team has set up a meeting to explore how the different Viva Insights settings will affect analysis.

The project team wants to analyze a business unit that's global in operations. However, for the system defaults, the team decides to set the default time zone to Contoso's headquarters location. This location is where the largest group of employees in this business unit resides. The team also refines the hourly rate to $85 per hour, which HR says better reflects the fully loaded cost of Contoso's high-tech workforce.

For the privacy settings, the team applies the settings that were established by the business leaders and the privacy review. They also decide to exclude the external domain of Contoso's retained law firm. This exclusion is due to the sensitivity of the law firm's communications.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”