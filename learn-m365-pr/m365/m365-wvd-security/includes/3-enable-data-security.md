A user profile is a collection of configurations that the user or administrator made, which represent the state of a system. Different system components bind to a user's profile. For example, applications, registry entries and others customized entries. Windows 10 offers several types of user profiles. The following table describes the four traditional types of Windows profiles.

| **Types of profiles** | **Description**                             |
| --------------------- | ---------------------------------- |
| Local user profile|A local user profile is  stored on the disk of the device. If a different device is used, the  customization isn't synchronized between devices.|
|Roaming user profile|A roaming user profile is a copy of the local user profile, stored on a shared folder. Any changes made locally to a roaming profile are synchronized to the file server’s Server Message Block (SMB) shared folder when the user signs out. If the user signs in to a different device, the customizations follow the user as the roaming profile is downloaded to the new system.  However, it's not possible to roam all settings for Windows and applications. A performance and maintenance penalty is paid for the  flexibility. The addition of FSLogix profile containers addressed the shortcomings of traditional roaming profiles. FSLogix profile containers are described in the following paragraph.|
|Mandatory profile| A mandatory profile is a roaming user profile that has been preconfigured by an administrator to specify settings for users. With mandatory user profiles, a user can modify their desktop, but the changes aren't saved when the user signs out. The next time the user signs in, the mandatory user profile created by the administrator is downloaded. Mandatory profiles are typically used in a kiosk environment.|
|Temporary profile|A fail-safe profile that is created when a user’s roaming profile has issues loading. It's discarded at sign-out.|

## FSLogix profile containers

In a Windows Virtual Desktop environment, Microsoft has made the FSLogix Profile Containers the default for storing the whole user profile. Profile containers aren't a traditional profile management solution but are a full remote profile solution for non-persistent environments. Profile containers redirect the entire user profile to a remote location. Profile container configuration defines how and where the profile is redirected. When used with Windows Virtual Desktop, the profile container can be stored in an Azure storage account.

When you sign in to Windows Virtual Desktop, a container (VHD) of a user profile, dynamically attaches to the VM a user is assigned. FSLogix is using an advanced filter-driver technology to allow the user profile to be immediately available and display in the system exactly like a local user profile.

FSLogix address key issues with non-persistent profiles. In summary, FSLogix enables local profiles to act like roaming profiles and offers the following key advantages:

- Performance Improvements. FSLogix profile containers offer high performance and address historic blocked cached exchange mode.

- Support for Microsoft OneDrive for Business, including Files on Demand. Previously, this support wasn't included in non-persistent virtualized environments.

- Additional folders. FSLogix provides for extending user profiles to provision enterprise-grade SMB volumes by using the Azure NetApp Files service. Azure NetApp Files supports SMB 2.1 and SMB 3.1.

## Secure your Windows Virtual Desktop data with Azure Disk Encryption

All Azure NetApp Files used by WIndows Virtual Desktop are encrypted using the Federal Information Processing Standards Publications (FIPS PUBS) 140-2 standard. The Azure NetApp Files service manages all keys and generates a unique XTS-AES-256 data encryption key for each volume. An encryption key hierarchy is used to encrypt and protect all volume keys. These encryption keys are never available or reported in an unencrypted format. The keys are also deleted immediately when a volume is deleted.

> [!NOTE] 
> Support for customer-managed keys (Bring Your Own Key) using Azure Dedicated HSM is available. Check for availability in your region.
