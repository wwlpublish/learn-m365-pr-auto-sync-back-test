Encryption is an important part of an organization's file protection and information protection strategy. The encryption process encodes your data (referred to as plaintext) into ciphertext. Unlike plaintext, ciphertext can't be used by people or computers unless and until the ciphertext is decrypted. Decryption requires an encryption key that only authorized users have. Encryption helps ensure that only authorized recipients can decrypt your content. Content includes files, email messages, calendar entries, and so on.

Encryption by itself doesn't prevent content interception. Encryption is part of a larger information protection strategy for your organization. By using encryption, you help ensure that only authorized parties can use the encrypted data.

You can have multiple layers of encryption in place at the same time. For example, you can encrypt email messages and also the communication channels through which your email flows. With Microsoft 365, your data is encrypted at rest and in transit, using several strong encryption protocols, and technologies that include Transport Layer Security/Secure Sockets Layer (TLS/SSL), Internet Protocol Security (IPSec), and Advanced Encryption Standard (AES).

Microsoft 365 offers various encryption services and features, with a basic differentiation between data at rest and data is transit.<br>

### Data at rest

Examples of data at rest include files that have been uploaded to a SharePoint library, Project Online data, documents that have been uploaded in a Skype for Business meeting, email messages (and attachments) that are stored in folders in your Microsoft 365 mailbox, and files uploaded to OneDrive for Business.

### Data in transit

Examples of data in transit include mail messages that are being delivered, or conversations that are taking place in an online meeting. In Microsoft 365, data is in transit whenever a user's device is communicating with a Microsoft 365 server, or when a Microsoft 365 server is communicating with another server.

With Microsoft 365, you can have multiple layers and kinds of encryption working together to secure your data. The following table includes some examples.

:::row:::
  :::column:::
    

**Kinds of Content**


  :::column-end:::
  :::column:::
    

**Encryption Technologies**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Files on a device.** Includes email messages saved in a folder, Office documents saved on a computer, tablet, or phone, or data saved to the Microsoft cloud.


  :::column-end:::
  :::column:::
    

BitLocker in Microsoft datacenters. BitLocker can also be used on client machines, such as Windows computers and tablets.


Distributed Key Manager (DKM) in Microsoft datacenters.


Customer Key for Microsoft 365.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Files in transit between users.** Includes Office documents or SharePoint list items shared between users.


  :::column-end:::
  :::column:::
    

TLS for files in transit.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Email in transit between recipients.** Includes email hosted by Exchange Online.


  :::column-end:::
  :::column:::
    

Office 365 Message Encryption with Azure Rights Management, S/MIME, and TLS for email in transit.


  :::column-end:::
:::row-end:::


### Encryption for data in transit

Microsoft 365 provides data protection and security controls that allow organizations to protect sensitive data from accidental or malicious exposure. These controls help companies adhere to compliance requirements, give access to services and content to individuals in the organization, and encrypt data in their Microsoft 365 tenants. Microsoft 365 provides three different encryption options for message and document encryption, each of which are outlined in the following table.

:::row:::
  :::column:::
    

**Encryption option**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Information Rights Management (IRM)


  :::column-end:::
  :::column:::
    

IRM is an encryption solution that applies usage restrictions to email messages (including attachments) and Office files. It helps prevent sensitive information from being printed, forwarded, or copied by unauthorized people.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Secure Multipurpose Internet Mail Extension (S/MIME)


  :::column-end:::
  :::column:::
    

S/MIME is a certificate-based encryption solution that allows users to encrypt and digitally sign an email message.

 -  The message encryption helps ensure that only the intended recipient can open and read the message.
 -  A digital signature helps the recipient validate the identity of the sender.

Both digital signatures and message encryption are made possible by using unique digital certificates that contain the keys for verifying digital signatures and encrypting or decrypting messages.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Office 365 Message Encryption (OME)


  :::column-end:::
  :::column:::
    

Office 365 Message Encryption (OME) is a service built on Azure Rights Management (Azure RMS). It lets companies send encrypted email to people inside or outside the organization, regardless of the destination email.


  :::column-end:::
:::row-end:::


The following graphic shows that business data in the cloud and on devices can be encrypted with RMS, and that the storage is encrypted with BitLocker (data at rest). The connection between both is also encrypted (data in transit).

:::image type="content" source="../media/encrypted-data-in-transit-and-at-rest-b29e57e1.jpg" alt-text="graphic showing encrypted data in transit and encrypted data at rest":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”