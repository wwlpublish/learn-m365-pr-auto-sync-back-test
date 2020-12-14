A user profile is a collection of configurations that the user or administrator made, which represent the state of a system. Different system components such as applications, registry entries, data, and file system layout bind to a user's profile. Windows 10 offers several types of user profiles. The following table describes the four traditional types of Windows profiles.

| **Types of profiles** | **Description**                             |
| --------------------- | ---------------------------------- |
| Local user profile|A local user profile is  stored on the disk of the device. If the user uses a different device, the  customization is not synchronized between devices.|
|Roaming user profile|A roaming user profile is a copy of the local user profile, stored on a shared folder. Any changes made locally to a roaming profile are synchronized  to the file server’s Server Message Block (SMB) shared folder when the user  signs out. If the user signs in to a different device, the customizations  follow the user as the roaming profile is downloaded to the new system.  However, it's not possible to roam all settings for Windows and  applications. There is also a performance and maintenance penalty for this  flexibility.|
|Mandatory profile| A mandatory profile is a  roaming user profile that has been preconfigured by an administrator to specify settings for users. Settings commonly defined in a mandatory profile include  but are not limited to icons that appear on the desktop, desktop backgrounds,  user preferences in Control Panel, and printer selections. With mandatory  user profiles, a user can modify their desktop, but the changes are not saved  when the user signs out. The next time the user signs in, the mandatory user  profile created by the administrator is downloaded. Mandatory profiles are typically  used in a kiosk environment.|
|Temporary profile|This is a fail-safe profile that is created when a user’s roaming  profile has issues loading. It's discarded at sign-out.|

## FSLogix profile containers

In a WVD environment, Microsoft recommends the use of FSLogix profile containers. Profile containers are not a traditional profile management solution but are a full remote profile solution for non-persistent environments. Profile containers redirect the entire user profile to a remote location. Profile container configuration defines how and where the profile is redirected. When used with WVD, the profile container is stored in an Azure storage account.

When you sign in to WVD, the container of a user profile dynamically attaches to the computing environment by using a locally supported virtual hard disk (VHD) and a Hyper-V VHD. These advanced filter-driver technologies allow the user profile to be immediately available and display in the system exactly like a local user profile.

FSLogix address key issues with non-persistent profiles. In summary, FSLogix enables local profiles to act like roaming profiles and offers the following key advantages:

- Performance Improvements. FSLogix profile containers offer high performance and address historic blocked cached exchange mode.

- Support for Microsoft OneDrive for Business. Previously, this support was not included in non-persistent VDI environments.

- Additional folders. FSLogix provides the ability to extend user profiles to provision enterprise-grade SMB volumes by using the Azure NetApp Files service. Azure NetApp Files supports SMB 2.1 and SMB 3.1.

## Secure your WVD data with Azure Disk Encryption

As previously mentioned, Azure NetApp Files is an Azure native service that is deployed into the Azure Virtual Network where the service is available and used by WVD. All Azure NetApp Files volumes are encrypted using the Federal Information Processing Standards Publications (FIPS PUBS)140-2 standard. The Azure NetApp Files service manages all keys and generates a unique XTS-AES-256 data encryption key for each volume. An encryption key hierarchy is used to encrypt and protect all volume keys. These encryption keys are never available or reported in an unencrypted format and are deleted immediately when a volume is deleted.

Support for customer-managed keys (Bring Your Own Key) using Azure Dedicated HSM is available. Check for availability in your region.

## Enable more secure data access when using Azure Files

You can use the Azure Private Link service to improve data access security. An Azure private endpoint is the bases  for Private Link. It enables Azure resources to privately communicate with Private Link resources. In WVD environment, it enhances secure access. Traffic between your virtual network and the service travels the Microsoft high speed backbone network. It's no longer necessary to expose your service to the public internet. You can create your own private link service in your virtual network and deliver it to your organization.

Azure private endpoints help to secure your Azure resources by removing the need for a public endpoint for Azure Files and by preventing data exfiltration from your network boundary.

Azure Private link provides the following benefits:

- Protection against data leakage. A private endpoint is mapped to an single instance of a resource instead of the entire service. Consumers can only connect to the specific resource, thereby preventing data leakage.
- Restricted access to Azure services. Connections from your virtual network to services in Azure without the use of a public IP address at the source or destination. The Private Link platform will manage the connectivity between the consumer and services over the Azure backbone network.
- Access to on-premises or peered networks. You can access services running in Azure from an on-premises location over ExpressRoute private peering, VPN tunnels, and peered virtual networks using private endpoints. There is no need to traverse the internet to reach the service.
- Global access. Connectivity is private to services running in other regions.
