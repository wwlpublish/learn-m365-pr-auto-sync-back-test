The external sharing features of SharePoint Online let users in an organization share content with people outside the organization (such as partners, vendors, clients, or customers). External sharing can also share between licensed users on multiple Microsoft 365 subscriptions if an organization has more than one subscription. Planning for external sharing should be included as part of an organization's overall permissions planning for SharePoint Online.

> [!NOTE]
> External sharing is turned on by default for an entire SharePoint Online environment and the sites in it. An organization may want to turn it off globally before people start using sites, or until the organization knows exactly how it wants to use the feature.

### How the external sharing settings work

SharePoint Online has external sharing settings at both the organization level and the site level (previously called the "site collection" level). To allow external sharing on any site, it must be enabled at the organization level. External sharing can then be restricted for other sites. If a site's external sharing option and the organization-level sharing option don't match, the most restrictive value is always applied.

Whichever option is chosen at the organization or site level, the more restrictive functionality is still available. For example, if an organization chooses to allow unauthenticated sharing using "Anyone" links (previously called "shareable" links or "anonymous access" links), users can still share with guests, who sign in, and with internal users.

> [!IMPORTANT]
> Even if an organization-level setting allows external sharing, not all new sites allow it by default. The default sharing setting for Microsoft 365 group-connected team sites is "New and existing guests." The default for communication sites and classic sites is "Only people in your organization."

### Security and privacy

If an organization has confidential information that should never be shared externally, it should store the information in a site that has external sharing turned off. As a general rule, an organization should only create extra sites as needed for external sharing. This approach helps an organization manage security risk by preventing external access to sensitive information.

> [!NOTE]
> To limit internal sharing of contents on a site, site members can be prevented from sharing and enabling access requests. When users share a folder with multiple guests, the guests can see each other's names in the Manage Access panel for the folder (and any items within it).

### Sharing Microsoft 365 group-connected team sites

When users create Microsoft 365 groups (for example in Outlook, or by creating a team in Microsoft Teams), a SharePoint team site is created. Admins and users can also create team sites in SharePoint, which creates a Microsoft 365 group.

For group-connected team sites, the group owners are added as site owners, and the group members are added as site members. In most cases, organizations will share these sites by adding people to the Microsoft 365 group. However, only the site can be shared.

> [!IMPORTANT]
> All group members must have permission to access the team site. If the group's permission is removed, many collaboration tasks (such as sharing files in Teams chats) won't work. An organization should only add guests to the group if it wants them to have access to the site.

### Sharing with people outside the organization

When users share with people outside the organization, an invitation is sent to the person in email, which contains a link to the shared item.

:::image type="content" source="../media/shared-item-in-email-invitation-ec593d50.png" alt-text="screenshot that shows a link to a shared item that appears in an email invitation":::


#### Recipients who sign in

When users share sites, recipients will be prompted to sign in with:

 -  A Microsoft account
 -  A work or school account in Azure AD from another organization

:::image type="content" source="../media/sharepoint-welcome-box-59025397.png" alt-text="screenshot that shows a Welcome dialog box when a recipient attempts to sign in":::


When users share files and folders, recipients are prompted to sign in if they have a Microsoft account. These recipients will typically be added to the organization's directory as guests, and then permissions and groups work the same for these guests as they do for internal users.

Because these guests don't have a license in an organization, they're limited to the following basic collaboration tasks:

 -  They can use Office.com for viewing and editing documents. If an organization's plan includes Office Professional Plus, they can't install the desktop version of Office on their own computers unless the organization assigns them a license.
 -  They can complete tasks on a site based on the permission level that they have been given. For example, if a guest is added as a site member, they'll have Edit permissions and they can add, edit, and delete lists, and they can view, add, update, and delete list items and files.
 -  They can see other types of content on sites, depending on the permissions they have been given. For example, they can navigate to different subsites within a shared site. They can also do things like view site feeds.

Sometimes an organization's authenticated guests need further capabilities, such as OneDrive storage or creating a Power Automate flow. In these situations, the organization must assign the guests an appropriate license within the Microsoft 365 admin center.

#### Recipients who provide a verification code

When users share files or folders, recipients will be asked to enter a verification code if they have:

 -  A work or school account in Azure AD from another organization.
 -  An email address that isn't a Microsoft account or a work or school account in Azure AD.

:::image type="content" source="../media/verification-code-dialog-box-b94de777.png" alt-text="screenshot that shows a verification code dialog box when a recipient attempts to sign in":::


If the recipient has a work or school account, they only need to enter the code the first time. Then they'll be added as a guest and can sign in with their organization's user name and password.

If the recipient doesn't have a work or school account, they must use a code each time they access the file or folder, and they won't be added to the organization's directory.

> [!NOTE]
> Sites can't be shared with people unless they have a Microsoft account or a work or school account in Azure AD.

#### Recipients who don't need to authenticate

Anyone with the link (inside or outside an organization) can access files and folders without having to sign in or provide a code. These links can be freely passed around and are valid until the link is deleted or expires (if an expiration date is set). The identity of the people using these links can't be verified, but their IP addresses are recorded in audit logs when they access or edit shared content.

:::image type="content" source="../media/send-link-invitation-a3b3c4ad.png" alt-text="screenshot of a Send Link invitation":::


People who access files and folders through "Anyone" links:

 -  aren't added to an organization's directory.
 -  can't be assigned licenses.
 -  can't access sites using an "Anyone" link.
 -  can only view or edit the specific file or folder for which they have an "Anyone" link.

### Stopping sharing

An organization can stop sharing with guests in either of two ways:

 -  By removing their permissions from the shared item.
 -  By removing them as a guest in the organization's directory.

An organization can stop sharing with people who have an "Anyone" link by deleting the link in the file or folder that's shared.
