When deploying an operating system in any organization with more than 100 computers, manual deployment of operating systems becomes impractical. Organizations employ methods such as Imaging and Autopilot to automate and streamline this process.

### What is Imaging?

Imaging is the process of creating a "snapshot" of a reference computer with the desired OS, configurations, and apps pre-installed, and then deploying that snapshot to multiple computers. When the image is deployed, it is essentially copying the reference computer configuration to the target computer. This has been the preferred method used in medium and large organizations for years.

#### Benefits of Imaging

 -  Eliminates the manual process of installing the OS and configuring the device (and included apps) on each target device.
 -  Ensures devices have a consistent configuration. The reduces the chance for human error during the deployment and helps ensure devices are compliant and secure.
 -  Imaging, along with a management tool such as MDT or Configuration Manager can make the deployment process completely automated, with little to no action needed by IT or the end user, once the device is plugged in.

#### Disadvantages of Imaging

 -  Creating and managing images takes effort. Scenarios such as different requirements within the organization, updates to apps and the operating system, and hardware architecture, can be contributing factors to the number of images needed. More images increase the overhead needed to maintain the images.
 -  Creating and deploying images is more complex and requires advanced tools to manage the process than manual deployment.
 -  Deploying images can consume considerable bandwidth during the process, and additional considerations are required when target clients have limited bandwidth and connectivity.

### Autopilot

Autopilot was first introduced in Windows 10. The concept behind autopilot was to reduce the need to reimage machines. Typically, when a new device is purchased, Windows is pre-installed on it by the hardware vendor, with the vendor's preferred configuration. Autopilot reconfigures the device to a clean Windows 10 or 11 install, providing an out-of-box experience while applying the organization's desired configuration and applications. Configuring a device using Autopilot is typically easier than creating and managing images.

In addition to deployments, Autopilot can also help with refreshing and troubleshooting scenarios. Support staff dealing with a troublesome device will frequently opt to wipe and reimage the device. Autopilot Reset enables a similar result, reverting to a clean install of Windows 10 or Windows 11 with configurations applied and applications reinstalled.

Customers can also use Endpoint Configuration Manager version 1806 or later to convert existing Windows 8.1 devices to Windows 10 or later devices using Windows Autopilot.
