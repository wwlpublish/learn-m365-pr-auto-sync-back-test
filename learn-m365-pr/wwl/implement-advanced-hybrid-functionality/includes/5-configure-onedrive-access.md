Exchange Server 2016 and Exchange Server 2019 enable organizations to configure on-premises mailboxes that can store attachments in OneDrive for Business. This functionality preserves space on your on-premises Exchange Servers because user attachments aren't stored in the mailbox. Instead, they're stored in OneDrive with a link in the e-mail to the original attachment, should the user choose to upload them.

This functionality requires the following prerequisites:

 -  The user’s mailbox must be located on an Exchange 2016 or 2019 server.
 -  The organization's on-premises Exchange environment must be configured as a hybrid deployment.
 -  OAuth must be configured between the organization's on-premises Exchange environment and Exchange Online.

OAuth connectivity can be tested by running the following PowerShell command:

```powershell
Test-OAuthConnectivity -Service EWS -TargetUri https://outlook.office365.com/ews/exchange.asmx -Mailbox <on-prem>
```

Once an organization has satisfied the prerequisites, it must complete the following steps to enable the ability to store attachments from an on-premises mailbox on OneDrive for Business:<br>

1.  Decide which OWA mailbox policy will be used for this configuration.
2.  Run the following PowerShell command (this example uses the default OWA mailbox policy):
    
    ```powershell
    Set-OwaMailboxPolicy Default -InternalSPMySiteHostURL https://<tenant>-my.sharepoint.com -ExternalSPMySiteHostURL
    ```
3.  Run the following PowerShell command:
    
    ```powershell
    Set-CASMailbox <user mailbox> -OwaMailboxPolicy Default
    ```

Optionally, you can run **Restart-WebAppPool MSExchangeOWAAppPool** on your local Exchange 2016 or 2019 server for the changes to immediately take effect.

> [!WARNING]
> This command will disconnect all your users from OWA.

> [!NOTE]
> If you're running a multi-geo Microsoft 365 tenant, you may need to create OWA Mailbox Policies for users aligned to the preferred location in which their data is stored. When doing so, you must provide the specific geo-related URL when configuring this feature.

**Additional reading.** For more information, see [Configure document collaboration with OneDrive for Business and Exchange on-premises](/exchange/hybrid-deployment/set-up-document-collaboration?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.