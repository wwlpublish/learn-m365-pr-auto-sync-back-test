When a BitLocker-enabled computer starts, BitLocker checks the operating system for conditions that might indicate a security risk. If BitLocker detects such a condition, it does not unlock the system drive and instead enters recovery mode. When a computer enters recovery mode, the user must enter the correct recovery password to continue. The recovery password is linked to a particular TPM or computer and not to an individual user. The recovery password typically does not change.

You should save the recovery information either on a USB flash drive or in AD DS, using one of these formats:

 -  A 48-digit number divided into eight groups. During recovery, use the function keys to type this password into the BitLocker Recovery Console.
 -  A recovery key in a format that the BitLocker Recovery Console can read directly.

### Scenarios where recovery is likely

There are a number of situations where BitLocker recovery might become necessary, including:

 -  Switching the computer's encrypted hard drive to another computer.
 -  Making the BitLocker-encrypted drive subordinate to another computer to recover its data.
 -  Turning the computer off during the encryption process.
 -  Updating the computer’s firmware.
 -  Changing the device boot order in the computer’s BIOS.

### Locating a BitLocker recovery password

The BitLocker recovery password is a 48-digit password that unlocks a system in recovery mode. The recovery password is unique to a particular BitLocker encryption, and you can store it in AD DS. The recovery password will be required if you move the encrypted drive to another computer, or if changes are made to the system startup information.

> [!NOTE]
> This password is very important. We recommend that you make additional copies of the password, and then store them in safe places to ensure access to your data. Microsoft does not have any access or work-around for a lost key.

If BitLocker enters a locked state, you will need the recovery password to unlock the encrypted data on the volume. A recovery password is unique to a particular BitLocker encryption, and you cannot use it to recover encrypted data from any other BitLocker encryption session.

A computer's password ID is a 32-character password unique to a computer name. You can find the password ID under a computer's property settings, which you can use to locate passwords stored in AD DS. To locate a password, the following conditions must be met:

 -  You must be a domain administrator or have delegate permissions.
 -  The client's BitLocker recovery information is configured for storage in AD DS.
 -  The client’s computer has been joined to a domain.
 -  BitLocker must be enabled on the client's computer.

Prior to searching for and providing a BitLocker recovery password to a user, confirm that the person is the account owner and is authorized to access data on the computer in question.

You search for the password in Active Directory Users and Computers by using one of the following:

 -  Drive label
 -  Password ID

When you search by drive label, after locating the computer, right-click the **drive label**, select **Properties**, and then select the **BitLocker Recovery** tab to view associated passwords.

To search by password ID, right-click the **domain container**, and then select **Find BitLocker Recovery Password**. In the Find BitLocker Recovery Password dialog box, enter the first eight characters of the password ID in the **Password ID** field, and then select **Search**.

Examine the returned recovery password to ensure that it matches the password ID that the user provides. Performing this step helps to verify that you have obtained the correct unique recovery password.

### Data recovery agent support

BitLocker for Windows provides data recovery agent support for all protected volumes. This provides users with the ability to recover data from any BitLocker and BitLocker To Go device when data is inaccessible. This technology assists in the recovery of corporate data on a portable drive using the key created by the enterprise.

Data recovery agent support allows you to dictate that all BitLocker-protected volumes (such as operating system, fixed, and new portable volumes), are encrypted with an appropriate data recovery agent. The data recovery agent is a new key protector that is written to each data volume so that authorized IT administrators will always have access to BitLocker-protected volumes.
