By default, the Hybrid Configuration Wizard automatically enables all hybrid deployment features each time it runs. If you want to disable specific hybrid configuration features, you need to use the Exchange Management Shell and the **Set-HybridConfiguration PowerShell** cmdlet.

Also by default, the following hybrid deployment features are enabled by the Hybrid Configuration Wizard:

**Free/busy sharing**: The free/busy sharing feature enables calendar information to be shared between on-premises and Exchange Online organization users.

**MailTips**: MailTips are informative messages displayed to users while they're composing a message.

**Online archiving**: Online archiving enables the Exchange Online organization to host user email archives for both on-premises and Exchange Online users.

**Outlook on the web redirection**: Outlook on the web redirection provides a single, common URL to access both on-premises and Exchange Online mailboxes.

**Exchange ActiveSync redirection**: When you move a mailbox from your on-premises Exchange organization to Exchange Online, all the clients that access the mailbox need to be updated to use Exchange Online; this includes Exchange ActiveSync devices. With Exchange ActiveSync redirection, Exchange ActiveSync clients will be automatically reconfigured when the mailbox is moved to Exchange Online.

**Secure mail**: Secure mail enables secure message delivery between the on-premises and Exchange Online organization via Transport Layer Security (TLS) protocol.

## Learn more

- [Hybrid Configuration Wizard](https://docs.microsoft.com/exchange/hybrid-configuration-wizard?azure-portal=true)
- [PowerShell Reference Library](https://docs.microsoft.com/powershell/windows/get-started?view=win10-ps&azure-portal=true)
