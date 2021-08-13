Microsoft 365 includes encryption features that are managed by Microsoft, and encryption features that can be managed and configured by customers. Rights Management Services (RMS) is a technology related to SharePoint that encrypts customer data at rest or in-transit. This cloud-based protection service uses encryption, identity, and authorization policies to help secure an organization's files and email, and it works across multiple devices—phones, tablets, and PCs. Information can be protected both within and outside an organization because that protection remains with the data, even when it leaves an organization’s boundaries.

**Additional reading.** For more information, see [Azure Rights Management](/azure/information-protection/understand-explore/what-is-azure-rms).

### Encryption of data at rest

There are two levels of encryption for data at rest within SharePoint Online:

 -  **Bitlocker encryption.** Provided by default on all:
    
     -  customer document libraries
     -  users' OneDrive for Business data
     -  site data that's stored in the Microsoft 365 datacenters
 -  **Per-file encryption.** Encrypts every individual file stored in SharePoint Online and OneDrive for Business with its own unique key. SharePoint Online and OneDrive for Business always provide encryption in-transit.

### Encryption of data in-transit

There are two levels of encryption for data in-transit within SharePoint Online:

 -  **Client communication with the server.** Communication to OneDrive for Business across the Internet uses SSL/TLS connections. All SSL connections are established using 2048-bit keys.
 -  **Data movement between datacenters.** The primary reason to move data between datacenters is for geo-replication to enable disaster recovery. For instance, SQL Server transaction logs and blob storage deltas travel along this pipe. While this data is already transmitted by using a private network, it's further protected with best-in-class encryption.

**Additional reading.** For more information about encryption services, see [Security in Office 365 Whitepaper](https://download.microsoft.com/download/7/A/B/7AB27601-86E3-44CE-B350-106D7B55F642/SecurityinOffice365Whitepaper.pdf?azure-portal=true).

The following graphic shows in a single picture all the areas of encryption mentioned in this unit. From top to bottom in the picture, the data in the Microsoft 365 datacenter is encrypted at rest, then it's encrypted in transit when downloaded or sent to a client, and it remains encrypted at rest on the external devices.

:::image type="content" source="../media/data-encryption-in-m365-datacenter-af6ad71e.jpg" alt-text="graphic showing data in the Microsoft 365 datacenter is encrypted at rest, encrypted in transit, and encrypted at rest on the external device":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”