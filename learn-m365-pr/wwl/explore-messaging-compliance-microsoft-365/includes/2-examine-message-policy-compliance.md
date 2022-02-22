Email has become a reliable and ubiquitous communication medium for information workers in organizations of all sizes. Messaging stores and mailboxes have become repositories of valuable corporate data. It's important for organizations to formulate messaging policies that dictate the fair use of their messaging systems, provide user guidelines for how to act on the policies, and where required, provide details about the types of communication that may not be allowed.

Organizations must also create policies to manage email lifecycle, keep messages for the length of time based on business, legal, and regulatory requirements, preserve email records for litigation and investigation purposes, and be prepared to search and provide the required email records to fulfill eDiscovery requests.

The following messaging policy and compliance features in Exchange Online can be configured in the Microsoft 365 Compliance center:

 -  **In-Place Archiving.** Helps you regain control of your organization's messaging data by eliminating the need for personal store (.pst) files and allowing users to store messages in an archive mailbox accessible in Outlook and Outlook on the web.
 -  **Retention Policies.** Enables you to keep or delete mailbox content based on policies to follow regulatory and legal rules.
 -  **Data loss prevention (DLP).** Includes sensitive information types that are ready to use for prevention of accidental or intentional data loss in messages.
 -  **eDiscovery.** Allows you to search mailbox data across your Exchange organization and create eDiscovery cases to organize compliance relevant search operations.

These features follow a unified approach that isn't limited to Exchange messaging only. While traditional messaging administrators and pure on-premises-only administrators configure most of the features in the Exchange Admin Center, you should use the Microsoft 365 Defender portal and the Compliance center portal when using Microsoft 365 services. Doing so enables you to implement unified protection solutions, even if you aren't managing Exchange Online only, but also when you're responsible for Exchange hybrid solutions.

> [!TIP]
> There are even more features for security and compliance for Microsoft 365 services that aren't part of this messaging administrator course. Microsoft 365 is continuously being improved, existing features are being updated, and new features are being added. It's recommended that you regularly monitor the Message center in the Microsoft 365 admin center to stay updated on all the changes and new features that are being planned for release.

### Encryption for data at rest and data in transit

People often use email to exchange sensitive information, such as financial data, legal contracts, confidential product information, sales reports and projections, patient health information, or customer and employee information. As a result, mailboxes can become repositories for large amounts of potentially sensitive information and information leakage can become a serious threat to your organization.

With the encryption features in Microsoft 365, your organization can send and receive encrypted email messages between people inside and outside your organization. Encryption in Microsoft 365 is separated into two different areas:

 -  **Data at rest.** This area includes all information storage objects, containers, and types that exist statically on physical media, whether magnetic or optical disk. An example of data at rest is disk encryption for Exchange Online.
 -  **Data in transit.** When data is being transferred between components, locations, or programs, it’s in transit. One of the features for encrypting data in transit is TLS encryption of the data stream.

Encryption of Microsoft 365 customer data at rest is provided by multiple service-side technologies, including:

 -  BitLocker
 -  Distributed Key Manager (DKM)
 -  Azure Storage Service Encryption
 -  Service encryption in Exchange Online, Skype for Business, OneDrive for Business, and SharePoint Online

Microsoft 365 Service Encryption includes an option to use customer-managed encryption keys that are stored in Azure Key Vault. This customer-managed key option, called Customer Key, is available for Exchange Online, SharePoint Online, and OneDrive for Business.

> [!NOTE]
> Features like Azure Information Protection, Azure Storage Service Encryption, and Customer Key are typically the responsibility of the Security Administrator, but there's some overlapping for messaging administrators.

:::row:::
  :::column:::
    **Feature**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    BitLocker
  :::column-end:::
  :::column:::
    Microsoft 365 servers use BitLocker to encrypt the disk drives containing customer data at rest at the volume-level. BitLocker encryption is a data protection feature that is built into Windows. BitLocker is one of the technologies used to safeguard against threats in case there are lapses in other processes or controls (for example, access control or recycling of hardware) that could lead to someone gaining physical access to disks containing customer data. In this case, BitLocker eliminates the potential for data theft or exposure because of lost, stolen, or inappropriately decommissioned computers and disks.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Distributed Key Manager (DKM)
  :::column-end:::
  :::column:::
    

Besides BitLocker, Microsoft also uses a technology called Distributed Key Manager. DKM is a client-side functionality that uses a set of secret keys to encrypt and decrypt information. Only members of a specific security group in Active Directory Domain Services can access those keys to decrypt the data that is encrypted by DKM.


In Exchange Online, only certain service accounts under which the Exchange processes run are part of that security group. As part of standard operating procedure in the datacenter, no person is given credentials that are part of this security group. As such, no person has access to the keys that can decrypt these secrets.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 365 Message Encryption
  :::column-end:::
  :::column:::
    

Office 365 Message Encryption allows email users to send encrypted email messages to anyone in- and outside your organization. Office 365 Message Encryption uses protection features from Azure Information Protection (Azure RMS).

Office 365 Message Encryption works with Outlook.com, Yahoo!, Gmail, and other email services. Email message encryption helps ensure that only intended recipients can view message content. Office 365 Message Encryption uses Azure RMS to encrypt and control access to emails and attachments sent out to internal and external recipients, such as Do Not Forward protection and content encryption.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Secure/Multipurpose Internet Mail Extensions (S/MIME)
  :::column-end:::
  :::column:::
    S/MIME is a client-side solution to protect sensitive information by sending signed and encrypted email. Encryption and signing are handled through personal certificates.
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.