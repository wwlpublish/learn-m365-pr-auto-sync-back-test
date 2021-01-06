You’ve learned about MSIX packages. Now let's consider how you can deploy those applications into your Windows Virtual Desktop environment and determine if MSIX app attach is right for Contoso.

## Purpose and benefits of MSIX app attach

MSIX app attach is a Microsoft application delivering approach design for a modern workspace. With MSIX app attach, you can use on application format, namely MSIX, to deliver applications to both physical and virtual machines. Although MSIX app attach can be used on-premises or in Azure, this technology is specially adopted for Windows Virtual Desktop.

The following are MSIX app attach benefits:

- You can use existing MSIX packages, without repacking or altering the structure.
- You don't need additional infrastructure servers to deploy the MSIX packages. You can use existing Azure Files for hosting the virtual hard disk (VHD) that contains the MSIX package.
- MSIX app attach separates application files from the operating system. If the device needs a reset or reimage, these applications will not require a reinstallation.
- You can edit and update the applications, after which all the changes will be saved as a new package that can replace the old MSIX app attach package.
- You can combine MSIX app attach with FSLogix Profile containers to isolate user profiles on a separate virtual hard disk VHD or VHDX.

Contoso is a good candidate for using MSIX app attach for their application delivery needs as they use Windows Virtual Desktop and Azure for file management.

## How MSIX app attach works

MSIX app attach stores application files in a separate virtual hard disk from the operating system. It registers the regular MSIX package on a device instead of on a physical download and install. The registration uses existing Windows Applications Programing Interfaces (API) and has minimal impact on user sign in times, which enhances the user experience.

When MSIX app attach is launched, the application files are accessed from a VHD, and the user isn’t even aware that the application isn’t locally installed.

MSIX app attach follows several steps or actions:

|Term| Definition|
|----------------|------------------------------------------------------------|
| Stage|Notifies the operating system that an application is available, and the virtual disk containing the MSIX package (also known as the MSIX image) is mounted.|
| Registration|Per user process that MSIX app attach uses to make the application available to the user.|
| Delayed registration|Process that delays complete registration of the application until the user decides to execute the application.|
| Deregistration|User signs out and the application is de-registered for that user. |
| Destage|VM shutdown or reboot, and the application is de-staged from the VM.|

After opening MSIX app attach, the user experiences the following:

1. From the Windows Virtual Desktop client, the user signs in and selects the host pool for which they have access. The process is similar to if the user opens published RemoteApps from the Windows Virtual Desktop environment.
2. The user is assigned a virtual machine within the host pool, on which a RemoteApp or Remote Desktop session is created with which the Windows Virtual Desktop client interacts.
3. If the user profiles are configured, the FSLogix agent on the session host provides the user profile from the file share, which can be Azure Files, Azure NetApp Files, or an IaaS file server.
4. Applications that are assigned to the user are read from Windows Virtual Desktop.
5. MSIX app attach applications are registered to the virtual machine for that user from the attached MSIX virtual disk. That virtual disk could be on an IaaS file share, Azure Files, or Azure NetApp Files.

:::image type="content" source="../media/03-How-MSIX-app-attach-works.PNG" alt-text="Diagram how MSIX app attach work." border="true":::

## MSIX terminology

As a review and reference, the following are key MSIX app attach terms.

|Term| Definition|
|----------------|------------------------------------------------------------|
| MSIX container|MSIX apps run in a lightweight container isolated from other apps.|
| MSIX application|An application that is packaged in MSIX format with an MSIX extension.|
| MSIX package|The package that contains the payload of the application with additional files.|
| MSIX image|An MSIX image is a VHD, VHDX, or CIM file that contains one or more MSIX packaged applications.|
| Repackage|The process to convert a non-MSIX application into MSIX using the MSIX Packaging tool. |
