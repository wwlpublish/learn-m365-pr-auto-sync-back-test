Office 365 Message Encryption (OME) is an online service that's built on Microsoft Azure Rights Management (Azure RMS, which is part of Azure Information Protection). Together, OME and Azure RMS provide encryption, identity, and authorization policies to help secure an organization's email.

OME enables organizations to encrypt messages by using rights management templates, the Do Not Forward option, and the encrypt-only option. With Azure RMS set up for an organization, administrators can enable message encryption by defining transport rules that determine the conditions for encryption. For example, organizations may create rules that:

 -  require the encryption of all messages addressed to a specific recipient.
 -  contains specific words in the subject line.
 -  specifies that recipients can't copy or print the contents of the message.

Users can then encrypt email messages and various Microsoft 365 attachments by using these options. When a user sends an email message in Exchange that matches an encryption rule, the message is sent out with an HTML attachment. Recipients follow instructions in the message to open the attachment and authenticate by using a Microsoft account or a work account associated with Microsoft 365. If recipients don't have either account, they're directed to create a Microsoft account that enables them to sign in to view the encrypted message. Or, they can choose to get a one-time passcode to view the message.

After signing in or using a one-time passcode, recipients can view the decrypted message and send an encrypted reply. Both options help to ensure that only the intended recipient can view the encrypted message.

OME provides a unified sender experience whether you're sending mail inside your organization or to recipients outside of Microsoft 365. Recipients who receive a protected email message sent to a Microsoft 365 account in Outlook 2016 or Outlook on the web don't have to do anything else to view the message. Message viewing works seamlessly with OME.

When someone sends an email message that matches an encryption mail flow rule, the message is encrypted before it's sent. All Microsoft 365 end users that use Outlook clients to read mail receive native, first-class reading experiences for encrypted and rights-protected mail even if they're not in the same organization as the sender. Supported Outlook clients include Outlook desktop, Outlook Mac, Outlook mobile on iOS and Android, and Outlook on the web (formerly known as Outlook Web App).

Recipients of encrypted messages who receive encrypted or rights-protected mail sent to their Outlook.com, Gmail, and Yahoo accounts receive a wrapper mail that directs them to the OME portal. From the portal, they can authenticate using a Microsoft account, or Gmail or Yahoo credentials. End users who read encrypted or rights-protected mail on clients other than Outlook can also use the OME portal to view encrypted and rights-protected messages they received.

The following diagram summarizes the passage of an email message through the encryption and decryption process.<br>

:::image type="content" source="../media/email-flow-through-encryption-decryption-539e7d7c.jpg" alt-text="graphic summarizes the passage of an email message through the encryption and decryption process":::


**Additional reading.** For more information, see [Encryption in Office 365](https://docs.microsoft.com/microsoft-365/compliance/encryption?azure-portal=true).<br>
