Being aware of employees’ rights is a key component to ensuring a successful program when using Workplace Analytics. It’s important to consider company policies and the ever-changing laws and regulations about employer-employee relationships, privacy, and personal data before using Workplace Analytics. Workplace Analytics doesn’t encode any specific policy. Instead, it provides controls that administrators can configure to make it consistent with applicable laws, regulations, and company policies. An organization can choose what data to use in Workplace Analytics, and who can see that data.

> [!IMPORTANT]
> Consult with your legal and HR teams before enabling Workplace Analytics for your organization.

### Data privacy within your organization<br>

Organizations decide who can see the data in Workplace Analytics. The Enterprise Administrator should ensure that primary users receive suitable training in data privacy, and in your company’s policies and other applicable subject areas, before being granted access to the data. The following levels of permission provide access to the data:

 -  **Analyst (Limited Access).** Has access to the Workplace Analytics Home page and can explore metrics features where minimum group size is enforced.
 -  **Analyst**. Has full access to all product features except the administrator features.
 -  **Administrator role**. Has access to administrator features only.
 -  **Program manager**. Has access to the Workplace Analytics Home page and lets the program managers explore metrics where the minimum group size is enforced. They also have access to Plans and its Manage and Track pages, where they can set up plans and track the progress of active or ended plans.
 -  **People managers**. Can receive access to Workplace Analytics through [Manager settings](/workplace-analytics/use/manager-settings). If they meet the minimum team size, they can see the Home page and explore metrics about their specific team. They also have access to Plans and its Manage and Track pages, where they can set up plans and track the progress of active or ended plans.

### Controlling your data<br>

An organization has full control over what data is used and how it’s used within Workplace Analytics. Workplace Analytics uses Microsoft 365 email and calendar metadata and external data defined by the organization (exported from an HR system) to compute how much time groups within the organization spend in meetings, emails, calls, and chats. It also tracks who the groups have been in contact with during these meetings, emails, calls, and chats.

Workplace Analytics processes data from two sources—organizational data from its own HR system and collaboration data from Microsoft 365. These data sets provide the organization's analysts with a unified pool of data to analyze.

 -  **Organizational data.** This data set is contextual information about your employees (for example: job title, level, location) and can come from Human Resources, Information Systems, or other line-of-business data stores. Workplace Analytics combines Microsoft 365 email, calendar, call, and instant message metadata with the organizational data that you choose to provide rich, actionable insights into your company’s communication and collaboration trends to help you make more effective business decisions.

    > [!CAUTION]
    > Other information provided in the organizational data set can be exposed in Workplace Analytics’ dashboards and reports. Organizations should ensure the data set doesn't include personal data (such as the employee ID). For more information about organizational data, see [Prepare organizational data](/workplace-analytics/setup/prepare-organizational-data)*.*

 -  **Collaboration data from Microsoft 365.** Microsoft 365 email, calendar, call, and instant message metadata provide the foundation for all Workplace Analytics analysis. As such, the first step is to determine which users you want to include in your analysis. When you select a user, you can specify or filter information by:<br>
    
     -  **Item.** Data derived from emails, meetings, calls, and chats.
     -  **Originator.** Data derived from a specific individual or group, such as a sender, an organizer, or a sender of an initial instant message.
     -  **Recipient.** Data derived from specific individuals who have received information, such as recipients of emails, invitees of meetings, invitees of calls, and chat recipients.
     -  **Subject.** Data derived from specific terms or group terms, such as email subject lines and meeting subject lines.
     -  **Chronology.** Data derived from a specific time, such as email sent time, Meetings scheduled time, Call duration, call joined time, scheduled call times, and instant message sent times.
     -  **Status.** Data derived from specific availability, such as Meeting attendee status or join status of calls.
     -  **Venue**. Data derived from specific locations, such as meeting locations.

    > [!IMPORTANT]
    > Attachments and text in the body of email and meetings are never used by Workplace Analytics. Rights-managed, confidential, and private email and meetings are excluded altogether.

### Privacy settings within Workplace Analytics<br>

The Workplace Analytics administrator should use **Privacy settings** to decide what data the organization wants to exclude from analysis and what data can be visible in Queries and Explore the statistics.

The privacy settings can be used to:

 -  **Set the minimum group size.** The minimum-group-size rule protects people from being identified in Workplace Analytics data, including in Insights, Explore the stats, and Plans. If you change this setting, your change takes effect immediately.
 -  **Hash subject lines.** Use this setting to control whether to show or hash subject lines in meeting query results, which, by default, aren't shown.
 -  **Exclude domains or email addresses.** Data can be excluded from specific domains. Data can also be excluded that includes specific email addresses.
 -  **Exclude terms from subject lines.** Subject lines are useful for analysts who want to set up meeting exclusion rules or to query meeting data. You can enter a list of specific keywords or terms that occur in the subject lines of emails and meetings that you want to exclude from analysis.

> [!NOTE]
> If an organization changes its privacy settings, the changes take effect after data is processed in the following week. As a result, the changes don’t affect data that's already been extracted.<br>

**Additional information.** For more information, see the following video on [Privacy in Workplace Analytics](https://player.vimeo.com/video/282897705?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”