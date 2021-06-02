Once auditing is turned on within an organization, a Microsoft 365 administrator or compliance officer can search for hundreds of individual types of events from multiple Microsoft 365 services. These searches can be conducted for the following reasons:

 -  Discover user and administrator activities.
 -  Find eDiscovery-related activities completed by administrators and compliance managers.

### Searching the audit log

Review the following steps to understand the procedure for searching the audit log.

1.  In the **Security &amp; Compliance Center**, in the left-hand navigation pane, select **Search**, and then select **Audit log search**.
2.  On the **Audit log search** window, configure the following search criteria (**Note**: Leave this page blank to return entries for all files, folders, and URLs in your organization):<br><br>:::image type="content" source="../media/audit-log-search-criteria-a2f04965.png" alt-text="screenshot of the Audit Log Search window":::
    
    
     -  **Activities**. Select the drop-down list to display the activities that you can search for. User and admin activities are organized into groups of related activities. You can select specific activities or select the activity group name to select all activities in the group. You can also select on a selected activity to clear the selection. After you run the search, only the audit log entries for the selected activities are displayed. Selecting **Show results for all activities** displays results for all activities completed by the selected user or group of users. Over 100 user and admin activities are logged in the Microsoft 365 audit log.
     -  **Start date** and **End date**. The last seven days are selected by default. Select a date and time range to display the events that occurred within that period. The date and time are presented in Coordinated Universal Time (UTC) format. The maximum date range that you can specify is 90 days. An error is displayed if the selected date range is greater than 90 days.
     -  **Users**. Select in this box and then select one or more users to display search results for. The audit log entries for the selected activity completed by the users you select in this box are displayed in the list of results. Leave this box blank to return entries for all users (and service accounts) in your organization.
     -  **File, folder, or site**. Type some or all of a file or folder name to search for activity related to the file or folder that contains the specified keyword. You can also specify a URL or part of a URL to display entries for activity on any object in the specified URL path. Special characters, such as forward slash (/), back slash (), dash (-), and underscore (\_), aren't supported in the search query. Be sure to replace special characters with a space.<br><br>For example, to search for activity by Patti Fernandez (alias: patti) in a OneDrive for Business site such as **`https://contoso-mysharepoint.com/personal/patti_contoso_onmicrosoft_com`**, you could type the following text in this search field: **personal patti contoso**.
3.  Select **Search** to run the search using your search criteria.
4.  The search results are loaded, and after a few moments they're displayed under **Results**.

    > [!NOTE]
    > A maximum of 5000 events will be displayed in increments of 150 events. If more than 5000 events meet the search criteria, only the most recent 5000 events are displayed.

### Tips for searching the audit log

Other considerations when searching the audit log include:

 -  Select specific activities to search for by clicking on the activity name. Or you can search for all activities in a group (such as **File and folder activities**) by clicking on the group name. If an activity is selected, you can select it to cancel the selection. You can also use the search box to display the activities that contain the keyword that you type.
 -  Select **Show results for all activities** in the **Activities** list to display events from the Exchange admin audit log. Events from this audit log display a cmdlet name (for example, **Set-Mailbox**) in the **Activity** column in the results.
 -  Select **Clear** to clear the current search criteria. The date range returns to the default of the last seven days. You can also select **Clear all to show results for all activities** to cancel all selected activities.
 -  If 5000 results are found, you can assume that more than 5000 events met the search criteria. You can either refine the search criteria and rerun the search to return fewer results, or you can export all the search results by selecting **Export results** &gt; **Download all results**.

### Viewing the search results

The results of an audit log search are displayed under **Results** on the **Audit log search** page.

:::image type="content" source="../media/audit-log-search-results-page-0a0339c5.png" alt-text="screenshot of the Results page from an audit log search":::


A maximum of 5000 (newest) events are displayed in increments of 150 events. To display more events, use the scroll bar in the **Results** pane or press **Shift + End** to display the next 150 events. The results contain the following information about each event returned by the search:

 -  **Date**. The date and time (in UTC format) when the event occurred.
 -  **IPaddress**. The IP address of the device that was used when the activity was logged. The IP address is displayed in either an IPv4 or IPv6 address format.
 -  **User**. The user (or service account) who completed the action that triggered the event.
 -  **Activity**. The activity completed by the user. This value corresponds to the activities that you selected in the **Activities** drop down list. For an event from the Exchange admin audit log, the value in this column is an Exchange cmdlet.
 -  **Item**. The object that was created or modified because of the corresponding activity. For example, the file that was viewed or modified or the user account that was updated. Not all activities have a value in this column.
 -  **Detail**. More information about an activity. Again, not all activities will have a value.

### Viewing the details for a specific event

You can view more details about an event by selecting the event record in the list of search results. A **Details** page is displayed that contains the detailed properties from the event record. The properties that are displayed depend on the Microsoft 365 service in which the event occurs. To display other details, select **More information.**

**Additional reading.** For more information on detailed properties descriptions, see [Detailed properties in the Office 365 audit log](https://support.office.com/article/detailed-properties-in-the-office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3?azure-portal=true).

### Working with your Microsoft 365 Audit log data in Azure Operations Management Suite (OMS)

Once you've added the Microsoft 365 management solution to your Azure OMS environment, you can monitor your Microsoft 365 environment in Log Analytics, which is part of Microsoft Azure's overall monitoring solution. Log Analytics is a web tool used to write and execute Azure Monitor log queries. These queries will help you monitor cloud and on-premises environments to maintain availability and performance.

**Additional reading.** For more information, see [Overview of log queries in Azure Monitor](/azure/azure-monitor/log-query/log-query-overview).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”