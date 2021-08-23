SharePoint and OneDrive are primary content services in Microsoft 365. Microsoft Teams uses SharePoint and OneDrive in Microsoft 365 for content collaboration. Team files are stored in SharePoint sites, and chat files are stored in OneDrive. Additionally, all Teams meeting recordings are saved to OneDrive or SharePoint.

If users aren't assigned SharePoint licenses, they don't have OneDrive storage in Microsoft 365. File sharing works in standard channels, but users won't be able to share files in chats without OneDrive storage in Microsoft 365.

By storing the files in the SharePoint document library and OneDrive, all compliance rules configured at the tenant level will be followed.

## SharePoint in Microsoft Teams

Each team in Microsoft Teams has a SharePoint team site associated. Files shared within a conversation are automatically added to the document library. 

Permissions and file security options set in SharePoint are automatically reflected within Teams. Permissions for the SharePoint team site are best managed through the associated Microsoft 365 group or Teams team. 

For public teams, the SharePoint team site is provisioned with **"Everyone except external users"** site members access. The public team isn't displayed in Teams for people who aren't members of that team. However, they can access content on the SharePoint team site using the URL of the SharePoint team site. 

Each channel in a team gets a **folder** within the default **Shared Documents** library. Depending on the channel type, the channel folder could be in the different SharePoint team sites. 

* **Standard Channel**

    Each standard channel, including the **General** channel (the default channel for each team), gets a **folder** within the default SharePoint team site document library. 

* **Private Channel**
    
    Each private channel has a **folder** in Shared Document library of its own **SharePoint team site** that's separate from the parent team site. This ensures access to private channel files is restricted to only members of the private channel.

    A private channel SharePoint site is created in the same geographic region as the SharePoint site of the parent team. Site membership is sync with the membership of the private channel within Teams. 

Additionally, the recordings for channel meetings are stored in the channel folder that's in the document library for that team. The person who started the recording has edit permissions. Permissions for all other channel members are inherited from the Teams channel permissions. If a user can access the channel in Teams, they can access the meeting recording just like any other file saved in the channel.

The following table shows the scenarios of Teams content stored in SharePoint. 

| **Scenario**| **Storage location** |
| - |-|
| Files shared in Teams channels. <br/>For example, post files or pictures to the channel conversation. | Files are stored in the **channel folder** of the SharePoint document library. |
| Files sent to a channel.  <br/>For example, send emails with file attachments to the channels email address.| Files are stored in the subfolder **Email Messages** of the channel folder in the SharePoint document library. |
|Channel meeting recordings| Channel meeting recordings are stored in a folder named **Recordings** in the channel folder that's in the document library for that team.|

‎:::image type="content" source="../media/teams-content-sharepoint.png" alt-text="A graphic explains the structure of Teams Channels in SharePoint":::

## OneDrive in Microsoft Teams

For every user, the OneDrive folder **Microsoft Teams Chat Files** is used to store all files shared within private chats with other users (1:1 or 1:many), with permissions configured automatically to restrict access to the intended user only.

Additionally, the recordings for non-channel meetings are stored in a folder named **Recordings** in the OneDrive for the person who **started** the meeting recording.  

* The **meeting organizer** and **the person who started the recording** will have **edit permissions** and can share the recording.

* People who were invited to the meeting will have **view permissions**.

* Guests **will not have access by default** - but they can request access or the recording can be shared with external users proactively.

The following table shows the scenarios of Teams content stored in OneDrive.

| **Scenario**| **Storage location** |
| - |-|
| Files shared in private chats(1:1 or 1:many chats.)| Files are stored in the sender's OneDrive folder **Microsoft Teams Chat Files**.  |
| Non-channel meeting recordings| Meeting recordings are stored in a folder named **Recordings** in the OneDrive for the person who started the meeting recording.| 


‎:::image type="content" source="../media/teams-content-onedrive.png" alt-text="A graphic explains the structure of Teams chat in OneDrive":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”