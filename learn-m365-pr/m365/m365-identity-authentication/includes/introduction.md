## Modernize your authentication flows

To give your users easy access to your cloud apps, Azure Active Directory (Azure AD) supports a broad variety of authentication protocols including legacy authentication. Legacy authentication is a term that refers to an authentication request made by:

- Older Office clients that do not use modern authentication methods (for example, Office 2010 client).
- Any client that uses legacy mail protocols such as IMAP/SMTP/POP3.

Today the majority of all compromising sign-on attempts come from legacy authentication because it does not support multi-factor authentication (MFA). Even if you have an MFA policy enabled on your directory, a bad actor can authenticate using a legacy protocol and bypass MFA. The best way to protect your account from malicious authentication requests made by legacy protocols is to block these attempts altogether.

Modern authentication is a method of identity management that offers more secure user authentication and authorization. Specifically, modern authentication enables Microsoft Authentication Library (MSAL)-based sign-on for Office client apps across different platforms. This allows sign-on features such as multi-factor authentication (MFA), smart card, and certificate-based authentication to be enabled. If you have an MFA policy in place on your directory, modern authentication ensures that the user is prompted for MFA when required. It is the more secure alternative to legacy authentication protocols.
