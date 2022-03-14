BitLocker uses a Trusted Platform Module (TPM) chip to verify the integrity of the startup process by:

 -  Providing a method to verify that early boot file integrity has been maintained, and to help ensure that there has been no adverse modification of those files, such as with boot sector viruses or root kits.
 -  Enhancing protection to mitigate offline software-based attacks. Any alternative software that might start the system does not have access to the decryption keys for the Windows operating system volume.
 -  Locking the system when it is tampered with. If anyone has tampered with monitored files, the system does not start. This alerts the user to the tampering because the system fails to start as usual. In the event that system lockout occurs, BitLocker offers a simple recovery process.

In conjunction with the TPM, BitLocker verifies the integrity of early startup components. This helps prevent additional offline attacks, such as attempts to insert malicious code into these components. This functionality is important because the components in the earliest part of the startup process must be available in an unencrypted format so that the computer can start.

> [!NOTE]
> You may need to enable the TPM functionality in your computer’s BIOS.

If an attacker can gain access to the startup process components, they can change the code in these components and gain access to the computer even though the data on the disk is encrypted. Once the attacker gains access to confidential information such as BitLocker keys or user passwords, they can circumvent BitLocker and other Windows security protections.

BitLocker does not require a TPM. However, only a computer with a TPM can provide the additional security of prestartup system-integrity verification. To determine if a computer has a TPM version 1.2 chip, perform the following steps:

1.  Open **Control Panel**, select **System and Security**, and then select **BitLocker Drive Encryption**.
2.  In the lower left corner, select **TPM Administration**. The TPM Management on the **Local Computer** console opens. If the computer does not have the TPM 1.2 chip, the “Compatible TPM cannot be found” message displays.

> [!NOTE]
> On computers that do not have TPM 1.2, you can still use BitLocker to encrypt the Windows operating system volume. However, this implementation does not include a TPM, and requires the user to insert a USB startup key to start the computer or resume from hibernation. It also does not provide the prestartup system integrity verification that BitLocker provides when working with a TPM.
