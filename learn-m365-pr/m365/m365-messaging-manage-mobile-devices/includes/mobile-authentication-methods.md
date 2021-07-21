Exchange Online often stores sensitive information, so it's vital to securely identify users and grant them access only to appropriate resources, such as their own mailbox.

## Modern authentication for mobile devices

When Outlook for iOS or Android connects to Exchange Online, it uses modern authentication to identify the user to Exchange. Exchange uses this confirmed identity to decide which mailboxes and resources the user can access.  

In Microsoft 365, user accounts are stored in Azure Active Directory (Azure AD). When Outlook connects to Exchange Online and requests access to a mailbox, Exchange authenticates the user in Azure AD by using one of two methods:

- **Multifactor authentication** - The user has to pass two or more tests, such as:
  - Entering the correct username and password.
  - Providing a one-time authentication code that has been sent to their mobile phone as a text message or voice call. 
  - Providing the correct time-limited code from the Microsoft Authenticator app on their mobile device. This method can also use other authenticator apps. 
- **Client certificate authentication** - The user is authenticated when they supply a certificate that correctly identifies them, and has been signed by a certificate authority that is trusted by Microsoft 365.

Once the user is authenticated, Azure AD uses the OAuth protocol to authorize that user to access Exchange. In this protocol, Azure AD issues a digital access token to the client app. When Outlook makes a request to Exchange, it includes this token, which Exchange uses to ensure the user should have access to the mailbox or resource requested.

Modern authentication enables Outlook for iOS and Android to use these features:

- AutoDetect - helps users set up access to Exchange by supplying only their email address and credentials. AutoDetect gets all the other information necessary from the Exchange Online server.
- Single sign-on. All Microsoft mobile device apps support Azure AD authentication. If the Office apps on a device use the same Microsoft 365 URL or use the same authenticator app, then they can reuse the tokens issued to other apps on the device. This feature is called single sign-on. For example, if you use Word to authenticate with Microsoft 365 and edit a document, you can subsequently use Outlook to open your mailbox without the need to sign in again.

>[!NOTE]
> Many EAS, IMAP4, and POP3 clients also support modern authentication and OAuth. Support for these clients is currently being rolled out in Exchange Online.  

## Basic authentication for mobile devices

In basic authentication, the user's client application sends the username and password to the server in plain text, so that the server can authenticate their identity. Basic authentication is simple and widely supported, but has the obvious disadvantage that the credentials can be intercepted and read by a malicious user as they traverse the network. You should only use basic authentication when you can't use a more secure method.

A small number of clients (like EAS, POP3, and IMAP4 clients, which don't support modern authentication) may need to use basic authentication. If you do use basic authentication, it's essential to protect the credentials by encrypting the communication with Transport Layer Security (TLS).  

## Learn more

[Account setup with modern authentication in Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/setup-with-modern-authentication?azure-portal=true)
