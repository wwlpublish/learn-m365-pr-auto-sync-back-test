Microsoft Purview Information Barriers (IBs) are policies that an admin can configure to prevent individuals or groups from communicating with each other. IBs are useful if, for example, one department is handling information that shouldn't be shared with other departments. IBs are also useful when a group needs to be isolated or prevented from communicating with anyone outside of that group.

The Shared channels feature in Microsoft Teams is supported by information barriers. Depending on the type of sharing, information barriers policies may restrict sharing in certain ways. For more information about shared channels and information barriers behavior, see [Information barriers and Shared Channels](/microsoftteams/information-barriers-shared-channels?azure-portal=true).

For Microsoft Teams, information barriers can determine and prevent the following kinds of unauthorized collaborations:

 -  Adding a user to a team or channel
 -  User access to team or channel content
 -  User access to 1:1 and group chats
 -  User access to meetings
 -  Prevents lookups and discovery, users won't be visible in the people picker.

Organizations may want to use IBs in situations like these within Microsoft Teams:

 -  A team must be prevented from communicating or sharing data with a specific other team.
 -  A team must not communicate or share data with anyone outside of the team.

The Information Barrier Policy Evaluation Service determines whether a communication complies with IB policies.

### Information barrier triggers

IB policies are activated when the following Teams events take place:

 -  **Members are added to a team**. Whenever an organization adds a user to a team, the user's policy must be evaluated against the IB policies of other team members. After the user is successfully added, the user can perform all functions in the team without further checks. If the user's policy blocks them from being added to the team, the user won't show up in search.
    
    :::image type="content" source="../media/information-barriers-add-members-dd5b65f6.png" alt-text="Screenshot of searching for a new member to add to a team and finding no matches to the user's name.":::
    
 -  **A new chat is requested**. Each time that a user requests a new chat with one or more other users, the chat is evaluated to verify that it isn't violating any IB policies. If the conversation violates an IB policy, then the conversation isn't started.
    
    Here's an example of a 1:1 chat.
    
    :::image type="content" source="../media/information-barriers-one-one-chat-ba337053.png" alt-text="Screenshot showing blocked communication in a one on one chat in Microsoft Teams.":::
    
    
    Here's an example of a group chat.
    
    :::image type="content" source="../media/information-barriers-group-chat-a1dc4917.png" alt-text="Screenshot showing group chat in Microsoft Teams, where an admin has added two users to the chat.":::
    
 -  **A user is invited to join a meeting**. When a user is invited to join a meeting, the IB policy that applies to the user is evaluated against the IB policies that apply to the other team members. If there's a violation, the user won't be allowed to join the meeting.
    
    :::image type="content" source="../media/information-barriers-meeting-20bda8ca.png" alt-text="Screenshot showing the message a user receives when they're blocked from joining a call in Microsoft Teams.":::
    
 -  **A screen is shared between two or more users**. When a user shares a screen with other users, the sharing must be evaluated to ensure that it doesn't violate the IB policies of other users. If an IB policy is violated, the screen share won't be allowed.
    
    Here's an example of screen share before the policy is applied.
    
    :::image type="content" source="../media/ib-before-screen-share-policy-501b0605.png" alt-text="Screenshot showing when a user shares a screen with other users before a policy is applied.":::
    
    
    Here's an example of screen share after the policy is applied. The screen share and call icons aren't visible.
    
    :::image type="content" source="../media/ib-after-screen-share-policy-34a7a7e0.png" alt-text="Screenshot showing when a user is blocked when trying to share a screen with other users after a policy is applied.":::
    
 -  **A user places a phone call in Teams**. Whenever a user initiates a voice call (through voice over IP, or VOIP) to another user or group of users, the call is evaluated to ensure that it doesn't violate the IB policies of other team members. If there's any violation, the voice call is blocked.
 -  **Guests in Teams**. IB policies apply to guests in Teams, too. If guests must be discoverable in an organization's global address list, see [Manage guest access in Microsoft 365 Groups](/microsoft-365/admin/create-groups/manage-guest-access-in-groups?azure-portal=true). Once guests are discoverable, the organization can define IB policies.

### How policy changes affect existing chats

When the IB policy administrator makes changes to a policy, or when a policy change is activated because of a change to a user's profile (such as for a job change), the Information Barrier Policy Evaluation Service automatically searches the members to ensure their membership in the team doesn't violate any policies.

If there's an existing chat or other communication between users, and a new policy is set or an existing policy is changed, the service evaluates existing communications to ensure the communications are still allowed to occur.

 -  **1:1 chat**. If communication between two users is no longer allowed (because of application to one or both users of a policy that blocks communication), further communication is blocked. Their existing chat conversations become read-only.
    
    Here's an example that shows the chat is visible.
    
    :::image type="content" source="../media/ib-before-1-1chat-policy-f4d5d521.png" alt-text="Screenshot showing when a user chat is available before an information barrier policy is applied.":::
    
    
    Here's an example that shows the chat is disabled.
    
    :::image type="content" source="../media/ib-after-1-1chat-policy-86f43252.png" alt-text="Screenshot showing when a user chat is disabled after an information barrier policy is applied.":::
    
 -  **Group chat**. If communication from one user to a group is no longer allowed (for example, because a user changed jobs), the user—along with the other users whose participation violates the policy—may be removed from group chat, and further communication with the group won't be allowed. The user can still see old conversations. However, they won't be able to see or participate in any new conversations with the group. If the new or changed policy that prevents communication is applied to more than one user, the users who are affected by the policy may be removed from group chat. They can still see old conversations.
    
    In this example, Enrico moved to a different department within the organization and is removed from the group chat.
    
    :::image type="content" source="../media/information-barriers-user-changes-job-201f5898.png" alt-text="Screenshot of a group chat from which a user has been removed.":::
    
    
    Enrico can no longer send messages to the group chat.
    
    :::image type="content" source="../media/information-barriers-user-changes-job-2-5c817b85.png" alt-text="Screenshot of not being able to send messages to group chat because the user was removed from the group.":::
    

 -  **Team**. Any users who have been removed from the group are removed from the team. As such, they won't be able to see or participate in existing or new conversations.

### Information barrier modes and Teams

Information barriers mode help strengthen who can be added to or removed from a Team. When an organization uses information barriers with Microsoft Teams, the following IB modes are supported:

 -  **Open**. This configuration is the default IB mode for all existing groups that were provisioned before information barriers were enabled. In this mode, there are no IB policies applicable.
 -  **Implicit**. This configuration is the default IB mode when a Team is provisioned after enabling Information barriers. Implicit mode allows an organization to add all compatible users in the group.
 -  **Owner Moderated**. This mode is set on a team when you want to allow collaboration between incompatible segment users that are moderated by the owner. The team owner can add new members per their IB policy.

Teams created before activating an information barrier policy in an organization's tenant are automatically set to **Open** mode by default. Once the organization activates IB policies on its tenant, it's required to update the mode of its existing teams to **Implicit** to ensure that existing teams are IB-compliant.

Organizations should use the **Set-UnifiedGroup** cmdlet with the **InformationBarrierMode** parameter that corresponds to the mode it wants to use for its segments. The allowed values for the **InformationBarrierMode** parameter are **Open, Implicit,** and **Owner Moderated**.

For example, to configure the **Implicit** mode for a Microsoft 365 Group, an organization should use the following PowerShell command:

```powershell
Set-UnifiedGroup -InformationBarrierMode Implicit

```

**Additional resource**. To update the mode from **Open** to **Implicit** for all existing teams, use this [PowerShell script](/microsoftteams/information-barriers-mode-script?azure-portal=true).

If an organization changes the Open mode configuration on existing Teams-connected groups to meet compliance requirements, it must [update the IB modes](/sharepoint/information-barriers#view-and-manage-ib-modes-as-an-administrator-with-sharepoint-powershell?azure-portal=true) for associated SharePoint sites connected to the Teams team.

### Known Issues

The following sections identify known issues when implementing information barriers in Microsoft Teams.

#### Users can't join ad-hoc meetings

If IB policies are enabled, users aren't allowed to join meetings if the size of the meeting roster is greater than the meeting attendance limits. The root cause is that IB checks rely on whether users can be added to a meeting chat roster. Only when they can be added to the roster are they allowed to join the meeting. A user joining a meeting once adds that user to the roster. As such, the roster can fill up fast for recurring meetings.

Once the chat roster reaches the meeting attendance limits, more users can't be added to the meeting. If IB is enabled for the organization and the chat roster is full for a meeting, new users (those users who aren't already on the roster) aren't allowed to join the meeting. But if IB isn't enabled for the organization and the meeting chat roster is full, new users (those users who aren't already on the roster) are allowed to join the meeting. However, they won't see the chat option in the meeting.

Until the size of meeting chat rosters is increased, a short-term solution is to remove inactive members from the meeting chat roster to make space for new users.

#### Users can't join channel meetings

If IB policies are enabled, users aren't allowed to join channel meetings if they aren't a member of the team. The root cause is that IB checks rely on whether users can be added to a meeting chat roster. Only when they can be added to the roster are they allowed to join the meeting. The chat thread in a channel meeting is available to Team/Channel members only. Non-members can't see or access the chat thread.

If IB is enabled for the organization and a non-team member attempts to join a channel meeting, that user isn't allowed to join the meeting. However, if IB isn't enabled for the organization and a non-team member attempts to join a channel meeting, the user is allowed to join the meeting. However, they won't see the chat option in the meeting.

#### Maximum number of segments allowed in an organization

Each organization can set up to 100 segments when configuring IB policies. There's no limit on the number of policies that can be configured.

#### IB policies don't work for federated users

If an organization allows federation with external organizations, the users of those external organizations won't be restricted by IB policies. If users of an organization join a chat or meeting organized by external federated users, then IB policies also won't restrict communication between users of the organization.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”