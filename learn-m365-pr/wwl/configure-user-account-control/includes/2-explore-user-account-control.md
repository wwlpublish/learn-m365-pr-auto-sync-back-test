UAC is a security feature that provides a way for users to elevate their status from a standard user account to an administrator account, without having to sign out or switch user profiles. UAC is a collection of features rather than just a prompt. These features, which include File and Registry Redirection, Installer Detection, the UAC prompt, the ActiveX Installer Service, and more, allow Windows users to operate with user accounts that are not members of the Administrators group. These accounts, typically referred to as standard users, are broadly described as operating with least privilege. The most important fact is that when users sign in with standard user accounts, the experience typically is much more secure and reliable.

When you need to make changes to your computer that require administrator-level permissions, UAC notifies you as follows:<br>

 -  If you are an administrator, select **Yes** to continue.
 -  If you are not an administrator, someone with an administrator account on the computer will have to enter their password for you to continue.

If you are a standard user, providing administrative credentials gives you administrator rights to complete the task. When you complete the task, permissions will revert to those that a standard user has. This ensures that even if you are using an administrator account, no one can make changes to your computer without your knowledge. Making elevated permissions temporary helps prevent malicious users from installing malware and spyware on, or making changes to, your computer.
