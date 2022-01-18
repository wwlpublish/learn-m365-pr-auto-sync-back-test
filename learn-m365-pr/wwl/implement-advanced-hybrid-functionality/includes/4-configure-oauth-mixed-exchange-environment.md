Open Authorization, or OAuth, is required for some Exchange-related features, such as cross-premises discovery and automatic archive retention. The following situations are examples of when you must manually configure Oauth:

 -  Your Exchange organization includes Exchange 2007 or 2010 servers. The Hybrid Configuration Wizard (HCW) doesn't configure OAuth in this situation.
 -  The HCW app failed to configure OAuth successfully.

A Messaging administrator can use the **Test-OAuthConnectivity** cmdlet to verify whether Oauth is already configured in their environment. For example, you can run the following PowerShell command in your on-premises Exchange Management Shell to verify Oauth is correctly configured and working:

```powershell
Test-OAuthConnectivity -Service EWS -TargetUri https://outlook.office365.com/ews/exchange.asmx -Mailbox <on-prem>
```

### Manually configure OAuth for your Exchange organization

You should complete the following steps to manually configure OAuth:

1.  Create an authorization server object for your Exchange Online organization.
2.  Enable the partner application for your Exchange Online organization.
3.  Export the on-premises authorization certificate.
4.  Upload the on-premises authorization certificate to Azure Active Directory ACS.
5.  Register all hostname authorities with Azure AD.
6.  Create an IntraOrganizationConnector from your on-premises organization to Microsoft 365.
7.  Create an IntraOrganizationConnector from your Microsoft 365 tenant to your on-premises Exchange organization.
8.  Configure an AvailabilityAddressSpace for any pre-Exchange 2013 SP1 servers.
9.  Test your OAuth implementation using the Test-OAuthConnectivity cmdlet.

**Additional reading.** For more information, see [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help?azure-portal=true).
