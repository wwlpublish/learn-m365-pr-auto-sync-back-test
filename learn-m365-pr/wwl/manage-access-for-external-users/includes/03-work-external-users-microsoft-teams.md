Microsoft Teams allows users to work with people both inside and outside your organization, such as partners, vendors, suppliers, or consultants. 

In the following image, User A is a member user in your organization, external users can be anyone:

* User B: With a business account (an Azure AD account)

* User C: With a consumer email account (with Outlook.com, Gmail.com, or others)

* User D: an anonymous user that hasn't been authenticated against your Active Directory. For example, anonymous users can join Teams meetings via a link without logging in with their Microsoft or organization’s account.

:::image type="content" source="../media/external-users.png" alt-text="External users can be accounts with their own work, school, or social identities":::

There are two options to collaborate and communicate with authenticated users outside of your organization when using Teams.

* **External access**: External access enables access permission to users of **an entire external domain**. External access is a type of federation that allows users to find, call, chat, and set up meetings with people in other organizations.

* **Guest access**: Guest access gives access permission to **an individual**. Guest access allows a user to invite people from outside your organization to join a team. Invited people get a guest account in Azure Active Directory.  

Both guest and external access can be used at the same time in Teams meetings. If for compliance and security reasons, you want to limit access to Teams resources, you should consider using external access. With guest access, you do have the capabilities to specify the level of restrictions to meet your compliance and security obligations.

These capabilities include:

* Deciding which teams a guest can be added to.

* Assessing the guest and grant access to a team based on the domain they're coming from.

* Deciding if the guest can access your teams and channels associated SharePoint site.

> [!NOTE]
> You can invite people outside your organization to Teams meetings without configuring external or guest access.

## External access

With external access, you can find, call, chat, and set up meetings with users from an entire external domain. You can also use external access to communicate with people from other organizations who are still using Skype for Business (online and on-premises) and Skype (in preview). A (External) label appears next to the name of the external (federated) user in Teams client.

Use external access when:  ‎

* You have users in different domains who need to collaborate.

    For example, Rob@contoso.com and Ann@northwindtraders.com are working on a project together along with some others in the contoso.com and northwindtraders.com domains.

* You want the people in your organization to use Teams to contact people in specific businesses outside of your organization.

* You want anyone else to find and contact you, using your email address in Teams.

:::image type="content" source="../media/external-access.png" alt-text="A type of federation that allows users to find, call, and chat with people in other organizations":::

## Guest access

With guest access, you can chat or invite people outside your organization to teams or channels.

Guest access in Teams uses the feature of
Azure Active Directory (Azure AD) business-to-business (B2B) collaboration, which lets you invite guest users to collaborate with your organization.

Guests are added to Azure Active Directory (Azure AD), with a user type of *Guest*. They must sign in to Teams using their guest account. This requirement means that they may have to sign out of their own organization to sign in to your organization.

A team owner in Microsoft Teams can add and manage guests in their teams. Everyone on the team can easily identify who is a guest. A (Guest) label appears next to each guest's name and a tag in the upper-right corner of the channel thread indicates the number of guests on the team.

:::image type="content" source="../media/guest-access.png" alt-text="The order of policy precedence":::

For more information, see:

* [Compare external and guest access](https://docs.microsoft.com/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access?azure-portal=true)

* [Comparison of team member and guest capabilities](https://docs.microsoft.com/microsoftteams/guest-experience#comparison-of-team-member-and-guest-capabilities?azure-portal=true)
