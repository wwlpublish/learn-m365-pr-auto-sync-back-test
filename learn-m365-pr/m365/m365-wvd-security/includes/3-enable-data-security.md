A user profile is a collection of configurations that the user or administrator made, which represent the state of a system. Different system components such as applications, registry entries, data, and file system layout bind to a user's profile. Windows 10 offers several types of user profiles. The following table describes the four traditional types of Windows profiles.

| **Types of profiles** | **Description**                             |
| --------------------- | ---------------------------------- |
| Local user profile|A local user profile is  stored on the disk of the device. If the user uses a different device, the  customization is not synchronized between devices.|
|Roaming user profile|A roaming user profile is a copy of the local user profile, stored on a shared folder. Any changes made locally to a roaming profile are synchronized to the file server’s Server Message Block (SMB) shared folder when the user signs out. If the user signs in to a different device, the customizations follow the user as the roaming profile is downloaded to the new system.  However, it's not possible to roam all settings for Windows and applications. There is also a performance and maintenance penalty for this flexibility. With the addition of FSLogix profile containers, the short coming of tradional roaming profiles are addressed. FSLogix profile containers are described below.|
|Mandatory profile| A mandatory profile is a roaming user profile that has been preconfigured by an administrator to specify settings for users. Settings commonly defined in a mandatory profile include but are not limited to icons that appear on the desktop, desktop backgrounds, user preferences in Control Panel, and printer selections. With mandatory  user profiles, a user can modify their desktop, but the changes are not saved when the user signs out. The next time the user signs in, the mandatory user profile created by the administrator is downloaded. Mandatory profiles are typically used in a kiosk environment.|
|Temporary profile|This is a fail-safe profile that is created when a user’s roaming profile has issues loading. It's discarded at sign-out.|

## FSLogix profile containers

In a Windows Virtual Desktop environment, Microsoft has make the FSLogix Profile Containers the default for storing the whole user profile. Profile containers are not a traditional profile management solution but are a full remote profile solution for non-persistent environments. Profile containers redirect the entire user profile to a remote location. Profile container configuration defines how and where the profile is redirected. When used with Windows Virtual Desktop, the profile container can be stored in an Azure storage account.

When you sign in to Windows Virtual Desktop, the container (VHD) of a user profile dynamically attaches to the VM a user is assigned. FSLogix is using an advanced filter-driver technology to allow the user profile to be immediately available and display in the system exactly like a local user profile.

FSLogix address key issues with non-persistent profiles. In summary, FSLogix enables local profiles to act like roaming profiles and offers the following key advantages:

- Performance Improvements. FSLogix profile containers offer high performance and address historic blocked cached exchange mode.

- Support for Microsoft OneDrive for Business including Files on Demand. Previously, this support was not included in non-persistent virtualized environments.

- Additional folders. FSLogix provides the ability to extend user profiles to provision enterprise-grade SMB volumes by using the Azure NetApp Files service. Azure NetApp Files supports SMB 2.1 and SMB 3.1.

## Secure your Windows Virtual Desktop data with Azure Disk Encryption

As previously mentioned, Azure NetApp Files is an Azure native service that is deployed into the Azure Virtual Network where the service is available and used by Windows Virtual Desktop. All Azure NetApp Files volumes are encrypted using the Federal Information Processing Standards Publications (FIPS PUBS) 140-2 standard. The Azure NetApp Files service manages all keys and generates a unique XTS-AES-256 data encryption key for each volume. An encryption key hierarchy is used to encrypt and protect all volume keys. These encryption keys are never available or reported in an unencrypted format and are deleted immediately when a volume is deleted.

> [!NOTE] 
> Support for customer-managed keys (Bring Your Own Key) using Azure Dedicated HSM is available. Check for availability in your region.
