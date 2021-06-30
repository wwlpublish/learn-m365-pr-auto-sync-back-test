Users can chat one-to-one or in groups by selecting **New chat** at the top of the chat list and sending a message to start the chat. Users then enter the names of people they would like to add in the **To** field, up to 250 people.

:::image type="content" source="../media/new-chat.png" alt-text="Start a new chat" lightbox="../media/new-chat.png":::

Teams saves all the chat history from the first message, even if someone leaves the group.

To troubleshoot chat:

- Users can restart Teams to force a refresh.
- Check Messaging policies. From the **Teams admin center**, select **Messaging policies**. Messaging policies are used to control behavior such as whether Giphy can be used in chat, whether users can delete sent messages, and chat permissions.
- Check the **Filter** option. If users receive a high volume of chat messages, they can set the filter option to reduce the number of displayed messages. The filter can be set to display only unread messages, meeting messages, or muted conversations.
- If you want to retrieve old chat messages, from the **Office 365 Security & Compliance Admin Center > Search > Content Search > Guided Search**. Name your search, and add specific query conditions, such as **Type: IM** or **Type: Call**.
  
## OneDrive for Business

You can share most types of files in Teams, providing that the file is stored in OneDrive, another cloud storage system, or on your local device. You can share files by sending a link or sending the actual file.

Share a copy of the file by selecting **Attach** under the chat box.

Share a link of a file stored in OneDrive by right clicking the file or folder, selecting **Share** and **Copy link**. Select **Copy** to copy the link to the clipboard. Links can also be copied from Teams Files tab.

File sharing in Teams is based on the settings configured in SharePoint and OneDrive, so whatever you set up for SharePoint and OneDrive will affect sharing in Teams.

- **OneDrive admin center > Sharing** defines OneDrive for Business file sharing settings. From here you can define settings for sharing in OneDrive and SharePoint.
- **SharePoint admin center > Policies > Sharing** defines SharePoint file sharing settings.

## Troubleshooting sharing OneDrive files

### A user cannot access OneDrive

Check that the user has a license for OneDrive. A license to use OneDrive is included in Office 365 E3 and E5 subscriptions. Check whether the user has access to SharePoint; if they can access SharePoint they will also have access to OneDrive.

It can take up to 24 hours for a user to be able to access OneDrive after the correct license has been assigned. If you are pre-provisioning OneDrive for a large number of users, using PowerShell scripts, it can take several days for OneDrive to be provisioned for all users.

### A user is having trouble sharing a file in their Personal Vault

Files in a user’s Personal Vault cannot be shared. Personal Vault is a BitLocker encrypted vault designed to store personally sensitive documents. Move the file to another folder in OneDrive, and then share.

### Microsoft account needs validating

File sharing problems might be due to a Microsoft account validation issue. Go to https://account.live.com/reputationcheck to validate your Microsoft Account.

### Your sharing limit has been reached

File sharing is limited in OneDrive. You can wait before sharing a file because sharing limits are reset after 24 hours. Alternatively, upgrade to a premium subscription.

### OneDrive desktop app is not installed

When a user has the OneDrive desktop app installed on their computer, files in OneDrive will have the Share option available when they right-click on a file or folder. If the OneDrive desktop app is not installed, the Share option is not shown. OneDrive is automatically provisioned the first time a user browses to OneDrive.

### OneDrive will not sync files correctly

Reinstalling Microsoft OneDrive can sometimes resolve sync issues and resets all OneDrive settings. OneDrive will perform a full sync after the reinstallation. Users will not lose any data by uninstalling OneDrive. Any files or data in OneDrive is still available when the user signs in at OneDrive.com. See the Learn more section for more information.

## Troubleshooting file sharing in person-to-person chat

When you share a file in person-to-person chat, the file is stored in a SharePoint document library and can be viewed in the Files tab. When a used deletes a shared file, it is also deleted from the SharePoint document library.

## Troubleshoot file sharing issues

### A user does not have file access permissions

Set and check how users can share files in the **SharePoint admin center > Policies > Sharing and Access control**.

### A user cannot share a file

If a user cannot share a file, check whether file sharing has been switched off for that file type. In the **Teams admin center > Org-wide settings > Teams settings > Files**.
 
### Storage limit has been reached

Use the SharePoint admin center to amend the site storage limits for SharePoint and OneDrive. From the **SharePoint admin center**, select **Settings > SharePoint Site storage limits**. This can be set to:

- **Automatic** Lets sites use as much of your organization’s storage as needed.
- **Manual** Set specific limits for each site.

### An external user does not have permission to share a file

External sharing settings are set at the:

- Organization level in the **Azure Active Directory admin** portal
- Site level in the **SharePoint admin center**.
 
From the **SharePoint admin center > Policies > Sharing**, select how you want external users to share files:

- Who can view a file or folder link. These settings apply to SharePoint and OneDrive, but include Teams because Teams inherits permissions:
 
    - People that the user specifies
    - People within the organization
    - Anyone
    
- What people can do with a link:
    - View 
    - Edit
- The number of days after which a link will expire 
- Link permissions for files and folders
    - Files: View and edit or View
    - Folders: View, edit, and upload or View
- Other settings
    - Audit settings including showing owners the names of people who viewed their files in OneDrive
    - Allowing site owners to display the names of people who viewed files or pages in SharePoint
    - Using short links for sharing files and folders

Also check Access control for **Unmanaged devices** and **Network location** settings.

### Someone from outside your organization is having difficulty sharing a file

File sharing is not available in Teams chat with external users.

## Verify access rights for the user

The Microsoft 365 admin center allows you to verify access rights for users. From the left navigation pane, select **Users > Active users**.

You can view and manage roles and groups, as well as being able to display their sign-in activity.  

## Configure a Teams client configuration policy

The Teams Client Configuration policy allows Teams administrators to define how Teams clients work across their organization. Each organization has one Teams Client Configuration policy, including settings such as:

- Third party cloud storage solutions that your organization allows.
- Whether or not guest users can access the Teams client.
- How Surface Hub devices can interact with Skype for Business meetings.

The Teams client configuration policy is created using PowerShell cmdlets. These settings are not currently included in the Teams admin center. See the Learn more section for details of the available PowerShell cmdlets.

## Troubleshoot issues with provisioning users

When you create a new user, either on-premises or in the cloud, there is a delay before the user is provisioned in Microsoft Teams

### A user cannot access a Teams feature

Until a user is created in Teams you cannot assign Teams policies to them, and they may not have access to all Teams features. From the **Teams admin center**, from the left-hand navigation, select **Users > Active Users** to display all Active users. From the top navigation, select the three dots (…) for more options, then select **Teams setup status** from the drop-down list.You can search within the list of users to find the Teams setup status for a particular user.