Organizations that use a split permissions model can choose between RBAC split permissions and Active Directory split permissions. The recommended model for most deployments is RBAC split permissions. However, organizations should still analyze and understand their individual business needs to determine whether the RBAC model provides the best solution for managing Exchange permissions.

### Configure RBAC split permissions

The RBAC security model modifies the default management role assignments. This design enables organizations to separate who can create security principals in the Active Directory domain partition from those users who administer the Exchange organization data in the Active Directory configuration partition. The following guidelines control the configuration of RBAC split permissions:

 -  Security principals, such as users with mailboxes and distribution groups, can be created by administrators who are members of the Mail Recipient Creation and Security Group Creation and Membership roles.
 -  These permissions remain separate from the permissions required to create security principals outside of the Exchange management tools.
 -  Exchange administrators who aren't assigned the Mail Recipient Creation or Security Group Creation and Membership roles can still modify Exchange-related attributes on security principals.
 -  Active Directory administrators also have the option of using the Exchange management tools to create Active Directory security principals.

Exchange servers and the Exchange Trusted Subsystem also have permissions to create security principals in Active Directory for users and third-party programs that integrate with RBAC.

An organization should consider using RBAC split permissions if the following conditions are true:

 -  The organization allows security principals to be created using tools besides the Active Directory management tools.
 -  The organization allows security principals to be created by users who aren't assigned specific Active Directory permissions.
 -  The organization allows services, such as Exchange servers, to create security principals.
 -  The organization wants to simplify the process required to create mailboxes, mail-enabled users, distribution groups, and role groups by allowing their creation from within the Exchange management tools.
 -  The organization wants to manage the membership of distribution groups and role groups within the Exchange management tools.
 -  The organization has third-party programs that require Exchange servers to create security principals on their behalf.

If your organization requires a complete separation of Exchange and Active Directory administration where no Active Directory administration can be performed using Exchange management tools or by Exchange services, see the Configure Active Directory Split Permissions section later in this unit.

Switching from shared permissions to RBAC split permissions is a manual process. The permissions required to create security principals must be removed from the role groups that are granted them by default.

The following table shows the roles that enable the creation of security principals in Exchange and the management role groups they're assigned to by default.

:::row:::
  :::column:::
    **Management role**
  :::column-end:::
  :::column:::
    **Role group**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail Recipient Creation role
  :::column-end:::
  :::column:::
    Organization Management
Recipient Management
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Security Group Creation and Membership role
  :::column-end:::
  :::column:::
    Organization Management
  :::column-end:::
:::row-end:::


To configure RBAC split permissions, you must complete the following tasks:

1.  Disable Active Directory split permissions if it's enabled.
2.  Create a role group, which will contain the Active Directory administrators that can create security principals.
3.  Create regular and delegating role assignments between the Mail Recipient Creation role and the new role group.
4.  Create regular and delegating role assignments between the Security Group Creation and Membership role and the new role group.
5.  Remove the regular and delegating management role assignments between the Mail Recipient Creation role and the Organization Management and Recipient Management role groups.
6.  Remove the regular and delegating role assignments between the Security Group Creation and Membership role and the Organization Management role group.

After doing this, only members of the new role group that you create can create security principals, such as mailboxes. The new group can only create the objects. It can't configure the Exchange attributes on the new object.

An Active Directory administrator who's a member of the new group must create the object. An Exchange administrator must then configure the Exchange attributes on the object.

Exchange administrators can't use the following cmdlets:

 -  New-Mailbox
 -  New-MailContact
 -  New-MailUser
 -  New-RemoteMailbox
 -  Remove-Mailbox
 -  Remove-MailContact
 -  Remove-MailUser
 -  Remove-RemoteMailbox

### Configure Active Directory split permissions

With Active Directory split permissions, the creation of security principals in the Active Directory domain partition, such as mailboxes and distribution groups, must be performed using Active Directory management tools.

Several changes are made to the permissions granted to the Exchange Trusted Subsystem and Exchange servers to limit what Exchange administrators and servers can do. This limitation is because Exchange completes the actions in Active Directory using these contexts, with RBAC filtering administrative permissions, rather than as the actual administrator accounts themselves.

The following changes in functionality occur when you enable Active Directory split permissions:

 -  Creation of mailboxes, mail-enabled users, distribution groups, and other security principals is removed from the Exchange management tools.
 -  Adding and removing distribution group members can't be done from the Exchange management tools.
 -  All permissions granted to the Exchange Trusted Subsystem and Exchange servers to create security principals are removed.
 -  Exchange servers and the Exchange management tools can only modify the Exchange attributes of existing security principals in Active Directory.

For example, to create a mailbox with Active Directory split permissions enabled, an organization must:

1.  Create a user using Active Directory tools by a user with the required Active Directory permissions.
2.  Use the Exchange management tools to mailbox enable the user.

> [!NOTE]
> Only the Exchange-related attributes of the mailbox can be modified by Exchange administrators using the Exchange management tools.

An organization should consider using Active Directory split permissions if the following conditions are true:

 -  The organization requires security principals to be created using only the Active Directory management tools.
 -  The organization requires security principals to be created only by users who are assigned specific Active Directory permissions.
 -  The organization wants to separate the ability to create security principals from those users who manage the Exchange organization.
 -  The organization wants to use Active Directory management tools to complete all distribution group management, including creation of distribution groups and adding and removing members of those groups.
 -  The organization doesn't want Exchange servers, or third-party programs that use Exchange on their behalf, to create security principals.

After you enable Active Directory split permissions, the following cmdlets are no longer available:

 -  New-Mailbox
 -  New-MailContact
 -  New-MailUser
 -  New-RemoteMailbox
 -  Remove-Mailbox
 -  Remove-MailContact
 -  Remove-MailUser
 -  Remove-RemoteMailbox

After you enable Active Directory split permissions, the following cmdlets are accessible, but you can't use them to create distribution groups or modify distribution group membership:

 -  Add-DistributionGroupMember
 -  New-DistributionGroup
 -  Remove-DistributionGroup
 -  Remove-DistributionGroupMember
 -  Update-DistributionGroupMember

Some cmdlets may offer only limited functionality when used with Active Directory split permissions. This limitation is because the cmdlets may allow you to configure:

 -  Recipient objects that are in the domain Active Directory partition.
 -  Exchange configuration objects that are in the configuration Active Directory partition.
 -  Exchange-related attributes on objects stored in the domain partition.

Attempts to use the cmdlets to create objects or modify non-Exchange-related attributes on objects in the domain partition will result in an error. For example, the Add-ADPermission cmdlet will return an error if you attempt to add permissions to a mailbox.

However, the Add-ADPermission cmdlet will succeed if you configure permissions on Exchange related objects, such as a Receive connector. This task will succeed because a mailbox is stored in the domain partition while Receive connectors are stored in the configuration partition.

Additionally, the associated features in the Exchange admin center and Outlook Web App, such as the New Mailbox wizard, will no longer be available. If you try to use them, it will generate an error. However, Exchange administrators can create and manage Exchange-specific objects, such as transport rules, and so on.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.