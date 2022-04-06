All the tools you've been using up to now also let you manage mail flows in a hybrid Exchange environment. These tools are installed automatically when you install Exchange server on your on-premises infrastructure.

## The Exchange admin center

As you've seen earlier, the Exchange admin center is used to perform most day-to-day administrative tasks for Exchange Online. The same Exchange admin center is installed for all versions of Exchange server installed on-premises from Exchange 2013.

:::image type="content" source="../media/4-enable-hybrid-exchange.png" alt-text="A screenshot of the Exchange admin center, showing the hybrid page." border="false":::

After you've completed setting up a hybrid deployment in Exchange Online, you can switch seamlessly between managing settings for your on-premises Exchange server and Exchange Online.

## The Exchange Management Shell

The remote PowerShell cmdlets included in the Exchange Manager Shell are more powerful than the Exchange admin center. You can use these commands to script all the actions you can take in the Exchange admin center. You can also run scripts to complete steps that aren't supported in the Exchange admin center.

For organizations with Exchange server running on-premises, there's an Exchange Management Shell icon that opens a PowerShell window to connect directly to the local Exchange server.

As you've done in earlier steps, you can use remote PowerShell commands to connect to Exchange Online and run management scripts remotely.

## Learn more

- [Exchange admin center in Exchange Server](/exchange/architecture/client-access/exchange-admin-center?azure-portal=true)
- [Exchange Server PowerShell](/powershell/exchange/exchange-server/exchange-management-shell?azure-portal=true)
