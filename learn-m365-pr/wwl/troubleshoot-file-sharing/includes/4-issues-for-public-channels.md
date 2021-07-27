## Verify SharePoint access permissions 

To verify SharePoint access permissions for public channels, in Teams select a public channel and select the Files tab. From the top navigation bar, select **Open in SharePoint** to open the relevant SharePoint document library. In SharePoint, from the top navigation select **Settings** (gear icon) and then select **Site permissions**. In the **Permissions** blade you can Invite people to collaborate in this group, view Site owners, Site members, and Site visitors.

Select **Change how members can share to open the Site sharing settings** blade. In the **Site sharing settings** blade you can define sharing permissions, turn access requests on or off, and define whether or not access requests can be sent by email. You can also add a custom message to the request access page.

Select **Advanced permissions** settings to view the SharePoint permissions page for the site.

## Steps for verifying SharePoint access permissions 

In the following interactive exercise you will start from the Teams client, and a public channel. You will learn how to get troubleshooting information by verifying file access permissions. 

[Troubleshoot file sharing interactive walkthrough](https://edxinteractivepage.blob.core.windows.net/edxpages/M365%20Troubleshoot/Troubleshooting%20files/index.html)

## Determine whether the name for a channel or team has been changed

Owners and members of team can change the name of a channel by selecting **More options** next to the **Channel name > Edit this channel**.

If **Edit this channel** is not visible, the team owner has changed the members permissions.

## Troubleshooting

### A user can't change the name of the General channel

This is by design — the General cannot be amended or deleted.

### A user has changed a channel name and cannot find shared files

This should not happen. Users should be able to change a channel name, without affecting shared files. Try renaming the channel back to its original name. Alternatively, search for the old channel name in SharePoint.

## Confirm that the SharePoint site collection link is intact 

You can check that the SharePoint site collection link is correct. In Teams, select the files tab of a public channel, and in the top navigation bar select **Copy link**. In the **Get link** dialog box, select the **SharePoint** tab and either copy the link or check the link.

## Troubleshoot file synchronization issues and missing files

### A user has shared a file in Teams, but it is not visible in the files tab

All Teams files are stored in a SharePoint document library.  From the top navigation select **Open in SharePoint** to find out if the file is visible in SharePoint. Check the SharePoint folder name; it should be the same as the Teams channel name. Also check whether you have reached the shared file limit.

### A user has set up file sync but cannot sync shared files in Teams with their OneDrive

Check that OneDrive is running, and the user has signed into OneDrive. OneDrive will show a padlock icon if the file or folder has settings that prevent it from syncing. Check that the sharing limit has not been reached, or that the file is not too large. See **Learn more** for details of current Restrictions and limitations in OneDrive and SharePoint.
