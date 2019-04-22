## Overcoming potential security-related deployment blockers
Before detailing the new capabilities available in Windows 10 and Office 365 ProPlus and connect those experiences to the cloud, we’ll start by covering a few trends that can often interrupt deployment progress.

## Disk encryption
One of the initial challenges during desktop deployment is hard disk encryption. Many hard disk encryption solutions cannot easily be upgraded from a previous version to a newer version of Windows.

Some disk encryption solutions allow you to perform the upgrades when using the ‘/reflectdrivers’ option with Windows Setup on certain platform versions, but others may require you to unencrypt the drive prior to deployment and then re-encrypt after Windows 10 is installed. Some solutions do not allow you to move from Master Boot Record (MBR), using legacy BIOS, to GUID Partition Table (GPT), required for UEFI. This is important because the 64-bit version of Windows 10 with UEFI is required for the new virtualization-based security capabilities in Windows 10.

One option for resolving these issues is using BitLocker in Windows 10, which is included in Windows 10 Pro and higher editions. BitLocker allows you to suspend protection for OS upgrades and feature updates as part of the process.


## Antivirus and antimalware application compatibility
More than [99% of Windows applications are compatible](https://www.microsoft.com/en-us/microsoft-365/blog/2018/09/06/helping-customers-shift-to-a-modern-desktop/) between Windows 7 and Windows 10. The exceptions are often anti-virus (AV) apps or Virtual Private Network (VPN) clients. These applications often implement non-standard development practices and APIs, using often undocumented techniques to protect systems or connect to network resources. As a result, these apps by nature can be susceptible to incompatibilities when shifting to a new version of Windows. If your AV or VPN software doesn’t work in Windows 10 or after upgrading, we recommend replacing the app you’re using with something supported and tested on Windows 10.

## Security policies
The Active Directory Group Policy settings used for older versions of Windows and Office may not translate directly to Windows 10 and Office 365 ProPlus, and there are different considerations with newer security and compliance capabilities. It’s a good idea to use the Microsoft Security Compliance Toolkit to get a baseline of the security policies for current versions of Windows and Office. it’s also worth looking into Mobile Device Management policies as part of Microsoft Intune.
