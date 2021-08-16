To ensure continued service delivery to your users, it’s important that you can identify common problems with Teams and know how to resolve those problems. This unit describes common Teams problems. 

## Service Health

Before you start troubleshooting in Teams, it’s worth just checking service health. You can access this on the **Microsoft 365 Admin center** main page. 

:::image type="content" source="../media/service-health.png" alt-text="A screenshot displays the Service health page in the Microsoft 365 admin center. All services, including Microsoft Teams, is displayed as Healthy." lightbox="../media/service-health.png":::


> [!TIP]
> Remember that Teams is built on additional Microsoft 365 services, so remember to also check the status of Exchange, SharePoint, and OneDrive for Business. 

You can also use log files that Teams generates for additional diagnostics and troubleshooting. There are three types of log files automatically produced by the client that you can use to assist in troubleshooting Teams:

- **Debug logs**. Produced by Teams desktop client, and record logins, connection requests, and call/conversation details.
- **Media logs**. Contain diagnostic data about audio, video, and screen sharing in Teams meetings. Required for support cases linked to call-related issues.
- **Desktop logs**. Contain log data that occurs between the desktop client and the browser.

 

> [!TIP]
> When creating a support request with Microsoft Support, the support engineer will require the debug logs. Have these logs on hand before creating the support request.

## General issues

Besides service health, you might also encounter some of the more general issues with Teams. The following table describes these general issues.

| Issue                             | Description                                                  |
| --------------------------------- | ------------------------------------------------------------ |
| Network  connectivity             | Most network  connectivity issues with the Teams client relate to firewall or proxy  connectivity. Ensure you verify that the necessary URLs, IP addresses, and  ports are open in your firewall or proxy. For details, refer to [Microsoft  365 and Office 365 URLs and IP address ranges](/microsoftteams/office-365-urls-ip-address-ranges). |
| Web browser  client               | Users should use the Teams Desktop app for the best  experience with Teams. If that’s not possible, users can choose to connect to  Teams using a browser. However, there are some limitations with certain  browsers. For example, use of Internet Explorer 11 is very limited, and as of  11/20/20, it’s no longer officially supported. |
| Windows  Defender Firewall        | When users are using the Desktop client for Teams, on  first use, they’re often prompted to allow Teams through Windows Defender  Firewall. This prompt can be disconcerting for users. So, consider using  Group Policy or a PowerShell script to reconfigure all your users’ firewall  settings. |
| External  access and guest access | There are two  ways to collaborate and communicate with people outside of your organization  when using Teams. You can add them as guest users in your tenant, or you can  enable external access. There are additional settings required to enable the  correct level of external or guest access. If users from outside your  organization can’t collaborate with users in your organization, verify  whether you have enabled and configured the appropriate external access  method. You must also determine whether the type of collaboration sought is  supported by either External access or Guest access. |


### Common issues

At the time of writing, the most common issues were collated on the [Teams troubleshooting](/MicrosoftTeams/troubleshoot/teams-welcome) website. They are:

- Virtual cameras stop working on macOS Teams desktop client
- Microsoft Teams is stuck in a login loop in Microsoft Edge or Internet Explorer
- Issue when you access a notebook for Microsoft Teams
- Teams is slow during video meetings on laptops docked to 4K/HDR monitors
- Unable to create a team in Microsoft Teams
- Removed user appears as "Unknown user" in Microsoft Teams
- Dial pad is missing in Microsoft Teams
- Error when signing into Teams: You're missing out! Ask your admin to enable Microsoft Teams for `"your company name"`

These issues, and many more, are addressed in this learning path. 