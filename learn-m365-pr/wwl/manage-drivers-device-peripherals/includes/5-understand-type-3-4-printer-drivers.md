Windows traditionally uses separate Type 3 printer drivers for each printer device model. Printer manufacturers created customized printer drivers for each specific device that they created, to ensure that Windows could use all of the printer features. When printers are shared on the network, the administrator must maintain drivers for each printing device in the environment, and the administrator must add separate 32-bit and 64-bit drivers for a single printer to support both type of clients.

:::image type="content" source="../media/type-4-drivers-26d3e18f.jpg" alt-text="screenshot of the settings for a type 4 driver.":::


Microsoft introduced Type 4 printer drivers in Windows 8 and Windows Server 2012. By following the Type 4 printer driver model, printer manufacturers can create a single Print Class Driver that supports similar printing features and printing language that are common to a large number of printer models. Common printing languages include PCL, and PostScript or XPS.

Type 4 printer drivers typically are delivered by using Windows Update or Windows Software Update Services (WSUS). Unlike Type 3 drivers, Type 4 drivers do not download from a print server.

A Type 4 printer driver model provides the following benefits:

 -  Sharing a printer does not require adding extra drivers that match the client architecture.
 -  A single Type 4 driver can support multiple printer models.
 -  Driver files are isolated on a per-driver basis, which prevents potential driver file-naming conflicts.
 -  Driver packages are smaller and more streamlined than Type 3 drivers, and Type 4 drivers install faster than Type 3 drivers.
 -  Printer driver and the printer user interface can be deployed independently with Type 4 drivers.
