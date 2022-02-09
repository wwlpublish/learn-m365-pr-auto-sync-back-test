When a user signs in with a domain account, they are typically authenticating to either an Active Directory Domain Service (AD DS) or Azure Active Directory (Azure AD).

## Active Directory Domain Services (AD DS) Authentication

The sign-in process authenticates both the computer and user accounts. In an AD DS environment, domain controllers perform authentication for computer accounts during the startup process and for user accounts when the user signs in.

At startup, a computer queries the configured Domain Name System (DNS) server to discover domain controllers that are available to perform authentication. If you configure your AD DS sites properly, a computer performs authentication by using domain controllers that are in the local physical location. This authentication process is much faster than authenticating to a domain controller that is in a different location.

If you do not configure the list of DNS servers on a Windows client computer appropriately, it cannot obtain a list of domain controllers. This could result in the following issues:

 -  **Authentication fails**. The user is unable to access the local computer or network resources.
 -  **Windows uses cached credentials**. The user is able to access the local computer and might be able to access some network resources.
 -  **Authentication is very slow but successful**. This occurs when a suitable domain controller is on the local subnet, and the client computer can locate it only by using NetBIOS broadcasts.

> [!NOTE]
> NetBIOS is a legacy session-management protocol that Windows 10 and later does not require.

During the sign-in process, Windows assigns a security token to both the computer and user accounts. The security token contains a list of groups of which the computer or user account is a member. Windows uses this list of groups to identify permissions when the computer or user attempts to access resources. If you add a computer or user account to a group, you must ensure that you reauthenticate the account to update the security token with group membership.

> [!NOTE]
> To reauthenticate a computer, you must restart the computer. To reauthenticate the user account, the user must sign out and then sign in again. Typical reasons why AD DS authentication might fail are:

 -  **Domain controller unreachable**. Due to a service failure, there is no available domain controller.
 -  **Name resolution issues**. The Windows computer cannot locate a domain controller in DNS, either because of configuration issues, or because of DNS unavailability.
 -  **Physical network issues**. If the client cannot connect to the network, then authentication fails.

## Azure AD Authentication

When users try to access cloud-based services, such as Microsoft 365, authentication must occur as it does in an on-premises AD DS environment. However, the process is different because the services that provide the authentication are not located locally. Therefore, the client computer must locate where the authentication services reside by using DNS.

Once the client computer locates the authentication services, the user typically receives a prompt to sign in by providing a user name and password that the client computer securely exchanges with the authentication service.

Obviously, if users provide incorrect sign-in information, authentication fails. Other reasons for failure include:

 -  **Name-resolution issues**. These issues occur if Windows cannot determine where the authentication service resides. This can occur because of a configuration error or local DNS service failure on your site, or with the Internet service provider (ISP) that provides your Internet service.
 -  **Internet connectivity is not available**. Without an Internet connection, your computer cannot locate the authentication services, and it cannot connect to Microsoft 365 or any other cloud-based applications.
 -  **Synchronization issues between on-premises AD DS and Azure AD**. In environments that use both cloud-based and on-premises directories, it is necessary to synchronize accounts between both platforms. Occasionally, it is possible for the two directories to be out of synchronization, which can lead to sign-in issues.
