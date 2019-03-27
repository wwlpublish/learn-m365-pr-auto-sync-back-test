Most organizations use the process of PC imaging to configure and capture a clone of Windows, including a base set of a few standard apps installed, or an even a thinner image with only application runtimes and updates. The best way to do this is using a virtual machine for capture to avoid any unexpected driver-related compatibility issues and for automation purposes.

When using the image capture method, it is best to automate as much as possible to ensure the best quality image and a repeatable process. For most deployments, it is also recommended to put as little customization and pre-installed apps as possible in the Windows image prior to capturing. This is what is called a ‘thin image’ approach, which can save overall bandwidth on the network by eliminating the number of apps within the image. By starting with a thin base image, you can layer on required apps, languages and configurations dynamically tailored to end users.

During the build and capture process, tools like System Center Configuration Manager and the Microsoft Deployment Toolkit use the System Preparation Tool – or Sysprep – along with the “Generalize” command to reseal your image before they capture the Windows 10 installation as an image.

The captured image will have the Windows image – or WIM – format like standard Windows installation media. With the custom WIM file, IT admins can use another task sequence as part of the OS deployment in System Center Configuration Manager or Microsoft Deployment Toolkit to perform deployment-related tasks, to apply the image, and run tasks before and after the Windows image is applied.

## Traditional deployment types
With a custom image ready, the installation or migration type will fall into the following categories:
- First, bare metal deployment. This is the scenario used to deploy an image to a clean disk, or to reimage a computer where you don’t intend to keep any of the data on the disk
- Second, similar to bare metal, is Computer Refresh with the key difference that user state remains on the disk or will be restored after the install is complete
- Last is Computer Replacement which as the name implies, involves replacing a PC with another PC. In this case, there is often a backup of end user files from the first PC to a central location, then a restore of those files to the second PC.

All three of these scenarios have something in common, they use a task sequence to run, and a custom image can be applied each time.

## Phased deployment
During deployment planning you’ll be targeting computers for bare metal, refresh, replace, and upgrade paths. The recommended approach in this case is to use phased deployment to collections of similar machines. This way, IT admins can validate compatibility, delivery and automation, user acceptance, network bandwidth consumption, and other factors before increasing the scale of the deployment.

**Recommended Tools: System Center Configuration Manager and the Microsoft Deployment Toolkit**

Regardless of the deployment type selected, it’s common practice to provide as much automation as possible for predictability and repeatability. Microsoft offers two solutions to automate OS deployment using automated task sequences:

**System Center Configuration Manager** provides built-in operating system deployment capabilities to complement its capabilities for software distribution and software update management. It is widely used by organizations of all sizes and supports all four Windows deployment types. Optionally, System Center Configuration Manager can be integrated with Microsoft Intune to add additional capabilities for deployment and device management.

**Microsoft Deployment Toolkit (MDT)** is the other popular and free option which is typically used by small and medium sized organizations for OS deployment. This requires very little infrastructure and MDT integrates with Windows Deployment Services (WDS) for network boot. It supports all four deployment types as well as installation of applications, drivers, and settings. Additionally, MDT can even be integrated with Configuration Manager.
