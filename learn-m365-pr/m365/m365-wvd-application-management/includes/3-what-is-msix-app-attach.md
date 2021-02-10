You've learned about MSIX packages. Now let's consider how you can deploy those applications into your Windows Virtual Desktop environment and determine if MSIX app attach is right for Contoso.

## Purpose and benefits of MSIX app attach

MSIX app attach is a Microsoft application-delivery approach that's designed for a modern workspace. With MSIX app attach, you can use one application format (MSIX) to deliver applications to both physical and virtual machines. Although you can use MSIX app attach on-premises or in Azure, this technology is specially adopted for Windows Virtual Desktop.

MSIX app attach offers the following benefits:

- You can use existing MSIX packages without repacking or altering the structure.
- You don't need additional infrastructure servers to deploy the MSIX packages. You can use Azure Files to host the virtual hard disk (VHD) that contains an MSIX package.
- MSIX app attach separates application files from the operating system. If the device needs a reset or reimage, these applications won't require a reinstallation.
- You can edit and update the applications. After that, all the changes will be saved as a new package that can replace the old MSIX app attach package.
- You can combine MSIX app attach with FSLogix profile containers to isolate user profiles on a separate VHD or VHDX.

Contoso is a good candidate for using MSIX app attach for its application delivery needs because the company uses Windows Virtual Desktop and Azure for file management.

## How MSIX app attach works

MSIX app attach stores application files in a separate virtual hard disk from the operating system. It registers the regular MSIX package on a device instead of on a physical download and installation. The registration uses existing Windows APIs and has minimal impact on user sign-in times, which enhances the user experience.

When you open MSIX app attach, the application files are accessed from a VHD. You're not even aware that the application isn't locally installed.

MSIX app attach follows several steps or actions:

|Term| Definition|
|----------------|------------------------------------------------------------|
| Stage|MSIX app attach notifies the operating system that an application is available, and that the virtual disk that contains the MSIX package (also known as the MSIX image) is mounted.|
| Registration|MSIX app attach uses a per-user process to make the application available to you.|
| Delayed registration|Complete registration of the application is delayed until you decide to run the application.|
| Deregistration|The application is no longer available to you after you sign out. |
| Destage|The application is no longer available from the virtual machine after shutdown or restart of the machine.|

After you open MSIX app attach, you experience the following process:

1. From the Windows Virtual Desktop client, you sign in and select the host pool for which you have access. The process is similar to opening published RemoteApp programs from the Windows Virtual Desktop environment.
2. You're assigned a virtual machine within the host pool, on which a RemoteApp or Remote Desktop session is created. The Windows Virtual Desktop client interacts with that session.
3. If the user profile is configured, the FSLogix agent on the session host provides the user profile from the file share. The file share can be Azure Files, Azure NetApp Files, or an infrastructure as a service (IaaS) file server.
4. Applications that are assigned to you are read from Windows Virtual Desktop.
5. MSIX app attach applications are registered to the virtual machine for you, from the attached MSIX virtual disk. That virtual disk might be on an IaaS file share, Azure Files, or Azure NetApp Files.

:::image type="content" source="../media/03-how-msix-app-attach-work.png" alt-text="Diagram of how M S I X app attach works." border="true":::

## MSIX terminology

Use the following key terms for MSIX app attach as a review and reference.

|Term| Definition|
|----------------|------------------------------------------------------------|
| MSIX container|The place where MSIX apps run. The container is lightweight and isolated from other apps.|
| MSIX application|An application that's packaged in MSIX format with an MSIX extension.|
| MSIX package|The package that contains the payload of the application with additional files.|
| MSIX image|A VHD, VHDX, or Composite Image (CIM) file that contains one or more MSIX packaged applications.|
| Repackage|The process to convert a non-MSIX application into MSIX by using the MSIX Packaging tool. |
