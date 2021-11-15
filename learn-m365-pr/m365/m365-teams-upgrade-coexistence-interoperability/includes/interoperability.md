Interoperability is the ability for Teams and Skype for Business users in the same organization to communicate across Teams and Skype for Business.

Interoperability is governed by the coexistence mode (also known as upgrade mode) of the receiver. There is no interoperability when the receiver is in Islands mode.

## Native interoperability and interoperability escalation

There are two types of interoperability experiences: native interoperability and interoperability escalation.

- A native interoperability experience occurs in the client that the user is currently using. One user will be in the Skype for Business client, the other in Teams. A native interoperability experience won't take them to another client to communicate, the users will be able to conduct their conversation in the client they're currently using. The native interoperability experiences are one-to-one chat and calling.
- An interoperability escalation experience means that as part of helping users perform an advanced action (such as sharing their desktop), the client facilitates the creation of a meeting which users can join to continue the experience in that meeting. The meeting is created on the platform of the initiator of the action. The user or users who aren't on that platform receive a meeting join link. As they click this link, they are joined to the meeting in a compatible client (browser, web app, or full client, depending on configuration). Interoperability escalation from Skype for Business requires a recent client. Interoperability escalation from Teams is now available. Both are supported in interoperability experiences in-tenant, and for federated communication cross-tenants.

## Native interoperability experiences

Depending on the coexistence modes assigned to users (as previously described), the following native interoperability experiences are available:

- Skype for Business users can chat one-on-one with Teams users, and vice versa. An interoperability chat needs to go through an interoperability gateway that's part of Teams cloud services (and therefore only exists online). Interoperability chats are plain text: rich text and emoticons aren't supported. Users in Teams and in Skype for Business are notified that the conversation is an interoperability conversation.
- Skype for Business users can make one-on-one voice and video calls to Teams users, and vice versa.

   > [!IMPORTANT]
   > Interoperability experiences with an on-premises deployment of Skype for Business require that the on-premises environment is in hybrid mode with Microsoft 365 Skype for Business.

These interoperability experiences are available to and between users who have one of the following coexistence modes assigned: 

- Skype for Business with Teams Collaboration
- Skype for Business with Teams Collaboration and meetings
- Skype for Business Only
- TeamsOnly

There is no interoperability for users in Islands mode.

## Native interoperability experience limitations

Because of the difference in protocols and technology, it is not possible to support all capabilities natively. Specifically, the following capabilities are not available:

- Markdown, rich text, and the full emoticon set aren't supported either from Teams or Skype for Business. Other native features of the compose box in Teams chats aren't supported.
- Screen sharing (desktop or app sharing) between Teams and Skype for Business isn't supported natively. However, it is supported through interoperability escalation.
- Group chats (multiple-party conversations) in Teams can only include participants who are using Teams.
- Multiple-party IM conversations (group chats) in Skype for Business can only include participants who are using Skype for Business. However, interoperability escalation to multiple-party is available from Skype for Business.
- Escalating an ongoing peer-to-peer voice or video call to a multiple-party call involving both Teams and Skype for Business users isn't supported.
- File transfer for two-party chats, or file attachment in group chats, from Teams to Skype for Business—and vice versa—aren't supported.
- There is no interoperability with Skype for Business Persistent Chat.

For all these limitations (except for Persistent Chat), one possible workaround is for one user to start a meeting and invite the other users to join it.

This workaround is the basis for interoperability escalation. In particular, screen sharing and escalation to multiparty are not achievable natively but they are supported via interoperability escalation.

## Interoperability escalation experiences

Interoperability escalation consists in supplementing the native interoperability capabilities with managed escalations to meetings. Meetings offer rich experiences available to anyone, regardless of which client they have.

When interoperability escalation is triggered by the Teams user, a Teams meeting is created. When it is triggered by the Skype for Business user, a Skype for Business meeting is created. In both cases, the meeting created is a Meet now meeting, which is not reflected on the user's calendar.

The other party receives the meeting join link through interoperability chat and joins by clicking that link. If the Skype for Business user has a Teams account and is invited by the Teams user, they will join the meeting authenticated. Otherwise, they will join as an anonymous participant. Conversely, Teams users almost always have a Skype for Business account and a Skype for Business client they can use to join a Skype for Business meeting as an authenticated participant, but they might also join as an anonymous participant, for example using the Skype Meeting App.

Once the parties have joined the meeting, they can conduct any activity supported in meetings, such as desktop or content sharing, file sharing or transfer, adding other participants, and so on.

## Interoperability escalation from Skype for Business

Interoperability and interoperability escalation from Skype for Business were updated in the July 2019 build of monthly C2R. Previously, Skype for Business did not have advance awareness that the remote party was using Teams. It only surmised that from the signaling received after a session was established.

When the signaling indicated that the response came from (or through) the interoperability gateway, it would display the yellow business bar (banner) indicating the other party was not using Skype for Business. With the evolution of our service, this resulted in false positives where Skype for Business users would see the business bar when they were connected to the Cloud Voicemail Service or other cloud voice services, rather than to an actual TeamsOnly user.

To prevent these false positives, the presence service is now informing the Skype for Business client when the other party is a TeamsOnly actual user. This allows Skype for Business to be aware that it needs to create an interoperability conversation ahead of it having been created, and the conversation window is specific to interoperability.

:::image type="content" source="../media/interop-create-conversation.png" alt-text="Screen shot showing a message that the user is not longer using Skype for Business and some features may not work." lightbox="../media/interop-create-conversation.png":::

If the Skype for Business user wanted to share their desktop, they would be informed that a meeting will start and guided through the steps.

:::image type="content" source="../media/start-meeting-with-teams-user.png" alt-text="Screen shot showing the messages that screen sharing will start with Teams users." lightbox="../media/start-meeting-with-teams-user.png":::

Meanwhile, the Teams user receives an incoming chat message with the link to the meeting and is guided to join.

This escalation to a Skype for Business meeting is available for both in-tenant interoperability and cross-tenant federated calls and chats. It is on by default and there is no setting the administrator has to provision.

## Interoperability escalation from Teams

Interoperability escalation from Teams to a Teams meeting is now available when the Teams user selects the desktop sharing button in an in-tenant interoperability thread with a Skype for Business user or in a cross-tenant interoperability federation thread. Interoperability escalation is supported from a 1:1 chat conversation or from a 1:1 call.

The capability is supported in the Teams desktop client for Windows, in the Teams desktop client for Mac, and in the Teams web client on browsers where content sharing is supported, while in communication with any Skype for Business client version.

In interoperability threads, and in federation interoperability threads, the Teams user now has the controls (button) to start content sharing. When the Teams user selects the button, they are presented with an additional menu that informs them that to share content, they will need to start a Teams meeting.

If the users were in a call, the menu also warns them that their current call between Teams and Skype for Business will be terminated as they are put into a Teams meeting. If they so choose, they can warn the Skype for Business user prior to accepting.

:::image type="content" source="../media/meeting-with-skype-user.png" alt-text="Screen shot of Teams warning message canceling call and joining user to a Teams call." lightbox="../media/meeting-with-skype-user.png":::

Upon acceptance, they are put in the Teams meeting; they must start sharing from the sharing tray in the meeting.

Meanwhile, the Skype for Business user receives an incoming chat message with the link to the meeting and is guided to join.

This escalation to a Teams meeting is available for both in-tenant interoperability and cross-tenant federated calls and chats. It is on by default and there is no setting the administrator has to provision. However, an administrator can switch this functionality off by using PowerShell.

   ```PowerShell
   Set-CsTeamsMeetingPolicy -Identity HrMeetingPolicy -AllowMeetNow $False
   ```
