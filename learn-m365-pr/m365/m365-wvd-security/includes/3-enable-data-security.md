A user profile is a collection of configurations that the user or administrator made to represent the state of a system. Various system components bind to a user's profile. These components include applications, registry entries, and other customized entries. 

Windows 10 offers several types of user profiles. The following table describes the four traditional types of Windows profiles.

| **Profile type** | **Description**                             |
| --------------------- | ---------------------------------- |
| Local user profile|A local user profile is stored on the disk of the device. If a different device is used, the customization isn't synchronized between devices.|
|Roaming user profile|A roaming user profile is a copy of the local user profile, stored on a shared folder. Any changes made locally to a roaming profile are synchronized to the file server's Server Message Block (SMB) shared folder when the user signs out. If the user signs in to a different device, the customizations follow the user as the roaming profile is downloaded to the new system. <br><br>However, it's not possible to roam all settings for Windows and applications. A performance and maintenance penalty is paid for the  flexibility. The addition of FSLogix profile containers addressed the shortcomings of traditional roaming profiles. The next section describes FSLogix profile containers.|
|Mandatory profile| A mandatory profile is a roaming user profile that an administrator has preconfigured to specify settings for users. With mandatory user profiles, a user can modify their desktop, but the changes aren't saved when the user signs out. The next time the user signs in, the mandatory user profile that the administrator created is downloaded. Mandatory profiles are typically used in a kiosk environment.|
|Temporary profile|A fail-safe profile is created when a user's roaming profile has problems loading. It's discarded at sign-out.|

## FSLogix profile containers

In an Azure Virtual Desktop environment, we recommend FSLogix profile containers for storing the whole user profile. Profile containers aren't a traditional profile management solution but are a full remote profile solution for non-persistent environments.

Profile containers redirect the entire user profile to a remote location. Profile container configuration defines how and where the profile is redirected. When a profile container is used with Azure Virtual Desktop, it can be stored in an Azure storage account.

When you sign in to Azure Virtual Desktop, a container (virtual hard disk) of a user profile dynamically attaches to the VM to which a user is assigned. FSLogix uses an advanced filter-driver technology to allow the user profile to be immediately available in the system, exactly like a local user profile.

FSLogix addresses key issues with non-persistent profiles. In summary, FSLogix enables local profiles to act like roaming profiles and offers the following key advantages:

- Performance improvements. FSLogix profile containers offer high performance and address historic blocked Cached Exchange Mode.

- Support for Microsoft OneDrive for Business, including Files on Demand. Previously, this support wasn't included in non-persistent virtualized environments.

- SMB folders. FSLogix provides for extending user profiles to provision enterprise-grade SMB volumes by using the Azure NetApp Files service. Azure NetApp Files supports SMB 2.1 and SMB 3.1.

### FSLogix profile containers with Azure Files

Azure Files supports SMB identity-based authentication by using on-premises Active Directory Domain Services (AD DS) with Azure Active Directory Domain Services (Azure AD DS). Azure Files applies Kerberos protocols for authenticating with either on-premises AD DS or Azure AD DS. Enabling identity-based access for your Azure file shares allows you to replace existing on-premises file servers with Azure file shares while maintaining your existing directory service.

The file shares are hosted in an Azure virtual machine that resides on the virtual network of your Azure Virtual Desktop host pool. The virtual machine that is the file share is joined to the domain of Active Directory on the virtual network. After the virtual machine is domain joined, it can act as an FSLogix profile container share for a host pool. 

We strongly recommend using Azure Files instead of file shares.

### Secure your Azure Virtual Desktop data by using Azure Disk Encryption

All files that Azure Virtual Desktop uses in Azure NetApp Files are encrypted through the Federal Information Processing Standards Publications (FIPS PUBS) 140-2 standard. The Azure NetApp Files service manages all keys and generates a unique XTS-AES-256 data encryption key for each volume. 

Azure Virtual Desktop uses an encryption key to encrypt and protect all volume keys. These encryption keys are never available or reported in an unencrypted format. The keys are also deleted immediately when a volume is deleted.

> [!NOTE]
> Support for customer-managed keys (bring your own key) through Azure Dedicated HSM is available. Check for availability in your region.
