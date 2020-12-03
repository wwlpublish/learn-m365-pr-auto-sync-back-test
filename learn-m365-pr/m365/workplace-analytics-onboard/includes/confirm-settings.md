After roles are assigned, the Workplace Analytics administrator must configure system defaults and privacy settings before the product can go live. 

The administrator can also set up additional partitions, manage access control, and configure data-export settings and manager settings. These additional settings can be completed anytime after Workplace Analytics is live.

## System defaults
1. **Time zone**, **Working days**, and **Working hours** are used to calculate employees’ collaboration hours within work hours and during after hours. The system defaults are applied only if settings are not already personalized in employees’ Outlook settings.
2. Workplace Analytics uses the **Hourly Rate** to calculate the cost of licensed employee time (for example, in “low-quality” meetings). This value can be customized at aggregate levels in the organizational data file, or a single number can be set by the Workplace Analytics admin as a default.
3. Workplace Analytics provides insights on how licensed employees collaborate with other employees within the company or with external individuals, using domain information. 

   The admin can use **Reclassify external domains** settings to treat external domains as internal collaborators. For example: If there are contractors or consultants that your company works closely with and you would like to treat those interactions as internal collaboration instead of as external collaboration, reclassify the consulting company’s domain as internal by using this setting. Note: The ability to reclassify settings becomes available only after the first Office 365 data extraction is complete.

>[!IMPORTANT]
>You can make changes to these system defaults any time. Changes made to these system defaults are applied after the next data refresh of your organizational data or Office 365 collaboration data. These changes apply to data retroactively and can affect previous calculations that use historical metrics.
>Screenshot of system defaults

## Privacy settings
1. The **minimum group size** suppresses *dashboard* results for groups that are smaller than the setting’s value (the smallest value permitted is five). This setting is applied to your application immediately and also applies retroactively.
2. If **hash subject lines** is set to **Yes**, subject lines will not be available in meeting-query results. This also disables the word-cloud feature in the Meeting Exclusion wizard. Again, this setting applies immediately and also retroactively.
3. **Processing exclusions** (**domains**, **email addresses**, **subject lines**):
   - Any activity that involves these excluded criteria is not processed or measured as part of your dataset. These settings reduce the amount of collaboration data that is processed from licensed employees and this results in a reduced dataset available for analysis.**

   **Example**: if sarah@contoso.com is excluded, any collaboration with this email address (either as the sender, receiver, or meeting attendee) will be excluded from being processed or measured. 

   These exclusions apply to new data processed during the next data refresh and do not affect historical data.

Confirmation of privacy settings (at the bottom of the page) is required before data processing begins.

Screenshot of privacy settings
 
## Example scenario 
You and Taylor hold a working session with the Workplace Analytics analysts to explore how the different Workplace Analytics settings will impact their analysis. For the system defaults, although the business unit they are analyzing is global in operations, they set the default time zone to that of their headquarters, which is located where the largest group of that business unit resides. The team also refines the hourly rate to $85 per hour, which HR informs them better reflects the fully loaded cost of Contoso's high-tech workforce.

For the privacy settings, the team applies the settings that were established by the business leaders and the privacy review. They exclude the external domain of Contoso's retained law firm because of the sensitivity of that communication and copy in the list of excluded terms that their General Counsel provided.