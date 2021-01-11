You’ve learned about MSIX app attach and how it works. Let's find out how you can use it in Contoso’s Windows Virtual Desktop environment.

## Create an MSIX image for MSIX app attach

MSIX app attach requires an MSIX image, which is the expanded content of the MSIX file stored in a VHD(X) or a Composite Image format (CIM). You already learned how to prepare the MSIX package; now let’s explore how to prepare the VHD.

First, download the [msixmgr tool](https://aka.ms/msixmgr) and save the msixmrg.zip file to a folder within a session host VM. Then, unzip the **msixmgr.zip** file and place the MSIX package in the same folder.

## Create a VHD or VHDX disk

You must create and initialize a VHD or VHDX disk. You can create the disk by using either the Disk Management MMC console or PowerShell.
Follow the steps below to create and initialize the VHD or VHDS disk by using PowerShell:

1. Run the following cmdlet in PowerShell to create a VHD:

    ```
    New-VHD -SizeBytes <size>MB -Path c:\temp\<name>.vhd -Dynamic -Confirm:$false
    ```

2. To mount the newly created VHD, run:

    ```
    $vhdObject = Mount-VHD c:\temp\<name>.vhd -Passthru
    ```

3. To initialize the VHD, run:

    ```
    $disk = Initialize-Disk -Passthru -Number $vhdObject.Number
    ```

4. To create a new partition, run:

    ```
    $partition = New-Partition -AssignDriveLetter -UseMaximumSize -DiskNumber $disk.Number
    ```

5. To format the partition, run:

    ```
    Format-Volume -FileSystem NTFS -Confirm:$false -DriveLetter $partition.DriveLetter -Force
    ```

6. Create a parent folder on the mounted VHD.

## Expand the MSIX package

You’ll then need to expand the MSIX package in the newly created VHD. To unpack the MSIX image:

1. Open a command prompt as Administrator and navigate to the folder where you downloaded and unzipped the msixmgr tool.
2. Run the following cmdlet to unpack the MSIX into the VHD you created and mounted in the previous section:

    ```
    msixmgr.exe -Unpack -packagePath <package>.msix -destination "f:\<name of folder you created earlier>" -applyacls
    ```

3. Navigate to the mounted VHD, open the app folder, and confirm the package content is present.
4. Unmount the VHD.

## Composite Image File System (CimFS)

You can prepare the MSIX image using the CimFS format that is available in the Windows 10 2004 release. CimFS provides faster mounting and unmounting times and lower memory and CPU consumption than VHD. You can also create the MSIX image with Composite Image (CIM) format that is similar to Windows Imaging Format (WIM) or read-only VHD.

## Use MSIX app attach in Windows Virtual Desktop

To use an MSIX app attach in your Windows Virtual Desktop environment:

- Set up an MSIX app attach share
- Upload the MSIX image to a file share
- Create a Windows Virtual Desktop host pool
- Publish an MSIX app
- Publish applications to a RemoteApp or remote desktop location
- Assign users or groups

### Set up an MSIX app attach share

You can use an SMB network share in your Windows Virtual Desktop environment to host the MSIX image. The network share can be on an IaaS file share, an Azure Files share, or Azure NetApp Files.

> [!Note]
> Your host pool must be granted Read permission on the file share that hosts the MSIX image.

### Upload the MSIX image to the file share

MSIX images are separated from the main operating system and reside in the file share. You can upload your MSIX image using different tools such as Azure portal, PowerShell, Azure CLI, or AzCopy.
You can also use Azure Storage Explorer which provides an intuitive UI and better performance than Azure portal.

### Create a Windows Virtual Desktop host pool

Windows Virtual Desktop is a desktop and app virtualization service that runs on the cloud.
You can deploy and manage virtual desktops using the Azure portal, Windows Virtual Desktop PowerShell, or REST interfaces.
To configure the host pools, create app groups, assign users, and publish resources use the following tutorial [Create a host pool with the Azure portal](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace).

### Create MSIX app

Once your Windows Virtual Desktop environment is ready and has at least one running VM, you can proceed with the step to add the MSIX image to the host pool.
To add the MSIX image to the host pool, you need to obtain the UNC path of the MSIX image. If you're using an Azure file share, select the properties of the MSIX image and convert the URL of the file in the UNC structure.
For example, if your storage account is called **contosostorage**, your file share **msixfileshare**, and your MSIX image is **mymsix.vhd**, use the following example:

```
URL
https://contosostorage.files.core.windows.net/msixfileshare/mymsix.vhd

UNC
\\contosostorage.files.core.windows.net\msixfileshare\mymsix.vhd
```

To add an MSIX image in the Windows Virtual Desktop environment, open the Azure portal, select your Windows Virtual Desktop host pool, and then select the **MSIX packages** tab.
From the toolbar, select **+ ADD** and in the MSIX image path, provide the UNC path to the MSIX image.

|Item|Description|
| --- | --- |
| **MSIX image path** | UNC path of the MSIX image |
| **MSIX package** | MSIX package, loaded from the MSIX image |
| **Package applications** | List of MSIX applications available in an MSIX package |
| **Display name** | Optional display name to be presented in the interface |
| **Version** | MSIX package version automatically delivered from parsing the package |
| **Registration type** | **On-demand –** User starts the MSIX application on demand. **Log on Blocking –** Registration is done during logon session. |
| **State** | **Active–** Users interact with active packages. **Inactive –** Inactive packages are not delivered to users. |

A remote desktop agent on a randomly selected VM from the host pool will access the MSIX image from the UNC path and will load it in the host pool.

:::image type="content" source="../media/04-Screenshot-of-Add-MSIX-package.PNG" alt-text="Screenshot of adding and MSIX package." border="true":::

### Publish applications

To publish MSIX applications using MSIX app attach, the state of the app in the host pool should be **Active**.
In the Azure portal, navigate to your Windows Virtual Desktop environment and select **Application Group**.
If you're publishing MSIX app attach to remote desktops, select the existing **Desktop** application group (DAG). From the Application group menu in the **Manage** section, select **Applications**, and from the toolbar, select **+ Add** to add an existing MSIX package.
To publish MSIX applications to a remote application group (RAG), follow a similar procedure to select **Application Group**.
From the toolbar, select **+ Add**, provide the name of the remote application group, and then in the Applications tab, add the existing MSIX application by selecting the application source to be the MSIX package.

:::image type="content" source="../media/04-Screenshot-of-Application-groups.PNG" alt-text="Screenshot of Application groups." border="true":::

### Assign users or groups

To assign users or groups to receive apps, in the DAG or RAG, in the Assignments tab, assign access to the MSIX app to specific users or groups.

## Maintain an MSIX app attach with updates and removals

You can manage new versions of the applications by uploading a new VHD on a file share. The process is similar to publishing a new MSIX app attach application.

You must update the MSIX app and modify the application to the new version.
Users can get the new version of the application by signing out and signing in again.
After the user signs in, the new application is staged and registered.
You can change the MSIX package registration type by opening the MSIX package and in the **Registration Type**, select **On-demand** or **Log on blocking**, as desired.
To remove the application using MSIX app attach, remove the app from Windows Virtual Desktop and from the file share.
