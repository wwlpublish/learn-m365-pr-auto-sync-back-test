Encrypting Files System (EFS) is another encryption feature in Windows. Unlike BitLocker, which encrypts the entire volume, EFS encrypts individual files based on user accounts.

BitLocker is a newer feature of Windows and generally recommended for encryption as it’s easier to implement and manage. However, there are some advantages that EFS provides that BitLocker does not. IT professionals who want to implement EFS should research it thoroughly before using it. You need to have a comprehensive understanding of EFS to implement a secure and recoverable EFS policy. A lack of understanding (by either an administrator or an end user) or an improper implementation can expose your data unnecessarily or leave it in a state from which you cannot recover it. This lesson provides a brief overview of EFS.

### What is EFS?

EFS is a built-in file encryption tool for Windows-based systems. EFS is a component of the NTFS file system, and it uses advanced, standard cryptographic algorithms to allow transparent file encryption and decryption. Through the Windows Information Protection functionality of Windows, EFS functionality is also simulated on volumes that use the FAT32 file system. Any individual or app that does not have access to a certificate store that holds an appropriate cryptographic key cannot read encrypted data. You can protect encrypted files even from those who gain physical possession of a computer on which files are stored. Even people who have the authorization to access a computer and its file system cannot view the encrypted data.

:::image type="content" source="../media/encrypting-files-system-dialog-43069b9c.jpg" alt-text="EFS Dialog Box":::


#### Common Scenarios for EFS

Utilizing EFS does provide advantages for protecting data from unauthorized access.

 -  **Protecting files on shared computers.** EFS allows users of shared computers to secure files so that other users of those computers cannot access them. While files access can be defined using NTFS permissions, you can use EFS with file and folder permissions as part of a defense-in-depth strategy.
 -  **Protecting files from privileged users.** EFS allows you to prevent privileged users from accessing certain files. Many data breaches are caused by attackers getting access to a privileged account and using that privileged account to override file and folder permissions. While the default Administrator account is also the data recovery agent for EFS-protected files, this can be changed so that privileged accounts cannot access these files.
 -  **Sharing encrypted files with specific users.** With BitLocker, files do not remain encrypted if they are moved or copied to another system that does not also provide encryption. With EFS, users can share encrypted files with other users on file shares and in web folders. This allows you to grant individual users’ permissions to access an encrypted file. After you encrypt a file, you can enable file sharing through the user interface. You first must encrypt a file and then save it before adding more users. You can add users from a local computer or from Active Directory Domain Services (AD DS) if the users have a valid certificate for EFS. EFS certificates can be located in roaming profiles, in the user profiles on the computer that is storing the file, or in AD DS. Caution users to share files only with trusted accounts, as any user who is authorized to decrypt a file can authorize other users to access the file. It is not restricted to the file owner. Removing the Write permission from a user or group of users can prevent this problem, but it also prevents the user or group from modifying the file. EFS-encrypted files do not remain encrypted when crossing the network, such as when you work with the files on a shared folder. The file is decrypted, and it then traverses the network in an unencrypted state. EFS encrypts it locally if you save it to a folder on the local drive that is configured for encryption. Solutions like WebDAV or IPSec can be leveraged to keep files encrypted while traversing the network.

### Comparing BitLocker and EFS

The following table compares BitLocker and EFS-encryption functionality.

:::row:::
  :::column:::
    **BitLocker functionality**
  :::column-end:::
  :::column:::
    **EFS functionality**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Encrypts volumes (the entire operating-system volume, including Windows system files, and the hibernation file).
  :::column-end:::
  :::column:::
    Encrypts files.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Does not require user certificates.
  :::column-end:::
  :::column:::
    Requires user certificates.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Does not protect against unauthorized privileged accounts.
  :::column-end:::
  :::column:::
    Helps protect against unauthorized privileged accounts.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Protects the operating system from modification (on devices with a TPM).
  :::column-end:::
  :::column:::
    Does not protect the operating system from modification.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Easier to implement.
  :::column-end:::
  :::column:::
    More complex to implement.
  :::column-end:::
:::row-end:::


Organizations can choose to use EFS or BitLocker separately, or together as part of a defense-in-depth strategy. Administrators should consider carefully the benefits and risks of implementing EFS. While EFS can solve certain scenarios, there is also greater potential for loss of data or unauthorized access if it is not implemented and used correctly.
