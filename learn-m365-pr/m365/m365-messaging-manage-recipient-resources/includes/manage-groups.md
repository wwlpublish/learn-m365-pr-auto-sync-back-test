It's important to note the terminology differences between Active Directory and Exchange Online. In Active Directory, a distribution group refers to any group that doesn't have a security context, whether it's mail-enabled or not. In contrast, in Exchange Online, all mail-enabled groups are referred to as distribution groups, whether they have a security context or not.

There are two types of Exchange Online distribution groups you can use to distribute messages:

- Mail-enabled universal distribution groups (also called distribution groups) can be used only to distribute messages
- Mail-enabled universal security groups (also called security groups) can be used to distribute messages, and to grant access permissions to resources

You can use the Exchange admin center or Exchange Online PowerShell to create a new distribution group in your Exchange Online organization, or to mail-enable an existing group.

## Manage distribution groups

To manage a distribution group, you'll need to make sure the account you're using has either the Organization Management or Recipient Management permission. If your organization has configured a group naming policy, it's applied only to groups created by users. When you or other administrators use the Exchange admin center to create distribution groups, the group naming policy is ignored, and isn't applied to the group name.

### Create a distribution group using the Exchange admin center

1. In the Exchange admin center, go to **Recipients > Groups**.
2. Click **New + > Distribution group**.
3. On the **New distribution group** page, enter the display name, alias, and organizational unit (only available in Exchange Server on-premises).  
4. To add members to the group, select **Add +**. When you finish adding members, select **OK** to return to the **New distribution group** page.
5. Under **Choose whether owner approval is required to join the group**, specify whether members need to be approved before they can join the group.
6. Under **Choose whether the group is open to leave**, specify whether the approval is required before a member can leave the group.
7. Select **Save** to create the distribution group.

### Create a distribution group using Exchange Online PowerShell

This example creates a distribution group with an alias **itadmin** and the name **IT Administrators**. The distribution group is created in the default OU, and anyone can join this group without approval by the group owners:

```PowerShell
New-DistributionGroup -Name "IT Administrators" -Alias itadmin -MemberJoinRestriction open 
```

## Manage security groups

To manage an Exchange Online security group, you'll need to make sure the account you are using has either the Organization Management or Recipient Management permission. A mail-enabled security group can be used to distribute messages, and to grant access permissions to resources in Active Directory.

### Create a security group using the Exchange admin center

1. In the Exchange admin center, go to **Recipients > Groups**.
2. Click **New + > Security group**.
3. On the **New security group** page, enter a display name, alias, description, organizational unit, owners, and members fields.  
4. Use **Add group owners as members** to add or remove the owners as members.
5. To add members to the group, click **Add +**. When you've finished adding members, click **OK** to return to the **New security group** page.
6. Select **Owner approval is required** if you want the group owners to receive user requests to join the group.
7. Select **Save** to create the security group.

### Create a security group using Exchange Online PowerShell

This example creates a security group with an alias **fsadmin** and the name **File Server Managers**. The security group is created in the default OU, and anyone can join this group with approval by the group owners:

```PowerShell
New-DistributionGroup -Name "File Server Managers" -Alias fsadmin -Type security 
```

## Microsoft 365 groups

Groups in Microsoft 365 let you choose a set of people with whom you wish to collaborate, and then easily set up a collection of resources for them to share. You don't need to manually assign permissions to those resources. This is because adding members to your group automatically gives them the permissions they need to access the tools and resources your group provides. Groups also provide a new and improved experience for those tasks that were previously handled by distribution lists and shared mailboxes.

## Learn more

- [Manage Distribution Groups](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Manage Security Groups](/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups)
- [Microsoft 365 Groups](/exchange/hybrid-deployment/set-up-microsoft-365-groups)

