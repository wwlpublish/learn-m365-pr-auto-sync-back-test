When an organization moves mailboxes or public folders, the back-end process that handles the data move is the Mailbox Replication Service (MRS). MRS also handles importing and exporting of .PST files. Organizations typically troubleshoot MRS when they have issues moving mailboxes or public folders. They may also troubleshoot MRS when move performance is poor.

The default MRS settings are sufficient for most organizations. The default settings enable Exchange Server to lower the priority for mailbox and public folder moves, mostly when the server is under heavy load from other activities. In some cases, MRS can stop all current mailbox and public folder moves until the server has adequate resources to handle the moves.

Exchange Server uses dynamic throttling. However, you can disable dynamic throttling and instead, customize throttling by adjusting several settings.

The following screenshot displays the MsExchangeMailboxReplication.exe.config file, which, controls the throttling settings. This file is stored in the %ExchangeInstallPath%\\Bin folder.

:::image type="content" source="../media/exchange-mailbox-replication-2ea72e58.png" alt-text="Screenshot displaying the file that controls the throttling settings. The file is named Microsoft Exchange Mailbox Replication dot exe dot config.":::


The first line in the file describes the values displayed for each setting. The first value in each line is the Setting Name. To the right of the setting name are the three values assigned to the setting - the default value, the minimum value, and the maximum value.

> [!IMPORTANT]
> These values aren't used with dynamic throttling. The values in the config file are only used if dynamic throttling is disabled.

After you make changes to the config file, restart the Microsoft Exchange Mailbox Replication service (MSExchangeMailboxReplication service).

Some indirect troubleshooting of MRS is often beneficial as well, such as collecting statistics to find information about move requests. For example, by running the following PowerShell command, you could gather information on Beth’s move:

```powershell
Get-MoveRequest Beth | Get-MoveRequestStatistics | FL
```

Let's assume you have a migration batch file that contains a bunch of user names. The name of the batch file is Batch1. To get information about the batch, you can run the following PowerShell command:

```powershell
Get-MigrationBatch -Identity Batch1 -IncludeReport | Select Report | FL
```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.