New versions of Windows have typically been deployed by organizations using an image-based process built on top of tools provided in the:

 -  [Windows Assessment and Deployment Kit](/windows/deployment/windows-adk-scenarios-for-it-pros?azure-portal=true).
 -  [Windows Deployment Services](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831764%28v=ws.11%29?azure-portal=true).
 -  [Deploy Windows 10/11 with the Microsoft Deployment Toolkit](/windows/deployment/deploy-windows-mdt/prepare-for-windows-deployment-with-mdt?azure-portal=true).
 -  [Microsoft Endpoint Configuration Manager](/windows/deployment/deploy-windows-cm/prepare-for-zero-touch-installation-of-windows-10-with-configuration-manager?azure-portal=true).

With the release of both Windows 10 and 11, these tools were updated to fully support both operating systems. Although newer scenarios such as in-place upgrade and dynamic provisioning may reduce the need for traditional deployment capabilities in some organizations, these traditional methods remain important, and will continue to be available to organizations that need them.

The traditional deployment scenario can be divided into different subscenarios. These subscenarios are explained in detail in the following sections, but the following list provides a brief summary:

 -  **New computer**. A bare-metal deployment of a new machine.
 -  **Computer refresh**. A reinstall of the same machine (with user-state migration and an optional full Windows Imaging (WIM) image backup).
 -  **Computer replace**. A replacement of the old machine with a new machine (with user-state migration and an optional full WIM image backup).

### New computer

Also called a "bare metal" deployment. This scenario occurs when an organization has a blank machine it must deploy, or an existing machine it wants to wipe and redeploy without needing to preserve any existing data. The setup starts from a boot media, using CD, USB, ISO, or Pre-Boot Execution Environment (PXE). An organization can also generate a full offline media that includes all the files needed for a client deployment. This design enables the organization to deploy without having to connect to a central deployment share. The target can be a physical computer, a virtual machine, or a Virtual Hard Disk (VHD) running on a physical computer (boot from VHD).

The deployment process for the new machine scenario is as follows:

1.  Start the setup from boot media (CD, USB, ISO, or PXE).
2.  Wipe the hard disk clean and create new volume(s).
3.  Install the operating system image.
4.  Install other applications (as part of the task sequence).

After an organization completes these steps, the computer is ready for use.

### Computer refresh

A refresh is sometimes called wipe-and-load. The process is normally initiated in the running operating system. User data and settings are backed up and restored later as part of the deployment process. The target can be the same as for the new computer scenario.

The deployment process for the wipe-and-load scenario is as follows:

1.  Start the setup on a running operating system.
2.  Save the user state locally.
3.  Wipe the hard disk clean (except for the folder containing the backup).
4.  Install the operating system image.
5.  Install other applications.
6.  Restore the user state.

After an organization completes these steps, the machine is ready for use.

### Computer replace

A computer replace is similar to the refresh scenario. However, since the machine is being replaced, this scenario is divided into two main tasks:

 -  Backup of the old client.
 -  Bare-metal deployment of the new client.

As with the refresh scenario, user data and settings are backed up and restored.

The deployment process for the replace scenario is as follows:

1.  Save the user state (data and settings) on the server through a backup job on the running operating system.
2.  Deploy the new computer as a bare-metal deployment.
    
    In some situations, the replace scenario can be used even if the target is the same machine. For example, replace can be used if an organization wants to modify the disk layout from the master boot record (MBR) to the GUID partition table (GPT). This process enables the organization to take advantage of the Unified Extensible Firmware Interface (UEFI) functionality. Replace can also be used if the disk must be repartitioned, since user data must be transferred off the disk.
