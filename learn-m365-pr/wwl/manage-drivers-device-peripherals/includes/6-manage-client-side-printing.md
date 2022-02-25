Companies typically use print servers to provide centralized access to network printing devices. However, Windows allows you to connect to a network printing device directly by using a print server. Alternately, you can connect it locally by using a local printer, such as via USB, or by a wireless or Bluetooth connection.

:::image type="content" source="../media/printer-client-side-ab73f616.jpg" alt-text="Screenshot showing the printer queue.":::


You can manage client-side printing by using various tools, such as Devices and Printers, Print Management console, and Windows PowerShell cmdlets, from the Print Management module. Typical operations include the following tasks:

 -  Modifying printer properties, such as sharing, security, and advanced properties.
 -  Selecting your default printer.
 -  Viewing and managing your print queue.
 -  Pausing or resuming a printer's operation.
 -  Pausing, resuming, restarting, or canceling print jobs.
 -  Reordering print jobs in your print queue.

#### Modifying printer properties

You can modify printer behavior by configuring printer properties, such as the:

 -  General printer properties.
 -  Printer's physical location.
 -  Printer-sharing functionality.
 -  Ports that the printer uses.
 -  Times during which the printer is available.
 -  Number of print jobs that can spool at one time.
 -  Names of groups that are allowed to use the printer.

#### Select a default printer

You can add many printers to a Windows-based computer, but only one of them can be the default printer. The default printer is marked with a green check mark in Devices and Printers, and it's used by default for printing documents. You can print a document from any of the other available printers, but you must manually select the specific printer that you want to use.

#### View and manage the print queue

After you initiate a print job, you can view, pause, or cancel it through the print queue, which displays what is printing or waiting to print. It also displays information such as the job status, who is printing what, and how many unprinted pages remain. From the print queue, you can view and maintain the print jobs for each printer.

You can access the print queue from Devices and Printers by right-clicking a printer, and then selecting the **See what's printing** option or by running the Get-PrintJob cmdlet, as the following example shows for the Printer1 queue: Get-PrintJob - PrinterName Printer1

You can view all printer-related cmdlets by running Get-Command -Module PrintManagement.

#### Pause or resume printer

If you pause a printer, it will still accept print jobs, but they'll wait in the print queue and they won't print. If you resume a printer, print jobs will be sent to the printing device. You can pause or resume a printer from the printer queue window.

#### Pause, resume, restart, or cancel a print job

You can pause and resume a single print job or multiple jobs in the queue. To pause or resume an individual print job, right-click the print job in print queue window, and then select **Pause** or **Resume**. To pause all print jobs, select the **Printer** menu, and then select **Pause Printing**. To resume printing, select **Resume Printing**.

If a print job is printing in the wrong color or the wrong size, you can start over. To restart a print job, right-click the specific print job, and then select **Restart**.

If you start a print job by mistake, it's simple to cancel the print job, even if printing is underway. To cancel an individual print job, right-click the print job that you want to remove, and then select **Cancel**. To cancel all print jobs, select the **Printer** menu, and then select **Cancel All Jobs**. The item that is printing currently might finish, but the remaining items will be canceled.

#### Reorder the print queue

If you're printing multiple items, you can change the order in which they print. To reorder the jobs in the print queue, right-click the print job to reorder, and then select **Properties**. Modify the print job priority by using the **Priority** slider on the **General** tab of the print job properties page. Print jobs with higher priority print first.
