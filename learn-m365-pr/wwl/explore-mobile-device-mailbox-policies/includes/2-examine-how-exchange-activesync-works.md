When mobile devices, such as smartphones, connect to Exchange to get email, they often use a protocol named Exchange ActiveSync (EAS). ActiveSync is used whether the mobile device is using native apps (such as Mail on iOS) or apps from the app store (such as the Outlook app).

ActiveSync's core functionality provides users with access to email, contacts, tasks, and calendaring. Additionally, it provides limited mobile device management (MDM) functionality.

Microsoft designed ActiveSync to function on high-latency and low-bandwidth networks. It uses HTTP and XML, which keeps the protocol lightweight. Many vendors have standardized on building in ActiveSync support on their devices. As such, it's common for any modern device to have built-in ActiveSync support.

By default, Exchange ActiveSync is enabled. All users who have an Exchange mailbox can synchronize their mobile device with Microsoft Exchange Server.

The following tasks can be completed within Exchange ActiveSync:

 -  Enable and disable Exchange ActiveSync for users.
 -  Set policies such as minimum password length, device locking, and maximum failed password attempts.
 -  Start a remote wipe to clear all data from a lost or stolen mobile phone.
 -  Run various reports for viewing and export reports into different formats.
 -  Control the types of mobile devices that can synchronize with your organization through device access rules.

Some of the key features of ActiveSync include:

 -  **Remote device wipe**. If a mobile device that is connected to your Exchange environment is lost or stolen, the user or an administrator can remotely wipe the device to erase all its data.
 -  **MDM features**. You can enforce passwords on connected devices, enforce specific settings such as encryption, and set minimum password policies. While the built-in features don’t rival the enterprise MDM products, they often complement them. In smaller organizations, it's common to solely use ActiveSync’s built-in MDM functionality. The MDM features are implemented by using mobile device mailbox policies.
 -  **Direct Push**. When new content is ready to be synced to a device, Exchange Server can use a feature named Direct Push to notify the client. The client, after notification, then starts a sync operation to obtain the latest content from the Exchange Server.

Messaging administrators are responsible for managing mobile device settings, including:

 -  **Policies with personal devices**. Many organizations choose to use mobile device mailbox policies to ensure a secure environment. Messaging administrators often must deal with the fallout of such policies, since they can cause consternation among employees who use a personal device for their work email. Not only do they take exception to having their personal device managed by their company, but they’re also worried about losing their personal data or losing control of their phone. Others aren’t sure what it means to have their personal device managed by the email system.
 -  **Third-party apps**. Some users want to use third-party apps to connect to their mailbox. In many cases, the IT team will be familiar with the most common apps. However, because there are hundreds of apps available, you'll occasionally have to work with apps that you aren’t familiar with. It can be challenging for IT teams to support different apps and all the different devices types and operating system versions that are available today.
 -  **Connectivity**. When devices connect to Exchange Server from the internet, you have little control over the quality of the connection. Users can connect from public Wi-Fi networks, from the middle of a national park, or from a congested network. Some users may not have enough data in their plan to effectively use email on their device. As the administrator, you should be familiar with these common scenarios so that you can help users during troubleshooting situations.

> [!CAUTION]
> It’s important that you understand what happens when a remote wipe is started, especially if you allow users to use ActiveSync with their personal devices. Remote wipe can clear all data on the mobile phone, including installed applications, photos, and personal information.

The Active Sync connection process includes the following steps:

1.  The mobile device uses HTTPS to connect to the Microsoft-Server-ActiveSync IIS virtual directory on the client access services of the Mailbox server, where the client is authenticated.
2.  After the client is successfully authenticated, the client access services proxy the client’s request to the Mailbox server where the active database copy of the user’s mailbox is located and retrieves the mailbox data.
3.  Once the client has established the ActiveSync connection to the Exchange server, it downloads email, calendar items, contacts, and other configured items.

The ActiveSync protocol provides many functionalities. Some of the most important features of Exchange ActiveSync in Exchange include:

 -  Support for HTML-formatted messages.
 -  Support for follow-up flags on messages.
 -  Conversation grouping of email messages.
 -  Ability to synchronize or not synchronize an entire conversation.
 -  Synchronization of Short Message Service (SMS) messages with a user's Exchange mailbox.
 -  Support for viewing message reply status.
 -  Support for fast message retrieval.
 -  Meeting attendee information.
 -  Enhanced Exchange Search.
 -  PIN reset.
 -  Enhanced device security through password policies.
 -  Autodiscover for over-the-air provisioning.
 -  Support for setting automatic replies when users are away, on vacation, or out of the office.
 -  Support for task synchronization.
 -  Direct Push.
 -  Support for free/busy information for contacts.
 -  Global address list (GAL) photos.
 -  A means of sending only the new portion of an email and avoiding redundant information.
 -  A method to apply digital rights management control and encryption to email messages that are sent and received.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.