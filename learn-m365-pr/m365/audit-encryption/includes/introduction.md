Encryption is the process of encoding information in a way that only authorized parties can read it. Using encryption protects data against theft, failures in physical security, and eavesdropping on data-in-transit. Most encryption methods use one or more keys. These keys provide the ability to read data that has been made unintelligible by encryption. Keys can be used to encrypt data, decrypt data, or both.

Encryption is an important part of the Microsoft data protection strategy and provides one layer of our Defense-In-Depth approach to security. Encryption contributes to data security and data privacy by providing an additional layer of defense against unauthorized disclosure of data. Encryption can also help meet compliance obligations or internal requirements to protect the confidentiality of sensitive or otherwise protected data.

Encrypting information renders it unreadable to unauthorized persons who manage to bypass other security controls. Even if an adversary were able to break through firewalls, infiltrate the network, obtain physical access to devices, or bypass permissions on a local machine, the data in our systems would remain protected by strong encryption. A malicious attacker who obtained encrypted data without the appropriate key would be unable to decrypt and read the stolen data.

## Overview of Microsoft 365 encryption

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4ynVf]

With Microsoft 365, multiple layers of encryption work together to secure customer data both at-rest and in-transit.

**Examples of data-at-rest** include files uploaded to a SharePoint library, Teams chat messages, documents uploaded in Microsoft Teams meetings, email messages and attachments stored in mailbox folders, and files uploaded to OneDrive for Business.

**Examples of data-in-transit** include email messages that are in the process of being delivered or conversations that are taking place in an online meeting. in Microsoft Purview, data is in transit whenever a user's device is communicating with a Microsoft server, or when Microsoft servers are communicating with one another.

Customer data is encrypted at rest and in transit using FIPS 140-2 compatible encryption algorithms and technologies, including BitLocker, service encryption, Transport Layer Security (TLS), Internet Protocol Security (IPSec), and Advanced Encryption Standard (AES) algorithms. In addition, Microsoft employs advanced key management solutions to ensure that encryption keys are properly secured. This module will explore how each of these technologies is used in Microsoft Purview, beginning with disk protection using BitLocker, followed by application-level protection with service encryption, and concluding with data-in-transit encryption implemented throughout Microsoft 365.
