When deploying an operating system in any organization with over 100 computers, manual deployment of operating systems becomes impractical. Organizations employ methods such as Imaging and Autopilot to automate and streamline this process.

### What is Imaging?

Imaging is creating a “snapshot” of a reference computer with the desired OS, configurations, and apps pre-installed and then deploying that snapshot to multiple computers. It copies the reference computer configuration to the target computer when deploying an image. This method has been the preferred used in medium and large organizations for years.

#### Benefits of Imaging

 -  Imaging eliminates the manual process of installing the OS and configuring the device (and included apps) on each target device.
 -  Imaging ensures devices have a consistent configuration. It reduces the chance of human error during the deployment and helps ensure devices are compliant and secure.
 -  Imaging, along with a management tool such as MDT or Configuration Manager, can automate the deployment process, with little to no action needed by IT or the end user once they plug in the device.

#### Disadvantages of Imaging

 -  Creating and managing images takes effort. Scenarios such as different requirements within the organization updates to apps and the operating system and hardware architecture can contribute to the number of images needed. More images increase the overhead required to maintain the images.
 -  Creating and deploying images is more complex and requires advanced tools to manage the process than manual deployment.
 -  Deploying images can consume considerable bandwidth during the process, and extra considerations are necessary when target clients have limited bandwidth and connectivity.

### Autopilot

Windows 10 was the first to introduce Autopilot. The concept behind Autopilot was to reduce the need to reimage machines. Typically, new devices come pre-installed with Windows on them by the hardware vendor, with the vendor’s preferred configuration. Autopilot reconfigures the device to a clean Windows 10 or 11 install, providing an out-of-box experience while applying the organization’s desired configuration and applications. Configuring a device using Autopilot is typically easier than creating and managing images.

Besides deployments, Autopilot can also help with refreshing and troubleshooting scenarios. Support staff dealing with a troublesome device will frequently opt to wipe and reimage the device. Autopilot Reset enables a similar result, reverting to a clean install of Windows 10 or 11 with configurations applied and applications reinstalled.

Customers can also use Endpoint Configuration Manager version 1806 or later to convert existing Windows 8.1 devices to Windows 10 or 11 using Windows Autopilot.
