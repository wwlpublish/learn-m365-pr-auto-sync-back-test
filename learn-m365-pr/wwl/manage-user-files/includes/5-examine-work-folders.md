Work Folders is a role service for file servers running Windows Server. Work Folders is designed to help Windows users sync work files to a central file server. It provides a consistent way for users to access their work files from their PCs and devices. With Work Folders users can store and access work files on personal computers and devices, often referred to as bring-your-own device (BYOD), in addition to corporate PCs. Users gain a convenient location to store work files, and they can access them from anywhere. Organizations maintain control over corporate data by storing the files on centrally managed file servers, and optionally specifying user device policies such as encryption and lock-screen passwords.

Work Folders can be deployed with existing deployments of Folder Redirection, Offline Files, and home folders. Work Folders stores user files in a folder on the server called a *sync share*. You can specify a folder that already contains user data, which enables you to adopt Work Folders without migrating servers and data or immediately phasing out your existing solution.

### Components of Work Folders

If you want to use Work Folders, several components must be available in your environment:

 -  **A Work Folders server**. You need a file server that is running Windows Server 2016 or later. The file server must be a member of an Active Directory domain, and it must have the Work Folder role service installed, which is part of the File and Storage Services role. When you install the role service, this adds an additional access protocol and extends Server Manager. You can use Server Manager to create and manage sync shares, which contain users’ Work Folders. You also can use Server Manager to view who can access sync shares, when and from which devices users can access them, and to perform other tasks, such as setting quotas and managing volumes. Users can access and sync their Work Folders by using the HTTPS encapsulated access protocol. Synchronization uses https encryption, so the file server must have an installed Secure Sockets Layer (SSL) certificate, and the devices from which users access the Work Folders must trust that certificate.
 -  **A sync share**. A sync share is a unit of synchronization between the Work Folders server and client devices. You can create multiple sync shares on a Work Folders server, and each sync folder maps to the physical folder on the file server. Each user who uses Work Folders has a personal subfolder inside the sync share, and users can access and sync only the content of their subfolders. You can configure who can access a sync share, and then specify a device policy. For example, you can create a policy that requires the encryption of the local copy of Work Folders data on client devices. Although users can have permissions to access multiple sync shares, they can access a single sync share only. By default, you can access a sync share only by using the Work Folders feature, but an administrator also can create a Server Message Block (SMB) share that uses the same folder as a sync share. The SMB protocol is a network file sharing protocol that allows applications on a computer to read and write to files and to request services from server programs in a computer network. If users can access sync share content by using SMB access, they can view synced content from devices that do not use Work Folders. A file server stores the sync share, so you can use features such as dynamic access control, quotas, and file screening when managing the sync share’s content.
 -  **User devices**. These are the devices from which you can access, modify, and sync content that Work Folders are storing. You can access Work Folders from workgroup devices, devices that are workplace-joined, or domain-member devices. Windows client devices support Work Folders by default, and you can add Work Folders support to Android, iPad, and iPhone devices. Devices also must trust the SSL certificate that the Work Folders server is using. If you configure devices to use Work Folders, Windows detects the changes to the local copies of data, and then synchronizes them with the server. By default, devices check the Work Folders server every 10 minutes and sync changes with local copies of the Work Folders data.

### Practical applications

Administrators can use Work Folders to provide users with access to their work files while keeping centralized storage and control over the organization's data. Some specific applications for Work Folders include:

 -  Provide a single point of access to work files from a user's work and personal computers and devices
 -  Access work files while offline, and then sync with the central file server when the PC or device next has Internet or intranet connectivity
 -  Deploy with existing deployments of Folder Redirection, Offline Files, and home folders
 -  Use existing file server management technologies, such as file classification and folder quotas, to manage user data
 -  Specify security policies to instruct user's PCs and devices to encrypt Work Folders and use a lock screen password
 -  Use Failover Clustering with Work Folders to provide a high-availability solution

### Comparing solutions

The following table discusses how various Microsoft sync technologies are positioned and when to use each.

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    **Work Folders**
  :::column-end:::
  :::column:::
    **Offline Files**
  :::column-end:::
  :::column:::
    **OneDrive for Business**
  :::column-end:::
  :::column:::
    **OneDrive**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Technology summary**
  :::column-end:::
  :::column:::
    Syncs files that are stored on a file server with PCs and devices
  :::column-end:::
  :::column:::
    Syncs files that are stored on a file server with PCs that have access to the corporate network (can be replaced by Work Folders)
  :::column-end:::
  :::column:::
    Syncs files that are stored in Microsoft 365 or in SharePoint with PCs and devices inside or outside a corporate network, and provides document collaboration functionality
  :::column-end:::
  :::column:::
    Syncs personal files that are stored in OneDrive with PCs, Mac computers, and devices
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Intended to provide user access to work files**
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Cloud service**
  :::column-end:::
  :::column:::
    None
  :::column-end:::
  :::column:::
    None
  :::column-end:::
  :::column:::
    Microsoft 365
  :::column-end:::
  :::column:::
    Microsoft OneDrive
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Internal network servers**
  :::column-end:::
  :::column:::
    File servers running Windows Server 2012 R2 or later
  :::column-end:::
  :::column:::
    File servers
  :::column-end:::
  :::column:::
    SharePoint server (optional)
  :::column-end:::
  :::column:::
    None
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Supported clients**
  :::column-end:::
  :::column:::
    PCs, iOS, Android
  :::column-end:::
  :::column:::
    PCs in a corporate network or connected through DirectAccess, VPNs, or other remote access technologies
  :::column-end:::
  :::column:::
    PCs, iOS, Android
  :::column-end:::
  :::column:::
    PCs, Mac computers, iOS, Android
  :::column-end:::
:::row-end:::


### Deploying Work Folders

To deploy Work Folders, a process that can involve multiple servers and technologies, you must complete the following steps:

1.  **Obtain SSL certificates**. Work Folders uses HTTPS to securely synchronize files between the Work Folders clients and the Work Folders server. The SSL certificates used by Work Folders must be issued by a trusted certification authority. For most Work Folders implementations, a publicly trusted CA is recommended, since certificates will be used by non-domain-joined, Internet-based devices.
2.  **Create DNS records**. To allow users to sync across the Internet, you must create a Host (A) record in public DNS to allow Internet clients to resolve your Work Folders URL. This DNS record should resolve to the external interface of the reverse proxy server. On your internal network, create a CNAME record in DNS named *workfolders* which resolves to the FDQN of a Work Folders server. When Work Folders clients use auto discovery, the URL used to discover the Work Folders server is https://workfolders.domain.com. If you plan to use auto discovery, the *workfolders* CNAME record must exist in DNS. Install Work Folders on file servers.
3.  **Install Work Folders on file servers**. You can install Work Folders on a domain-joined server by using Server Manager or by using Windows PowerShell, locally or remotely across a network. This is useful if you are configuring multiple sync servers across your network.
4.  **Binding the SSL certificate on the sync servers**. Work Folders installs the IIS Hostable Web Core, which is an IIS component designed to enable web services without requiring a full installation of IIS. After installing the IIS Hostable Web Core, you should bind the SSL certificate for the server to the Default Web Site on the file server. However, the IIS Hostable Web Core does not install the IIS Management console. There are two options for binding the certificate to the Default Web Interface. To use either option you must have installed the private key for the certificate into the computer's personal store.
5.  **Create security groups for Work Folders**. Before creating sync shares, a member of the Domain Admins or Enterprise Admins groups needs to create some security groups in Active Directory Domain Services (AD DS) for Work Folders (they might also want to delegate some control as described in Step 6). Here are the groups you need:
    
     -  One group per sync share to specify which users are allowed to sync with the sync share.
     -  One group for all Work Folders administrators so that they can edit an attribute on each user object that links the user to the correct sync server (if you're going to use multiple sync servers).
6.  **Optionally delegate user attribute control to Work Folders administrators**. If you are deploying multiple sync servers and want to automatically direct users to the correct sync server, you'll need to update an attribute on each user account in AD DS. However, this normally requires getting a member of the Domain Admins or Enterprise Admins groups to update the attributes, which can quickly become tiresome if you need to frequently add users or move them between sync servers. For this reason, a member of the Domain Admins or Enterprise Admins groups might want to delegate the ability to modify the msDS-SyncServerURL property of user objects to the Work Folders Administrators group you created in Step 5.
7.  **Create sync shares for user data**. At this point, you're ready to designate a folder on the sync server to store your user's files. This folder is called a sync share. Sync shares can be created using Server Manager or by using the **New-SyncShare** cmdlet in Windows PowerShell.
