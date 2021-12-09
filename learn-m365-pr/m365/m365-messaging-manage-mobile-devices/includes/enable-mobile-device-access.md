Most of your mobile device users probably have Outlook, but others may use other mail clients or protocols to reach their mail. Make sure these devices, regardless of the mail client or protocol, can connect to Exchange Online securely.

## Which mobile devices can you use with Exchange Online?

If your organization issues mobile devices to all users, you may have to support only a small range of clients. However, in most cases, you have a mix of older and newer devices. Because users often bring their own mobile phones, tablets, and other devices to work, you'll also have to support many different mobile operating systems and hardware. Microsoft 365 and Exchange Online support several different mailbox access protocols so this range of clients shouldn't cause any problems. Before you can administer the different mailbox protocols, you need to understand them.

### Outlook for iOS and Android

For devices running an iOS or Android operating system, you can install Outlook and get email, calendar, contacts, and other functionality like the same features in Outlook on PCs. There are also some important features relevant to their administration:

- All of the user's mailbox data stays in the tenant's region and complies with data protection regulations for that region.
- All of the user's data is encrypted end-to-end by the Transport Layer Security (TLS) protocol.
- Because each device connects to Microsoft 365 with a unique device ID, you can manage each device individually in the Microsoft 365 Admin console.
- The user's credentials are protected with Modern Authentication and Open Authorization (OAuth).
- You can use Microsoft Enterprise Mobility + Support to access advanced management tools, such as Microsoft Intune and Azure Active Directory Premium.
- Outlook for iOS and Android uses the native Microsoft sync technology, which reduces delivery latency and eliminates the need for middle-tier services.

### Other client protocols

If your users have devices that don't support Outlook, you can still connect it to Exchange Online by using one of these protocols:

- **Exchange ActiveSync (EAS)** - A Microsoft protocol designed to support mailbox access with high-latency or low-bandwidth connections. Users can synchronize emails, contacts, and calendars. A range of advanced features are included, like setting up automatic responses or follow-up flags.
- **IMAP4** - Governed by international standards, this protocol sets a standard way to connect to, and download emails from, a mailbox with multiple folders. Users can't access their calendar or contact information, and there aren't any advanced features like the other protocols or operating systems.
- **POP3** This standardized protocol enables a client to download emails from a mailbox with a single folder. Users can't access subfolders, calendars, contacts, or advanced features.

> [!NOTE]
> The IMAP4 and POP3 protocols retrieve emails from your email server but aren't used to send mail. Clients that use these protocols use the SMTP protocol to send email.

By default, IMAP4 and POP3 are enabled. You can disable them for each user to help harden your Exchange Online system. If you've enabled the security defaults feature in Azure Active Directory (Azure AD), then IMAP4 and POP3 are disabled by default for all mailboxes.

## Manage mobile devices in Exchange Online

If you have a large number of mobile device users, you need a way to impose a secure but functional configuration on those devices without consuming too much administration time. You can manage mobile devices with these tools:  

- Microsoft Enterprise Mobility + Security
- Mobile Device Management for Microsoft 365
- Mobile device mailbox policies

### Microsoft Enterprise Mobility + Security

This suite has the broadest set of device protection features and is the recommended way to manage mobile devices. The suite includes Microsoft Intune, Azure Information Protection, and Azure AD Premium features. With these tools, you can:

- Set Conditional Access requirements. Devices must meet these requirements before they can access their email in Exchange Online.
- Require that users use a PIN or fingerprint authentication on their mobile device before they access Exchange mailboxes.
- Wipe Exchange Online emails from a device but leave email in other, personal accounts. This feature is known as selective wipe.

> [!NOTE]
> The Enterprise Mobility + Security suite is an additional subscription service that you can add to Microsoft 365 Apps. A range of pricing options are available, to suit different organizations' needs and there is also a free trial.

### Mobile Device Management (MDM) for Microsoft 365

This feature is built into Microsoft 365 and provides mobile device management features at no extra cost. It's not as comprehensive as the Enterprise Mobility + Security Suite, but it gives you a core set of controls over mobile devices that can ensure users can access their mailboxes in a secure way.  

With MDM for Microsoft 365 you can, for example:

- Wipe all data from a mobile device, or selectively wipe only data that belongs to your organization.
- Use device security policies to require a minimum password length, require an alphanumeric password, or require data encryption.
- View the details about the devices that are enrolled in your organization.

### Mobile device mailbox policies

Mobile device mailbox policies (formerly known as Exchange ActiveSync policies) are used to manage mobile devices that use EAS to access mailboxes in Exchange. Here are a few  examples of the tasks you can do with these policies:

- Require a password complexity level and minimum length.
- Enable or disable device features such as Bluetooth and wi-fi.
- Require storage encryption on the device.
- Enable the device to download attachments.

> [!NOTE]
> Although you should use Enterprise Mobility + Security  or MDM to manage Outlook for iOS and Android clients, mobile device mailbox policy settings also apply to Outlook clients. For example, you can use them to impose a minimum password length or require encryption.

## Learn more

- [Clients and mobile in Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online?azure-portal=true)
- [Outlook for iOS and Android in Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android?azure-portal=true)
- [Exchange ActiveSync in Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync?azure-portal=true)
