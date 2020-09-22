When you've set up Direct Routing for your organization, there will be different options available to help manage it day to day.

In your clothing retailer, you've completed your Direct Routing configuration. Now you want to ensure that the system runs smoothly and that you can diagnose and correct any potential problems before they become a problem for users.

Here, you'll learn about management tools in Microsoft Teams Direct Routing.

## Support map

When you have a Direct Routing environment in place, there are several components involved to make sure everything is running smoothly. For example, you might have a Session Border Controller (SBC), or maybe multiple SBCs connected to Microsoft Teams. You may even have a third-party private branch exchange (PBX) system:

:::image type="content" border="false" source="../media/6-environment-diagram.png" alt-text="Environment example":::

The question then becomes: how do you monitor your environment and manage what's going on?

### Health dashboard

You can use the health dashboard in the Microsoft Teams admin center portal to monitor the overall health of your connected SBCs. The health dashboard is usually the best place to start. If your SBC isn't working, you can't make or receive calls through it, so you'll need to address that first.

To access the health dashboard, you select **Direct Routing** under **Voice** on the left menu in Microsoft Teams admin center:

:::image type="content" source="../media/6-health-dashboard.png" alt-text="Health dashboard":::

The health dashboard shows details of all your SBCs and which ones might be having issues. You can select individual issues to discover more, and to help figure out how to resolve them.

You can also select a specific SBC to dig deeper:

:::image type="content" source="../media/6-individual-session-border-controller.png" alt-text="Health dashboard session border controller":::

You'll have access to details such as when it last made a successful Transport Layer Security (TLS) connection, how many concurrent calls the SBC has handled, and more.

### Call Quality Dashboard and call analytics

The Call Quality Dashboard operates in near real time and helps you to see user calls that contain all of the end-user identifiable information, like call details, user IDs, full IP addresses of users, MAC address details, and more. This data is also aggregated, so you can use trend analysis on calls, based on this information.

:::image type="content" source="../media/6-call-quality-dashboard.png" alt-text="Call Quality Dashboard":::

The Call Quality Dashboard also gives you access to Power BI reports that include summary reports, help desk reports, user feedback reports, mobile device reports, and more. The reports are available in the dashboard, but you can also download them to use with your Power BI desktop application for further analysis and reporting.

You can also use call analytics available in the Microsoft Teams admin center to dig deeper into individual calls.

:::image type="content" border="false" source="../media/6-call-analytics.png" alt-text="Call analytics":::

Call analytics gives you access to information like call reliability and quality for any individual call. A user might have experienced and reported bad call quality, or that the call had dropped out at some point. You can use call analytics to investigate and figure out how to fix the issue.

### SBC and private branch exchange (PBX) logs

Your SBC could also be connected to other environments, giving you access to logs that help you troubleshoot or debug issues. If your SBC communicates with a third-party PBX, you can also collect logs from there.

### Public switched telephone network (PSTN) provider

You can also work with your PSTN provider to get additional insight into issues that might arise from the PSTN side of your environment.

## Common SBC configuration issues

Some SBC configuration issues are common and have known solutions for dealing with them. For example, the **failed to verify peer certificate** issue is common. SBCs rely on TLS to make sure that the device or person on the other end is indeed who they claim to be. To communicate successfully with the Microsoft Phone System, you'll need to make sure you import the Baltimore Root Certificate into your SBC. All vendor documentation for configuring your SBC will have a step that covers this area. If you forget to import this certificate, the SBC won't trust the service. That's why you'll have received an error.

Here are some other configuration issues, along with common solutions to resolve them:

|Issue  |Common solution  |
|---------|---------|
|"404 Not Found" error for incoming calls|The user's phone number isn't configured correctly in Microsoft 365. For example, the number might be missing a plus sign.|
|Outbound calls fail|Dial plan has Regex for a rule that's invalid, even if it isn't used for all calls.|
|Outbound caller ID is anonymous|ForwardPAI has been set to $True, which causes all outgoing calls to be anonymous. Reconfigure the parameter in your SBC. |
|Call connects but with no audio, and call disconnects shortly after|Network address translation (NAT) traversal not configured correctly for a NATed IP address|
| | |
