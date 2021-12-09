Coexistence modes provide an easy, predictable experience for end users as organizations transition from Skype for Business to Teams. 

For an organization moving to Teams, the TeamsOnly mode is the final destination for each user. You don't have to assign TeamsOnly mode to all users at the same time. You can use any Skype for Business modes to ensure predictable communication between users who are TeamsOnly and those users who aren't yet.

From a technical perspective, a user's mode governs several aspects of the user's experience:

- **Incoming routing**: In which client (Teams or Skype for Business) do incoming chats and calls land?

- **Presence publishing**: Is the user's presence that is shown to other users based on their activity in Teams or Skype for Business?

- **Meeting scheduling**: Which service is used for scheduling new meetings and ensuring that the proper add-in is present in Outlook? Users can always *join* any meeting, whether it be a Skype for Business meeting or a Teams meeting.

- **Client experience**: What functionality is available in Teams or Skype for Business client? Can users start calls and chats in Teams, Skype for Business, or both? Is Teams & Channels experience available?  

However, from an experience perspective, mode can be described as defining the experience for:

- **Chat and Calling**: Which client does a user use?

- **Meeting Scheduling**: Do users schedule new meetings as Teams or Skype for Business meetings?

- **Availability of collaboration functionality in Teams client**: Is Teams & Channels and Files functionality available while users still have Skype for Business?

Here are coexistence modes that are available when you decide to upgrades to Teams.

:::image type="content" source="../media/skype-to-teams-upgrade-paths.png" alt-text="Screenshot of upgrade building blocks from Skype for Business to Teams":::

## Skype for Business Only

In this coexistence mode, users remain in Skype for Business—not Teams—for chat, meeting, and calling capabilities, and they don't use Teams for teams and channels. In the current implementation, teams, and channels are not automatically turned off for the user. You can use the App Setup policy to hide teams and files.

This mode can be used prior to starting a managed deployment of Teams to prevent users from starting to use Teams ahead of having built readiness. This mode is also a way to enable authenticated participation in Teams meetings for Skype for Business users, provided the users are licensed for Teams.

## Islands

Users can run Teams alongside Skype for Business as two separate solutions that deliver similar and overlapping capabilities. The capabilities include presence, chat, calling, and meetings. Teams users also can take advantage of new collaboration capabilities such as teams and channels, access to files in Microsoft 365 or Office 365, and applications.

In this coexistence mode, called **Islands**, each of the client applications operates as a separate island. Skype for Business talks to Skype for Business, and Teams talks to Teams. Users are expected to run both clients always and can communicate natively in the client from which the communication was started. As such, there's no need for interoperability in **Islands** mode.

To avoid a confusing or regressed Skype for Business experience, the Skype for Business handles the following integrations that aren't handled in Teams **Islands** mode:

- External (federated) communications.

- PSTN voice services and voice applications, Office integration.

- HID controls for USB devices.

- Several other integrations.  

## Skype for Business with Teams Collaboration

Use this mode to introduce Teams in your environment while you continue to use your existing investment in Skype for Business. Leave Skype for Business unchanged for chat, calling, and meeting capabilities. Add Teams collaboration capabilities:

- Teams and channels.

- Access to files in Microsoft 365 or Office 365.

- Applications. Teams communications capabilities—private chat, calling, and scheduling meetings.

## Skype for Business with Teams Collaboration and Meetings, also known as Meetings First

Use this coexistence mode to accelerate the availability of Teams meeting and collaboration capabilities in your organization. The coexistence mode lets your users take advantage of the superior Teams meetings experience:

- Great quality.

- Transcription and translation.

- Background blurring.

- Superior user experience across all platforms, including mobile devices and browsers.

Along with using Teams for teams and channels–based conversations in this mode, users will use Teams to schedule and conduct their meetings. Private chat and calling remain on Skype for Business. Teams and Skype for Business benefit from a range of "better together" capabilities, such as presence reconciliation, automatic hold/unhold, and HID device support across both applications. It's possible to hide teams and channels, if desired, using the App Setup policy.

This coexistence mode is especially useful for organizations with Skype for Business on-premises deployments with Enterprise Voice. These organizations are likely to take some time to upgrade to Teams and want to benefit from the superior Teams meetings as soon as possible.

## Teams Only

A **Teams Only** user (also called an *upgraded* user) has access to all the capabilities in Teams. They may retain the Skype for Business client to join meetings on Skype for Business that have been organized by non-upgraded users or external parties. An upgraded user can continue to communicate with other users in the organization who are still using Skype for Business by using the interoperability capabilities between Teams and Skype for Business (provided the Skype for Business users are not in **Islands** mode). However, an upgraded user can't initiate a Skype for Business chat, call, or meeting.

As soon as your organization is ready for some or all users to use Teams as their only communications and collaboration tool, upgrade those users to **Teams Only** mode. If you're upgrading from **Islands** mode, we advise that you first saturate Teams adoption throughout your organization before beginning the upgrade process. This adoption avoids broken communication scenarios due to **Islands** mode not providing interoperability.

When in **Teams Only** mode, Teams is the default app for the SIP/Tel protocol. Links in a user's contact card in Outlook for calling or chat will be handled by Teams.

For more information, see:

- [Migration and interoperability guidance for organizations using Teams together with Skype for Business](/microsoftteams/migration-interop-guidance-for-teams-with-skype?azure-portal=true)

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”