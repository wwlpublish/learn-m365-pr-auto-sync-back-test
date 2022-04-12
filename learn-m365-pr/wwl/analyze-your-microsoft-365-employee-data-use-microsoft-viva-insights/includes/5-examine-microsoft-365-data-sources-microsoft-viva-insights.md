Microsoft Viva Insights includes a **Microsoft 365 data** page that organizations can use to confirm their Microsoft 365 data is up-to-date. Analysts can use this page to look for data ranges that have:

 -  Unexpected gaps in activity.
 -  Inconsistent or degraded data.
 -  Activity levels that are higher or lower than what might be considered normal for their organization.

:::image type="content" source="../media/microsoft-365-data-1e685813.png" alt-text="screenshot of the Microsoft 365 data page in Microsoft Viva Insights":::


This view includes the following Microsoft 365 data:

 -  **Measured employees**. The employees to whom your Viva Insights admin assigned licenses during setup. After license assignments, the Microsoft 365 data about meetings, email, unscheduled calls, and instant messages for measured employees is extracted by Viva Insights. When the data extraction process is successful for these employees, they're included in your measured population. If extraction errors occur and Viva Insights didn't get data for a person, that person is licensed but not counted as a measured employee in Viva Insights. If you're an analyst or limited analyst, measured employees are the population that you can analyze within Viva Insights. The number of measured employees can help determine whether you have good data coverage for analysis.

    > [!NOTE]
    > Your admin can assign employees Viva Insights licenses as a group with Azure Active Directory (Azure AD). If this number seems inaccurate, confirm with your admin that only active employees are assigned licenses through Azure AD.

 -  **Internal collaborators**. These people are unmeasured employees. They were included in extractions of Microsoft 365 data with whom the measured employees collaborated. These people are internal to your organization, but they aren't part of your measured population. Internal collaborators can include employees from other groups, vendors, or contractors that are working with your team. They must be included in the same internal domain as your team, but they're not in your measured population.
 -  **External collaborators**. These people are outside of your company or external to your email domain with whom your measured employees collaborated.
 -  **Average weekly collaboration chart**. This chart shows the last refreshed on weekly collaboration hours for measured employees by type, which can include hours spent on email, in meetings, in unscheduled calls, and on instant messages. The Last refreshed date shows when Microsoft 365 Exchange and Teams data was most recently processed for this chart.

Hover your cursor over the **Average weekly collaboration** chart data to get more details. You can also use the chart legend to change what data (meetings, email, instant messages, and calls) the chart shows.

:::image type="content" source="../media/measured-collaboration-4070d0c5.png" alt-text="diagram shows how the Global admin role includes all the service admin roles":::


### Origin of data counts

In **Sources > Microsoft 365 data**, you can see the current count of three categories of data. Most of this data originates with people in your organization, who may or may not have Microsoft Viva Insights licenses. However, some data originates outside of your organization or comes from mailboxes of other types.

Determining the origins of data also determines how to categorize it, as shown in the following flow chart.

:::image type="content" source="../media/data-sources-flowchart-a2c17acf.png" alt-text="flowchart that determines how to categorize Microsoft 365 data":::


The following **Average weekly collaboration** chart shows where each category of Microsoft 365 data appears.

:::image type="content" source="../media/three-categories-of-data-sources-789181f0.png" alt-text="diagram showing the three categories of Microsoft 365 data":::


### Possible causes of inconsistent data

Organizations can encounter instances of inconsistency in the volume of email, meetings, calls, and instant messages data. The following items are sources of typical data inconsistencies:

 -  **Major holidays**. Drops in email and meeting activity around major holidays are typical and can potentially affect analysis. You can remove these weeks from your outputs to reduce their impact.
 -  **Email archive policies**. Business policies can affect historical data processed during initial setup. For example, a steady decline or point-in-time drop-off in email and/or meeting activity may be due to archiving. By using the **Average weekly collaboration** chart (see the preceding illustration), you can select a date range to analyze your collaboration data where the mail volume is stable.
 -  **Recurring meetings**. When a recurring meeting series is removed from a calendar, all past instances of this meeting are removed. As a result, if you see a steady decline in meeting activity, it may be due to recurring meetings having been removed from calendars. By using the **Average weekly collaboration** chart (see the preceding illustration), you can select a date range to analyze your collaboration data where the meeting volume is stable.
