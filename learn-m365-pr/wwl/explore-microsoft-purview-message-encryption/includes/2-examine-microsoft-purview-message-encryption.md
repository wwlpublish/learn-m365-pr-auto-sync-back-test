Microsoft Purview Message Encryption is an online service that's built on Microsoft Azure Rights Management (Azure RMS). Azure RMS is part of Azure Information Protection. Microsoft Purview Message Encryption includes encryption, identity, and authorization policies to help organizations secure their email. They can encrypt messages by using:

 -  **Rights Management templates**. These default templates make it easy for organizations to immediately start protecting their sensitive data. They can be used with Azure Information Protection labels, or by themselves with applications and services that can use Rights Management templates. When an organization obtains its subscription for Azure Information Protection or for a Microsoft 365 subscription that includes the Azure Rights Management service, two default templates are automatically created for its tenant. These templates restrict access to authorized users in the organization. These templates are configured to allow offline access for seven days and don't have an expiration date. Organizations can also create their own custom templates.
 -  **Do Not Forward option**. When this option is applied to an email, the email is encrypted and recipients must be authenticated. Then, the recipients can't forward it, print it, or copy from it.
 -  **Encrypt-only option**. This option enables organizations to encrypt data without other restrictions. The recipients have all usage rights except **Save As**, **Export** and **Full Control**. This combination of usage rights means the recipients have no restrictions except that they can't remove the protection.

**Additional reading**. For more information on these encryption features, including the permissions assigned to Rights Management templates, see [Configure usage rights for Azure Information Protection](/azure/information-protection/configure-usage-rights?azure-portal=true).

Users can encrypt email messages and various attachments by using these options. Administrators can define mail flow rules to apply this protection. For example, an administrator can create mail flow rules that:

 -  require the encryption of all messages addressed to a specific recipient.
 -  contain specific words in the subject line.
 -  restrict recipients from copying or printing the contents of the message.

The predecessor to Microsoft Purview Message Encryption was Office 365 Message Encryption (OME). Unlike OME, Microsoft Purview Message Encryption provides a unified sender experience whether you're sending mail inside your organization or to recipients outside of Microsoft 365. In addition, recipients who receive a protected email message sent to a Microsoft 365 account in Outlook 2016 or Outlook on the web, don't have to take any other action to view the message. It works seamlessly. Recipients using other email clients and email service providers also have an improved experience.

**Additional reading**. For a detailed list of the differences between OME and Microsoft Purview Message Encryption, see [Compare versions of message encryption](/microsoft-365/compliance/ome-version-comparison?azure-portal=true).

When someone sends an email message that matches a mail flow rule that invokes Microsoft Purview Message Encryption, the message is encrypted before it's sent.

All Microsoft 365 end users that use Outlook clients to read mail will receive native, first-class reading experiences for encrypted and rights-protected mail. And they do so even if they aren't in the same organization as the sender. Supported Outlook clients include:

 -  Outlook desktop
 -  Outlook Mac
 -  Outlook mobile on iOS and Android
 -  Outlook on the web (formerly known as Outlook Web App)

Recipients of encrypted messages who receive encrypted or rights-protected mail sent to their Outlook.com, Gmail, and Yahoo accounts receive a wrapper mail that directs them to the message encryption portal where they can easily authenticate using a Microsoft account, Gmail, or Yahoo credentials.

End users that read encrypted or rights-protected mail on clients other than Outlook also use the message encryption portal to view encrypted and rights-protected messages that they receive.

### Sending, viewing, and replying to encrypted email messages

With Microsoft Purview Message Encryption, users can send encrypted email from Outlook and Outlook on the web clients. Additionally, admins can set up mail flow rules in Microsoft 365 to automatically encrypt emails based on keyword matching or other conditions.

Recipients of encrypted messages who are in organizations will be able to read those messages seamlessly in any version Outlook, including Outlook for PC, Outlook for Mac, Outlook on the web, Outlook for iOS, and Outlook for Android. Users that receive encrypted messages on other email clients can view the messages in the message encryption portal.

For detailed guidance about how to send and view encrypted messages, see the following articles.

| **Read this article...**                                                                                                                                                                                           | **If you are...**                                                                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Learn about protected messages in Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx?azure-portal=true).                                                                    | An end user who wants to learn more about how encrypted messages work and what options are available to you.                                                                                                                                                                                                               |
| [How do I open a protected message?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx?azure-portal=true)                                                                               | An end user who wants to read a protected message that was sent to you. This article includes information about reading messages in several versions of Outlook and from different email accounts, including those accounts outside of Microsoft 365 such as gmail and Yahoo! accounts.                                    |
| [Send, view, and reply to encrypted messages in Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980?azure-portal=true). | An end user who wants to send, view, or reply to an encrypted message from Outlook. Even if you're not a member of an organization, you still receive notification of encrypted messages sent to you in Outlook. Use this article for instructions on how to view and reply to encrypted messages sent from Microsoft 365. |
| [Send a digitally signed or encrypted message](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547?azure-portal=true).                          | An end user who wants to send, view, or reply to encrypted messages using Outlook for Mac. This article also covers using encryption methods other than Microsoft Purview Message Encryption, such as S/MIME.                                                                                                              |
| [View encrypted messages on your Android device](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb?azure-portal=true).                                                                       | An end user who has received a message encrypted with Microsoft Purview Message Encryption on your Android device, you can use the free OME Viewer app to view the message and send an encrypted reply. This article explains how.                                                                                         |
| [View encrypted messages on your iPhone or iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf?azure-portal=true).                      | An end user who has received a message encrypted with Microsoft Purview Message Encryption on your iPhone or iPad, you can use the free OME Viewer app to view the message and send an encrypted reply. This article explains how.                                                                                         |
