One of the primary tasks involved in managing Exchange recipients is creating and managing user mailboxes. User mailboxes, or just mailboxes, are the most common requirement for providing users with e-mail functionality.

While Exchange Server mailboxes are created in the on-premises Exchange admin center (EAC), Exchange Online mailboxes are created within the Microsoft 365 EAC. They're also assigned a Microsoft 365 license that includes an Exchange Online plan for that user.

User mailboxes can also be created in the Exchange Management Shell and Exchange Online PowerShell. Furthermore, the Exchange Management Shell enables you to create scripts to automate the mailbox creation process and complete bulk mailbox creation operations.

### Create a user mailbox

When you create a mailbox in Exchange Server, you can either associate the mailbox with an existing AD user account or create a new AD account that will be associated with the mailbox. You can also configure different mailbox properties, such as choosing a specific mailbox database for the mailbox.

If you create or enable a user mailbox through the Exchange Management Shell, you can configure multiple attributes at the same time that you create the account.

In the following example, the **New-Mailbox** command creates a user account and mailbox in the contoso.com domain for Patti Fernandez. The command assigns pattif as the user account name, pattif@contoso.com as the alias, and specifies dc1.contoso.com as the domain controller that will be used to read data from or write data to Active Directory.

```powershell
New-Mailbox -Name AlexD -UserPrincipalName pattif@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -Alias pattif@contoso.com -FirstName Patti -LastName Fernandez -DisplayName “Patti Fernandez” -DomainController dc1.contoso.com
```

If you want to create a mailbox for an existing user account, you can use the on-premises EAC or the **Enable-Mailbox** PowerShell cmdlet. Once the user mailbox is created, you can use the **Set-Mailbox** cmdlet to modify the attributes of the mailbox. This cmdlet allows you to update more attributes than is allowed in the EAC.

### Manage user mailboxes

After you create the mailbox, you can manage the mailbox settings by using the Exchange Admin Center or the Exchange Management Shell. The following list contains some of the mailbox configuration options available in Exchange Server and Exchange Online:

:::row:::
  :::column:::
    **Tab**
  :::column-end:::
  :::column:::
    **Configuration settings**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    general
  :::column-end:::
  :::column:::
    Usernames and custom attributes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    mailbox usage
  :::column-end:::
  :::column:::
    Displays the last sign-in information.
In Exchange Online: View mailbox size and limits
In Exchange Server: View and configure mailbox size and limits.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    contact information
  :::column-end:::
  :::column:::
    Configure information such as address and phone number.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    organization
  :::column-end:::
  :::column:::
    Configure the title, department, company, and manager settings.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    email address
  :::column-end:::
  :::column:::
    Configure the email addresses assigned to the mailbox.
Can include Single Mail Transfer Protocol (SMTP), Exchange Unified Messaging addresses, or addresses associated with other messaging systems.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    mailbox features
  :::column-end:::
  :::column:::
    Configure the policies that apply to the mailbox.
Configure mail flow settings including delivery options, message size, and delivery restrictions.
Configure different types of access such as mobile devices, MAPI, Outlook on the Web.
Configure Archiving.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    member of
  :::column-end:::
  :::column:::
    View the groups to which the user account belongs.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MailTip
  :::column-end:::
  :::column:::
    Configure MailTip for the mailbox to be displayed when users add this recipient as a message recipient.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    mailbox delegation
  :::column-end:::
  :::column:::
    Configure Send As, Send on Behalf of, and Full Access permissions to the user mailbox.
  :::column-end:::
:::row-end:::


A user’s Archive mailbox can be enabled during the mailbox creation process or after the mailbox is created by using the EAC or Exchange PowerShell. For example, to create an archive mailbox for an existing user mailbox, such as Patti Fernandez, you would run the following Exchange PowerShell command:

```powershell
Enable-Mailbox "Patti Fernandez" -Archive
```

In Exchange Server, the mailbox size for different types of users in an organization plays an important role in planning the disk space needed. It’s recommended that you use the Exchange Server Role Requirements Calculator for estimating the optimal disk size and configuration to accommodate disk space for users’ mailboxes.

In Exchange Online, depending on the subscription, users may have different mailbox size limits. For example:

 -  In Office 365 Business Essentials and Business Premium subscriptions, users have a 50-GB primary mailbox limit and a 50-GB archive mailbox limit.
 -  In Office 365 E3 and E5 subscriptions, users have a 100-GB primary mailbox limit and unlimited storage for the archive mailbox.

### Delete a user mailbox

A user mailbox can be disabled or deleted, depending on whether the user account is still needed in the organization. Disabling a user mailbox deletes the mailbox, but the associated user account will still be present.

Disabling a mailbox is different than disabling a user account in Active Directory. When a mailbox is disabled:

 -  All Exchange attributes are removed from the associated user account in Active Directory.
 -  The disabled mailbox is then hidden and marked for removal.
 -  The user in Active Directory isn't disabled and can sign into the domain.
 -  The disabled mailbox is permanently deleted (purged) based on the **MailboxRetention** property value for the mailbox database, which by default is 30 days. Within this 30-day timeframe, you can reconnect the disabled mailbox to a new or existing user account that doesn't already have an associated mailbox.

You can disable a user mailbox in the EAC or by using the **Disable-Mailbox** cmdlet in Exchange PowerShell. For example, to disable the mailbox for Patti Fernandez (whose alias is pattif), you would run the following command:

```powershell
Disable-Mailbox pattif@contoso.com
```

If both a user account and its associated user mailbox are no longer needed, such as when an employee leaves the organization, you can delete the mailbox by using the EAC or Exchange PowerShell. For example, to remove the mailbox for Patti Fernandez, you would run the following command:

```powershell
Remove-Mailbox -Identity "Patti Fernandez"
```

The deleted mailbox is permanently deleted (purged) based on the **MailboxRetention** property value for the mailbox database, which by default is 30 days. Within this 30-day timeframe, you can reconnect the disconnected mailbox to another user account that doesn't already have an associated mailbox.

If a mailbox has an associated archive mailbox, the **Remove-Mailbox** cmdlet also marks the associated archive mailbox for deletion. You can optionally disable the archive mailbox rather than delete it by running the following command:

```powershell
Disable-Mailbox "Patti Fernandez" -Archive
```

**Additional information.** For more information, see [Create user mailboxes in Exchange Server](/exchange/recipients/create-user-mailboxes?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.