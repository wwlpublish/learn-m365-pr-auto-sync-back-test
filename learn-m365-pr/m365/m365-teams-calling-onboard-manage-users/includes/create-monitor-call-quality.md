After an organization has deployed Calling for Microsoft Teams they should begin to monitor, troubleshoot, and manage the call quality. Microsoft provides two tools to allow administrators to keep on top of call quality. Administrators have access to the Microsoft Call Quality Dashboard (CQD) and call analytics.

You'll review what data you can access from the CQD and call analytics to keep Calling for Microsoft Teams running smoothly for your company. Then you'll access this data via Power BI report templates. With this data to hand, you'll see how you can troubleshoot poor call quality.

## What is the Microsoft Call Quality Dashboard?

:::image type="content" source="../media/teams-call-quality-dashboard.png" alt-text="Screenshot of the Teams Call Quality Dashboard.":::

Administrators can access the CQD at [https://cqd.teams.microsoft.com/](https://cqd.teams.microsoft.com/). The CQD provides a feed of data with details about calls that have ended in the last 30 minutes. The dashboard is designed for administrators to support call quality at an organization-wide level.

The dashboard lets you track call quality trends over time, focused on the overall call quality, server to client, and client to client. If you have building and endpoint information available, you can upload that data and use it in the dashboard.

The building data file can be tab or comma-separated data, with no headers, and up to a million rows. For the full column specification, see [Microsoft docs](/microsoftteams/cqd-upload-tenant-building-data#upload-building-data-file).

The endpoint file is in the same format, for the full column specification see [Microsoft docs](/microsoftteams/cqd-upload-tenant-building-data#endpoint-data-file).

After you've added the information, the CQD becomes more useful to your organization as you have access to extra functionality like filtering reports by location.

Once you have uncovered issues at the org-wide level, you can drill down to a specific user, or meeting, by combining what you've discovered in the CQD reports with per-user call analytics.

## What data is available in the CQD?

Microsoft has created a default set of summary and detailed reports that should be all you need to manage and monitor the call quality in your company.

Once you've signed in to the CQD, you'll see the org-wide Summary Reports. The report has a tab interface with the first tab showing you the overall call quality being achieved by Calling for Microsoft Team. The report is an aggregation of information from the other Server-Client, Client-Client, and Voice Quality SLA tabs of the report. It's a great place to start troubleshooting and at a glance can show you if your organization is having poor quality issues over time.

The full list of reports available to you is:

- Summary Reports
- **Location-Enhanced Reports**
- Reliability Reports
- Quality of Experience Reports
- Quality Drill Down Reports
- Failure Drill Down Reports
- Rate My Call Reports
- Help Desk Reports
- Client Version Reports
- Endpoint Reports
- **Detailed Reports**

> [!NOTE]
> You'll only gain access to the Location-Enhanced Reports after uploading your building and endpoint information. You can add additional custom reports to the Detailed Reports section. Microsoft provide two curated CQD report templates to get you started.

## Use Power BI and report templates to analyze CQD data

You aren't limited to using the CQD to troubleshoot your organizations call quality issues. Microsoft has created a suite of Power BI report templates that you can use without making edits to them. The report templates can be downloaded from [CQD Power BI Query Templates](https://www.microsoft.com/download/details.aspx?id=102291).

Before you can run and edit the reports, you'll need to install the Power BI Connector for the CQD. It's included in the download, unpack the zip file and save the pbx file to this location [user]\Documents\Power BI Desktop\Custom Connectors\MicrosoftCallQuality.pqx.

You can then either double-click on a template, or open Power BI Desktop and select one the templates to use:

- CQ and AA combined Analytics 20201105.pbit
- CQD Helpdesk Report.pbit
- CQD Location Enhanced Report.pbit
- CQD Mobile Device Report.pbit
- CQD PSTN Report.pbit
- CQD Summary Report.pbit
- CQD Teams Usage Report.pbit
- CQD User Feedback Report (Rate My Call).pbit

For more information on what each template contains and how to use it, see [Use Power BI to analyze CQD data for Microsoft Teams](/microsoftteams/cqd-power-bi-query-templates)

## What is call analytics?

Call analytics allow you to view detailed information about a specific user's Teams calls. The information includes data about devices used, networks, how apps connected to the network, and the overall quality of calls and meetings. Compare this to information in the CQD, you'd use the information there to be pro-active about call quality. The information in call analytics will be used reactively after users have finished their calls.

To enable call analytics, you'll need to upload the same building data that the CQD uses to provide enhanced location reports. You can reuse the same files. Begin with signing in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/reporting-labels), then select **Locations**.

:::image type="content" source="../media/teams-admin-location-upload.png" alt-text="Screenshot of the location data uploading screen.":::

Select **Upload data** and upload your csv, or tsv, file containing your organization's building information in.

To view the call analytics for a user navigate to [Microsoft Teams admin center](https://admin.teams.microsoft.com/users), then select **Users**.

:::image type="content" source="../media/teams-user-call-analytics.png" alt-text="Screenshot of users in your organization.":::

Select the user you are interested in, then scroll down and select **Call history**.

:::image type="content" source="../media/teams-user-call-history.png" alt-text="Screenshot of a user's call history.":::

Call history lists the last 30 days of calls and meetings, selecting one of the sessions listed will enable you to drill down into specifics about that specific call. You can review the call quality, the devices, and network connectivity.

:::image type="content" source="../media/teams-difference-between-call-analytics-and-call-quality-dashboard.png" alt-text="Screenshot of details shown of a specific meeting or call.":::

## Reviewing call quality issues and learn how to resolve them

Imagine you're providing support to your organization's Teams users. A user has contacted you complaining of call quality issues. Follow the above steps to navigate to the users call history. Review this list of sessions for the last 30 days and select the session you'd like to troubleshoot.

Select the **ADVANCED** tab, and look for items listed in yellow or red.
