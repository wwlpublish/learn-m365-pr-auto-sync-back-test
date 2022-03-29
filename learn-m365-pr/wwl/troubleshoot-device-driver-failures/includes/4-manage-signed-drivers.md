Device drivers run with system-level privileges and can access files or information on a computer. Therefore, it's critical to trust installed device drivers. Trust, in this context, includes two main principles:

 -  **Authenticity**. This is a guarantee that the package came from its claimed source.
 -  **Integrity**. This is an assurance that the package is intact, and there have been no modifications since its release.

:::image type="content" source="../media/signed-drivers-891eb0a5.jpg" alt-text="Screenshot showing signed drivers.":::


A digital signature uses a digital certificate to encrypt specific details about the device driver package. The encrypted information in a digital signature includes a thumbprint for each file that the package includes. A special cryptographic algorithm, or hashing algorithm, generates the thumbprint. The algorithm generates a code that only the file’s contents can create, and changes to a single bit in the file cause the thumbprint to change. After the file generates the thumbprints, the publisher combines them into a catalog, and encrypts them. A digital signature doesn't modify the device driver. It only assures that the device driver wasn't modified after it was signed.

Microsoft digitally signs all device drivers that are included in Windows. Windows checks for a driver’s digital signature during installation, and prompts the user if device driver isn't signed. 64-bit editions of Windows require that all drivers are signed digitally, and by default, you can't use device drivers with 64-bit editions of Windows if they're unsigned.

> [!NOTE]
> You can configure 64-bit editions of Windows to use unsigned device drivers, such as if you want to test the driver before signing it, but we don't recommend this. To disable the enforcement of driver signatures, you should restart the computer, and then select **Disable** driver signature enforcement on the **Startup Settings** menu.

You can use Device Manager to verify if a device driver is signed digitally, but you need to do it for each device driver separately. In Device Manager, you right-click a device, select Properties, and then on the Driver tab, select the Driver Details button. You can verify if a device driver was signed and by whom in the Driver File Details dialog box.

### The Signature Verification tool

You can use the Signature Verification tool (Sigverif.exe) to scan and determine if Windows is using unsigned drivers if the signature enforcement is disabled. Sigverif.exe writes the scan’s results to a log file that includes the system file, the signature file, and the signature file’s publisher. The log file shows any unsigned device drivers, and you then can replace the unsigned drivers with signed drivers.

To remove an unsigned device driver, follow these steps:

1.  Run **Sigverif.exe** to scan for unsigned drivers.
2.  Review the resulting log file.
3.  Create a temporary folder for the unsigned driver storage.
4.  Manually move any unsigned drivers from **C:\\WIndows\\System32\\Drivers** into the temporary folder.
5.  Disable or uninstall the associated hardware devices.
6.  Restart the computer.

You should try to obtain a signed device driver from the hardware vendor, or replace the device with a device that that uses a digitally signed device driver.

At a command prompt, you can run the **driverquery** command with the **/si** switch to obtain a basic list of signed and unsigned device drivers.

> [!NOTE]
> Some hardware vendors use their own digital signatures so that drivers can have a valid digital signature, even if Microsoft hasn't tested them. The Sigverif report lists the vendors for each signed driver. This can help you identify problem drivers issued by vendor.

### Configure the Certificate Store to support an unknown certification authority

On each computer, Windows maintains a store for trusted certification authorities. If an unknown certification authority has signed a driver package, 32-bit editions of Windows require confirmation that the publisher is trusted. However, Windows 64-bit editions do not install device drivers signed by untrusted certification authority. When you place a certification authority certificate in the certificate store, you inform Windows that the driver packages signed by the certification authority are trusted. Group Policy is the most common way to deploy certificates to client computers.

> [!NOTE]
> It is unusual to install a certificate into the Trusted Root Certification Authority store simply to support driver signing.
