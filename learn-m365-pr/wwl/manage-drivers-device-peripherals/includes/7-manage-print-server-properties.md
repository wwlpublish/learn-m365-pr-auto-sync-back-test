Windows can act as a print server, or you can connect to Windows-based print servers through the Print Management Console and manage them remotely. Windows includes the Print Management Console in the Administrative Tools, and you can open it from there or by typing Printmanagement.msc in the Search the web and Windows field on the taskbar. The Print Management Console provides a single interface through which you can administer multiple printers and print servers and perform management tasks, such as:

 -  Add and remove print servers.
 -  Add and delete printers.
 -  Add and manage drivers.
 -  Manage print queues.
 -  View and modify status of printers.
 -  Create custom filters to view printers that match certain criteria.

:::image type="content" source="../media/print-server-05e44ea1.jpg" alt-text="Screenshot of the print server":::


#### Add and remove print servers

When you open the Print Management Console for the first time, it's connected only to a local Windows-based print server. If you have appropriate permissions, and you want to manage other Windows-based print servers, you must first add them to the Print Management Console by right-clicking the Print Servers node, and then selecting Add/Remove Print Servers.

#### Add and delete printers

You can add or delete printers locally or remotely on any print server that is added to the Print Management Console. You add printers by using Network Printer Installation Wizard, which is similar to the Add Printer Wizard in Devices and Printers. The Network Printer Installation Wizard allows you to:

 -  Search the network for printers.
 -  Add a TCP/IP or Web Service Printer by IP address or host name.
 -  Add a new printer by using an existing port.
 -  Create a new port, and add a new printer.

#### Add and manage drivers

When you add a printer, Windows also installs a driver for the appropriate printing device. For example, if you add a PostScript printing device, a Windows driver for PostScript will be installed. However, when you share that printer, other users might connect to it and be able to use a printer. Therefore, you should provide drivers for the operating systems that they're using. Most drivers designed for Windows 10 should work with Windows 11, however, you should check with the manufacturer. If different drivers are available for the different versions, you might want to add a 64-bit driver to your Windows client-based print server.

The Print Management Console allows you to add printer drivers by running the Add Printer Driver Wizard. You should be aware that with Type 4 printer drivers, users no longer need multiple drivers for different printers, and printer drivers cannot be downloaded from the print server, but from Windows Update or from Windows Update for Business.

#### Managing print queues

You can view printers that are installed on a specific print server by selecting the **Printers** node under that print server. You also can view all installed printers on all print servers that are added to the Print Management Console by selecting the **All Printers** node. You can view the printer queue by right-clicking the printer, and then selecting **Open Printer Queue** from the shortcut menu. From the print queue window, you can pause, resume, restart, cancel, or reorder print jobs.

#### View and modify the status of printers

The **All Printers** node shows information about every printer that is connected to any print server that you've added to the Print Management Console. There you can view the print queue status of the printer, number of jobs in the queue, name and version of the printer driver, and the driver type.

#### Create custom filters to view printers that match certain criteria

The Print Management Console includes four custom filters by default: All Printers, All Drivers, Printers Not Ready, and Printers With Jobs. You can add new custom printers or driver filters by defining a condition(s) that printers must match to appear when you select a filter. For example, you could create a custom filter to show printers that are at a specific location, regardless of the print server to which they're connected, or to show printers that have more than five print jobs in a print queue.

> [!NOTE]
> You can use the Devices and Printers tool to manage printers only on local Windows-based computers. When you use the Print Management Console, you can manage printers on local Windows-based computers, in addition to printers that are connected to other Windows-based printer servers.
