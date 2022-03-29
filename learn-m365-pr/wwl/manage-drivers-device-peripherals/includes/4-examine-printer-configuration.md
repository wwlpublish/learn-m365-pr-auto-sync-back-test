Like most modern peripherals for a computer, when you attach a printer directly to the device, Windows will automatically discover and download the appropriate driver needed. However, there are several unique factors related to managing printers that require additional discussion on the topic.

The most significant factor is that most printers used are not intended for use by a single device. In organizations, most printers are attached directly to the network or a printer server, and not connected directly to the end user computer. Even in the home with a printer connected to one computer, there is often a desire to enable other devices to print to it.

When you install and share a printer in Windows, you must define the relationship between the printing device, which is the physical printer, and the Windows-based computer. You can do this by adding a printer in Windows, and then specifying which driver will be used for communicating with the printing device and processing print jobs, and which port will be used for connecting with the physical printing device. Typically, locally attached Plug and Play printing devices install automatically. However, when you add a wireless printing device or a network-printing device in Devices and Printers by using the Add printers button, Windows must be able to communicate with the printing device or the print server to which the printing device is connected.

## Printing device

A printing device is a physical device that is available locally, connected to the network, or connected to the print server. You use it to produce the print job output, which is typically a printed document. By default, Windows supports many printing devices and includes drivers for communicating with those devices. You can add support for additional devices if needed.

### Printer port

Windows can automatically detect printers when you connect them to your computer, and it installs the printer driver without interaction if the driver is available in the driver store. However, a Windows operating system might not detect printers that you connect by using older ports, such as serial (COM) or parallel (LPT) ports, or network printers. In these cases, you must configure a printer port manually.

### Printer and printer driver

A printer is a Windows representation of a physical printing device. Like other devices, it is associated with a driver, which is used for communicating with a print device and rendering print jobs. Without a printer driver, the printing device that connects to a computer will not work properly.

Another consideration for printers is that there is often third-party software installed for managing the printer. While the driver is usually all that's required for basic printer capabilities, additional software is often needed to take advantage of the printers advanced functions, such as selecting a paper tray, or viewing ink or toner status. While the manufacturer may bundle the management software and driver as one app, there is typically an option for installing just the driver.

> [!NOTE]
> The Add Printer Wizard presents you with some basic drivers. You can select the Windows Update button to download a more exhaustive list. However, if your printer is not on the list, you must obtain and install the necessary driver.

## Methods for installing a printer

> [!NOTE]
> The Add Printer Wizard presents you with an extensive list of currently installed printer types. However, if your printer is not listed, you must obtain and install the necessary driver. You can pre-install printer drivers in the driver store, and then make them available in the printer list by using the Pnputil.exe command-line tool.

> [!NOTE]
> Some USB printers require that you install the printer driver before you attach it. Failure to follow this procedure can result in the printer not functioning correctly. Check the product documentation before attaching the printer to your computer.

The installation of printers on client computers is one of the most important tasks to perform when you configure network printing. There are several ways to install printers on Windows client computers:

 -  **Add a locally attached printing device automatically**. Windows automatically detects locally attached printers and installs them if their driver is available. If Windows does not find an appropriate driver in the driver store, standard users are unable to install the printer. To allow a standard user to install the printer, you could add an appropriate printer driver to the driver store by using the Pnputil.exe command-line tool. Alternatively, you can edit the local security policy to allow standard users to load and unload device drivers.
 -  **Manually browse for a shared network printer**. Users can install network printers on a Windows client computer by browsing to a print server, and then double-clicking the icon for the shared printer. The drawback to this method is that it relies on users knowing which print server is sharing the printer, which is not the case in most companies.
 -  **Find a printer in the directory**. When a printer is shared in an AD DS environment, the print administrator has the option to publish the printer in AD DS. Users can search the directory to locate the printer based on the location or printer feature. That makes it easier to locate an appropriate printer, as you can search only among printers that are available in the same location and support the required features, such as support color printing.
 -  **Deploy printers by using Group Policy settings**. When you deploy printers by using Group Policy, you can deploy printers centrally to users and computers, and make them available when users sign in. You can use Group Policies to deploy printers based on different criteria, such as group membership, or the organizational unit of the user account or computer location. One of the ways to deploy printers by using Group Policy is to right-click a printer in the Print Management console, and then select the Deploy with Group Policy option.
 -  **Deploy printers by using Group Policy preferences**. You can use Group Policy preferences to distribute printers to users and computers. Group Policy preferences are more flexible than Group Policy settings because you can deploy printers based on additional criteria, such as whether users are using laptops, the IP address range of computers, time ranges, or Lightweight Directory Access Protocol (LDAP) queries. You can use Group Policy preferences to create, update, replace, or delete a printer.

Manual methods for printer installation generally are not scalable in mediums-sized organizations, as it is too time-consuming to add and remove required printers manually to users' computers.
