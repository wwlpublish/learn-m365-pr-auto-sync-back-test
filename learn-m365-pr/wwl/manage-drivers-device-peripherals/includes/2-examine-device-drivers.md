Windows uses device drivers to control and communicate with a variety of hardware devices. A device driver is a program that communicates with a hardware device on one side and the operating system on the other. Device drivers are a critical part of the operating system. The operating system cannot use a device if its driver is unavailable.

Windows is capable of detecting most hardware and automatically downloading and installing the correct driver. This occurs when Windows is first installed, or when new hardware is installed in the device. Manufactures provide and certify their driver with Microsoft, making the process seamless to the end user.

Device drivers execute in the operating system kernel and have access to all system resources. Thorough testing of device drivers is very important to ensure that they do not include malicious code. A digital signature from a trusted authority is proof that you can safely use a device driver. Unless a 32-bit version of Windows is installed, all drivers must be signed.

## Installing Drivers Manually

Occasionally, there may be the need to manually install the driver. This may be due to reasons such as:

 -  The hardware is older and not available from Windows Update.
 -  The hardware driver is only provided by the manufacturer.
 -  The scenario may call for a different driver from the manufacturer other than the one provided to Microsoft.

In cases such as these, most manufacturers make their drivers available for download on their website. These are typically referred to as driver packages. A driver package is a set of files that make up a device driver. A driver package is device-specific and enables Windows to communicate with the device. A driver package includes:

A driver package is a set of files that make up a driver. A driver package includes:

 -  The .inf file.
 -  Any files that the .inf file references.
 -  The catalog (.cat) file that contains the digital signature of the device driver.

:::image type="content" source="../media/driver-file-details-f60c2acf.jpg" alt-text="Screen shot of a device driver.":::


How the driver is installed depends on how the driver was packaged. Some are provided with an executable, while allows the driver to be installed in the driver store, just like installing an app. When the respective hardware is detected, Windows uses that driver to communicate with the hardware. If the driver package isn't self-installed, when the hardware is connected, Windows will search several locations for the matching driver or the user may specify the location of the driver package.

Once the driver is installed, it's located in the driver store at %SystemRoot%\\System32\\DriverStore. When managing drivers at scale, Administrators can include driver packages in the OS image or deploy then separately using methods such as Group Policy or management tools like MDT or Configuration Manager. Once drivers are in the driver store, the end user experience is still seamless when they attach the hardware.

## 32-bit and 64-bit drivers

If managing a 32-bit installation of Windows, you must use the 32-bit version. Likewise, 32-bit versions of drivers will not work 64-bit versions. As deployments of 32-bit Windows are becoming increasingly rare, and Windows 11 does not offer a 32-bit version, many manufactures no longer offer 32-bit drivers.

## Driver store

The driver store is the Windows driver package repository. Because the driver store is a trusted location, when you connect compatible hardware, Windows installs the driver for the appropriate device automatically from the driver store. Standard users can install any device driver from the driver store. Therefore, users can attach and use new devices without help from the IT helpdesk, if their driver package is in the driver store. Information technology (IT) administrators can pre-load the driver store with the necessary driver packages for commonly used devices. The driver store is located at %SystemRoot%\\System32\\DriverStore.
