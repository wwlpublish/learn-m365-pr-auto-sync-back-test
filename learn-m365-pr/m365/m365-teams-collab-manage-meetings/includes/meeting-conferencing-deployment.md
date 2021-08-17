Teams provides a great out-of-the-box meeting and conferencing experience, and most organizations find that the default meeting settings work well for them. But depending on your organization's needs, you may decide to change some or all the default settings.

## Meetings and conferencing prerequisites

To get the best Teams experience, you must have deployed Exchange Online and SharePoint Online and have a verified domain for Microsoft 365 such as *your-organization.com.*

You'll also need to make sure that the following common ports are open to the internet from your user's locations:

- TCP ports 80 and 443 outgoing from clients that will use Teams
- UDP ports 3478 through 3481 outgoing from clients that will use Teams

## Core deployment decisions

The settings most organizations want to change (if the Teams default settings don't work for them) are detailed in this table.

| Setting | Considerations |
|---|---|
| Teams administrator roles |Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators.  |
| Meetings settings |Meetings settings are used to control whether anonymous users can join meetings, set up meeting invitations, and set the ports for real-time traffic (if you want to turn on Quality of Service (QoS)). These settings will be used for all the Teams meetings that users schedule in your organization.  |
| Meeting policies | Meeting policies are used to control what features are available to users when they join Teams meetings. You can create custom meeting policies for people that host meetings in your organization. |
|Audio conferencing policies  | Audio Conferencing provides organizations with additional entry points to any meeting by allowing meeting participants to join via public switched telephone network (PSTN) using a traditional land line, private branch exchange (PBX), or mobile phone. |
|Meeting room and personal device policies  |For the optimal meeting experience, consider using Teams devices such as room systems, phones, headsets, and cameras.  |

## Additional deployment decisions

You may want to consider the following additional deployment decisions, based on your organization's needs and configuration.

| Setting/requirement | Considerations |
|---|---|
| Bandwidth planning | Bandwidth planning lets organizations estimate the bandwidth required to support meetings across their wide area networks and internet links. |
| Meeting recording and archiving | Users can record their meetings and group calls to capture audio, video, screen sharing activity, and automatic transcription. |
| Live events policies | Teams live events policies are used to manage event settings for groups of users. |
|Conference room systems rollout| Organizations with many conference rooms may want to consider a structured approach to inventorying their rooms, identifying the appropriate devices, and then rolling them out. |
|Cloud video interop  |Cloud video interop makes it possible for third-party meeting room devices to join Teams meetings without expensive meeting room system and device upgrades. |
|Personal device rollout  |When planning a larger rollout of personal devices to support meetings or voice deployments, consider using a repeatable site-by-site rollout process that delivers repeatable quality.  |
| Troubleshoot meeting and call quality |Teams gives you two ways to monitor and troubleshoot call quality problems: **Call Analytics** shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user, and is designed to help administrators and help desk agents troubleshoot call quality problems with specific calls. **Call Quality Dashboard** helps administrators and network engineers optimize a network by shifting focus from specific users and instead looks at aggregate information for an entire Teams organization. |
|Operate your meetings service  |Operate my service articles provide in-depth guidance for service operations.  |
|Licensing |Although you can hold meetings without having any additional licenses—all you need is a license for Microsoft Teams—audio conferencing, which lets participants join Teams meetings from a regular phone, requires an additional license.|

## Use activity reports

Use activity reports to see how users in your organization are using Teams so you can prioritize training and communication efforts. You should carefully monitor both the usage and quality of meetings:

- Low usage means that users aren't using the product. Reasons can range from the perception that meetings are falling short of user requirements, to a lack of awareness or training, to quality problems.
- Low quality means that there are issues with connectivity between users and Microsoft 365. Low quality can lead to bad user experience and lower usage.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Meetings & conferencing in Microsoft Teams](/microsoftteams/deploy-meetings-microsoft-teams-landing-page)
- [Tutorial: Meetings in Teams](/microsoftteams/tutorial-meetings-in-teams?tutorial-step=1)
