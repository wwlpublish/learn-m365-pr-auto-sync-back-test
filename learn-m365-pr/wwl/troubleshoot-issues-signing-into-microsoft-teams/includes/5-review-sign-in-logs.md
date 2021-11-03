Occasionally, users experience problems signing into Teams. In many cases, these problems might actually relate to Azure AD, since that provides the authentication service for Teams. 

## Monitor Azure AD

There are a number of monitoring and logging options you can enable and review in Azure AD. These are accessible in the **Monitoring** section of the Azure Active Directory admin center. The following table describes some of the available options.

| Monitoring option | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| Sign-ins          | Enables you to review sign-in logs to help  identify and resolve authentication issues. You can review the recent  sign-ins (the default time period is the last 24 hours). You can also filter  the returned results using a number of factors to help you locate specific  sign-ins |
| Audit logs        | Lists recent activities performed in your  tenant, such as updating policies, or performing user management. |
| Provisioning logs | Lists details about activities performed  by the provisioning service, such as the creation of a group in ServiceNow or  a user imported from Workday. |
| Logs              | Requires that you’ve first configured Log  Analytics integration. Once enabled and configured, you can use Azure Monitor  logs to query data to find particular events, analyze trends, and perform  correlation across various data sources. With the integration of Azure AD  activity logs in Azure Monitor logs, you can compare your Azure AD sign-in  logs against security logs published by Microsoft Defender for Cloud. You can  troubleshoot performance bottlenecks on your application’s sign-in page by  correlating application performance data from Azure Application Insights |
| Usage & insights  | Provides a link to the Azure AD  application activity page. You can review Azure AD application activity, AD  FS application activity, and Authentication methods activity. The Azure AD  application activity page displays information in a per-app list. For  example, you can scroll down the returned list of sign-ins to review those  for Microsoft Teams. |

## Review Azure AD sign-in logs 

You can also review sign-in logs in Azure AD using the following procedure: 

1. Open the **Azure Active Directory admin center**.
2. Select the **Azure Active Directory** tab, and then select **Diagnose and solve problems**. 
3. In the details pane, select **Troubleshoot** beneath the **Sign-in Diagnostic** heading. 
4. On the **Sign-in Diagnostic** page, enter the following information, and then select **Next**:

   - User
   - Application (enter Microsoft Teams)
   - Approximate date and time of problem

5. Review the information returned. 

## Collect and analyze Teams debug logs

If you cannot locate the cause of a sign-in problems in Azure AD, you should consider enabling Teams debug logs, and reviewing the resulting log files. 

You can use log files that Teams generates for diagnostics and troubleshooting. There are three types of log files automatically produced by the client that you can use to assist in troubleshooting Teams. These are:

- Debug
- Media
- Desktop

It’s the debug logs that are most useful when troubleshooting sign-in issues. Debug logs are produced by the desktop clients, as well as by browser-based clients. You can read these logs with any text editor from the bottom up. Debug logs show the following data flows: Sign-in, connection requests to middle-tier services, and call/conversation details.

To access the logs, in Windows, right-click the Teams icon in the system tray, and then select **Collect support files**. Logs are collected in a single folder called **MSTeams Diagnostics Log**. The folder contains subfolders for Desktop, Meeting (Media), and Debug (web) log files. If you use the key combination CTRL + ALT + SHIFT + 1, these logs are copied to the downloads folder for review.

Review the logs for problems with sign-in issues. 

## Troubleshoot Teams Rooms System sign-in issues 

Microsoft Teams Rooms provides a complete meeting experience that brings HD video, audio, and content sharing to meetings of all sizes, from small huddle areas to large conference rooms. When you start a Microsoft Teams Rooms device, a Windows 10 IoT Enterprise instance starts up. 

After Windows start, Teams Rooms signs in using a local account called **Skype**. However, when the device connects to Teams, you must enable and configure modern authentication. You can learn more about this procedure by reviewing the [Authentication in Microsoft Teams Rooms](/microsoftteams/rooms/rooms-authentication) document. 

If you experience problems with connecting to Teams from Teams Rooms, consider:

- Verifying your modern authentication configuration
- Reviewing Conditional Access policies in Azure AD
- Collect and review logs on the Teams Room device

### Analyze log data from Teams Room devices

To collect logs, you must invoke the log collection script that ships with the Microsoft Teams Rooms app. In Admin mode, start an elevated command prompt, and issue the following command:

```PowerShell
powershell -ExecutionPolicy unrestricted c:\rigel\x64\scripts\provisioning\ScriptLaunch.ps1 CollectSrsV2Logs.ps1
```

> [!TIP]
> You can examine the logs in a folder called `C:\rigel`. 
