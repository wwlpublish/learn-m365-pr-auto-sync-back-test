Exchange provides the following recipient types that can be used by organizations in different scenarios.

:::row:::
  :::column:::
    **Recipient Types**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **When to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mailboxes
  :::column-end:::
  :::column:::
    This recipient type is a mailbox that you assign to an individual user in your Exchange organization. Mailboxes are the most common type of recipient in Exchange.
  :::column-end:::
  :::column:::
    To any user who wants to use Outlook, Outlook on the Web, or Outlook Mobile to send or receive personal messages.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Shared mailboxes
  :::column-end:::
  :::column:::
    Mailboxes that can be accessed by multiple users as an extra mailbox in Outlook.
  :::column-end:::
  :::column:::
    Team, department, or project mailboxes are used to centrally store, respond to, and manage messages. Organizations often use a shared mailbox to provide one specific mailbox for a dedicated group of people, such as sales, help desk, or general information requests.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Room mailboxes
  :::column-end:::
  :::column:::
    Used to book meetings or conference rooms in Outlook. Can be configured to automatically process booking requests.
  :::column-end:::
  :::column:::
    Conference or meeting rooms, special team rooms, or buildings. You can include resource mailboxes as resources in meeting requests, which provide a simple and efficient way to schedule resource usage.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Equipment mailboxes
  :::column-end:::
  :::column:::
    Used to book equipment. Can be configured to automatically process booking requests.
  :::column-end:::
  :::column:::
    Use it for equipment that can be moved between locations; for example, a projector or a car.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Distribution groups
  :::column-end:::
  :::column:::
    Distribute messages to a set of users or contacts.
  :::column-end:::
  :::column:::
    The most common form of a globally available distribution list for sending out one-to-many e-mail messages or where you need to use the membership list elsewhere, such as to determine who Transport Rules should apply to. It can also be used for reaching out to a team as a contact address or used to allow send-as another email alias without creating a shared mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Security groups
  :::column-end:::
  :::column:::
    Distribute messages and provide access to resources to a set of users.
  :::column-end:::
  :::column:::
    Used when you need to apply permissions to resources such as a shared mailbox or Public Folder. But can also be used the same time as a distribution group, and be used outside Exchange Online, for example in SharePoint Online.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Dynamic distribution groups
  :::column-end:::
  :::column:::
    Dynamically create a set of users based on an LDAP search in Active Directory (AD) to distribute messages.
  :::column-end:::
  :::column:::
    Commonly used to create a global company distribution list that uses attributes in the company address book, such as region, office, department, and roles.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft 365 groups
  :::column-end:::
  :::column:::
    These groups are available only in Microsoft 365 and provide team collaboration such as document storage, a centralized calendar, a OneNote notebook, working collaborative on project plans, and team email distribution in one space.
  :::column-end:::
  :::column:::
    Excellent for team or department collaboration that uses other resources such as a OneNote or OneDrive. Because Microsoft 365 groups provide hooks into multiple Microsoft 365 services, they can be used as a tool to aid adoption and drive business value.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail contacts
  :::column-end:::
  :::column:::
    Contacts that contain information about people or organizations that exist outside an Exchange organization and that have an external email address.
  :::column-end:::
  :::column:::
    Show external contacts in Global Address List so that your users can add them to their distribution lists. Exchange routes all messages sent to the mail contact to this external email address.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail users
  :::column-end:::
  :::column:::
    Users who have a user account in the organization but have an external email address. All messages sent to the mail user are routed to this external email address.
  :::column-end:::
  :::column:::
    A mail user is typically created for temporary employees or external vendors who need to access resources in the organization but use their own email address that's located outside their organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail-enabled public folders
  :::column-end:::
  :::column:::
    Mail-enabled public folders, which are in the public folder hierarchy, have an email address assigned. As such, they can receive email messages.
  :::column-end:::
  :::column:::
    Used if your team already works extensively with public folders.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Linked mailboxes
  :::column-end:::
  :::column:::
    User mailboxes that are associated with specific users in a separate, trusted forest.
  :::column-end:::
  :::column:::
    When you create a linked mailbox, a disabled user account is created in the Exchange organization, and a user account from a trusted forest is given access to the mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Remote mailboxes
  :::column-end:::
  :::column:::
    Remote mailboxes are mailboxes that are located in the Exchange Online environment in a hybrid Exchange Server deployment.
  :::column-end:::
  :::column:::
    You can create and manage remote mailboxes in the Exchange Online environment by using the Exchange Admin Center and the Exchange Management Shell.
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.