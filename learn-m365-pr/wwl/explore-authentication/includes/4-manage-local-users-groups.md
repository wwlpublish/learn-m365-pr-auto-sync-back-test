Local user accounts are stored locally on the client. Choose a local account if you aren't connecting to a network domain. You'll be able to sign in, change your settings, install software, and keep your user area separate from others on the system. However, local users won't be able to access features made possible by Microsoft Accounts. Typically each user has its own account, which governs what permissions they have, but also defines which user profile is loaded, which contains various settings and personalization choices.

Local users accounts are typically only for used in scenarios such as home use, and only when there are specific reasons not to use a Microsoft Account. However, it's important to understand the fundamentals of local accounts and the default local user accounts that are part of Windows.

### Default local user accounts

Default local user accounts are used to manage access to the local client's resources based on the rights and permissions that are assigned to the account. The default local user accounts are built-in accounts that are created automatically when you install Windows. The default local user accounts can’t be removed or deleted. In addition, default local user accounts don't provide access to network resources.

#### Administrator account

The default local Administrator account is a user account for the system administrator. The Administrator account has full control of the files, directories, services, and other resources on the local computer. The Administrator account can create other local users, assign user rights, and assign permissions. The Administrator account can take control of local resources at any time simply by changing the user rights and permissions.

The default Administrator account can’t be deleted or locked out, but it can be renamed or disabled. Because the Administrator account is known to exist on many versions of the Windows operating system, it's a best practice to disable the Administrator account when possible to make it more difficult for malicious users to gain access to the server or client computer.

In a typical install, Windows disables the built-in Administrator account and creates another local account that is a member of the Administrators group. Members of the Administrators groups can run apps with elevated permissions without using the *Run as Administrator* option. As a security best practice, use a non-administrator account to sign in and then use **Run as administrator** to accomplish tasks that require a higher level of rights than a standard user account. Don't use the Administrator account to sign in to your computer unless it's entirely necessary.

#### Default Account

The DefaultAccount is a built-in account. It's a user-neutral account that can be used to run processes that are either multiuser aware or user-agnostic, such as apps that launch, but have the option to sign in. This account should be left at its default disabled state (which doesn't prevent the account from serving its purpose).

#### Default local system accounts

There are many services and processes in the Windows operating system that need the capability to sign in internally, such as during a Windows installation. The SYSTEM account is designed to be used by the operating system and by services that run under Windows. It's an internal account that doesn't show up in User Manager, and it can’t be added to any groups.

The NETWORK SERVICE and LOCAL SERVICE accounts are also predefined local accounts. Unlike the SYSTEM account, these accounts have minimum privileges, and are used by Windows to perform services that don't need full permissions. Using least privilege accounts is part of defense-in-depth security strategy that helps limit malicious damage, in the event, a particular service is compromised.

### Managing users and using account groups

Local accounts can be managed in the Accounts option of the Settings app. Here, users can be created or removed, as well as changed between a Standard user, which has limited permissions, and an Administrator with full permissions.

To create a local account, on Windows Home and Windows Professional editions:

1.  Select the **Start** button, then select **Settings** &gt; **Accounts** &gt; **Family &amp; other people** &gt; **Add someone else to this PC**.
2.  Enter a user name, password, password hint, and then select **Next**.

On Windows Enterprise edition:

1.  Select the **Start** button, then select **Settings** &gt; **Accounts** &gt; **Other people** &gt; **Add someone else to this PC**.
2.  At the bottom of the page, select **I don’t have this person’s sign in information**, and at the bottom of the next page, select **Add** a user without a Microsoft account.
3.  Enter a user name, password, password hint, and then select **Next**.

The Settings app doesn't display default accounts or account groups. To manage these, use the local Computer Management Microsoft Management Console (MMC).

1.  Right-click on **Start** and select **Computer Management**.
2.  Under System Tools, expand the **Local Users and Groups** option and select either **Users** or **Groups** to show the respective accounts objects.

You can also manage local users in a command prompt using NET.EXE, or by using various PowerShell cmdlets.

### Using Groups

Within the settings app, you can switch an account type between Standard User and Administrator, which adds or removes the user from the Administrators group.

Alternatively, you can use Local Users and Groups to assign rights and permissions on a more granular level. Windows comes with several built-in groups that grant various permissions to resources and services. Some examples of these built-in groups include:

 -  Administrators
 -  Users
 -  Guests
 -  Device Owners
 -  Event Log Readers
 -  Hyper-V Administrators
 -  Network Configuration Operators
 -  Remote Desktop Users

By using these groups, administrators are able to grant privileges to what the user needs access to, without granting privileges to services they don't need. One of the main reasons for doing this, is to limit the damage in the event a device is compromised by a threat such as malware. The malware, which typically might run at the user level, isn't capable of using services the user doesn't have permission to use.

For example, Elyssa works for a company that has a policy where users don't have administrative privileges to their computer. In their position, however, they need to frequently change the network settings on here device. As a standard user, they wouldn't be able to do this. By making them a member of the Network Configuration Operators group, they now have the ability to change their network settings, without IT having to grant them full administrative privileges to the device. If their account or device is compromised, their credentials can’t be used to perform malicious attacks such as logging on to the device remotely.
