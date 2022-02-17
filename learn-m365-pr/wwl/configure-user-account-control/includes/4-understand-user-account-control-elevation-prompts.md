Many applications require users to be administrators, by default, because they check Administrators group membership before running an application.

### Standard user account permission tasks

The following list details some of the tasks that a standard user can perform:

 -  Establish a local area network (LAN) connection.
 -  Establish and configure a wireless connection.
 -  Modify display settings.
 -  Users cannot defragment the hard drive, but a service does this on their behalf.
 -  Play CD/DVD media (configurable with Group Policy).
 -  Burn CD/DVD media (configurable with Group Policy).
 -  Change the desktop background for the current user.
 -  Open Date and Time in Control Panel, and change the time zone.
 -  Use Remote Desktop to connect to another computer.
 -  Change a user’s own account password.
 -  Configure battery power options.
 -  Configure accessibility options.
 -  Restore a user’s backup files.
 -  Set up computer synchronization with a mobile device, including a smartphone, laptop, or personal digital assistant (PDA).
 -  Connect and configure a Bluetooth device.

### Administrator account permission tasks

The following list details some of the tasks that require elevation to an administrator account:

 -  Install and uninstall applications.
 -  Install a driver for a device, such as a digital camera driver.
 -  Install Windows updates.
 -  Configure Parental Controls.
 -  Install an ActiveX control.
 -  Open Windows Defender Firewall in Control Panel.
 -  Change a user’s account type.
 -  Modify UAC settings in the Security Policy Editor snap-in (Secpol.msc) to the Microsoft Management Console (MMC).
 -  Configure Remote Desktop access.
 -  Add or remove a user account.
 -  Copy or move files into the Program Files or Windows directory.
 -  Schedule Automated Tasks.
 -  Restore system backup files.
 -  Configure Automatic Updates.
 -  Browse to another user’s directory.

When you enable UAC, members of the local Administrators group run with the same access token as standard users. A process can use an administrator’s full access token only when a member of the local Administrators group gives approval.

This process is the basis of the Admin Approval Mode principle. Users elevate only to perform tasks that require an administrator access token. When a standard user attempts to perform an administrative task, UAC prompts the user to enter valid credentials for an administrator account. This is the default for standard user-prompt behavior.

The elevation prompt displays contextual information about the executable that is requesting elevation. The context is different, depending on whether the application is signed by Authenticode technology. The elevation prompt has two variations that the following table describes: the consent prompt and the credential prompt.

:::row:::
  :::column:::
    **Elevation prompt**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Consent prompt**
  :::column-end:::
  :::column:::
    Displayed to administrators in Admin Approval Mode when they attempt to perform an administrative task. It requests approval to continue from the user.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Credential prompt**
  :::column-end:::
  :::column:::
    Displayed to standard users when they attempt to perform an administrative task.
  :::column-end:::
:::row-end:::


Elevation entry points do not remember that elevation has occurred, such as when you return from a shielded location or task. As a result, the user must reelevate to enter the task again.

The Windows client operating system reduces the number of UAC elevation prompts for a standard user who performs everyday tasks. However, there are times when it is appropriate for an elevation prompt to be returned. For example, viewing firewall settings does not require elevation. However, changing the settings does require elevation because the changes have a system-wide impact.

### Types of elevation prompts

When a permission or password is necessary to complete a task, UAC will notify you with one of three different types of dialog boxes. The following table describes the different types of dialog boxes that users will see, and provides guidance on how to respond to them.

:::row:::
  :::column:::
    **Type of elevation prompt**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A setting or feature that is part of Windows needs your permission to start.
  :::column-end:::
  :::column:::
    This item has a valid digital signature that verifies that Microsoft is the publisher of this item. If this type of dialog box displays, it usually is safe to continue. If you are unsure, check the name of the program or function to decide if it is something that you want to run.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A program that is not part of Windows needs your permission to start.
  :::column-end:::
  :::column:::
    This program has a valid digital signature, which helps to ensure that the program actually is what it claims to be, and it verifies the identity of the program’s publisher. If this type of dialog box displays, make sure the program is the one that you want to run and that you trust the publisher.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A program with an unknown publisher needs your permission to start.
  :::column-end:::
  :::column:::
    This program does not have a valid digital signature from its publisher. This does not necessarily indicate danger, because many older, legitimate apps lack signatures. However, use extra caution, and only allow a program to run if you obtained it from a trusted source, such as the product CD or a publisher’s website. If you are unsure, search the Internet for the program’s name to determine if it is a known program or malware.
  :::column-end:::
:::row-end:::


Most of the time, you should sign in to your computer with a standard user account. You can browse the Internet, send email, and use a word processor, all without an administrator account. When you want to perform an administrative task, such as installing a new program or changing a setting that will affect other users, you do not have to switch to an administrator account. The Windows operating system will prompt you for permission or an administrator password before performing the task. We also recommend that you create standard user accounts for all of the people that use your computer.
