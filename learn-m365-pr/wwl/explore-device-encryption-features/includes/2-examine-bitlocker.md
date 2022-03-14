BitLocker provides additional protection for a computer’s operating system and any data that is stored on that operating system or in other volumes. BitLocker helps ensure that data stored on a computer remains encrypted, even if someone tampers with the computer while the operating system is not running.

BitLocker provides a closely integrated solution in Windows to help address the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers. Data on these types of computers can become vulnerable to unauthorized access when a hacker either runs a software attack tool against it or transfers the computer’s hard disk to a different computer.

BitLocker helps mitigate unauthorized data access by enhancing Windows file and system protections. BitLocker also helps render data inaccessible when you decommission or recycle BitLocker-protected computers.

BitLocker performs two functions that provide both offline data protection and system-integrity verification:

 -  It encrypts all data that is stored on the Windows operating system volume (and configured data volumes). This includes the Windows operating system, hibernation files and paging files, applications, and data that applications use. BitLocker also provides an umbrella protection for non-Microsoft applications, which benefits the applications automatically when they are installed on the encrypted volume.
 -  It is configured, by default, to use a Trusted Platform Module (TPM) chip to help ensure the integrity of early startup components by ensuring that no modifications have been made to the trusted boot path, such as BIOS, boot sector, and boot manager. Once the TPM has verified that there are no changes, it releases the decryption key to the Windows OS Loader. If TPM does detect changes, it locks any BitLocker-protected volumes, so they remain protected even if someone tampers with the computer when the operating system is not running.

> [!NOTE]
> The Windows installation process partitions the computer’s hard disk to enable the use of BitLocker.

:::image type="content" source="../media/bitlocker-configuration-1b2ec57f.jpg" alt-text="BitLocker Drive Encryption Screen in Control Panel":::


Windows now offers a newer encryption algorithm, XTS-AES, for BitLocker. BitLocker organizations concerned with brute-force attacks of their devices given physical access may want to consider migrating their BitLocker default encryption to XTS-AES. This option can be configured using Group Policy. Microsoft recommends that customers enable this level of encryption on newly provisioned devices.
