Azure AD B2B collaboration enables communication and collaboration with people outside an organization. Microsoft Teams can also provide this same functionality. Teams provides two different ways to make that happen:

 -  **External access (federation).** This feature enables users to find, call, and chat with users in other domains (for example, contoso.com).
 -  **Guest access.** Lets users add individuals to their teams, as guests, using their email address. Users can collaborate with guests just as they would with any other users in their organization.

An organization can use both external access and guest access. Using one doesn't prevent an organization from using the other.

### External access

An organization can use external access (federation) when it needs a solution that lets external users in other domains find, call, chat, and set up meetings with its users. External users have no access to an organization's teams or team resources. An organization's users should choose external access when they want to communicate with external users who are still on Skype for Business (online or on premises) or Skype.

External access is turned On by default in Teams. With this option turned On, an organization can communicate with all external domains. The Teams admin can turn this option Off or specify which domains to include (or exclude). Guest access may be a more acceptable option if an organization wants external users to have access to teams and channels.

:::image type="content" source="../media/external-access-supporting-external-sharing-ee1a4798.jpg" alt-text="graphic shows how external sharing works":::


**Additional reading.** For more information, see [Manage external access](/microsoftteams/manage-external-access).

### Guest access

Guest access can be used to add an individual user to a team. The user's domain doesn't matter when providing guest access. Once on a team, guest users can chat, call, meet, and collaborate on organization files. Files can be created using Microsoft 365 apps such as Word, Excel, and PowerPoint. They can then be stored in SharePoint or OneDrive for Business. A guest user can be given nearly all the same Teams capabilities as a native team member. Guest access functionality includes:

 -  Guests are added to an organization’s Active Directory.
 -  To communicate with a guest, the guest must be signed into Teams using their guest account. To do so, a guest may have to sign out of their own Teams account to sign into the organization's Teams account.
 -  Guest users have access to more resources in Teams - such as files, teams, and channels - than external-access (federated) users.
 -  The Teams admin controls everything that a guest can or can’t do in the Teams admin center. To learn more, read [Manage guest access](/microsoftteams/manage-guests).

If an organization is ready to turn on guest access, start with the [Guest access checklist](/microsoftteams/guest-access-checklist).

The following graphic shows the fact that because Guest Users are user objects in foreign tenants that reference the user in their source tenant, the user should express the connection between those two user objects.

:::image type="content" source="../media/external-user-using-guest-access-to-access-team-f533b33e.jpg" alt-text="graphic shows how Guest Users are user objects in foreign tenants that reference the user in their source tenant":::


**Additional reading.** For more information, see [Manage guest access](/microsoftteams/guest-access).
