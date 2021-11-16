Exchange includes several built-in role groups. These role groups provide permissions to manage specific areas in Exchange. Some role groups may overlap with other role groups.

The following table identifies each role group and whether it's available in Exchange Server, Exchange Online, or both.

:::row:::
  :::column:::
    **Role group**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Available in…**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Organization Management
  :::column-end:::
  :::column:::
    Administrators who are members of the Organization Management role group have administrative access to the entire Exchange organization. They can also complete any task against any Exchange Server object, with some exceptions, such as the Discovery Management role.
Because the Organization Management role group is a powerful role, only users or USGs that complete organizational-level administrative tasks that can potentially impact the entire Exchange organization should be members of this role group.
The administrative access doesn't include the Discovery Management role to access mailbox content.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    View-Only Organization Management
  :::column-end:::
  :::column:::
    Administrators who are members of the View Only Organization Management role group can view the properties of any object in the Exchange organization.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Recipient Management
  :::column-end:::
  :::column:::
    Administrators who are members of the Recipient Management role group have administrative access to create or modify Exchange recipients within the Exchange organization.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Help Desk
  :::column-end:::
  :::column:::
    By default, the Help Desk role group enables members to view and modify the Outlook on the web (formerly known as Outlook Web App) options of any user in the organization. These options can include modifying the user's display name, address, and phone number. They don't include options that aren't available in Outlook on the web options, such as modifying the size of a mailbox or configuring the mailbox database on which a mailbox is located.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Hygiene Management
  :::column-end:::
  :::column:::
    Members of this management role group can manage Exchange anti-spam features and grant permissions for antivirus products to integrate with Exchange.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Records Management
  :::column-end:::
  :::column:::
    Users who are members of the Records Management role group can configure compliance features, such as retention policy tags, message classifications, and transport rules.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Discovery Management
  :::column-end:::
  :::column:::
    Administrators or users who are members of the Discovery Management role group can run searches of mailboxes in the Exchange organization for data that meets specific criteria. It can also configure legal holds on mailboxes.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Public Folder Management
  :::column-end:::
  :::column:::
    Administrators who are members of the Public Folder Management role group can manage public folders on servers running Exchange Server.
  :::column-end:::
  :::column:::
    Exchange Server only
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Server Management
  :::column-end:::
  :::column:::
    Administrators who are members of the Server Management role group can configure server-specific configuration of transport, client access, and mailbox features such as database copies, certificates, transport queues and Send connectors, virtual directories, and client access protocols.
  :::column-end:::
  :::column:::
    Exchange Server only
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Delegated Setup
  :::column-end:::
  :::column:::
    Administrators who are members of the Delegated Setup role group can deploy servers running Exchange Server that have been previously provisioned by a member of the Organization Management role group.
  :::column-end:::
  :::column:::
    Exchange Server only
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Compliance Management
  :::column-end:::
  :::column:::
    Users who are members of the Compliance Management role group can configure and manage Exchange compliance settings that follow their organization's policies.
  :::column-end:::
  :::column:::
    Exchange Server and Exchange Online
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Company Administrators (TenantAdmins\_ &lt;unique value&gt;)
  :::column-end:::
  :::column:::
    The Company Administrators role group is a special role group that ties together the Global administrators Microsoft 365 role and the Organization Management role. The Company Administrators role group doesn't have any roles assigned to it. However, it's a member of the Organization Management role group and inherits the permission provided by that role group.
This role group can't be managed in Exchange Online. You can add members to this role group by adding users to the Global administrator Microsoft 365 role.
  :::column-end:::
  :::column:::
    Exchange Online only
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Help Desk Administrators (HelpdeskAdmins\_ &lt;unique value&gt;)
  :::column-end:::
  :::column:::
    The Help Desk Administrators role group doesn't have any roles assigned to it. However, it's a member of the View-Only Organization Management role group and inherits the permissions provided by that role group.
This role group can't be managed in Exchange Online. You can add members to this role group by adding users to the Password administrator Microsoft 365 role.
  :::column-end:::
  :::column:::
    Exchange Online only
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    UM Management
  :::column-end:::
  :::column:::
    Administrators who are members of the UM Management role group can manage features in the Exchange Online organization, such as UM properties on mailboxes, UM prompts, and UM auto attendant configuration.
The UM Management role isn't available in Exchange Server 2019.
  :::column-end:::
  :::column:::
    Exchange Online only
  :::column-end:::
:::row-end:::


Small organizations that have only a few administrators typically add those administrators to just the Organization Management role group. These organizations often never use another role group.

Large organizations typically have administrators who complete specific tasks administering Exchange, such as recipient or organization-wide Public Folder configuration. Those organizations usually add one administrator to the Recipient Management role group and another administrator to the Public Folder Management role group. This design enables those administrators to manage their specific areas of Exchange, but they won't have permissions to manage areas they aren't responsible for.

> [!TIP]
> If the built-in role groups in Exchange don't match the job function of your administrators, you can create custom role groups and add roles to them.

### Microsoft 365 permissions in Exchange Online

The roles in the Microsoft 365 admin center, Microsoft 365 Defender portal, and the service-specific RBAC roles in Exchange Online and SharePoint Online typically don’t interfere with each other, although there are some exceptions.

When you create a user in Microsoft 365, you can choose whether to assign various administrative roles in the Microsoft 365 admin center, such as Global administrator, Service administrator, Password administrator, and so on, to the user. Some, but not all, Microsoft 365 roles grant the user administrative permissions in Exchange Online, as defined in the following table.

:::row:::
  :::column:::
    **Microsoft 365 Admin Center role**
  :::column-end:::
  :::column:::
    **Exchange Online role group**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Global administrator
  :::column-end:::
  :::column:::
    Organization Management
The Global administrator role and the Organization Management role group are linked together using a special Company Administrator role group. The Company Administrator role group is managed internally by Exchange Online and can't be modified directly.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Billing administrator
  :::column-end:::
  :::column:::
    No corresponding Exchange Online role group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password administrator
  :::column-end:::
  :::column:::
    Help Desk administrator
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Service administrator
  :::column-end:::
  :::column:::
    No corresponding Exchange Online role group
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User management administrator
  :::column-end:::
  :::column:::
    No corresponding Exchange Online role group
  :::column-end:::
:::row-end:::


> [!NOTE]
> Role-Based Access Control is available within other services, such as Azure Active Directory and Microsoft Teams. While these services don't implement RBAC in the same way as Microsoft Exchange, they do function in a similar way to the Microsoft 365 admin center. You can assign users to roles, but you can't create roles with granular permissions that allow or restrict administrative capabilities or user capabilities to the same level of detail as Exchange Online.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.