These days, you can attach most hardware devices to computers by using a USB device, which is convenient and require no special skills or tools to use. Install a new USB hardware by plugging the device into a free USB port on your device, and the device driver installs automatically, if available. However, this convenience could pose risks to your network’s security.

USB devices represent a potential security risk to your network because a malicious user could copy sensitive or confidential network data onto a mobile device, such as an external hard disk, and then remove it from the workplace. USB device installation is simple, and users are installing an increasing number of USB devices more frequently. Therefore, as the number and variety of these devices increases, so does the associated support and maintenance costs for issues that they introduce. Therefore, controlling use of these devices has become an important consideration for administrators.

Many organizations restrict employee use of USB devices because of security and management reasons. However, implementing restrictions on USB devices can affect user productivity. It also can have a significant impact on hardware troubleshooting if the person who is performing troubleshooting diagnoses these restrictions as hardware faults incorrectly. Windows uses two methods to control USB device installation: device identification strings and device setup classes.

#### Device identification strings

Hardware manufacturers assign one or more device identification strings to each device. These identification strings are in the setup information (.inf) file in the driver package. During device initialization, Windows retrieves these device identification strings, and matches them to corresponding identification strings in the .inf file. Identification strings are either general or specific. If specific, they identify the device’s exact make and model. Device identification strings are one of two types:

 -  **Hardware identifiers**. Hardware identifiers provide an exact match between a device and a device driver package. The first string in the device identifier list is the individual device’s specific identifier. Additional strings in the list identify the device more generally. This allows Windows to install a different device revision driver if the correct one is not available.
 -  **Compatible identifiers**. Windows uses compatible identifiers to select a device driver only if the driver store has no available drivers for any of the hardware identifiers that Windows retrieves from the device. These strings are optional, and Windows lists them in decreasing order of suitability if the hardware manufacturer provides them. Typically, the strings are generic and identify the hardware device at the component level, such as a Small Computer System Interface (SCSI) hard disk drive. This enables Windows to select a generic SCSI driver for the disk drive, but may result in limited device functionality and slower read/write performance.

Multifunction devices are physical devices that include more than one logical device. Combination printer/scanner/fax devices and modem/network cards are common multifunction devices. Manufacturers assign hardware identifiers to each logical device so that it can manage part of the functionality of the physical device. For example, an all-in-one scanner/printer/fax might have different device identification strings for each function. To control installation of multifunction devices, you specifically must allow or deny all hardware identifiers for each multifunctional device. If you do not do this, you could cause unexpected results from some of the logical devices that have drivers installed for the one physical device.

The following sample is the relevant portion of an .inf file for a keyboard device driver:

```
[MsMfg]

;========= Microsoft USB Internet Keyboard (IntelliType Pro)

%HID\\VID_045E&PID_002D&MI_00.DeviceDesc%=MicrosoftKBD_Dev,HID\\VID_045E&PID_002D&MI_00

;========= Microsoft USB Wireless MultiMedia Keyboard (IntelliType Pro) - with
Wireless Optical Mouse

%HID\\VID_045E&PID_005F&MI_00.DeviceDesc%=MicrosoftKBD_Dev,HID\\VID_045E&PID_005F&MI_00

;========= Microsoft USB Wireless MultiMedia Keyboard (106/109) (IntelliType
Pro) - with Wireless Optical Mouse

%HID\\VID_045E&PID_0061&MI_00.DeviceDesc%=MicrosoftKBD_Dev_109,HID\\VID_045E&PID_0061&MI_00

;========= Microsoft USB Wireless Natural MultiMedia Keyboard (IntelliType Pro)

- with Wireless Optical Mouse

%HID\\VID_045E&PID_0063&MI_00.DeviceDesc%=MicrosoftKBD_Dev,HID\\VID_045E&PID_0063&MI_00


```

To interpret the preceding and subsequent configuration files, use the following key:

 -  HID = Human Interface Device, such as keyboards and mice.
 -  VID = Vendor ID
 -  PID = Product ID

#### Device setup classes

The device setup class groups devices that you install and configure in the same way. For example, all keyboards belong to the Keyboard device setup class, and they use the same co-installer when installed. A GUID represents each device setup class. The manufacturer of a device driver package assigns the device setup class, and then Windows builds a memory-tree structure that contains the GUIDs for all devices that it detects, including that of any bus that you attach to the device. You can use Group Policy to specify the device class for which you allow or disallow installation. The following sample is the relevant portion of an .inf file for a keyboard device driver.

```
[Version]

CatalogFile.NT= type32.cat ;Digital Signing

Signature="\$Windows NT\$" ;All Platforms

Class=Keyboard

ClassGUID={4d36e96b-e325-11ce-bfc1-08002be10318}

Provider=Microsoft

LayoutFile=layout.inf

DriverVer=06/29/2010, 8.0.219.0


```

:::image type="content" source="../media/usb-devices-f79a9d8f.jpg" alt-text="Screenshot showing USB Class GUID references.":::


#### Control USB device access

In Windows, you can use Group Policy to control how USB devices access your computer. You can use Group Policy to:

 -  Prevent users from installing any device.
 -  Allow users to install only devices on an approved list.
 -  Prevent users from installing devices that are on a prohibited list.
 -  Deny read or write access to removable devices or removable media.

> [!NOTE]
> USB device firmware might include malicious code, which can execute, without user interaction, when a user connects an affected USB device. Restricting USB device installation can benefit hardware support in several ways, including by ensuring:

 -  **More simple data security**. When you limit the devices that users can install, you can reduce the risk of data theft. For example, allowing users to connect only encrypted USB flash drives provides additional protection for data that users transfer from the company network.
 -  **Reduced support costs**. You can ensure that users only install devices that your help desk has preapproved and tested, which reduces support costs and user confusion.

However, controlling USB device installation could cause issues, including:

 -  **Misdiagnosed faults**. Unless policy restrictions are simple, consistent, and easily understood by IT staff and users, IT staff might diagnose a restriction as a hardware problem.
 -  **Policy management**. Some manufacturers use a range of identifiers for similar device models. When you have a batch of such devices, you could have difficulty supporting policy restrictions based on identifiers. Consequently, the success of these policies could be inconsistent. For example, although a batch of devices from a single vendor could appear identical, you should check each device identifier to verify that the entire batch uses the same identifier. If there is a range of identifiers, you will need to modify your Group Policy settings to include all of these identifiers.

> [!NOTE]
> You also must consider the USB version on specific devices. Many computers provide both USB 2 and USB 3 ports for peripheral devices. However, some tablet devices provide only USB 2 ports. If your peripheral requires a USB 3 connection, you will be unable to use that device with a USB 2 port.
