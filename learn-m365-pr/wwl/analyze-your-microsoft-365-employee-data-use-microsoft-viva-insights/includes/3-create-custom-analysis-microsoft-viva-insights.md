The prior unit examined how business outcomes and associated insights can be analyzed on the Microsoft Viva Insight's **Home** page. Organizations also use Viva Insights to create custom analytical queries. The main features that support custom analysis are:

 -  Query designer
 -  Peer analysis
 -  Plans
 -  Data sources
 -  Exclusions

The following sections examine how organizations can use these features to customize their workplace analysis.

### Query designer

When building your own custom queries, you can select from a list of predefined templates with preselected filters and metrics. These templates provide a great starting point for specific types of analysis. At the same time, they give you the flexibility to add new metrics and customize them, as needed.

Most of the templates are designed for Power BI. They typically include a download option to set up automatically refreshed reports in Power BI through an OData link. Setting up predefined templates can vary depending on what's required for its Power BI dashboard. Select the template you'd like to use in Power BI dashboards to view more details about setup and how to use the template in Power BI.

:::image type="content" source="../media/query-designer-d92aaa52.png" alt-text="screenshot of the Query Designer page" lightbox="../media/query-designer-d92aaa52.png":::


Queries in the **Query designer** tool provide access to row-level data and customizable metrics. You can import the row-level data into other analysis tools to create custom analyses, models, and dashboards. Queries report the same underlying data, but the type of query determines the structure of the output. The most common query types include:

 -  **Person query**. Extracts person metrics for analysis of aggregated employee data. Each observation in a Person query represents a person, their measured collaboration, and their descriptive attributes.
 -  **Meeting query**. Extracts meeting-related metrics for analysis of aggregated meeting data. Each observation in a Meeting query represents a meeting, its attributes, and the total collaboration associated with the meeting attendees.

You should complete the following steps to create a query using the Query Designer tool:

1.  Open the **Query designer**.
2.  Select **Get started** under **Query**, and then select the query type.
3.  Select **Start a new query**, and then select **Set up query.**
4.  Enter a name and description for the query.
5.  Select the **Group by** timeframe (day, week, or month), the applicable **Time period**, and if you want the query to **Auto-refresh**.
6.  In **Exclusions**, select the meeting and attendee exclusions to exclude any irrelevant calendar activity from this analysis.
7.  In **Select metrics**, select what metrics you want to include from the list. You can also customize one or more metrics by using filters. For example, filter for meeting hours with the word "budgeting" in the subject line.
8.  In **Select filters**, you can change the scope of the data you'd like to analyze. You can do so by limiting it to active employees and applying other filters to organizational attributes.
9.  In **Organizational data**, select which organizational attributes to include in your output, and then select **Run** to run the query.
10. In **Query designer &gt; Results**, you can select to view only your results (My results) or all query results. Select the **Download** icon to download a query's results as a .csv file or to copy the OData link for loading the data into other business intelligence apps (such as Power BI). For queries that show the **Visualization** icon, you can also visualize the results directly from this page.

#### Business process analysis

In the Query Designer tool, the Business process analysis feature can help organizations identify business processes that have quietly grown beyond their intended scope. This view provides greater visibility into how these processes affect your business. It also helps you identify opportunities to improve efficiency.

To analyze a business process:

1.  **Define a dataset** that only analyzes the data that's relevant, such as organizationally and geographically.
2.  **Define a business process** to analyze within the dataset that you defined in the preceding step.
3.  **Analyze a business process** through a query where you select the business process as a parameter.

Each of these steps is outlined in greater detail in the following sections.

#### Define a dataset

Before you can analyze a business process, you must first create a dataset for it. The Query designer can create a query that includes only the organizational data required for this analysis.

For example, the following steps define a query for meetings of a particular length that were attended by at least one sales representative.

1.  Open **Business process analysis**.
2.  Select **Data sets**, and then select **Add data set**.
3.  In **New data set**, enter a name (for example, Sales data) and a description, and then select **Continue**.
4.  For **Time period**, select the start and end dates. For example, all meetings that occurred outside of a specific time period can be excluded from the dataset.
5.  For **Meeting exclusions**, specify a meeting exclusion rule or accept the default.
6.  For **Which meetings do you want to include in your query results**, define the filters to scope the dataset for the analysis. For example, to filter out specific meetings, select **Add filter**, and then select **Meeting** with a **Duration** of less than or equal to one hour. This Duration filter can be used to specify the duration that you want to analyze. If you don't define this filter, then all meeting hours will be included regardless of their duration.
7.  Select **Attendee**, and then select the group (such as Sales) for the meeting attendees.
8.  Select **Organize**r, and then select the group (such as Sales) for the meeting organizer.
9.  Select **Submit** to create the dataset that matches these criteria (and no other data). The process time for the dataset varies depending on its size.

#### Define a business process

Before you can analyze a business process, you must first define it. A business process is defined by assembling a list of keywords that's typically found in the dataset that's associated with the process. An example of such a dataset would be meeting subject lines. This list defines the business-process filter.

> [!NOTE]
> Currently, you can only use English keywords for defining a business process, even when your instance of Microsoft Viva Insights is in a language other than English.

1.  Open **Business process analysis**.
2.  Select A**dd business process**.
3.  In N**ew Business process**, enter a name and an optional description for it, such as Sales interactions, and then select **Continue**.
4.  In **Data set,** select what to use for this analysis.
5.  For **Content type**, keep **Meetings** selected, and then select **Continue**.
6.  In **Enter a search term**, enter a keyword that represents a common term about this business process. The system then uses this keyword to display related words found in the dataset.
7.  Optionally, you can sort the keyword columns by selecting a header in the table, such as Rank. The Rank column indicates relevance ranking.
8.  Scan the words in the **Keyword** column to find what closely relates to this business process, such as "Sales activities." You can complete the following tasks to confirm relevance:
    
     -  **Find related keywords**. Expand the keyword by selecting the &gt; (greater-than) sign to see multiple-word phrases that include it. For each keyword, you can see the **Number of meetings** with this word in the subject line. You can also see the amount of time spent in those meetings (Attendee meeting hours).
     -  **View the meeting metadata**. Select a keyword to see a list of meetings with this word in the subject line, the number of attendees, and whether the meeting is recurring. If these meetings are relevant, select them.
9.  After you decide which keywords are relevant, you should select the keywords. To do so, hover your cursor over each keyword's row to see and select the check box to the left of the word. After selecting the keywords, select **Add selected to**, and then select **Included keywords**.
10. After you select keywords, you'll see them in the Included keywords list to the right of the results table.
11. Optionally, you can explicitly exclude terms from the keyword list by repeating these steps and selecting **Excluded keywords** in the previous step. As you add keywords, the system becomes more context-aware. As such, it will automatically start uncovering more content that's relevant to the keywords that you've added. This content will then be displayed in the results list.
12. You may already know the keywords your company uses for a business process. You should complete the following steps to manually include (or exclude) them:
    
    1.  Select **Included keywords &gt; Add** (for keywords to explicitly exclude, use the **Excluded keywords** option).
    2.  Enter the keyword (or multiple words separated with a semicolon).
    3.  Select **Enter**.
13. Confirm the totals at the top of the page that reflect meeting hours and meetings in the entire dataset. The smaller totals reflect the number of meeting hours and meetings in the data that are associated with the currently selected keywords. These smaller numbers change as you add or delete keywords. If you're familiar with the hiring process, these numbers could indicate that your defined keywords are either too narrow (too few meetings and hours) or too broad (too many). In this situation, you can adjust accordingly by adding or deleting keywords.
14. Select **Submit** to start the processing. This option is only available when at least one keyword is listed in **Included Keywords**. During this phase, the status will indicate **In progress.**

#### Analyze a business process

Real-world business processes can be analyzed by creating a query with metrics that filter by a digital business process. This design enables the analysis to focus on a set of collaboration activities, such as relevant meetings.

You can filter by business processes wherever the Meeting is available as a filter or a customizable metric. For example, the following steps use Meeting as an available filter.

1.  Open the **Query designer**.
2.  Select **Get started** under **Query**, and then select **Meeting &gt; Next**.
3.  Select **Set up query** and enter the initial information about it. This information may include a name, time period, and which exclusions to use.
4.  In **Select filters**, select **Meeting**.
5.  Select **Business process**, and then select an available business process. Only business processes with a **Ready** status are available.
6.  In **Organizational data**, select **BusinessProcesses** as an attribute to include in the query.
7.  Finish defining your query, and then select **Run**.

The meeting query results include a **BusinessProcesses** column where each meeting row that matches the business process name will show it. If multiple business processes match a single meeting, this column will contain a comma-delimited list of matched business process names for the meeting.

### Peer analysis

Peer analysis compares the collaboration behaviors of two different groups within an organization. This feature can help management understand how two teams in the same function work differently, or how work-life activities differ across the organization.

:::image type="content" source="../media/peer-analysis-9f44a8ff.png" alt-text="screenshot of the Peer Analysis page":::


To create peer analysis:

1.  Open **Peer analysis**.
2.  Select **New analysis**, select your **Reference group**, enter a name and date range for this analysis, and then enter a name for the reference group.
3.  Identify the group members by selecting one of the following options:
    
     -  **Upload .csv**. This option uploads a .csv file with the email addresses of the people you want to include in the reference group.
     -  **Use filters**. This option filters by the HR (organizational) attributes in the uploaded .csv file (with the group's email addresses). It can also apply filters to the organizational data attributes.
4.  Choose the **Other group** as the comparison group and enter a name for that group.
5.  Identify the group members, as follows:
    
     -  **Upload .csv**. This option uploads a .csv file with the email addresses of the people you want to include in the other (comparison) group.
     -  **Use filters**. This option filters by the HR (organizational) attributes in the uploaded .csv file (with the group's email addresses). It can also apply filters to the organizational data attributes.
6.  Apply **Conditions** (optional) with filters that specify the attributes that should be similar for comparing the groups. For example, to compare Reference group's managers to the Other group's managers, add a conditional filter to include only managers in the output.
7.  Select **Submit**. When the analysis is ready, select the **View** (eye) icon to see the results on the Peer analysis page.

Peer analysis results include:

 -  The date range.
 -  A Highlights section with differences in the three most variant metrics between the groups.
 -  Charts that compare raw averages for multiple metrics.

### Plans

An organization can gain valuable information about how its employees get work done from the other Analyze features. The organization can then transform these insights into actions by using the **Plans** feature in Microsoft Viva Insights.

Enrollment in a Plan requires employees to have access to Personal insights in Microsoft Viva Insights. Plans are designed to help employees transform the way they work to better meet company goals. It combines team goal setting and tracking with useful suggestions through an employee's personal insights.

The following plans are currently available:

 -  **Focus plan**. Helps participants get more time to do deep-dive work and reclaim their calendar for work that matters most.
 -  **Collaboration plan**. Helps participants reduce the number of excessive meetings the group schedules.
 -  **Wellbeing plan**. Helps participants unwind and protect their personal time by disconnecting outside of work.
 -  **Seller success plan**. Helps participants prioritize time, increase network quality and size, and connect with the right roles.

For each plan type, you can select **Analyze** and get answers to questions involving relevant metrics. Then select **Start plan** to create, manage, and track a targeted plan for employees in your organization.

Plans help give managers and employees visibility into how they're spending time. This insight is designed to help them increase their focus and improve collaboration and wellbeing.

### Data sources

Microsoft Viva Insights enables analysts and administrators to review the quality of their data sources. They can use the Data sources feature to view the Microsoft 365 collaboration data for their measured population over a period of time. The **Data sources** view identifies any dates or date ranges that an organization wants to include or exclude from its analysis, such as scheduled company holidays.

The Data sources feature also enables an organization to assess the quality and completeness (coverage) of the uploaded organizational data (HR attributes) for its measured population.

Additionally, if your admin has uploaded Microsoft Dynamics CRM data, you can also confirm the quality of join coverage. Join coverage is the percentage of CRM contact and sales assignment data associated with CRM accounts.

#### Example scenario for Data sources

You want a high-level look at some fourth-quarter custom metrics. To do so, you want to create a query that excludes specific dates as outliers.

You begin by going to **Data sources** and looking at the collaboration data over time for the measured population. For this example, you see two dips in the data, both national holidays. So when you run the query, you can filter out the holiday dates from the query results to provide more accurate analysis.

### Exclusions

Not all scheduled meetings are business-related. People often have personal appointments or holidays scheduled in their work calendars. For analysis in Microsoft Viva Insights, organizations may want to exclude excessively long or large meetings, or attendees who haven't responded or have responded as "tentative."

Viva Insights has a built-in solution to address these issues called Exclusions. There are two types of exclusions - Meeting exclusions and Attendee exclusions. Analysts can use meeting or attendee exclusions to create specific rules that determine which meetings or attendees should be excluded from specific analysis.

With meeting exclusions, you can:

 -  Exclude canceled meetings.
 -  Exclude appointments (time schedule with only one attendee).
 -  Set thresholds for attendance size and duration of meetings to include.
 -  Exclude meeting subjects by topic.

Viva Insights has a default meeting exclusion rule that excludes the following types of meetings:

 -  Meetings with only one attendee.
 -  Meetings longer than eight hours.
 -  Meetings with 250 or more participants.
 -  Canceled meetings.

This default meeting rule is used if no other meeting exclusion is selected.

With attendee exclusions, you can:

 -  Exclude invitees who didn't respond to meeting invitations.
 -  Exclude invitees who accepted meeting invitations as tentative.

Meeting and attendee exclusions can be used to exclude meetings or attendees you don't want to include in your analysis. They can also be used to include meetings that were excluded by the default meeting exclusion rule.

#### Example scenario for exclusions

You want to analyze when people are working remotely from home. The employees at your organization let their managers know they are working from home with a one-person meeting that's titled "Remote day."

Because the default meeting exclusion rule excludes these meetings, you must create a new rule. To do so, go to **Analyst settings &gt; Meeting exclusions** and select **Add exclusion**. By doing so, you can create a new meeting exclusion rule that includes meetings with only one person and with that meeting title.
