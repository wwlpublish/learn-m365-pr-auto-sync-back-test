People often use email to exchange sensitive information, such as financial data, legal contracts, confidential product information, sales reports and projections, patient health information, or customer and employee information. As a result, mailboxes can become repositories for large amounts of potentially sensitive information and information leakage can become a serious threat to your organization.

With Office 365 Message Encryption, your organization can send and receive encrypted email messages between people inside and outside your organization. Office 365 Message Encryption works with Outlook.com, Yahoo!, Gmail, and other email services. Email message encryption helps ensure that only intended recipients can view message content.

At a high level, encryption is the process of encoding your data (referred to as plaintext) into ciphertext that cannot be used by people or computers unless and until the ciphertext is decrypted. Decryption requires an encryption key that only authorized users have. Encryption helps ensure that only authorized recipients can decrypt your content, such as email messages and files.

Encryption by itself doesn't prevent content, such as files, email messages, calendar entries, and so on, from getting into the wrong hands. Encryption is part of a larger information protection strategy for your organization. By using encryption, you can help ensure that only those users who can use encrypted data are able to do so.

There are many scenarios in which email message encryption may be required, such as:

 -  A bank employee sending credit card statements to customers.
 -  An insurance company representative providing policy details to customers.
 -  A mortgage broker requesting financial information from a customer for a loan application.
 -  A health care provider sending health care information to patients.
 -  An attorney sending confidential information to a customer or another attorney.
 -  A consultant sending a contract to a customer.

Exchange administrators set up Office 365 Message Encryption (OME) by defining encryption rules. As an administrator, you can also customize encrypted messages with your own text and logo, presenting a company brand that is familiar to message recipients.

### Overview of Office 365 Message Encryption

Office 365 Message Encryption combines email encryption and rights management (RMS) capabilities, that are provided with Azure Information Protection (AIP).

To use the new OME capabilities, you need one of the following plans:

 -  Office 365 Message Encryption is offered as part of:
    
     -  Office 365 E3 and E5
     -  Microsoft E3 and E5
     -  Office 365 A1, A3, and A5
     -  Office 365 G3 and G5
 -  You can also add Azure Information Protection Plan 1 to the following plans to receive the new Office 365 Message Encryption capabilities:
    
     -  Exchange Online Plan 1
     -  Exchange Online Plan 2
     -  Office 365 F1
     -  Office 365 Business Essentials
     -  Office 365 Business Premium
     -  Office 365 Enterprise E1

**Additional reading.** For the complete list of Office 365 Business plans, see [Exchange Online service descriptions for Office 365 Message Encryption](https://technet.microsoft.com/library/exchange-online-service-description.aspx?azure-portal=true).

### Comparing Office 365 Message Encryption to S/MIME

Office 365 Message Encryption and S/MIME both provide email encryption. Message encryption with S/MIME works from the sender’s client to the recipient’s client. By comparison, OME is a service-based encryption tool that grants more flexibility.

The primary difference between these two encryption services is that S/MIME requires the client sending the message to encrypt the email message using a public key infrastructure (PKI) certificate. OME doesn't have this requirement.

With S/MIME, the PKI certificate must be installed or available on the client computer. As a result, before the encrypted message can be composed and sent, S/MIME message encryption requires a certificate key exchange between the intended recipient of the encrypted message and the sender.

In contrast to S/MIME, Office 365 Message Encryption uses built-in certificates to encrypt messages in the OME service during the transport of the message. From a Microsoft 365 service point of view, an S/MIME encrypted message is just an email message that the Microsoft 365 service can't interpret. OME ensures that only the intended recipient can view the message after it has validated the recipient’s identity. As a result, it doesn't require a certificate key exchange before sending or encrypting a message.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”