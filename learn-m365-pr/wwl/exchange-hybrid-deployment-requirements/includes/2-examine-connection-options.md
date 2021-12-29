When organizations choose a migration strategy from on-premises Exchange Server to Microsoft 365, it’s essential they consider their coexistence requirements and functionality. It’s also important that they understand the consequences of their migration choice.

The following table identifies the different migration options and their effect on coexistence.

:::row:::
  :::column:::
    **Migration option**
  :::column-end:::
  :::column:::
    **Effect on coexistence**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    IMAP Migration
  :::column-end:::
  :::column:::
    No coexistence available. This option provides basic mail data migration.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cutover migration
  :::column-end:::
  :::column:::
    Not a real coexistence. This option provides migration of the user account information and mailbox data.
No mail routing coexistence is required. Organizations just need to switch their DNS.
Transition from on-premises Exchange Server to Exchange Online once the user accounts are migrated.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Staged Migration
  :::column-end:::
  :::column:::
    Requires directory synchronization to be in place and mail routing between on-premises Exchange and Exchange Online.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Hybrid deployment
  :::column-end:::
  :::column:::
    Requires Exchange 2010 or later to be installed in your on-premises Exchange environment.
Requires directory synchronization using Azure AD Connect and mail routing between on-premises Exchange and Exchange Online.
The SMTP email entry point can be on-premises or online.
Minimal hybrid and full hybrid deployments enable native mailbox migrations.
Full hybrid also enables rich coexistence, including free/busy data, secure SMTP, and Public Folder migrations.
  :::column-end:::
:::row-end:::


### Connection Options to Microsoft 365 Requirements

All connection options have requirements for which mail servers can be used to establish a connection. For a full hybrid feature set, the latest Exchange Server version must be running in your Exchange environment. If you run older Exchange Server versions such as Exchange Server 2000 or earlier or other messaging systems, the connection features are limited to e-mail-only migration support for IMAP migrations.

:::image type="content" source="../media/connection-office365-requirements-7a0b29c9.jpg" alt-text="Diagram showing Connection Options for each version of Exchange":::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.