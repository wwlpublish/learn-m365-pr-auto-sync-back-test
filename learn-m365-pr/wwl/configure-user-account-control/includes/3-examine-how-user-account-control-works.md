There are two general types of user groups in Windows clients: standard users and administrative users. UAC simplifies users’ ability to operate as standard users and perform all necessary daily tasks. Administrative users also benefit from UAC, because administrative permissions are available only after UAC requests permission from the user for that instance.

### Standard users

In previous versions of the Windows operating system, many users were configured to use administrative permissions rather than standard user permissions. This was because previous Windows versions required that users have administrator permissions to perform basic system tasks, such as adding a printer or configuring a time zone. In Windows 10 and later, many of these tasks no longer require administrative permissions.

When users have administrative permissions on their computers, they can install additional software. Despite organizational policies against installing unauthorized software, many users still do it, which can make their systems less stable and drive up support costs. When you enable UAC and a user must perform a task that requires administrative permissions, UAC prompts the user for administrative credentials. In an enterprise environment, the help desk can give a user temporary credentials that have local administrative permissions to complete a task. The default UAC setting allows a standard user to perform the following tasks without receiving a UAC prompt:

 -  Install updates from Windows Update.
 -  Install drivers from Windows Update or those that are included with the operating system.
 -  View Windows settings. However, a standard user is prompted for elevated permissions when changing Windows settings.
 -  Pair Bluetooth devices with the computer.
 -  Reset the network adapter and perform other network-diagnostic and repair tasks.

### Administrative users

Administrative users automatically have:

 -  Read/write/enact permissions for all resources.
 -  All Windows permissions.

While it might seem clear that all users will not be able to read, alter, and delete any Windows resource, many enterprise IT departments that run older versions of Windows operating systems had no other option but to assign all of their users to the local Administrators group.

One of the benefits of UAC is that it allows users with administrative permissions to operate as standard users most of the time. When users with administrative permissions perform a task that requires administrative permissions, UAC prompts the user for permission to complete the task. When the user grants permission, the task is performed by using full administrative rights, and then the account reverts to a lower level of permission.
