Depending on how you choose to deploy Teams, Teams capabilities may overlap with the capabilities delivered by Skype for Business for a given user. The default mode is to run Teams alongside Skype for Business with the capabilities overlapping; however, a user can be assigned one of several coexistence modes (also known as upgrade modes) that were designed to ensure that these capabilities don't overlap for that user (in which case interoperability between Teams and Skype for Business is available). For example, if you have significant Skype for Business Server on-premises assets with a complex Enterprise Voice deployment but want your users to enjoy modern meetings as quickly as possible, you might want to evaluate Meetings First as an alternative path.

Review the following coexistence modes to help determine which path is right for your organization.

## Islands mode  

By default, users can run Teams alongside Skype for Business as two separate solutions that deliver similar and overlapping capabilities such as presence, chat, calling, and meetings. Teams users also can take advantage of new collaboration capabilities such as teams and channels, access to files in Microsoft 365, and applications.

In this coexistence mode, called Islands mode, each of the client applications operates as a separate island. Skype for Business talks to Skype for Business, and Teams talks to Teams. Users are expected to run both clients at all times and can communicate natively in the client from which the communication was initiated. As such, there's no need for interoperability in Islands mode.

To avoid a confusing or regressed Skype for Business experience, external (federated) communications, PSTN voice services and voice applications, Office integration, HID controls for USB devices, and several other integrations continue to be handled by Skype for Business and are not available in Teams in Islands mode. Phone System is not supported in Teams in Islands mode; in this mode, the only Enterprise Voice client is Skype for Business.

> [!NOTE]
> In Islands mode, all messages and calls from federated users (people outside your organization) are delivered to Skype for Business. After upgrading to TeamsOnly mode, all messages and calls from outside your organization are delivered to Teams.

The recommended path for Skype for Business Online customers is to start with the default Islands mode, drive Teams adoption saturation in the organization, and then move to TeamsOnly mode rapidly. On-premises and hybrid customers, especially complex ones, might benefit from deploying the Skype for Business with Teams Collaboration mode as a starting point rather than Islands mode, and progress from there to Skype for Business with Teams Collaboration and Meetings mode (that is, Meetings First), if appropriate, and to TeamsOnly mode when the organization is ready to adopt Teams.

## Skype for Business only mode

In this coexistence mode, users remain in Skype for Business—not Teams—for chat, meeting, and calling capabilities, and they don't use Teams for teams and channels. This mode is available today; however, in the current implementation, teams and channels are not automatically turned off for the user. This can be achieved by using the App Permissions policy to hide teams and channels.

This mode can be used prior to starting a managed deployment of Teams to prevent users from starting to use Teams ahead of having built readiness, or as a way to enable authenticated participation in Teams meetings for Skype for Business users, provided the users are licensed for Teams.

## TeamsOnly mode

A TeamsOnly user (also called an upgraded user) has access to all the capabilities in Teams. They may retain the Skype for Business client to join meetings on Skype for Business that have been organized by non-upgraded users or external parties. An upgraded user can continue to communicate with other users in the organization who are still using Skype for Business by using the interoperability capabilities between Teams and Skype for Business (provided these Skype for Business users are not in Islands mode). However, an upgraded user can't initiate a Skype for Business chat, call, or meeting.

As soon as your organization is ready for some or all users to use Teams as their only communications and collaboration tool, you can upgrade those users to TeamsOnly mode. If you are upgrading from Islands mode, we advise that you first saturate Teams adoption throughout your organization before beginning the upgrade process. Doing so avoids broken communication scenarios due to Islands mode not providing interoperability.

:::image type="content" source="../media/now-using-teams.png" alt-text="Screen shot of a generic Teams window.":::

## Skype for Business with Teams Collaboration mode

Use this mode to introduce Teams in your environment while you continue to take advantage of your existing investment in Skype for Business. In this mode, you leave Skype for Business unchanged for chat, calling, and meeting capabilities, and you add Teams collaboration capabilities—teams and channels, access to files in Microsoft 365, and applications. Teams communications capabilities—private chat, calling, and scheduling meetings—are off by default in this mode.

Organizations with a starting point of Skype for Business Server on-premises or hybrid should consider this mode as an alternative to Islands mode if they want to give users interoperability and predictability for their communications, as well as having a predictable timeline for their upgrade to Teams (as opposed to relying on adoption saturation in Islands mode).

## Skype for Business with Teams Collaboration and Meetings, also known as Meetings First mode

Use this coexistence mode to accelerate the availability of Teams meeting capabilities in your organization. This mode enables your users to take advantage of the superior Teams meetings experience-great quality, innovative capabilities such as transcription and translation or background blurring, and superior user experience across all platforms, including mobile devices and browsers.

Along with using Teams for teams and channels–based conversations in this mode, users will use Teams to schedule and conduct their meetings. Private chat and calling remain on Skype for Business. Teams and Skype for Business benefit from a range of "better together" capabilities, such as presence reconciliation, automatic hold/unhold, and human interface device support across both applications. You can hide teams and channels if desired by using the App Permissions policy.

This coexistence mode is especially useful for organizations with Skype for Business on-premises deployments with Enterprise Voice, who are likely to take some time to upgrade to Teams and want to benefit from the superior Teams meetings as soon as possible.

> [!NOTE]
> When deployed in any coexistence mode except Islands, Teams and Skype for Business can interoperate, enabling users to chat with and call one another, and ensuring that communications remain fluid across your organization during your upgrade journey to Teams. Coexistence modes govern interoperability. The coexistence mode of the receiver determines whether interoperability will be available. For example, if the receiver is in a mode in which chat is only available in one client (say, Teams), chat interoperability will generally be available in case the initiator uses the other client (in this case, Skype for Business) to start the chat. At the same time, if the receiver is in the mode in which chat is available in both clients (Islands mode), interoperability won't be available for the chat. The message will be received by the receiver in the same client in which the initiator started the chat. Therefore, proper communication in Islands mode requires Teams adoption saturation; that is, all users actively using and monitoring both clients.

> [!TIP]
> To help identify the recommended upgrade mode based on the capabilities you want to enable in Teams while Skype for Business is still in use, use the Skype to Teams Upgrade Wizard.

You can learn more about coexistence modes in the module **Upgrade to Teams from Skype for Business.**

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Understand Microsoft Teams and Skype for Business coexistence and interoperability](/MicrosoftTeams/teams-and-skypeforbusiness-coexistence-and-interoperability)
- [Skype to Teams Upgrade Wizard](https://www.microsoft.com/fasttrack/teams-upgrade-plan?rtc=1)
