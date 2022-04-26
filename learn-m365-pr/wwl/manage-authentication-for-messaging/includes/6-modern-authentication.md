Modern authentication is really an umbrella term for multiple authentication and authorization methods between a client and a server. Modern Authentication is based on Open Authentication (OAuth) 2.0 and the Active Directory Authentication Library (ADAL). In Exchange Online, if modern authentication has been disabled, client connections to Exchange Online will revert to using basic authentication (legacy) which is a less secure. Some security measures rely on modern authentication such as:

 -  **Authentication methods** \- Multifactor authentication (MFA), smart card authentication, client certificate-based authentication and third-party SAML identity providers.
 -  **Authorization methods** \- Microsoft's implementation of Open Authorization (OAuth).
 -  **Conditional access policies** \- Mobile Application Management (MAM) and Azure Active Directory (Azure AD) Conditional Access.

Managing user identities with modern authentication gives you many different tools to use when it comes to securing resources and offers more secure methods of identity management both in Exchange Online and Exchange Hybrid (using hybrid modern authentication).

The following clients support the use of modern authentication:

:::row:::
  :::column:::
    **Client**
  :::column-end:::
  :::column:::
    **Protocol**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outlook 2013 and later
  :::column-end:::
  :::column:::
    MAPI over
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outlook 2016 for Mac and later
  :::column-end:::
  :::column:::
    Exchange Web Services
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outlook for iOS and Android
  :::column-end:::
  :::column:::
    Microsoft sync technology
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Exchange ActiveSync clients
  :::column-end:::
  :::column:::
    Exchange ActiveSync
  :::column-end:::
:::row-end:::


### Enable or disable modern authentication in Exchange Online

Within the Microsoft 365 admin center:

1.  In the navigation pane, select **Settings** and then select **Org settings**.
2.  Scroll down and find **Modern authentication** in the list.
3.  Once selected, the Modern authentication window will expand and you'll see:
    
     -  Turn on modern authentication for Outlook 2013 for Windows and later (default)
     -  Allow access to basic authentication protocols:
        
         -  Outlook client
         -  Exchange ActiveSync
         -  Autodiscover
         -  IMAP4
         -  POP3
         -  Authenticated SMTP
         -  Exchange Online PowerShell

Using Exchange Online PowerShell:

1.  Connect to Exchange Online PowerShell.
2.  Do one of these steps:
    
     -  Run the following command to enable modern authentication connections to Exchange Online by Outlook 2013 or later clients:<br>
        
        ```powershell
        Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
        ```
     -  Run the following command to prevent modern authentication connections (force the use of basic authentication connections) to Exchange Online by Outlook 2013 or later clients:<br>
        
        ```powershell
        Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
        ```

To verify that these changes where successful, again using Exchange Online PowerShell, run the following command:

```powershell
Get-OrganizationConfig | Format-Table Name,OAuth* -Auto
```
