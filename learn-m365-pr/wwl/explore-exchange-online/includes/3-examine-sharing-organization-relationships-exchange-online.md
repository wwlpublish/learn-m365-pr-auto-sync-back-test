Employees in one organization may need to coordinate schedules with employees in another organization. They may also need to coordinate with friends and family members so they can work together on projects or plan social events. With Microsoft 365, administrators can set up different levels of calendar access in Exchange Online to allow businesses to collaborate with other businesses and to let users share their schedules with others.

Exchange Online supports the following sharing scenarios:

:::row:::
  :::column:::
    **Sharing goal**
  :::column-end:::
  :::column:::
    **Setting to use**
  :::column-end:::
  :::column:::
    **Requirements**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Share calendars with another Microsoft 365 organization.
  :::column-end:::
  :::column:::
    Organization relationships
  :::column-end:::
  :::column:::
    None, ready to configure
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Share calendars with an on-premises Exchange organization.
  :::column-end:::
  :::column:::
    Organization relationships
  :::column-end:::
  :::column:::
    The on-premises Exchange administrator has to set up an authentication relationship with the cloud (also known as "federation") and must meet minimum software requirements.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Share a Microsoft 365 user's calendar with another internet user.
  :::column-end:::
  :::column:::
    Sharing policies
  :::column-end:::
  :::column:::
    None, ready to configure
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Share a Microsoft 365 user's calendar with an Exchange on-premises user.
  :::column-end:::
  :::column:::
    Sharing policies
  :::column-end:::
  :::column:::
    The on-premises Exchange administrator has to set up an authentication relationship with the cloud (also known as "federation") and must meet minimum software requirements.
  :::column-end:::
:::row-end:::


> [!NOTE]
> Business-to-business calendar sharing is set up by creating organization relationships. User-to-user calendar sharing is set up by applying sharing policies. This unit examines business-to-business calendar sharing by using organization relationships.

### Organization relationships

An organization relationship is a one-to-one relationship between businesses. It enables users in each organization to view calendar availability information.

For example, consider the scenario where Contoso wants to set up a one-to-one relationship with Fabrikam.<br>

 -  When Contoso sets up the organization relationship, it's responsible for setting up its side of the relationship. As such, it must specify the level of Contoso information that Fabrikam users can view.
 -  Fabrikam, on the other hand, is responsible for setting up its side of the relationship. As such, it must specify the level of Fabrikam information that's visible to Contoso users. This level may be different than the level of information defined by Contoso.

> [!IMPORTANT]
> The organization relationship must be set up at both ends for calendar availability information to be shared. Contoso users will be able to schedule meetings and view the availability of Fabrikam users by adding Fabrikam user email addresses to meeting invitations. Likewise, Fabrikam users will also see the availability of Contoso users when scheduling meetings.

Organizations can specify three levels of access to its information:<br>

 -  No access.
 -  Access to availability (free/busy) time only.
 -  Access to free/busy, including time, subject, and location.

> [!NOTE]
> If users don't want to share their free/busy information with others, they can change their permissions entry in Outlook. To do so, users must go to the **Calendar Properties &gt; Permissions** tab, select one or more users/groups, and select any of the Permissions options. To completely hide their calendar, they can remove the user/group from the list of users/groups with which their calendar is shared. Their free/busy information won't be seen by internal or external users, even if an organization relationship exists. Instead, the permissions set by the user will apply.

### Create an organization relationship in Exchange Online

You should complete the following steps to create an organization relationship using the Exchange admin center:

1.  From the **Microsoft 365 admin center**, select **Exchange** in the navigation pane.
2.  In the **Exchange admin center** navigation pane, select **organization** and then select **sharing**.
3.  Under **Organization Sharing**, select **New+.**
4.  In **new organization relationship**, in the **Relationship name** box, type a friendly name for the organization relationship.
5.  In the **Domains to share with** box, type the domain for the external Microsoft 365 organization or the Exchange on-premises organization that you want to create a relationship with. If you need to add more than one domain, you can do it after you create the organization relationship by editing it.
6.  Select the **Enable calendar free/busy information sharing** check box to turn on calendar sharing with the domains you listed. Set the sharing level for calendar free/busy information and set which users can share calendar free/busy information.
7.  To set the free/busy access level, select one of the following values:
    
     -  **Calendar free/busy information with time only**
     -  **Calendar free/busy with time, subject, and location**
8.  To set which users will share calendar free/busy information, select one of the following values:
    
     -  **Everyone in your organization**
     -  **A specified security group**
9.  Select **Browse** to pick the security group from a list, and then select **OK**.
10. Select **Save** to create the organization relationship.
