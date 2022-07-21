Windows 10/11 Enterprise E3 and Windows 10/11 Enterprise E5 are available as online services through subscription. Deploying Windows 10 Enterprise or Windows 11 Enterprise in an organization can now be accomplished with no keys and no reboots.

If an organization is running Windows 10, version 1703 or later, or Windows 11:

 -  Devices with a current Windows 10 Pro license or Windows 11 Pro license can be seamlessly upgraded to Windows 10 Enterprise or Windows 11 Enterprise, respectively.
 -  Product key-based Windows 10 Enterprise or Windows 11 Enterprise software licenses can be transitioned to Windows 10 Enterprise and Windows 11 Enterprise subscriptions.

Organizations that have an Enterprise agreement can also benefit from the new service, using traditional Active Directory-joined devices. In this scenario, the Active Directory user that signs in on their device must be synchronized with Azure AD using Azure AD Connect Sync.

> [!NOTE]
> The Subscription Activation feature is available for qualifying devices running Windows 10 or Windows 11. You can't use Subscription Activation to upgrade from Windows 10 to Windows 11.

### Configure virtual machines to enable Windows 10/11 Subscription Activation

Organizations can configure virtual machines (VMs) to enable Windows 10/11 Subscription Activation in a Windows Virtual Desktop Access (VDA) scenario. Windows VDA is a device or user-based licensing mechanism for managing access to virtual desktops.

The following requirements must be met before an organization can configure VMs to enable Windows 10/11 Subscription Activation:

 -  VMs must be running either Windows 10 Pro, version 1703 or later, or Windows 11.
 -  VMs must be either Active Directory-joined or Azure AD-joined.
 -  VMs must be hosted by a Qualified Multitenant Hoster (QMTH), such as Microsoft Azure. For more information, see [Qualified Multitenant Hoster Program](https://download.microsoft.com/download/3/D/4/3D445779-2870-4E3D-AFCB-D35D2E1BC095/QMTH%20Authorized%20Partner%20List.pdf?azure-portal=true) (PDF download).

VMs can be configured to enable Windows 10/11 Subscription Activation in the following scenarios:

 -  **Scenario 1**
     -  The VM is running Windows 10, version 1803 or later, or Windows 11.
     -  The VM is hosted in Azure or another Qualified Multitenant Hoster (QMTH).
     -  When a user with VDA rights signs in to the VM using their Azure Active Directory credentials, the VM is automatically stepped-up to Enterprise and activated. There's no need to perform Windows 10/11 Pro activation. This design eliminates the need to maintain Key Management Services (KMS) or a Multiple Activation Key (MAK) in the qualifying cloud infrastructure.
 -  **Scenario 2**
     -  The Hyper-V host and the VM are both running Windows 10, version 1803 or later.
     -  [Inherited Activation](/windows/deployment/windows-10-subscription-activation#inherited-activation?azure-portal=true) is enabled.
     -  All VMs created by a user with a Windows 10/11 E3 or E5 license are automatically activated independent of whether a user signs in with a local account or using an Azure Active Directory account.
 -  **Scenario 3**
     -  The VM is running Windows 10, version 1703 or 1709, or the hoster isn't an authorized [QMTH](https://download.microsoft.com/download/3/D/4/3D445779-2870-4E3D-AFCB-D35D2E1BC095/QMTH%20Authorized%20Partner%20List.pdf?azure-portal=true) partner.
     -  In this scenario, the underlying Windows 10/11 Pro license must be activated prior to Subscription Activation of Windows 10/11 Enterprise. Activation is accomplished using a Generic Volume License Key (GVLK) and a Volume License KMS activation server provided by the hoster. Alternatively, a KMS activation server can be used. KMS activation is provided for Azure VMs. For more information, see [Troubleshoot Azure Windows virtual machine activation problems](/azure/virtual-machines/troubleshooting/troubleshoot-activation-problems?azure-portal=true).

For examples of activation issues, see [Troubleshoot the user experience](/windows/deployment/deploy-enterprise-licenses#troubleshoot-the-user-experience?azure-portal=true).

Organizations should be familiar with the deployment scenarios provided in the following sections.

### Active Directory-joined VMs

Before an organization uploads a Windows virtual machine (VM) from on-premises to Azure, it must prepare the virtual hard disk (VHD or VHDX). Azure supports both generation 1 and generation 2 VMs that are in VHD file format and that have a fixed-size disk. The maximum size allowed for the OS VHD on a generation 1 VM is 2 TB.

Organizations can convert a VHDX file to VHD, and convert a dynamically expanding disk to a fixed-size disk. However, they can't change a VM's generation. For more information, see [Should I create a generation 1 or 2 VM in Hyper-V?](/windows-server/virtualization/hyper-v/plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V?azure-portal=true) and [Support for generation 2 VMs on Azure](/azure/virtual-machines/generation-2?azure-portal=true).

Perform the following steps to enable Windows 10/11 Subscription Activation in Active Directory-joined VMs:

1.  Complete the instructions in the following document to prepare the VM for Azure: [Prepare a Windows VHD or VHDX to upload to Azure](/azure/virtual-machines/windows/prepare-for-upload-vhd-image?azure-portal=true).
2.  (Optional) To disable network level authentication, type the following instruction at an elevated command prompt:
    
    ```powershell
    REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp" /v UserAuthentication /t REG_DWORD /d 0 /f
    ```
3.  At an elevated command prompt, type **sysdm.cpl** and press ENTER.
4.  On the **Remote** tab, select **Allow remote connections to this computer** and then select the **Select Users** option.
5.  Select **Add**, type **Authenticated users**, and then select **OK** three times.
6.  Follow the instructions to use sysprep at [Steps to generalize a VHD](/azure/virtual-machines/windows/prepare-for-upload-vhd-image#steps-to-generalize-a-vhd?azure-portal=true) and then start the VM again.
7.  If you must activate Windows 10/11 Pro as described above in **Scenario 3**, complete steps 8 through 19 to use Windows Configuration Designer and inject an activation key. Otherwise, skip to step 20.
8.  Complete the instructions in the following document: [Install Windows Configuration Designer](/windows/configuration/provisioning-packages/provisioning-install-icd?azure-portal=true).
9.  Open **Windows Configuration Designer** and select **Provision desktop services**.
10. Under **Name**, type **Desktop AD Enrollment Pro GVLK**, select **Finis**h, and then on the **Set up device** page, enter a device name.
    
    > [!NOTE]
    > You can use a different project name, but this name is also used with **dism.exe** in a subsequent step.
11. Under **Enter product key** type the **Pro GVLK** key: **W269N-WFGWX-YVC9B-4J6C9-T83GX**
12. On the **Set up network** page, select **Off**.
13. On the **Account Management** page, select **Enroll into Active Directory** and then enter the account details.
    
    > [!NOTE]
    > This step is different for [Azure AD-joined VMs](/windows/deployment/vda-subscription-activation#azure-active-directory-joined-vms?azure-portal=true).
14. On the **Add applications** page, add applications if desired. This step is optional.
15. On the Add certificates page, add certificates if desired. This step is optional.
16. On the **Finish** page, select **Create**.
17. In **File Explorer**, double-click the VHD to mount the disk image. Determine the drive letter of the mounted image.
18. Type the following command at an elevated command prompt. Replace the letter **G** with the drive letter of the mounted image, and enter the project name you used if it's different than the one suggested:
    
    ```powershell
    Dism.exe /Image=G:\ /Add-ProvisioningPackage /PackagePath: "Desktop AD Enrollment Pro GVLK.ppkg"
    
    ```
19. Right-click the mounted image in File Explorer and select **Eject**.
20. Complete the instructions in [Upload and create VM from generalized VHD](/azure/virtual-machines/windows/upload-generalized-managed#log-in-to-azure?azure-portal=true) to sign in to Azure, get your storage account details, upload the VHD, and create a managed image.

### Azure Active Directory-joined VMs

> [!IMPORTANT]
> Azure Active Directory (Azure AD) provisioning packages have a 180 day limit on bulk token usage. You'll need to update the provisioning package and reinject it into the image after 180 days. Existing virtual machines that are Azure AD-joined and deployed won't need to be recreated.

For Azure AD-joined VMs, follow the same instructions (above) as for Active Directory-joined VMs, with the following exceptions:

 -  In step 10, during setup with Windows Configuration Designer, under **Name**, type a name for the project that indicates it isn't for Active Directory-joined VMs, such as Desktop Bulk Enrollment Token Pro GVLK.
 -  In step 13, during setup with Windows Configuration Designer, on the **Account Management** page, instead of enrolling in Active Directory, select **Enroll in Azure AD**, select **Get Bulk Token**, sign in and add the bulk token using your organization's credentials.
 -  In step 18, when entering the **PackagePath**, use the project name you entered in step 10 (ex: Desktop Bulk Enrollment Token Pro GVLK.ppkg).
 -  When attempting to access the VM using remote desktop, you'll need to create a custom RDP settings file as described in the section below titled **Create custom RDP settings for Azure**.

### Azure Gallery VMs

An image is a copy of either a full VM (including any attached data disks) or just the OS disk, depending on how it's created. When you create a VM from the image, a copy of the VHDs in the image are used to create the disks for the new VM. The image remains in storage and can be used over and over again to create new VMs.

If an organization has a large number of images that it needs to maintain, and it would like to make them available throughout the company, it can use an [Azure Compute Gallery](/azure/virtual-machines/azure-compute-gallery?azure-portal=true) as a repository.

When an organization uses a gallery to store images, multiple resource types are created.

| **Resource**     | **Description**                                                                                                                                                                                                                                                                                                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Image source     | This resource can be used to create an image version in a gallery. An image source can be an existing Azure VM that's either [generalized or specialized](/azure/virtual-machines/shared-image-galleries?tabs=azure-cli#generalized-and-specialized-images?azure-portal=true), a managed image, a snapshot, a VHD, or an image version in another gallery. |
| Gallery          | Like the Azure Marketplace, a gallery is a repository for managing and sharing images and other resources. However, an organization can control who has access.                                                                                                                                                                                                                      |
| Image definition | Image definitions are created within a gallery and they carry information about the image and any requirements for using it to create VMs. This information includes whether the image is Windows or Linux, release notes, and minimum and maximum memory requirements. It's a definition of a type of image.                                                                        |
| Image version    | An image version is what an organization uses to create a VM when using a gallery. It can have multiple versions of an image as needed for its environment. Like a managed image, when an image version is used to create a VM, the image version is used to create new disks for the VM. Image versions can be used multiple times.<br><br>                                         |

1.  (Optional) To disable network level authentication, type the following command at an elevated command prompt:
    
    ```powershell
    REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp" /v UserAuthentication /t REG_DWORD /d 0 /f
    ```
2.  At an elevated command prompt, type **sysdm.cpl** and press ENTER.
3.  On the **Remote** tab, select **Allow remote connections to this computer** and then select the **Select Users** option.
4.  Select **Add**, type **Authenticated users**, and then select **OK** three times.
5.  Complete the instructions in the following document: [Install Windows Configuration Designer](/windows/configuration/provisioning-packages/provisioning-install-icd?azure-portal=true).
6.  Open **Windows Configuration Designer** and select **Provision desktop services**.
7.  If you must activate Windows 10/11 Pro as described above in **Scenario 3**, complete steps 8 through 9. Otherwise, skip to step 10.
8.  Under **Name**, type **Desktop Bulk Enrollment Token Pro GVLK**, select **Finish**, and then on the **Set up device** page, enter a device name.
9.  Under **Enter product key,** type the Pro GVLK key: **W269N-WFGWX-YVC9B-4J6C9-T83GX**
10. Under **Name,** type **Desktop Bulk Enrollment**, select **Finish**, and then on the **Set up device** page enter a device name.
11. On the **Set up network** page, select **Off**.
12. On the **Account Management** page, select **Enroll in Azure AD**, select **Get Bulk Token**, sign in, and add the bulk token using your organizations credentials.
13. On the **Add applications** page, add applications if desired. This step is optional.
14. On the **Add certificates** page, add certificates if desired. This step is optional.
15. On the **Finish** page, select **Create**.
16. Copy the **.ppkg** file to the remote virtual machine. Double click to initiate the provisioning package installation. Doing so will reboot the system.

> [!NOTE]
> When attempting to access the VM using remote desktop, you must create a custom RDP settings file as described in the next section.

### Create custom RDP settings for Azure

Organizations can specify custom Remote Desktop Protocol (RDP) settings, such as audio redirection, for virtual desktop connections. These settings are applied when a user connects to a virtual desktop pool or a personal virtual desktop through RemoteApp and Desktop Connection. There are separate custom RDP settings for virtual desktop pools and personal virtual desktops. For more information on the RDP settings for Azure that can be customized, see [Supported Remote Desktop RDP file settings](/windows-server/remote/remote-desktop-services/clients/rdp-files?azure-portal=true).

Perform the following steps to create a custom Remote Desktop Protocol (RDP) settings file for Azure. This example updates two connection settings: **enablecredsspsupport** and **authentication level**.

 -  **enablecredsspsupport**.Changing this setting to a value of 1 indicates that RDP will use Credential Security Support Provide (CredSSP) for authentication if the OS supports CredSSP.
 -  **authentication level**. Changing this setting to a value of 2 indicates that if server authentication fails, a warning will be displayed and the user will be allowed to connect or refuse the connection.

1.  Open **Remote Desktop Connection** and enter the **IP address** or **DNS name** for the remote host.
2.  Select **Show Options**, and then under **Connection settings**, select **Save As** and save the RDP file to the location where you'll use it.
3.  Close the **Remote Desktop Connection** window.
4.  Open **Notepad**.
5.  Drag the RDP file into the Notepad window to edit it.
6.  Enter or replace the line that specifies authentication level with the following two lines of text:
    
    ```
    enablecredsspsupport:i:0
    authentication level:i:2
    ```
    
        > [!NOTE]
        > **enablecredsspsupport** and **authentication level** should each appear only once in the file.
7.  Save your changes, and then use this custom RDP file with your Azure AD credentials to connect to the Azure VM.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”