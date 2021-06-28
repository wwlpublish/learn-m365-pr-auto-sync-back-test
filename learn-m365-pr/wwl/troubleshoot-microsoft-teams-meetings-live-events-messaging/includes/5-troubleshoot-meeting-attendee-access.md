When users attempt to join meetings, they might encounter problems. These problems are often related to policy settings. 

## Review attendee access settings

To verify the settings for attendee access, open the appropriate meeting policy and navigate to **Participants & guests**. 

:::image type="content" source="../media/guest-settings.png" alt-text="A screenshot that displays the Participants & guests section of a meeting policy. Default settings are displayed.":::


The following section describes access policy settings. 

- **Let anonymous people start a meeting**. Enables an unauthenticated user to start a meeting. This is a per-organizer setting. 
- **Automatically admit people**. Determines who can be automatically admitted to a meeting. Defaults to **People in my organization and guests**. This is a per-organizer setting. You can choose from the following options: 

   - Everyone
   - People in my organization and guests
   - People in my organization, trusted organizations, and guests
   - People in my organization
   - Organizer only
   - Invited users only

- **Allow dial-in users to bypass the lobby**. You can only enable this setting when the preceding setting is not configured as **Everyone**. This is a per-organizer setting.

## Troubleshoot the Teams client

Occasionally, users can experience problems that are related to the Teams client. This might be an authentication issue to Teams itself rather than a specific issue with joining a particular meeting. In these instances, consider using the following guidance to try to pinpoint and resolve the issue. 

### Verify the correct account is selected

The desktop and mobile Teams clients support the use of multiple accounts. For example, a user can associate a personal account and multiple work or school accounts with Teams. If they are using the incorrect account for a scheduled meeting, Teams might be attempting to authenticate as a guest, anonymous, or external user. To verify and resolve this issue, open the Teams client and switch accounts:

- To do this in the mobile app, tap the account picture in Teams, and then, under the Accounts and Orgs heading, select the correct account. The user might need to provide credentials to sign in. 
- To do this in the desktop app, select the account picture and then select the appropriate account. The user might need to provide credentials to sign in.

### Clear client cache

If you experience persistent sign in issues when joining meetings, consider clearing the desktop client cache. 

1. In File Explorer, navigate to **%appdata%\Microsoft\Teams**.
2. Open the **Cache** folder and delete its contents.
3. Restart Teams and try to sign in to your meeting.
4. If that doesn’t resolve the issue, in **%appdata%\Microsoft\Teams**, consider deleting the contents of the following subfolders:

    - \application cache\cache
    - \blob_storage
    - \databases
    - \GPUcache
    - \IndexedDB
    - \Local Storage
    - \tmp

5. Restart Teams and try to sign in to your meeting.

> [!TIP]
> If you are able to connect to a meeting using the Teams Web App, that suggests an issue with the desktop client. Consider using an InPrivate Browsing session to join the meeting.