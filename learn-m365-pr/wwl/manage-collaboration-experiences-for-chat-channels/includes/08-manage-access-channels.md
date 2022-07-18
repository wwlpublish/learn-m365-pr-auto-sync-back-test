Channels are places where conversations happen and where the work actually gets done. Channels are most valuable when extended with apps that include tabs, connectors, and bots that increase their value to the members of the team.

## Manage channel creation

By default, any team owner or team member can create a standard or private channel.

**Teams administrator** can restrict the creation of private or shared channels by creating a **Teams policy** that restricts private or shared channel creation.

**Team owners** can also restrict the standard or private channel creation on a per team level basis themselves. This can be handy when team owners want to retain full control of their team activity, which includes restricting members from creating private channels, which team owners in turn cannot control.

The table summarizes the controls for channel creation with different levels and channel types.

| Channel creation controls | Organization level  (Controlled by Teams admins) | team level  (Controlled by team owners)                                   |
|---------------------------|--------------------------------------------------|---------------------------------------------------------------------------|
| Standard channel          | N/A                                              | Settings in a team <br/> \>Member permissions   <br/>\>Guest permissions |
| Private channel           | Teams admin center  <br/>\> Teams policy              | Settings in a team <br/>\>Member permissions                           |
| Shared channel            | Teams admin center  <br/>\> Teams policy              | N/A                                                                       |

### Manage channel creation for a team

To restrict team members from creating standard or private channels, the team owner can follow the steps below:

1.  Sign in to one of the Microsoft Teams clients.
2.  Select the ellipsis icon (the three dots) to the right of the team and select **Manage team**.
3.  Open the **Settings** tab.
4.  Expand the menus and configure the settings.

    **Member permissions**

    -   Allow members to create and update channels
    -   Allow members to create private channels

    **Guest permissions**

    -   Allow guests to create and update channels

    :::image type="content" source="../media/team-private-channel-creation-restriction.png" alt-text=" Screenshot of managing member permissions.":::

## Manage channel membership

Channels can be open to all team members (standard channels), selected team members (private channels), or selected people both inside and outside the team (shared channels).

### Standard channel

The team owners and members can access the standard channel. The membership of a standard channel is inherited from the parent team. Team members can add other members to a **public team** and need to send request to team owner for adding members to a **private team**.

Teams admins can use **sensitivity labels** to protect and regulate access to sensitive organizational content created during collaboration within teams. You can control the following access to standard channels by applying a sensitivity label to a team.

1.  **Set the privacy level (public or private) for teams**

    For example, you create and publish a sensitivity label named "Confidential" that has the label privacy option configured as **Private**. As a result, any team that's created with this label must be a private team.

    When a user creates a new team and selects the **Confidential** label, the only privacy option that's available to the user is **Private**. Other privacy options such as Public and Org-wide aren't available for the user to select:

    When the team is created, the sensitivity label is visible to users in the upper-right corner of channels in the team.

2. **Control guest access to teams**

    You can use sensitivity labels to control guest access to your teams. Teams created with a label that doesn't allow guest access are only available to users in your organization. People outside your organization can't be added to the team

Admins can also go to the **Org settings** in **Microsoft 365 admin center** to control the following **guest access**:

-   Let group owner add people outside your organization to Microsoft 365 Groups as guests.
-   Let guest group members access group content.

### Private channel

-   The person who creates a private channel is the **private channel owner.**
-   Only the private channel owner can directly add or remove people from it. (You can add more than one owner if you want.)
-   A private channel owner can add any team member to a private channel they created, including guests.
-   Only the private channel owners and members can access the channel.

### Shared channel

-   Only **team owners** can create a shared channel. Team members and guests can't create them. The person who creates a shared channel becomes the **shared channel owner.**
-   Only the shared channel owner can directly add or remove people from it. (You can add more than one owner if you want.)
-   A shared channel owner can add anyone from the organization or people outside your organization to a shared channel. Guests (people with Azure Active Directory guest accounts in your organization.) can't be added to a shared channel.
-   Only the shared channel owners and members can access the channel.

**Note: Team owners** can see the names of all **private** and **shared** channels in their team and can also delete any channel in the team. Team owners can't see the files in a private or shared channel or the conversations and member list of a private or shared channel unless they are members of that channel.

## Channel owner and member actions

The following table outlines what actions owners, members, and guests can do in private and shared channels.

| **Action**                             | **Team owner** | **Team member** | **Team guest** | **Private/Shared channel owner**         | **Private/Shared channel member** | **Private/Shared channel external participant** |
|----------------------------------------|----------------|-----------------|----------------|------------------------------------------|-----------------------------------|-------------------------------------------------|
| Delete private/shared channel          | Yes            | No              | No             | Yes                                      | No                                | No                                              |
| Leave private/shared channel           | N/A            | N/A             | N/A            | Yes unless they are the last owner       | Yes                               | Yes                                             |
| Edit private/shared channel            | No             | N/A             | N/A            | Yes                                      | No                                | No                                              |
| Restore deleted private/shared channel | Yes            | No              | No             | Yes                                      | No                                | No                                              |
| Add members                            | No             | N/A             | N/A            | Yes                                      | No                                | No                                              |
| Edit settings                          | No             | N/A             | N/A            | Yes                                      | No                                | No                                              |
| Manage tabs and apps                   | No             | N/A             | N/A            | Yes, apps must be installed for the team | Channel owner controlled          | No                                              |

## Considerations around file access in channels

Each **private** or **shared channel** has its own SharePoint site. The separate site is to ensure access to channel files is restricted to only members of the shared channel. These sites are created with a document library by default, and can be easily enhanced to a full-featured site through the site management interface.

Membership to the site owner and member groups are kept in sync with the membership of the private or shared channel. Site permissions for a channel site can't be managed independently through SharePoint.

Files, folders, and OneNote notebooks in a channel can be shared with people outside the channel by using standard SharePoint file sharing.

If a user is granted access to a file, folder, or notebook in a private or shared channel through SharePoint, removing the user from the team or shared channel won't remove the user's access to the file, folder, or notebook.

If an existing notebook is added as a tab to a private or shared channel, access to the private or shared channel isn't changed and the notebook retains its existing permissions.
