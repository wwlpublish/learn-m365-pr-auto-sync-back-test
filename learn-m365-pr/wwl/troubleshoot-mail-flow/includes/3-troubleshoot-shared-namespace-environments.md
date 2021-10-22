Shared namespace is a scenario where an organization shares the same SMTP domain in either of the following situations:

 -  Between its Exchange Server and a third-party email solution.
 -  Between two different Exchange Server organizations (with two different Active Directory forests).

These scenarios commonly occur when organizations migrate from a third-party email solution to Exchange Server, or in organizations that merge. Since the domain suffix is the same for all users, Exchange Server must be configured properly to allow correct email routing.

A Messaging administrator must complete the following steps to configure a shared namespace environment:

1.  **Create an internal relay accepted domain.** Using either the Exchange admin center (EAC) or Enterprise Mobility + Security (EMS), you should create a new accepted domain that matches the shared SMTP domain namespace. The new accepted domain type should be Internal Relay.<br><br>For example, to create an internal relay accepted domain titled Contoso.com in EMS, you would run the following PowerShell command:<br>
    
    ```powershell
    
    New-AcceptedDomain -Name "Contoso" -DomainName Contoso.com -DomainType InternalRelay
    ```
2.  **Create a send connector.** Using either the EAC or EMS, you should create a new send connector that routes messages to the shared SMTP domain.<br><br>For example, to create a send connector in EMS for Contoso.com that routes messages through a smart host named smarthost.Contoso.com, you would run the following command:
    
    ```powershell
    New-SendConnector -Name "Contoso.com Send Connector" -Custom -AddressSpace Contoso.com -DNSRoutingEnabled $false -SmartHosts smarthost.Contoso.com -SmartHostAuthMechanism ExternalAuthoritative
    ```

Troubleshooting shared name space environments includes checking whether previous steps that created and configured connectors were completed properly. It's also important to analyze whether any third-party SMTP gateway solution was involved in the message transport of the organization.

For example, consider the scenario where an SMTP gateway completes LDAP lookups in Active Directory and determines that a user isn't present in Active Directory. In this case, the gateway may reject the email, even though the user has a mailbox located on a non-Exchange mail system.
