You’ve learned about MSIX app attach and how it works, now let's find out how you can use it in Contoso’s Windows Virtual Desktop environment.

# Create an MSIX image for MSIX app attach

MSIX app attach requires a MSIX image, which is a separate virtual hard disk (VHD) that contains MSIX packages. You already learned how to prepare the MSIX package, now let’s explore how to prepare the VHD.

First, download the [msixmgr tool](https://aka.ms/msixmgr) and save the msixmrg.zip folder to a folder within a session host VM. Then, unzip the **msixmgr.zip** folder and place the MSIX package in the same folder.

## Create a VHD or VHDX disk using PowerShell

1. Run the following cmdlet in PowerShell to create a VHD:

```
 \> New-VHD -SizeBytes \&lt;size\&gt;MB -Path c:\temp\\&lt;name\&gt;.vhd -Dynamic -Confirm:$false
```

2. To mount the newly created VHD run:
```

 \> $vhdObject = Mount-VHD c:\temp\\&lt;name\&gt;.vhd -Passthru
```

3. To initialize the VHD run:

```
 \> $disk = Initialize-Disk -Passthru -Number $vhdObject.Number
```

4. To create a new partition run:
```

 \> $partition = New-Partition -AssignDriveLetter -UseMaximumSize -DiskNumber $disk.Number
```

5. To format the partition run:
```

 \> Format-Volume -FileSystem NTFS -Confirm:$false -DriveLetter $partition.DriveLetter -Force
```

6. Create a parent folder on the mounted VHD.

## Expand the MSIX package

You’ll then need to expand the MSIX package in the newly created VHD. To unpack the MSIX image:

1. Open a command prompt as Administrator and navigate to the folder where you downloaded and unzipped the msixmgr tool.
2. Run the following cmdlet to unpack the MSIX into the VHD you created and mounted in the previous section.
```

 \> msixmgr.exe -Unpack -packagePath \&lt;package\&gt;.msix -destination&quot;f:\\&lt;name of folder you created earlier\&gt;&quot; -applyacls
```

3. Navigate to the mounted VHD, open the app folder, and confirm the package content is present.
4. Unmount the VHD.

# Test MSIX app attach

To test an MSIX app attach, you follow four ordered phases.

1. Make an app attach package available on a VM.
2. Make a staged app attach package available for the user. You can choose between two options:

   - Full registration
   - On-demand registration. The applications are shown to the user (in the Start menu) and registration is finished upon the user clicking the app.

1. Remove the application from the user.
2. Remove the application from the computer.

You can prepare for each phase using PowerShell scripts that run at the specific stage on the virtual machine. You can find sample scripts for each phase in the [MSIX app attach](https://github.com/Azure/RDS-Templates/tree/master/msix-app-attach) repo on GitHub.

Each of the following automatic scripts runs a different script for each phase of the app attach process:

- The startup script runs the stage script.
- The logon script runs the register script.
- The logoff script runs the deregister script.
- The shutdown script runs the destage script.

# Publish an MSIX App Attach application as a remote app

To publish an MSIX app attach application as a remote app in your Windows Virtual Desktop environment:

- Stage and then register the MSIX app attach app for the user in question.
- Configure the remote app with the required Application group in the Azure portal in the Windows Virtual Desktop console.
- Configure the remote app using the correct file paths.

## Set up an MSIX app attach share

In your Windows Virtual Desktop environment, create a network share and move the package there. The network share can be on an IaaS file share, Azure Files share or Azure NetApp Files.

# Maintain an MSIX app attach with updates and removals

You can manage new versions of the applications by uploading a new VHD on a file share. The process is similar to publishing a new MSIX app attach application.

1. You must update the MSIX app group and modify the application to the new version.

2. Users can get the new version of the application by signing out and signing in again.

3. After the user signs in, the new application is staged and registered.

4. To remove the application using MSIX app attach, remove from the group and from the file share.
