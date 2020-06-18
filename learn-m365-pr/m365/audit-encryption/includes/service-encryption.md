In addition to using BitLocker for volume-level encryption, Microsoft 365 uses service encryption to encrypt customer data at the application layer. Service encryption protects customer data with data encryption keys using one of the following key management options:

- **Microsoft Managed Keys** – In the default implementation for customers not leveraging Customer Key, Microsoft manages all cryptographic keys used for service encryption. This option is currently available in SharePoint Online and OneDrive for Business.
- **Customer Key** – This option allows customers to use their own root keys to encrypt customer data. Customer keys are uploaded to or generated within in Azure Key Vault, allowing customers to retain control over their keys. This option is currently available for Exchange Online, SharePoint Online, OneDrive for Business, and files in Microsoft Teams.

All keys used for service encryption are stored securely in private repositories, such as Azure Key Vault, where they can be used by automated service code without direct accessibility by Microsoft personnel. Service encryption also allows regular key rotation to maintain key security.

## Microsoft Managed Keys

With Microsoft Managed Keys, the Microsoft service manages and stores the root encryption keys used for service encryption, relieving the customer of the burden of provisioning and managing encryption keys. Microsoft Managed Keys are stored in private key vaults that can only be accessed indirectly by Microsoft 365 services for data encryption. These keys cannot be accessed directly by Microsoft employees.

Microsoft Managed Keys can be a viable solution for cloud customers that don't have particular key management requirements. For some customers, Microsoft Managed Keys may not meet their compliance obligations, such as specific restrictions on key management, operation, and storage. To meet these obligations, customer-managed keys can be implemented using the Customer Key feature in Microsoft 365.

![Two flow diagrams showing the Microsoft-managed key hierarchy. The diagram to the left shows the key hierarchy for Exchange Online, which shows how two Microsoft-managed RSA keys and one equivalent AES-256 availability key are used to protect the Data Encryption Policy Key, which in turn protects the Mailbox Key used to encrypt mailboxes in Exchange Online. The diagram to the right shows the key hierarchy for SharePoint Online, OneDrive for Business, and Microsoft Teams files, which use SQL Transparent Data Encryption to protect File Chunk Encryption Keys for SQL Databases.](../media/managed-keys.png)
