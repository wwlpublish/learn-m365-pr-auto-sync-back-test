In addition to protecting customer data at rest, Microsoft uses encryption technologies to protect customer data in transit. Data-in-transit scenarios include:

- When a client machine communicates with a Microsoft server.
- When a Microsoft server communicates with another Microsoft server.
- When a Microsoft server communicates with a non-Microsoft server (for example, Exchange Online delivering email to a third-party email server).

Inter-datacenter communications between Microsoft servers take place using TLS or IPsec, and all customer-facing servers negotiate a secure session using TLS with client machines. For example, client connections to Exchange Online use TLS with AES and FIPS 140-2 compatible implementations. This applies to the web protocols used by all clients, including Outlook, Microsoft Teams, and Outlook on the web.

Microsoft owns and manages its own certificate authority to manage the certificates used for TLS encryption and utilizes third party solutions such as DigiCert and GlobalSign. The public certificates are issued by Microsoft using SSLAdmin, an internal Microsoft tool to protect confidentiality of transmitted information. All certificates issued by Microsoft IT have a minimum length of 2048 bits. Any IP addresses that fail to meet this criterion must be reviewed using a standardized exception process.

Customers can validate Microsoft’s TLS configurations by going to Qualys SSL Labs and searching for the addresses of our public web portals.

## Learn more

- [Encryption for Data in Transit](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-for-data-in-transit?view=o365-worldwide&azure-portal=true)
- [Email encryption in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/email-encryption?view=o365-worldwide&azure-portal=true)
- [Technical reference details about encryption](https://docs.microsoft.com/microsoft-365/compliance/technical-reference-details-about-encryption?view=o365-worldwide&azure-portal=true)
- [Qualys SSL Labs](https://www.ssllabs.com/ssltest/?azure-portal=true)
