

Managing Teams settings includes several options to control basic features of Microsoft Teams, including notifications and feeds, tagging, email integration, cloud storage options, and devices. These settings are organizational-wide settings and apply to all users and teams in an organization. You can go to the Teams admin center, select **Teams** > **Teams settings** for the settings page.  

:::image type="content" source="../media/teams-settings.png" alt-text=" Screenshot of Microsoft Teams admin center: Teams settings"::: 


## Notifications and feeds

Activity feed is a summary of everything that's happened in the team channels users follow. You can control whether suggested feeds appear in users' activity feed in Teams.

Suggested feeds may improve open communication and collaboration, even between users that do not know each other.           

## Tagging

Tags let users communicate with a subset of people on a team.  There are two kinds of tags in Teams:

* Custom tags
* Tagging by shift

Tags can be added to one or more team members. After a tag is added, it can be used in @mentions by anyone on the team in a channel post to communicate with only those people who are assigned that tag. As an admin, you can control how tags are used across your organization in the Microsoft Teams admin center.


:::image type="content" source="../media/manage-tags-admin-settings.png" alt-text=" Screenshot of tagging settings in the Microsoft Teams admin center"::: 

Use the following settings to control who can add tags and how tags are used across your organization. 

- **Who can manage tags**: By default, team owners can add custom tags. You can change this setting to allow team owners and team members to create, edit, delete, and manage tags or you can turn off tags for your organization.

- **Team owners can change who can manage tags**: When you turn on the setting, team owners can set whether team members can create and manage tags within a team and the value of the **Who can manage tags** setting is the default value for each team. If you turn off the setting, the **Who can manage tags** setting can't be changed per team.

- **Suggested tags**: Use this to add a set of default tags. You can add up to 25 tags, and each tag can contain a maximum of 25 characters. Team owners and members (if the feature is enabled for them) can use these suggestions, add to them, or create a new set of tags.

- **Custom tags**: Turn on this setting to let people add tags other than the suggested default tags that you set. If this is turned off, people can only use the suggested default tags. If you turn this off, make sure that you add one or more default tags.

- **Shifts app can apply tags**: Controls if the Shift app can apply tags. Tagging by shift allows your users to reach the people on-shift in real-time. Teams automatically assigns users with tags matching their schedule and shift group name from the Shifts app, enabling dynamic role-based messaging. Notifications are sent only to those people who are on shift at the time a tag is used to start a chat or in a channel post.

## Email integration

Email integration lets people send an email to a Teams channel, and have the contents of the email displayed in the conversations for all team members to view.

* **Allow users to send emails to a channel email address**: Turn on this feature so users can send email to a channel in Teams, using the channel email address. Users can do this for any channel belonging to a team they own. Users can also send emails to any channel in a team that has adding connectors turned on for team members.

* **Accept channel email from these SMTP domains**: This setting controls users from which SMTP domains can send messages to channels. This can help to avoid spamming or unauthorized senders.

## Files

Admins can turn on or turn off file sharing and cloud file storage options.

In addition to the OneDrive and SharePoint storage included in Teams, which gives every channel a SharePoint folder users can upload and share files from cloud storage services in Teams channels and chats.  Cloud storage options in Teams currently include **Dropbox, Box, ShareFile, Google Drive, and Egnyte**. Turn on the switch for the cloud storage providers that your organization wants to use.

To add a cloud storage service to Teams:

1.  Go to Teams clients, select **Files** on the left side of Teams, and then select **Add cloud storage**.

2.  Select your cloud storage service from the list that comes up.   
    
    :::image type="content" source="../media/cloud-file-options.png" alt-text=" Screenshot of cloud file storage options in Teams client"::: 

3.  Sign in with your account. You may need to turn off your pop-up blocker first.

Now you can add files from the cloud as well as from your computer to channels.



## Organization

The Organization tab shows the org chart for the organization, so when users have a one-on-one conversation with someone, users can see who they report to and who reports to them. Admin can turn on the Organization tab, which shows the detailed organizational chart for the user's organization. 


## Devices

These settings control resource account behavior for Surface Hub devices attending Microsoft Teams meetings. Use these settings to configure authentication requirements, require a content PIN, and turn on Surface Hub resource accounts to send messages.

-   **Require a secondary form of authentication to access meeting content** – Select the level of access that users have when they enter the content PIN. This setting only applies to Skype for Business users
-   **Set content PIN** – Require users to enter this PIN to prevent unauthorized access to documents. The setting prevents an unauthorized user from joining upcoming meetings and browsing attachments. This setting only applies to Skype for Business users.
-   **Surface hub accounts can send messages** – Turn this setting **On** to allow messages to be sent from the Surface Hub resource account.


## Search by name

Microsoft Teams scoped directory search uses Exchange address book policy (APB) to allow organizations to create virtual boundaries that control how users can find and communicate with other users in their organization. You might want to use a scoped directory search in situations like these:

- Your organization has multiple companies within its tenant that you want to keep separate. 
- Your school wants to limit chats between faculty and students. 

Enable this option to turn on scoped directory searches. The configuration is a prerequisite for **Microsoft Purview Information barrier policies**.

## Safety and communications

Supervised chat allows organizations and schools to limit chat capabilities using role-based permissions. These permissions control the amount of supervision a user requires while chatting with others. 