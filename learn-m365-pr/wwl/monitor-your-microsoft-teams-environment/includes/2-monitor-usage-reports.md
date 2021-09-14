There are various reports in the Microsoft Teams admin center to get different insights into how users in your organization are using Teams. For example,

* How many users communicate through channel and chat messages.
* The kinds of devices they use to connect to Teams. 
* Understand usage patterns to help make business decisions and inform training and communication efforts for successful user adoption.

Here's a list of the Teams reports available in the Microsoft Teams admin center:

|Report |Description |
|-----|----|
|Teams usage report | An overview of the usage activity in Teams, including the number of active users and channels, guests, and messages in each team. You can quickly see how many users across your organization are using Teams to communicate and collaborate. |
|Teams user activity report | An overview of the types of activities that users in your organization do in Teams. | 
|Teams app usage report | The Teams app usage report in the Microsoft Teams admin center provides you with information about which apps users are using in Teams.|
|Teams device usage report | The information about how users connect to Teams. You can use the report to see the devices that are used across your organization, including how many use Teams from their mobile devices when on-the-go. |  
|Teams live event usage report | An overview of the activity for live events held in your organization, including event status, start time, views, and production type for each event. |  
|Teams PSTN blocked users report | The information about  the users in your organization who are blocked from making PSTN calls in Teams.|  
|Teams PSTN minute pools report | An overview of audio conferencing and calling activity in your organization by showing you the number of minutes consumed during the current month. | 
|Teams PSTN usage report - Calling Plans | An overview of calling and audio conferencing activity for Calling Plans in your organization, including the number of minutes that users spent in inbound and outbound PSTN calls and the cost of these calls. | 
|Teams PSTN usage report - Direct Routing | An overview of calling and audio conferencing activity for Direct Routing in your organization, including the SIP address and call start and end times. | 
|Teams information protection license report - Direct Routing | The Teams information protection license report gives insight into apps that have subscribed to change notification events to listen to created, updated, or deleted messages at tenant level. A change notification corresponding to the message is sent successfully only when the user has the required license. |

## Access Teams reports

To access the Teams usage reports, you need to have one of the following roles assigned: 

* Global admin in Microsoft 365 or Office 365
* Teams  admin
* Skype for Business admin


Go to the Microsoft Teams admin center, in the left navigation, select **Analytics & reports**, and then under **Report**, choose the report you want to run. You can select different **Data range** or **Columns** to be shown in the report. 

|Report  |What's measured? |Screenshot |
|---------|---------|---------|
|Teams usage report | Active users<br/>Active users in teams and channels<br/>Active channels<br/>Messages<br/>Privacy setting of teams<br/>Guests in a team   |‎:::image type="content" source="../media/microsoft-teams-usage-reports.png" alt-text="Microsoft Teams Usage Reports" lightbox="../media/microsoft-teams-usage-reports.png":::|
|Teams user activity report | Messages a user posted in a team chat<br/>Messages a user posted in a private chat<br/>  1:1 calls a user participated in<br/> Number of meeting each user organized <br/>number of meeting each user participated in<br/>Meetings Audio, Video, and Screen sharing time<br/>   Last activity date of a user     |‎:::image type="content" source="../media/microsoft-teams-user-activity-report.png" alt-text="07-Microsoft Teams user activity report" lightbox="../media/microsoft-teams-user-activity-report.png":::|
|Teams app usage report|App name <br/> Active users <br/> App type <br/> Active teams <br/> Publisher <br/> Version <br/> |‎:::image type="content" source="../media/microsoft-teams-app-usage-report.png" alt-text="Teams app usage report" lightbox="../media/microsoft-teams-app-usage-report.png":::|
|Teams device usage report  |  Windows users<br/>Mac users<br/>iOS users<br/>Android phone users     |‎:::image type="content" source="../media/microsoft-teams-device-usage-reports.png" alt-text="Microsoft Teams device usage reports" lightbox="../media/microsoft-teams-device-usage-reports.png":::|
|Teams live event usage report  |  Total views<br/>Start time<br/>Event status<br/>Organizer<br/>Presenter<br/>Producer<br/>Recording setting<br/>Production type  |‎:::image type="content" source="../media/microsoft-live-events-usage-report.png" alt-text="Microsoft Live events usage report" lightbox="../media/microsoft-live-events-usage-report.png":::|
|Teams PSTN blocked users report  |  Display name<br/>Phone number<br/>Reason<br/>Action type<br/>Action date and time   |‎:::image type="content" source="../media/microsoft-teams-blocked-users-report.png" alt-text="Microsoft Teams PSTN blocked users report" lightbox="../media/microsoft-teams-blocked-users-report.png":::|
|Teams PSTN minute pools report |  Country or region<br/>Capability (license) <br/>Total minutes<br/>Minutes used<br/>Minutes available|‎:::image type="content" source="../media/teams-reports-minute-pools-with-callouts.png" alt-text="Microsoft Teams PSTN minute pools report" lightbox="../media/teams-reports-minute-pools-with-callouts.png":::|
|Teams PSTN usage report - Calling Plans | Time stamp<br/>User name<br/>Phone number<br/>Call type <br/>Called to<br/>To country or region <br/>Called from <br/>From country or region<br/>Charge<br/>Currency<br/>Duration<br/>Domestic/International<br/>Call ID<br/>Number type<br/>Country or region<br/>Conference ID<br/>Capability (license)|‎:::image type="content" source="../media/teams-reports-usage-calling-plans-with-callouts.png" alt-text="Teams PSTN usage report - Calling Plans" lightbox="../media/teams-reports-usage-calling-plans-with-callouts.png":::|
|Teams PSTN usage report - Direct Routing |  Time stamp<br/>Display name<br/>SIP address<br/>Phone number <br/>Call type<br/>Called to<br/>Start time<br/>Invite time<br/>Failure time<br/>End time<br/>Duration<br/>Number type<br/>Media bypass<br/>SBC FQDN<br/>Azure region<br/>Event type<br/>Final SIP code<br/>Final Microsoft subcode<br/>Final SIP phrase<br/>Correlation ID  |‎:::image type="content" source="../media/teams-reports-usage-direct-routing-with-callouts.png" alt-text="Teams PSTN usage report - Direct Routing" lightbox="../media/teams-reports-usage-direct-routing-with-callouts.png":::|
|Teams information protection license report - Direct Routing | Whether users have valid licenses to push their messages via change notifications<br/><br/>Total number of change notification events triggered by a user<br/><br/>What apps are listening to org-wide change notification events<br/>|‎:::image type="content" source="../media/teams-information-report.png" alt-text="Teams information protection license report - Direct Routing" lightbox="../media/teams-information-report.png":::|


> [!NOTE]
> The Teams reports display the data for the users and channels that have been active. For example, if a user in your organization isn't active in Teams during the date range specified for a report, data for that user will not be included in that report. 

| Item| Definition |
| - |-|
| Active user| Measures the number of unique users who do an action in Teams during the specified date range. |
| Active channel| Measures the number of channels of a team in which users do an action during the specified date range. |


## Download Teams reports
 
You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, select **Download** to download the report when it's ready.

‎:::image type="content" source="../media/microsoft-teams-usage-reports-download.png" alt-text="Microsoft Teams usage reports download" lightbox="../media/microsoft-teams-usage-reports-download.png":::

For more information, see [Teams analytics and reporting](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference?azure-portal=true).

 
