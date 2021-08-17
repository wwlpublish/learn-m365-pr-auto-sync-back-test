You can use Certificate-based authentication (CBA) so your users are authenticated using client certificates. This ensures that users can access their mailboxes without providing credentials.

## Prerequisites

There are a number of prerequisites before you configure certificates:

- You must have access to the root certificate authority and any intermediate certificate authorities.
- Each certificate authority must have a certificate revocation list (CRL) that can be referenced through an internet-facing URL.
- For Exchange ActiveSync clients, the client certificate must have the user's routable email address in Exchange Online in either the Principal Name or the RFC822 Name value of the **Subject Alternative Name** field.
- Your users must have client certificates for client authentication. This is typically deployed using mobile device management (MDM).

## Implementing CBA

These are the steps to implement certificates:

1. Configure the certificate authorities in Active Directory or Azure Active Directory.
2. Configure the revocation list to let you deny access to a device if it is lost or stolen.

Test your configuration using every device type that you need to support.

## Learn more

[Certificate-Based Authentication (CBA) for Exchange Online](/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started)
