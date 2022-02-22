Either sharing policies or organization relationships can be used to control federated sharing. The main difference is that with sharing policies, users in your organization send sharing invitations to external users they want to share calendars or contacts with.

A sharing policy can be assigned to specific mailboxes, or it can determine what information a user can share with external users. Although the organization that contains the external user’s mailbox doesn't require a federation trust, you should configure a federation trust to enable a two-way sharing relationship.

Sharing policies that are available within Exchange include:

 -  The default sharing policy, which applies to all users.
 -  Specific sharing policies, which are assigned to selected users.

This design enables you to ensure that sharing policies can be granular and not automatically available for everybody in an external organization as when you configure organization relationships.

Each sharing policy – both the default sharing policy and other policies you create – consist of two core components:

 -  Domains you want to share with.
 -  The level of sharing you want to allow for those domains.

You can configure the following settings for domains:

 -  Sharing with all domains
 -  Sharing with a specific domain

For the domains in-scope within the policy, you can then configure the following levels of sharing allowed:

 -  Calendar free/busy information with time only.
 -  Calendar free/busy information with time, subject, and location.
 -  All calendar appointment information, including time, subject, location, and title.

The default sharing policy automatically applies to all Exchange Server mailboxes. It enables the sharing of free/busy information with all domains, unless you modify it. The default sharing policy enables users to share their free/busy information with external users immediately after a federation trust is created. As a result, changing the default sharing policy will, by default, apply to every mailbox in your Exchange organization as well.

While the default sharing policy is automatically applied to all mailboxes, any other sharing policies must be applied to mailboxes to take effect. You can also apply only a single sharing policy in each mailbox. A policy is applied to a mailbox by using the policy’s properties or the recipient’s properties.

You can use the Exchange admin center or the Exchange Management Shell to create sharing policies and assign them to specific mailboxes. For example, if you want to create a sharing policy for **adatum.com** that includes sharing free/busy details, you should run the following command:

```powershell
New-SharingPolicy -Name "Adatum.com"   
-Domains 'adatum.com: CalendarSharingFreeBusyDetail'

```

Once you created a new sharing policy, you can apply it to one or more mailboxes. For example, you should run the following command to apply the sharing policy for adatum.com to a user named Alex in your organization:

```powershell
Set-Mailbox -Identity Alex -SharingPolicy "Adatum.com"

```
