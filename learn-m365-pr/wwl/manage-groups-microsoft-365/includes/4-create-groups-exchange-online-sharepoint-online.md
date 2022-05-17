An organization can create groups not only in the Microsoft 365 admin center, but also in Exchange Online and SharePoint Online.

### Creating groups in Exchange Online

An organization can use the Exchange Online admin center to create groups of users. A major benefit of using groups is that you send an email to all the users in a group at the same time. When you create a group in Exchange Online, the appropriate group type must be selected depending on the purpose of the group:

 -  **Distribution group.** Used to distribute messages to a group of users. It's also called a mail-enabled distribution group, or, in Microsoft 365, a distribution group. For more information, see [Manage distribution groups](https://technet.microsoft.com/library/bb124513.aspx?azure-portal=true).
 -  **Security group.** Can be used to distribute messages to a group of users, or to grant access permissions to resources. This group is also called a mail-enabled security group. For more information, see [Manage mail-enabled security groups](https://technet.microsoft.com/library/bb123521.aspx?azure-portal=true).
 -  **Dynamic distribution group.** A type of distribution group whose list of recipients is recalculated every time a message is sent based on filters and conditions the organization defines. For more information, see [Manage dynamic distribution groups](https://technet.microsoft.com/library/bb123722.aspx?azure-portal=true).

After you create distribution groups and mail-enabled security groups in the Exchange admin center, their names and user lists appear on the Microsoft 365 Security groups page. These groups can be deleted in both locations. However, they can only be edited in the Exchange admin center. Dynamic distribution groups don't appear on the Microsoft 365 Security groups page.

### Creating groups in SharePoint Online

SharePoint groups are created automatically whenever a site collection is created. SharePoint Online groups are collections of users who have the same permission level. This design enables an organization to grant multiple users access to a SharePoint Online site by granting permission to the group. SharePoint Online groups greatly enhance and simplify the permissions-management process for administrators. Although SharePoint Online groups can contain individual users, it's easier to manage them with security groups from Microsoft 365.

Several built-in groups are automatically created when a site collection is created in SharePoint Online. These groups are referred to as default SharePoint Online groups. The default SharePoint Online groups that are created depend on the site template that's used to create the site. For example, the Team Site template contains the following default SharePoint Online groups: Team Site Visitors, Team Site Members, and Team Site Owners.

The default groups use the default permission levels in SharePoint—sometimes called SharePoint roles—to grant users rights and access. For more information, see [Default SharePoint groups in SharePoint Online](https://support.office.com/article/13bb2b6b-dd8c-447e-b71b-0e4bb9efe1d3.aspx?azure-portal=true).

### Frequently asked questions about security groups

Let's take a look at some frequently asked questions about security groups to help clarify this subject:

 -  **Question:** How is a security group in Microsoft 365 different from security groups I create in SharePoint?
    
     -  **Answer:** Security groups created in Microsoft 365 can be used with SharePoint, Exchange, MDM, Windows, and more. A security group you create in SharePoint is only recognized by that SharePoint site collection.
 -  **Question:** Do I have to use security groups for my organization to be secure?
    
     -  **Answer:** No. Security groups are just another way to manage security for your organization. You can always grant user permissions and access to sites individually. But with security groups, you can easily manage larger groups of users.
 -  **Question:** Can I send email to a security group?
    
     -  **Answer:** Yes. But if you want to use groups for email and collaboration, it's recommended that you create a Microsoft 365 group instead.
