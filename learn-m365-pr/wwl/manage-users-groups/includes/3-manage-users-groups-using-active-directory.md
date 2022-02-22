There are two forms of common security principals in Active Directory: user accounts and computer accounts. These accounts represent a physical entity (a person or a computer).

As with local accounts, domain user accounts are created for each user in most cases. This account contains their username and password, as well as information about the user, such as their name, location, department, etc. However, unlike a local account, domain accounts can be used to sign in using other devices on the network (with the correct permissions). The obvious benefit to this is administrators can centrally manage user accounts across an organization instead of each individual device.

Like local accounts, domain user accounts can also be used as dedicated service accounts for applications or services..

### Active Directory groups

Groups are used to collect user accounts, computer accounts, and other groups into manageable units. Using groups allows administrators to manage activities like permissions at scale. With users entering, leaving, or changing positions within the company, it's best to define groups - which could represent a role as well as a group - and assign permissions to the group. Users can be added and removed from groups, instead of having to determine permissions every time a personnel change occurs.

There are two types of groups in Active Directory:

 -  **Distribution groups** Used to create email distribution lists. Distribution groups can be used only with email applications (such as Exchange Server) to send email to collections of users. Distribution groups are not security enabled, which means that they cannot be listed in discretionary access control lists (DACLs).
 -  **Security groups** Used to assign rights and permissions.
    
     -  *User rights* are assigned to a security group to determine what members of that group can do within the scope of a domain or forest. User rights define a person’s administrative role in the domain. For example, a user who is added to the Backup Operators group in Active Directory has the ability to back up and restore files and directories that are located on each domain controller in the domain. This is possible because, by default, the user rights *Backup files and directories* and *Restore files and directories* are automatically assigned to the Backup Operators group. Therefore, members of this group inherit the user rights that are assigned to that group. You can use Group Policy to assign user rights to security groups to delegate specific tasks.
     -  Permissions are different than user rights. Permissions are assigned to the security group for the shared resource. Permissions determine who can access the resource and the level of access, such as Full Control. Security groups are listed in DACLs that define permissions on resources and objects such as file shares or printers.

> [!NOTE]
> Both distribution groups and security groups can be used as an email entity.

### Active Directory default security groups

There are several built-in groups that are created by default when Active Directory is installed. The following list is some of the commonly used groups:

 -  **DnsAdmins** \- Members of this group have administrative access to the DNS Server service.
 -  **Domain Admins** \- Designated administrators of the domain; the Domain Admins group is a member of every domain-joined computer's local Administrators group and receives rights and permissions granted to the local Administrators group, in addition to the domain's Administrators group.
 -  **Domain Computers** \- All workstations and servers that are joined to the domain are by default members of this group.
 -  **Domain Users** \- All users in the domain
 -  **Enterprise Admins** \- Enterprise Admins are like Domain Admins, but have permissions to change forest-wide configuration settings; the Enterprise Admins group is a member of every domain's Administrators group and receives rights and permissions granted to that group.
 -  **IIS\_IUSRS** \- Built-in group used by Internet Information Services.
 -  **Print Operators** \- Members of this group can administer domain printers.
 -  **Remote Desktop Users** \- Members of this group are granted the right to log on remotely using RDP.
