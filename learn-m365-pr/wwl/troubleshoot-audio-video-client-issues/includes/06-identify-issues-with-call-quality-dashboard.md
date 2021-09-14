Microsoft Teams Call Quality Dashboard (CQD) provides a summary view of an organization's calls and meetings on a monthly, daily, or hourly basis. It enables an organization to investigate problems based on quality, failure, and in-product user feedback. 

CQD is designed to help Microsoft Teams administrators and network engineers monitor call and meeting quality at an organization-wide level. The near real-time data enables Teams admins to quickly resolve troubleshooting efforts by drilling down to find where issues originated, and who was affected.

Suppose a user's poor call quality is because of a network issue that also affects other users. The individual call experience isn't visible in CQD, but the overall quality of calls made using Microsoft Teams is captured.

## Permissions to access Call Quality Dashboard  

Employees who aren't administrators, such as help desk agents, can use CQD if they're assigned the Teams Communications Support Engineer, Teams Communications Support Specialist, or Reports Reader role.

Users with the following roles can access the Call Quality Dashboard:

* Global Administrator
* Global Reader
* Skype for Business Administrator
* Teams Service Administrator
* Teams Communications Administrator
* Teams Communications Support Engineer
* Teams Communications Support Specialist
* Reports Reader

## The Call Quality Dashboard (CQD) in Teams admin center

CQD data can be accessed using several different methods, including:

* Teams admin center
* CQD portal (Teams admin center > Call Quality Dashboard)
* Graph API
* Power BI

When you first sign into the CQD Portal, you'll see the summary reports. These show daily and monthly call quality trends. Call quality is classified as good, poor, or unclassified.

In the Product Filter, select **Microsoft Teams**. Using the tabs, select **Overall Call Quality**, **Server-Client**, **Client-Client**, or **Voice Quality SLA**.

### **Summary reports**

These reports are displayed on the CQD Dashboard when you first sign in to CQD. They provide an at-a-glance look at quality trends with daily, monthly, and table reports to assist with identifying subnets that have poor quality.

| Tab | Description |
|---------|---------|
|Overall Call Quality     | Aggregate of the other 3 tabs.       |
|Server—Client     |Details of the streams between server and client endpoints.        |
|Client—Client     |Details of the streams between two client endpoints.        |
|Voice Quality SLA     |Info about calls included in the Skype for Business voice quality SLA.        |

‎:::image type="content" source="../media/call-quality-dashboard-summary-report.png" alt-text="Quality Dashboard":::

### Detailed reports

Use the menu at the top to select other reports. For each type of report, you can filter and show different selections.

| Name | Description |
|---------|---------|
|Location-Enhanced Reports     |Shows quality trends based on location information. This report appears only if you've uploaded your tenant data.        |
|Reliability Reports     |Includes audio, video, video-based screen sharing (VBSS), and app sharing reports.        |
|Quality of Experience Reports     |Audio quality and reliability for all clients and devices, including meeting rooms. These reports are a “slimmed-down” version of the downloadable [CQD templates](https://docs.microsoft.com/microsoftteams/cqd-data-and-reports#import-the-cqd-report-templates?azure-portal=true), focusing on key areas for analyzing audio quality and reliability.         |
|Quality Drill Down Reports     | Drill downs: Date by region, locations, subnets, hour, and users.        |
|Failure Drill Down Reports     | Drill downs: Date by region, locations, subnets, hour, and users.        |
|Rate My Call Reports     |Analyze user call ratings by region, location, or by user. Includes verbatim feedback.         |
|Help Desk Reports     |Help Desk Reports look at call and meeting data for individual users, groups of users, or everyone. Incorporating building and end-user personal information, these reports help identify possible system issues based on network location, conference details, devices, or firmware.         |
|Client Version Reports     |Client Version Summary: View the Sessions and Users counts for each client app version<br><br>Client Version by User: View user names for each client app version <br><br>Pre-built filters for Product and Client Type help focus the versions to specific clients.         |
|Endpoint Reports     |Shows call quality by machine endpoints (computer make and model).

‎:::image type="content" source="../media/call-quality-reports.png" alt-text="Reports in CQD ":::
