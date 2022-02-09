Windows client provides several security technologies for devices, including authentication and authorization. Authentication is a process that confirms a user’s identity when he or she accesses a computer system or a system resource. In private and public computer networks, including the Internet, the most common authentication method that controls access to resources is the verification of a user’s credentials, which typically is their user name and password.

:::image type="content" source="../media/authenticate-authorize-access-09edb4ba.jpg" alt-text="Diagram showing how authentication systems validate user identity.":::


However, password authentication is inherently weak when you use it for certain critical transactions, such as payment processing, and user name and password authentication. Passwords can be stolen or revealed inadvertently. Therefore, most Internet businesses implement digital certificates that a certification authority (CA) issues and verifies. Logically, authentication comes before authorization, through which an operating system can determine if an authenticated user has the required permissions to access and update secured system resources. Authorized permissions include access to files and folders, hours of access, amount of allocated storage space, and other specifications. Authorization has two facets:

 -  A system administrator defines permissions for system resources initially.
 -  A system or application verifies users’ permission values when users attempt to access or update a system resource.

You can provide authorization and access without implementing authentication, such as when granting permissions for anonymous users that have not been authenticated. However, these permissions typically are limited.

## Windows authentication methods

Users must authenticate to verify their identity when they access files over a network, and authentication occurs during the network logon process. The Windows client operating system supports the following authentication methods for network logons:

 -  **Kerberos version 5 protocol**. Windows-based clients and servers use this as the main sign-in authentication method. It provides authentication for user and computer accounts.
 -  **NTLM**. This method provides backward compatibility with pre-Windows 2000 operating systems and some applications. However, it is less flexible, less efficient, and not as secure as the Kerberos protocol.
 -  **Certificate mapping**. Typically, users utilize this method in conjunction with smart cards. The certificate that a smart card stores can link to a user account. Users utilize a smart card reader, which scans the card’s chip to authenticate a user.

---
