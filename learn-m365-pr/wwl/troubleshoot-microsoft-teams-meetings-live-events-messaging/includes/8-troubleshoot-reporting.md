Microsoft 365 provides a number of reports that you can use to help troubleshoot Teams usage. These are accessible in the **Microsoft Teams admin center** and also in **Microsoft 365 admin center**. 

## Review Teams reports in Microsoft Teams admin center

Reports are accessible on the **Analytics & reports** page in the **Microsoft Teams admin center**. The following table describes the reports available that can help troubleshoot meetings, live events, and messaging.

| Report                  | Description                                                  |
| ----------------------- | ------------------------------------------------------------ |
| Teams device  usage     | Reports on  usage by Windows users, Mac users, iOS users, and Android phone users. |
| Teams live  event usage | Reports on total  views, start time, event status, organizer, presenter, producer, recording setting,  and production type. |
| Teams usage             | Reports on  active users, active users in teams and channels, active channels, messages,  privacy setting of teams, and guests in a team. |
| Teams user  activity    | Reports on  messages a user posted in a team chat, messages a user posted in a private  chat, 1:1 calls a user participated in, number of meetings a user organized,  number of meetings a user participated in, meetings audio, video and screen  sharing time, and last activity date of a user. |

You can generate reports for the following time periods:

- Last 7 days
- Last 30 days
- Last 90 days

## Review Teams reports in Microsoft 365 admin center

To access reports in Microsoft 365, open the **Microsoft 365 admin center**, select **Reports** and then select **Usage**. Select the period for the report (up to 180 days) and then review the active users for each of the subscribed services, including Microsoft Teams. 

## Analyze log files

You can also use log files that Teams generates for additional diagnostics and troubleshooting. There are three types of log files automatically produced by the client that you can use to assist in troubleshooting Teams. These are described in the following table. 

| Log file | Description                                                  |
| -------- | ------------------------------------------------------------ |
| Debug    | Produced by  the desktop clients, as well as by browser-based clients. You can read these  logs with any text editor from the bottom up. Debug logs show the following  data flows: Login, connection requests to middle-tier services, and  call/conversation details. |
| Media    | Contain  diagnostic data about audio, video, and screen sharing in Teams meetings.  They are required for support cases that are linked to call-related issues.  Media logging is off by default. |
| Desktop  | Contain log  data that occurs between the desktop client and the browser. The logs are  text-based and can be read using any text editor from the top down. |

### Collect and enable logging

You must enable logging before you can review log files. In Windows, right-click the Teams icon in the system tray, and then select **Collect support files**. 

For media logs, in Teams, select **Settings**, select **General**, and select the **Enable logging for meeting diagnostics (requires restarting Teams)** check box. Restart Teams and reproduce your issue.

> [!TIP]
> Debug, Desktop, and Media logs are collected in a single folder called **MSTeams Diagnostics Log**. The folder contains subfolders for Desktop, Meeting (Media), and Debug (web) log files.

## Review logs

Watch the following video for a demonstration of how to review logs:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWH62U]