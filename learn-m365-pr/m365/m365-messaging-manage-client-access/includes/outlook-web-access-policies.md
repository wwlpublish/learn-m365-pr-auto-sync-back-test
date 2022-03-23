**Outlook on the web** (formerly known as Outlook Web App) lets users access their mailboxes using a web browser. If users have an up-to-date version of Internet Explorer, Microsoft Edge, Mozilla Firefox, Google Chrome, or Apple Safari, they can use the standard version of Outlook on the web, including emails with attachments and calendars with scheduling.

## Outlook on the web mailbox policies

Mailbox policies control the settings and features that are applied in Outlook on the web. A default policy called **OwaMailboxPolicy-Default** already exists, and you can create a new policy using the Exchange admin center in Exchange Online or by using Exchange Online PowerShell. New policies have the most common settings already enabled.

You can only apply one mailbox policy per mailbox.

To create a new policy in the Exchange admin center, click **Permissions > Outlook Web App policies > New +**.

## Public attachment handling

For Outlook on the web users, attachments can present particular security risks. You can use mailbox policy settings to define whether users can open, view, send, or receive attachments when they are signed into Outlook on the web, including whether the user is on a computer that is part of a private or public network.

To set up the ability to enforce attachment handling from external networks for an entire organization, use these steps:

1. Use the **Set-OrganizationConfig** PowerShell cmdlet to enable public attachment handling for your organization. Set the *PublicComputersDetectionEnabled* parameter to $true.
1. Enable public attachment handling on the Outlook on the web mailbox policy either by using the Exchange admin center or the **Set-OwaMailboxPolicy** cmdlet.
1. Create claim rules in Active Directory Federation Services (ADFS). These rules detect whether the attachment is coming from an internal or external network.

## Outlook for iOS and Android

With the Outlook for iOS and Outlook for Android apps, users can synchronize their email, calendar, and contacts from their Exchange Online mailbox to their devices. The first time the user opens the app, they authenticate directly against an identity platform (either Azure AD or an on-premises identity provider like ADFS) and receive an access token in return, which grants Outlook for iOS and Android access to the user's mailbox or files. At no time does the service have access to the user's password in any form.

User mailbox data stays in place and continues to respect the data locality and regionality promises of Microsoft 365 for data at rest. In other words, the user's mailbox data is stored in the region in which the tenant (or mailbox in a multi-geo tenant) is located. Data synchronization with the native Microsoft sync technology occurs between the app and Microsoft 365, eliminating the need for any middle tier services.

## Inbox rules

Inbox rules in Outlook on the web and Outlook are limited to 256 KB total for all rules. Each rule you create takes up space in your mailbox. The actual amount of space a rule uses depends on several factors, such as how long the name is and how many conditions you've applied. When you reach the 256 KB limit, you'll be warned that you can't create any more rules or that you can't update a rule. You can't increase the amount of space that's allocated to store Inbox rules in Exchange Online, but you can decrease it to suit your business needs.

>[!NOTE]
> The valid range for the Inbox rules quota is 32 KB to 256 KB.
> There isn't a maximum number of rules that users can create.
> The quota for Inbox rules applies only to enabled rules. There's no restriction on the number of disabled rules that a mailbox can have. However, the total size of rules that are enabled or active in the mailbox can't exceed the quota value.

## Learn more

- [Public attachment handling in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/public-attachment-handling)
- [Windows PowerShell Reference Library](/powershell/windows/get-started?azure-portal=true)
