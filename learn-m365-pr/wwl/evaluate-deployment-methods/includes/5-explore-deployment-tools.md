Microsoft provides several tools for facilitating deployments and managing devices when using imaging to deploy an OS. To successfully deploy the Windows operating system and applications for your organization, it is essential that you know about the available tools to help with the process. In this topic, you will learn about the most commonly used tools for Windows deployment.

### Windows Assessment and Deployment Kit

Windows Assessment and Deployment Kit (ADK) for Windows is a collection of tools that you can use to automate the deployment of Windows operating systems and mitigate application compatibility issues. Previously, Windows ADK was called the Windows Automated Installation Kit (for Windows 7). SQL Server 2012 Express is also included here for the tools that require a connection to a SQL Server.

:::image type="content" source="../media/windows-assessmen-deployment-kit-features-install-8026a9af.png" alt-text="The ADK installer showing the various tools availble to choose to install.":::


Windows ADK contains core assessment and deployment tools and technologies, including Deployment Image Servicing and Management (DISM), Windows Imaging and Configuration Designer (Windows ICD), Windows System Image Manager (Windows SIM), User State Migration Tool (USMT), Volume Activation Management Tool (VAMT), Windows Assessment Services, Windows Performance Toolkit (WPT), Application Compatibility Toolkit (ACT), and Microsoft SQL Server 2012 Express.

### Deployment Image Servicing and Management (DISM)

Deployment Image Servicing and Management (DISM) is a command-line tool that enables you to create and manage images. You can use it to capture a "reference" device, with a desired configuration, The desired configuration might be the choice of OS edition, Windows configurations, pre-installed drivers, appliations, and files. Once the image is captures, you can use the image to deploy the pre-configured OS install to multiple devices. Once images are created, you can also DISM to change the image or keep it up to date. This can include applying updates, drivers, and language packs to the Windows image, offline or online.

For example, to capture a Windows partition to a USB storage drive, the command line might look like this:

```powershell
Dism /Capture-Image /ImageFile:"D:\Images\Fabrikam.wim" /CaptureDir:C:\ /Name:Fabrikam

```

### DISM Offline Servicing

DISM can be used to modify images while they are not in use. To edit an existing image, mount the image, make the desired changes, and then dismount the image.

:::image type="content" source="../media/service-mount-ce81e592-908467a7.png" alt-text="Graphic that shows the process of mounting an image, modifying the mounted folders, unmounting the image, and then applying to multiple devices.":::


For example, if you need to add a driver to an existing image, you first mount the image, then

```powershell
DISM /Mount-Image /ImageFile:C:\test\images\install.wim /MountDir:C:\test\offline
DISM /Image:C:\test\offline /Add-Driver /Driver:C:\drivers\mydriver.inf
DISM /Unmount-Image /MountDir:C:\test\offline /Commit
```

### Windows Imaging and Configuration Designer

Windows Imaging and Configuration Designer (Windows ICD) is a tool designed to assist with the creation of provisioning packages that can be used to dynamically configure a Windows device (PCs, tablets, and phones). This is particularly useful for setting up new devices, without the need for re-imaging the device with a custom image.

:::image type="content" source="../media/windows-imaging-configuration-designer-4e902d40-f966ab55.png" alt-text="The WICD dashboard, showing buttons to create a new provisioning pkg  or image, and buttons to open recent projects.":::


<sup>The WICD Start Page.</sup>

### Windows System Image Manager (Windows SIM)

Windows System Image Manager (Windows SIM) is a graphical tool that you can use to create unattended installation answer files (Unattend.xml) and distribution shares, or modify the files that a configuration set contains. When using MDT and/or Configuration Manager, you don’t need Windows SIM very often because those systems automatically update the Unattend.xml file during the deployment, greatly simplifying the process overall.

:::image type="content" source="../media/microsoft-deployment-toolkit-11-figure-07-1d0c144e-e5a55228.png" alt-text="Windows answer file opened in Windows SIM.":::


<sup>Windows answer file opened in Windows SIM.</sup>

### Volume Activation Management Tool (VAMT)

Volume Activation Management Tool (VAMT) is a graphical tool that you can use to automate and manage activation of Windows, Windows Server, and Microsoft Office. If you don’t use KMS, you can still manage your MAKs centrally with the Volume Activation Management Tool (VAMT). With this tool, you can install and manage product keys throughout the organization. VAMT also can activate on behalf of clients without Internet access, acting as a MAK proxy.

:::image type="content" source="../media/microsoft-deployment-toolkit-11-figure-08-d3bf0f01-1d190384.png" alt-text="The VAMT tool dashboard. On the left pane, shows products Office and Windows, as well as VL Reports. The center pane shows inventory and licence counts, the right pane shows actions.":::


<sup>The Volume Activation Management Tool.</sup>

VAMT also can be used to create reports, switch from MAK to KMS, manage Active Directory-based activation, and manage Office 2010 and Office 2013 volume activation. VAMT also supports PowerShell (instead of the old command-line tool). For example, if you want to get information from the VAMT database, you can type:

```powershell
Get-VamtProduct


```

### Windows Preinstallation Environment (Windows PE)

Windows PE is a minimal 32 bit or 64-bit operating system with limited services, built on the Windows kernel. Windows PE replaces the DOS or Linux boot disks that were once used. Use Windows PE during Windows installation and deployment to boot the computer and start the setup program. Windows PE provides read and write access to Windows file systems, and supports a range of hardware drivers, including network connectivity, which makes it useful for troubleshooting and system recovery. You can run Windows PE from the CD/DVD, USB flash drive, or a network, by using the Pre-Boot Execution Environment (PXE). The Windows ADK includes the tools to build and configure Windows PE. The key thing to know about Windows PE is that, like the operating system, it needs drivers for at least network and storage devices in each PC. Luckily Windows PE includes the same drivers as the full Windows operating system, which means much of your hardware will work out of the box.

The Windows PE is no longer part of the ADK install, and is now a separate download that can be found at [Download WinPE](/windows-hardware/manufacture/desktop/download-winpe--windows-pe?view=windows-11).

:::image type="content" source="../media/microsoft-deployment-toolkit-11-figure-09-a0045fa8-b72cdadf.png" alt-text="A machine booted with the Windows ADK default Windows PE boot image.":::


<sup>A machine booted with the Windows ADK default Windows PE boot image.</sup>

### Windows Deployment Services (WDS)

Windows Deployment Services (WDS) enables the deployment of Windows operating systems. You can use WDS to set up new clients with a network-based installation without requiring that administrators visit each computer or install directly from CD or DVD media. Images are added to a server running WDS, and transmit the image to clients using multicast funcationality.

:::image type="content" source="../media/microsoft-deployment-toolkit-11-figure-11-af96b09e-0c99e7e8.png" alt-text="Windows Deployment Services using multicast to deploy three machines.":::


<sup>Windows Deployment Services using multicast to deploy three machines.</sup>

WDS requires AD DS, DHCP, and DNS. WDS can be managed using the WDSUTIL command-line tool, Windows PowerShell, or an MMC snap-in. WDS also has the capability to manage drivers; however, driver management through MDT and Configuration Manager is more suitable for deployment due to the flexibility offered by both solutions, so you will use them instead.

### Microsoft Deployment Toolkit

Microsoft Deployment Toolkit (MDT) is a free deployment solution from Microsoft. It provides end-to-end guidance, best practices, and tools for planning, building, and deploying Windows operating systems. MDT builds on top of the core deployment tools in the Windows ADK by contributing guidance, reducing complexity, and adding critical features for an enterprise-ready deployment solution.

MDT has two main parts:

 -  **Lite Touch**. A stand-alone deployment solution.
 -  **Zero Touch**. An extension to System Center 2012 R2 Configuration Manager.

> [!NOTE]
> Lite Touch and Zero Touch are names for the two solutions that MDT supports, and the naming has nothing to do with automation. You can fully automate the stand-alone MDT solution (Lite Touch), and you can configure the solution integration with Configuration Manager to prompt for information.

:::image type="content" source="../media/microsoft-deployment-toolkit-11-figure-13-9198f864-09b5de1c.png" alt-text="The Deployment Workbench in, showing a task sequence.":::


<sup>The Deployment Workbench in, showing a task sequence.</sup>
