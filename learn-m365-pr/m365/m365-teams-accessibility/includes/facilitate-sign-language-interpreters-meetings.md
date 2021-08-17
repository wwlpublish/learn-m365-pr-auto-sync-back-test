There could be users in your organization who are deaf and use sign language interpreters to effectively participate and contribute to meetings. Microsoft Teams makes it possible to include sign language interpreters in meetings.

Here, you'll learn how to enable sign language interpreters to access Microsoft Teams meetings. You'll also learn about which policies you can employ to help users who are deaf and interpreters work more effectively together.

## Enable access to meetings for interpreters

Sign language interpreters likely don't work for your organization, so granting them access to your Teams environment should be done in a way that is in line with your organization's compliance and security requirements. Microsoft's cloud solutions, including Azure Active Directory, Microsoft 365, SharePoint, and Teams allow for fine-controls for guests, so your configuration fits your security and compliance requirements.
You can invite interpreters in Microsoft Teams meetings by providing them guest access.

### Guest access

Guest access allows teams in your organization to collaborate with people outside your organization by granting them access to existing teams and channels in Microsoft Teams. Anyone with a business or personal email account, such as Outlook, Gmail, or others, can participate as a guest in Microsoft Teams with full access to team chats, meetings, and files.

As the Microsoft Teams admin, you'll control which features guests can (and can't) use in Microsoft Teams.
Guest access is an organization-wide setting in Microsoft Teams and is turned off by default. Guest access is subject to Azure Active Directory and Microsoft 365 or Office 365 service limits:

- Guests are added to your organization's Active Directory.
- To communicate with a guest, they have to be signed in to Microsoft Teams using their guest account.
- Guest users have access to more resources in Microsoft Teams--such as files, teams, and channels--than external-access (federated) users.

If you want to use guest user access, but want the flexibility to employ some specific restrictions, you can:

- Block or allow guest users from being added to any specific team in your Microsoft Teams environment.
- Block or allow guest users based on a user's domain.
- Block or allow guest access to all teams in your Microsoft Teams environment.
- Block guest users from Microsoft Teams, but still give them access to SharePoint sites for collaboration.

This short five-minute video walks you through the steps, at a high level, for turning on and enabling guest access in Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr]

### Configure meeting policy settings for guests

Use meeting policies to control the features available to meeting participants (including guest users) for meetings scheduled by users in your organization. You can use the **Global (Org-wide default)** policy that's automatically created or create and assign custom policies. These settings control which meeting participants wait in the lobby before they're admitted to the meeting and the participation level they're allowed in a meeting.

## Admit sign language interpreters to meetings

It's helpful for interpreters to join a meeting before the discussion begins, to make sure their equipment is working, their workspace is distraction-free, and they're present before their client joins the meeting. The **Automatically admit people** setting controls whether people join a meeting directly or wait in the lobby until an authenticated user admits them. This setting doesn't apply to dial in users. You should either allow everyone to bypass the lobby, or the organizer should plan to activate the meeting and admit the interpreter from the lobby several minutes before the meeting start time.

Meeting organizers can select **Meeting Options** in the meeting invitation to change this setting for each meeting they schedule.

As the admin, you can control this using the meeting options. The setting is labeled **Automatically admit people**.

:::image type="content" source="../media/microsoft-teams-admin-center-meeting-policies-automatically-admit-people.png" alt-text="Screenshot showing how to allow automatically admit people to a teams meeting.":::

You can set it to one of the following options:

| Setting value                                          | Join behavior                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Everyone**                                                 | All meeting participants join the meeting directly without waiting in the lobby.  It includes authenticated users, external users from trusted organizations  (federated), guests, and anonymous users. |
| **Everyone in your organization and federated organizations** | Authenticated users within the organization, including guest users and the users from trusted organizations, join the meeting directly without waiting in the lobby. Anonymous users wait in the lobby. |
| **Everyone in your organization**                           | Authenticated users from within the organization, including guest users, join the meeting directly without waiting in the lobby. Users from trusted organizations and anonymous users wait in the lobby. This is the default setting. |

### Allow interpreters and participants to share IP video feed  

Sign language interpreters need to be able to share their video feed with meeting participants so that users can see their interpretation, and so that the interpreters can also read signs from users who are deaf.

As an admin, you need to make sure video isn't turned off in your organization's policies. You do this by ensuring that **Allow IP video** is set to **On** in your **meeting policies**:

:::image type="content" source="../media/microsoft-teams-admin-center-meeting-policies-allow-ip-video.png" alt-text="Screenshot showing the Teams admin center meeting policies to allow IP video.":::

### Use pin video and Dynamic View to keep interpreters in view

By default, Teams switches the live stream view to whoever is talking. However, it's important for people who are deaf or hard of hearing to clearly see their sign language interpreter's video feed at all times. Teams provides **Dynamic View**, which allows users to pin up to four people's video streams so that they remain on the screen regardless of who is speaking. With **Dynamic View**, when an interpreter's video is pinned, even when other content is shared, the interpreter's video remains large and on the screen at all times.

## Learn more

[Manage meeting policies in Teams - Allow IP Video](/MicrosoftTeams/meeting-policies-in-teams#allow-ip-video)
