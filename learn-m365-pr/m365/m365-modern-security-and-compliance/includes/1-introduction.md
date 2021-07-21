> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3idqx]

Before detailing the new capabilities and connecting those experiences to the cloud, we'll cover a few security issues that can often interrupt the deployment progress.

**Disk encryption.** One of the initial challenges during desktop deployment is hard disk encryption. Many hard disk encryption solutions cannot easily be upgraded from a previous version to a newer version of Windows.

With some disk encryption solutions, let you can use the **/reflectdrivers** option with Windows Setup to upgrade certain platform versions; with others you have to unencrypt the drive before deployment and then re-encrypt after you install Windows 10. Some solutions don't let you move from a master boot record (MBR), using legacy BIOS, to a GUID partition table (GPT), required for UEFI. This is important because the 64-bit version of Windows 10 with UEFI is required for the new virtualization-based security capabilities in Windows 10.

One option for resolving these issues is using BitLocker, which is included in Windows 10 Pro and higher editions. With BitLocker, you can suspend protection for OS upgrades and feature updates as part of the process.

**Antivirus and antimalware application compatibility.** More than [99% of Windows applications are compatible](https://www.microsoft.com/microsoft-365/blog/2018/09/06/helping-customers-shift-to-a-modern-desktop/) between Windows 7 and Windows 10. The exceptions are often anti-virus (AV) apps or virtual private network (VPN) clients. These applications often use non-standard development practices and APIs, using undocumented techniques to protect systems or connect to network resources. As a result, these apps can be susceptible to incompatibilities when shifting to a new version of Windows. If your AV or VPN software doesn't work in Windows 10 after upgrading, we recommend replacing the app you're using with something supported and tested on Windows 10.

**Security policies.** The Active Directory Group Policy settings used for older versions of Windows and Office may not translate directly to newer versions, and there are different considerations with newer security and compliance capabilities. It's a good idea to use the **Microsoft Security Compliance Toolkit** to get a baseline of the security policies for current versions of Windows and Office. It's also worth looking into mobile device management (MDM) policies as part of Microsoft Intune.
