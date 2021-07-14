Exchange Online provides a range of recipient types that enable organizations to work more effectively and maintain details in one place, the Exchange Global Address List (GAL). The GAL can be accessed in Outlook and Outlook on the web. The following recipient types are the most commonly used types in Exchange Online.

:::row:::
  :::column:::
    

**Recipient types**


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
    

Normal user mailbox in Exchange Online. Currently a user mailbox can be up to 50 GB in size and provides another free archive mailbox.


  :::column-end:::
  :::column:::
    

To any user who wants to use Outlook or Outlook on the web to receive or send personal messages. You require a mailbox to access, for example, shared mailboxes or public folders.


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
    

Team, department, or project mailboxes to centrally store, respond to, or manage messages.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Room mailboxes


  :::column-end:::
  :::column:::
    

Used to book meeting or conference rooms in Outlook. Can be configured to automatically process booking requests.


  :::column-end:::
  :::column:::
    

Conference or meeting rooms, special team rooms, or buildings.


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
    

Use it for equipment that can be moved between locations, for example, a projector or a car.


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
    

Most common form of a globally available distribution list for sending out one-to-many e-mail messages. Also applies when the membership list must be used elsewhere, such as determining who Transport Rules should apply to. In some use-cases, distribution groups can be used for contacting a team as a contact address, or to allow send-as another email alias without creating a shared mailbox.


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
    

Used when you need to apply permissions to resources such as a shared mailbox or Public Folder. Can also be used as a distribution group, and be used outside Exchange Online, such as in SharePoint Online.


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
    

Commonly used to create a global company distribution list using attributes in the company address book, such as region, office, department, or roles.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Microsoft 365 groups


  :::column-end:::
  :::column:::
    

Provides team collaboration such as document storage, a centralized calendar, a OneNote notebook, working collaborative on project plans, and team email distribution in one space.


  :::column-end:::
  :::column:::
    

Excellent for team or department collaboration when other resources such as OneNote or OneDrive are needed. Because it's integrated into multiple Microsoft 365 services, it can be used as a tool to aid adoption and drive business value.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Mail contacts


  :::column-end:::
  :::column:::
    

Mail contacts don't have a user account in Microsoft 365. As such, they can't sign in.


  :::column-end:::
  :::column:::
    

Show external contacts in the Global Address List so that your users can add them to their distribution lists.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Mail users


  :::column-end:::
  :::column:::
    

A mail user combines some of the attributes of a full mailbox user along with the characteristics of a contact.


  :::column-end:::
  :::column:::
    

Provide sign in facilities while forwarding their emails to their external email address.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Mail-enabled Public Folders


  :::column-end:::
  :::column:::
    

These folders are Active Directory universal security group objects that have an assigned email address, which enables them to receive email messages.


  :::column-end:::
  :::column:::
    

These folders can be used to assign access permissions to resources in Active Directory and can also be used to distribute messages.


  :::column-end:::
:::row-end:::


### Recipient types in a synchronized environment

If an organization's Microsoft 365 environment doesn't use directory synchronization, its environment will use cloud IDs for Exchange Online only. This design enables the organization to create, modify, and delete all recipient types in Microsoft 365 using the Microsoft 365 admin center, Exchange admin center, or Windows PowerShell.

When directory synchronization is implemented in a Microsoft 365 tenant (that is, Azure AD Connect is installed to synchronize the local Active Directory), all recipient management tasks must be completed locally. In doing so, the on-premises Exchange management tools such as the Exchange Admin Center or Exchange Management Shell must be used to create, modify, and delete recipients.

**Additional reading.** For more information, see the following resources:

 -  [Outlook](https://aka.ms/edx-cld222x-ol?azure-portal=true)
 -  [Outlook on the web](https://aka.ms/edx-cld222x-ol01?azure-portal=true)

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”