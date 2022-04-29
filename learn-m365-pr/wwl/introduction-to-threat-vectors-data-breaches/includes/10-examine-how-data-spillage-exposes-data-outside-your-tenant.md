Data spillage is when a confidential document is released into an untrusted environment. When a data spillage incident is detected, it's important to quickly:

 -  assess the size and locations of the spillage.
 -  examine user activities around it.
 -  permanently purge the spilled data from the system.

Data spillage typically occurs when an employee unknowingly shares a highly confidential document with multiple people through email. if an event like this occurs, it's essential that you quickly assess who received this document internally and externally. Once identified, you should share case findings with other investigators to review, and then permanently remove the data from Microsoft 365. After the investigation is complete, you want to generate a report with the evidence of permanent removal and other case details for any future reference.

The following instructions describe how to manage a data spillage event. These steps permanently remove a message from Microsoft 365 so the message isn't accessible or recoverable.<br>

### Step 1 (Optional): Manage who can access the case and set compliance boundaries.

Depending on your organizational practice, you must control who can:

 -  Access the eDiscovery case used to investigate a data spillage incident.
 -  Set up compliance boundaries.

The easiest way to control who can access a case is to:

1.  Add investigators as members of an existing role group in the Microsoft Purview compliance portal.
2.  Add the role group as a member of the eDiscovery case.

**Additional reading**. For information about the built-in eDiscovery role groups and how to add members to an eDiscovery case, see [Assign eDiscovery permissions](/microsoft-365/compliance/assign-ediscovery-permissions?azure-portal=true).

You can also create a new role group that aligns with your organizational needs. For example, by completing the following steps, you can create a group of data spillage investigators in the organization to access and collaborate on all data spillage cases:

1.  Create a **Data Spillage Investigator** role group.
2.  Assign the appropriate roles (Export, RMS Decrypt, Review, Preview, Compliance Search, and Case Management).
3.  Add the data spillage investigators to the role group.
4.  Add the role group as a member of the data spillage eDiscovery case.

**Additional reading.** For more information, see [Set up compliance boundaries for eDiscovery investigations in Office 365](/microsoft-365/compliance/tagging-and-assessment-in-advanced-ediscovery?azure-portal=true).

### Step 2: Create an eDiscovery case.

An eDiscovery case provides an effective way to manage your data spillage investigation. By creating an eDiscovery case, you can:

 -  add members to the role group that you created in Step 1.
 -  add the role group as a member of new a eDiscovery case.
 -  conduct iterative searches to find the spilled data.
 -  export a report to share.
 -  track the status of the case.
 -  refer to the details of the case, if needed.

Consider establishing a naming convention for eDiscovery cases used for data spillage incidents. When creating a case, provide as much information as you can in the case name and description. This information enables you to locate and refer to the case in the future, if necessary.

### Step 3: Search for the spilled data.

Once you've created a case and managed access, you can use the case to iteratively search to find the spilled data and identify the mailboxes that contain the spilled data. You'll use the same search query that you used to find the email messages to delete those same messages in Step 7.

> [!IMPORTANT]
> The keywords that you use in the search query may contain the actual spilled data that you're searching for. For example, if you're searching for documents containing a social security number (SSN) and you use the SSN as the search keyword, you must delete the query afterwards to avoid further spillage (see step 8).<br>

### Step 4: Review and validate case findings.

After you create a content search, you must verify the search results only consist of the email messages that must be deleted. In a content search, you can preview a random sampling of 1,000 email messages without exporting the search results to avoid further data spillage.

If you've more than 1,000 mailboxes or more than 100 email messages per mailbox to review, you can divide the initial search into multiple searches. You can do so by using other keywords or conditions, such as date range or sender/recipient. The results of each search must then be reviewed individually. Make sure to document all search queries that were used for deleting messages in Step 7.

If a custodian or end user is assigned an Office 365 E5 license, you can examine up to 10,000 search results at once using Microsoft Purview eDiscovery (Premium). If there are more than 10,000 email messages to review, you can divide the search query by date range and review each result individually as search results are sorted by date. In Microsoft Purview eDiscovery (Premium), you can tag search results using the "Label as" feature in the preview panel and filter the search result by the tag you labeled. Tagging search results in this manner is helpful when you collaborate with a secondary reviewer. By using other analytics tools in Microsoft Purview eDiscovery (Premium), such as optical character recognition, email threading, and predictive coding, you can quickly process and review thousands of messages and tag them for further review.

When you find an email message that contains spilled data, check the recipients of the message to determine if it was shared externally. To further trace a message, you can collect sender information and date range so you can use the message trace logs. This process is described in Step 5.

After you verified the search results, you may want to share your findings with others for a secondary review. People who you assigned to the case in Step 1 can review the case content in both eDiscovery and Microsoft Purview eDiscovery (Premium) and approve case findings. You can also generate a report without exporting the actual content. You can use this same report as a proof of deletion, which is described in Step 8.

### Step 5: Use message trace log to check how spilled data was shared.<br>

To further investigate whether email with spilled data was shared, you can optionally query the message trace logs with the sender information and the date range information that you gathered in Step 4. The retention period for message trace is 30 days for real-time data and 90 days for historical data.

You can use Message trace in the Microsoft Purview compliance portal. For PowerShell enthusiasts, you can use the corresponding cmdlets in Exchange Online PowerShell. It's important to note that message tracing doesn't offer full guarantees on the completeness of data returned.

### Step 6: Prepare the mailboxes.

After you review and validate that the search results contain only the messages that must be deleted, you must collect a list of the email addresses of the affected mailboxes to use in Step 7 when you delete the spilled data.

You may also have to prepare the mailboxes before you can permanently delete email messages. Doing so depends on whether single item recovery is enabled on the mailboxes that contain the spilled data, or if any of those mailboxes are on hold.

### Step 7: Permanently delete the spilled data.<br>

At this point, you have collected and prepared mailbox locations in Step 6. You also created and refined a search query in Step 3 that found email messages containing spilled data. You can now use that information to permanently delete the spilled data.

As previously noted, you must satisfy one of the following requirements to delete messages:

 -  You must be a member of the Organization Management role group.
 -  You must be assigned the Search And Purge management role.<br>

### Step 8: Verify, provide a proof of deletion, and audit.<br>

The final step in the workflow to manage a data spillage incident is to verify the spilled data was permanently removed from the mailbox. This task can be accomplished by going to the eDiscovery case and rerunning the same search query that was used to delete that data. In doing so, you should confirm that no results are returned.

After you confirm the spilled data has been permanently removed, you can export a report and include it (along with the original report) as a proof of deletion. You're now ready to close the case, which will allow you to reopen it if you must refer to it in the future.

Once you close the case, you can also:

 -  revert mailboxes to their previous state.
 -  delete the search query used to find the spilled data.
 -  search for auditing records of tasks that were completed when managing the data spillage incident.
