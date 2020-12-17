You’ve learned about MSIX app attach and how it works. Let's find out how you can use it in Contoso’s Windows Virtual Desktop environment.

## Create an MSIX image for MSIX app attach

MSIX app attach requires a MSIX image, which is a separate VHD that contains MSIX packages. You already learned how to prepare the MSIX package; now let’s explore how to prepare the VHD.

First, download the [msixmgr tool](https://aka.ms/msixmgr) and save the msixmrg.zip file to a folder within a session host VM. Then, unzip the **msixmgr.zip** file and place the MSIX package in the same folder.

## Create a VHD or VHDX disk

You must create and initialize a VHD or VHDX disk. You can create the disk either using Disk Management mmc console or by using PowerShell. 
Follow the steps bellow to create and initialize the VHD or VHDS disk using PowerShell:

1. Run the following cmdlet in PowerShell to create a VHD:

```
 New-VHD -SizeBytes \&lt;size\&gt;MB -Path c:\temp\\&lt;name\&gt;.vhd -Dynamic -Confirm:$false
```

2. To mount the newly created VHD run:

```
 $vhdObject = Mount-VHD c:\temp\\&lt;name\&gt;.vhd -Passthru
```

3. To initialize the VHD run:

```
 $disk = Initialize-Disk -Passthru -Number $vhdObject.Number
```

4. To create a new partition run:

```
 $partition = New-Partition -AssignDriveLetter -UseMaximumSize -DiskNumber $disk.Number
```

5. To format the partition run:

```
 Format-Volume -FileSystem NTFS -Confirm:$false -DriveLetter $partition.DriveLetter -Force
```

6. Create a parent folder on the mounted VHD.

## Expand the MSIX package

You’ll then need to expand the MSIX package in the newly created VHD. To unpack the MSIX image:

1. Open a command prompt as Administrator and navigate to the folder where you downloaded and unzipped the msixmgr tool.
2. Run the following cmdlet to unpack the MSIX into the VHD you created and mounted in the previous section.

```
msixmgr.exe -Unpack -packagePath \&lt;package\&gt;.msix -destination&quot;f:\\&lt;name of folder you created earlier\&gt;&quot; -applyacls
```

3. Navigate to the mounted VHD, open the app folder, and confirm the package content is present.
4. Unmount the VHD.

## Composite Image File System (CimFS)

You can prepare MSIX image using CimFS format that is available in Windows 10 2004 release. CimFs provide faster mounting and unmounting times and lower memory and CPU consumption then VHD.
You can create MSIX image with Composite Image (CIM) format that is similar to Windows Imaging Format (WIM) or read-only VHD. 
You can use your MSIX app attach image either in the on-premises or in your Windows Virtual Desktop environment. 

## Use MSIX app attach locally

Setting up MSIX app attach outside Windows Virtual Desktop requires all phases for MSIX app attach to be performed with PowerShell scripts.
You can prepare for each phase using PowerShell scripts that run at the specific stage on the virtual machine. You can find sample scripts for each phase in the [MSIX app attach](https://github.com/Azure/RDS-Templates/tree/master/msix-app-attach) repo on GitHub.

Each of the following automatic scripts runs a different script for each phase of the app attach process:

- The startup script runs the stage script.
- The logon script runs the register script.
- The logoff script runs the deregister script.
- The shutdown script runs the destage script.

To test an MSIX app attach, you follow four ordered phases.

1. Make an app attach package available on a VM.
2. Make a staged app attach package available for the user. You can choose between two options:

   - Full registration
   - On-demand registration. The applications display in the Start menu and registration is complete when the user selects the app.

3. Remove the application from the user.
4. Remove the application from the computer.

You can integrate deployment of these PowerShell scripts using Group Policy.

## Use MSIX app attach in Windows Virtual Desktop

To use an MSIX app attach in your Windows Virtual Desktop environment:

- Set up and MSIX app attach share
- Upload MSIX image to File Share
- Create a WVD host pool
- Create MSIX app group
- Publish applications to a RemoteApp/RemoteDesktop
- Assign users or groups

### Set up an MSIX app attach share

You can use SMB network share in your Windows Virtual Desktop environment, to host MSIX image. The network share can be on an IaaS file share, Azure Files share or Azure NetApp Files. 

> [!Note]

> Your host pool must be granted Read permission on the file share that host MSIX image.

### Upload MSIX image to File Share

MSIX images are separated from the main operating system and they reside in the file share. 
You can upload your MSIX image using, different tools, such as Azure portal, PowerShell, Azure CLI or AzCopy.
You can also use Azure Storage Explorer that provide intuitive UI and better performance then Azure portal.

### Create a WVD host pool

Windows Virtual Desktop is a desktop and app virtualization service that runs on the cloud. 
You can deploy and manage virtual desktops using the Azure portal, Windows Virtual Desktop PowerShell, or REST interfaces.
To configure the host pools, create app groups, assign users, and publish resources use the following tutorial [Create a host pool with the Azure portal](https://docs.microsoft.com/en-us/azure/virtual-desktop/create-host-pools-azure-marketplace).

### Create MSIX app group

Once your WVD is ready and has at least one running virtual machine (VM) you can proceed with the step to add MSIX image to host pool.
To add the MSIX image in the host pool you need to obtain the UNC path of the MSIX image. 
If you are using Azure file share, select the properties of the MSIX image and convert the URL of the file in the UNC structure.
For example, if your storage account is called **contosostorage**, your file share **msixfileshare** and your MSIX image, is **mymsix.vhd** follow the following example:

```
URL
https://contosostorage.files.core.windows.net/msixfileshare/mymsix.vhd

UNC
\\contosostorage.files.core.windows.net\msixfilesharezmymsix.vhd
```

To add an MSIX image in the WVD, open the Azure portal, select your WVD host pool, and then select **MSIX packages** tab.
From the toolbar select **+ADD** and in the MSIX image path provide the UNC path to the MSIX image. 
Remote desktop agent on a randomly selected VM from the host pool will access the MSIX image from the UNC path and will load in the host pool.

:::image type="content" source="../media/04-Screenshot-of-Add-MSIX-package-in-WVD.PNG" alt-text="Screenshot of MSIX package in WVD." border="true":::

### Publish applications

To publish MSIX application using MSIX app attach, the state of the app in the host pool should be **Active**.
In the Azure portal, navigate to your WVD and select **Application Group**. 
If you are publishing MSIX app attach to Remote Desktops, select the existing **Desktop** application group (DAG). From the Application group menu in the **Manage** section, select **Applications** and from the toolbar select **+Add** to add and existing MSIX package.
To publish MSIX application to remote application group (RAG) follow the similar procedure to select **Application Group**. 
From the toolbar select **+Add**, provide name of the remote application group, and then in the Applications tab add the existing MSIX application, by selecting the application source to be MSIX package.

:::image type="content" source="../media/04-Screenshot-of-Application-groups-in-WVD.PNG" alt-text="Screenshot of Application grous in WVD." border="true":::

### Assign users or groups

To assign users or groups to receive apps, in the DAG or RAG, in the Assignments tab, assign access to the MSIX app to specific users or groups.

## Maintain an MSIX app attach with updates and removals

You can manage new versions of the applications by uploading a new VHD on a file share. The process is similar to publishing a new MSIX app attach application.

1. You must update the MSIX app group and modify the application to the new version.

2. Users can get the new version of the application by signing out and signing in again.

3. After the user signs in, the new application is staged and registered.

4. To remove the application using MSIX app attach, remove from the group and from the file share.
