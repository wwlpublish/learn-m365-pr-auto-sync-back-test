Azure Active Directory (Azure AD) Identity Governance allows organizations to balance their need for security and employee productivity with the right processes and visibility. It provides capabilities to ensure the right people have the right access to the right resources. These and related Azure AD and Enterprise Mobility + Security features allow organizations to mitigate access risk by protecting, monitoring, and auditing access to critical assets, while ensuring employee and business partner productivity.

Identity Governance give organizations the ability to do the following tasks across employees, business partners and vendors, and across services and applications both on-premises and in clouds:

 -  Govern the identity lifecycle.
 -  Govern access lifecycle.
 -  Secure privileged access for administration.

Specifically, it's intended to help organizations address these four key questions:

 -  Which users should have access to which resources?
 -  What are those users doing with that access?
 -  Are there effective organizational controls for managing access?
 -  Can auditors verify that the controls are working?

### Azure Active Directory entitlement management

Azure Active Directory (Azure AD) entitlement management is an Azure AD Identity Governance feature. It enables organizations to manage identity and access lifecycle at scale. It does so by automating access request workflows, access assignments, reviews, and expiration.

Employees in organizations need access to various groups, applications, and sites to perform their job. Managing this access is challenging. Requirements change, new applications are added, or users need extra access rights. This scenario gets more complicated when you collaborate with outside organizations. You may not know who in the other organization needs access to your organization's resources. At the same time, they may not know what applications, groups, or sites your organization is using.

Azure AD entitlement management can help you more efficiently manage access to groups, applications, and SharePoint Online sites for internal users. It can also do the same for users outside your organization who need access to those resources.

### Why use Azure AD entitlement management?

Enterprise organizations often face challenges when managing employee access to resources, such as:

 -  Users may not know what access they should have. And even if they do, they may have difficulty locating the right individuals to approve their access.
 -  Once users find and receive access to a resource, they may hold on to access longer than is required for business purposes.

These problems are compounded for users who need access from another organization. These users are often external users from supply chain organizations or other business partners. The challenges faced by these external users include:

 -  No one person may know all the external individuals in another organization's directory to be able to invite them.
 -  Even if they were able to invite these users, no one in that organization may remember to manage all of the users' access consistently.

Azure AD entitlement management can help address these challenges.

**Additional reading**. To learn more about how customers have used Azure AD entitlement management, see the [Avanade case study](https://customers.microsoft.com/story/avanade-professional-services-azure-canada?azure-portal=true) and the [Centrica case study](https://customers.microsoft.com/story/757467-centrica-energy-azure?azure-portal=true).

For a short overview of entitlement management, watch this video titled: [Azure Active Directory: What is Entitlement Management?](https://www.microsoft.com/videoplayer/embed/RE4MFIb?postJsllMsg=true?azure-portal=true)

### What are access packages and what resources can I manage with them?

Azure AD entitlement management introduces the concept of an access package. An access package is a bundle of all the resources with the access a user needs to work on a project or perform their task. Access packages are used to govern access for your internal employees, and also users outside your organization.

Access packages are used to manage a user's access to the following resources with entitlement management:

 -  Membership of Azure AD security groups.
 -  Membership of Microsoft 365 Groups and Teams.
 -  Assignment to Azure AD enterprise applications, including SaaS applications and custom-integrated applications that support federation/single sign-on and/or provisioning.
 -  Membership of SharePoint Online sites.

You can also control access to other resources that rely upon Azure AD security groups or Microsoft 365 Groups. For example:

 -  You can give users licenses for Microsoft 365 by using an Azure AD security group in an access package and configuring [group-based licensing](/azure/active-directory/enterprise-users/licensing-groups-assign?azure-portal=true) for that group.
 -  You can give users access to manage Azure resources by using an Azure AD security group in an access package and creating an [Azure role assignment](/azure/role-based-access-control/role-assignments-portal?azure-portal=true) for that group.
 -  You can give users access to manage Azure AD roles by using groups assignable to Azure AD roles in an access package and [assigning an Azure AD role to that group](/azure/active-directory/roles/groups-assign-role?azure-portal=true).

Other capabilities that are included in Azure AD entitlement management include:

 -  **Delegate the ability to create access packages to non-administrators**. Access packages contain resources that users can request. Delegated access package managers can define policies with rules that identify:
    
     -  The users who can request resources.
     -  The user who must approve their access.
     -  The date when their access expires.
 -  **Select the connected organizations whose users can request access**. A user who isn't in your directory can request access. Once the access request is approved, the user is automatically invited into your directory and assigned access. When their access expires, if they have no other access package assignments, their B2B account in your directory can be automatically removed.

### Common scenarios requiring access packages

Access packages don't replace other mechanisms for access assignment. They're most appropriate in situations such as:

 -  Employees need time-limited access for a particular task. For example, you may use group-based licensing and a dynamic group to ensure all employees have an Exchange Online mailbox. You can then use access packages for situations in which employees need more access, such as to read departmental resources from another department.
 -  Access that requires the approval of an employee's manager or other designated individuals.
 -  Departments want to manage their own access policies for their resources without IT involvement.
 -  Two or more organizations are collaborating on a project. As a result, multiple users from one organization will need to be brought in through Azure AD B2B to access another organization's resources.

### How does an organization control who gets access?

With an access package, an administrator or delegated access package manager identifies:

 -  The resources (groups, apps, and sites) the users need access to.
 -  The roles the users must be assigned to access those resources.

Access packages also include one or more policies. A policy defines the rules or guardrails for assignment to access packages. Each policy can be used to:

 -  Ensure that only the appropriate users are able to request access.
 -  There are approvers to review and approve any request.
 -  User access to the resources in a resource request is time-limited and will expire if not renewed.

:::image type="content" source="../media/access-package-options-81a7b19e.png" alt-text="Graphic showing the list of options available for an access package.":::


Within each policy, an administrator or access package manager must define the following items:

 -  The users who are eligible to request access. These users are either existing users (typically employees or already-invited guests), or the external users within a partner organization.
 -  The approval process and the users who can approve or deny access.
 -  The duration of a user's access assignment, once approved, before the assignment expires.

### How is access delegated?

Access packages are defined in containers called catalogs. You can have a single catalog for all your access packages, or you can designate individuals to create and own their own catalogs.

An administrator can add resources to any catalog. However, a non-administrator can only add to a catalog the resources they own. A catalog owner can add other users as catalog co-owners, or as access package managers.

**Additional reading**. For more information on these scenarios, see the article: [Delegation and roles in Azure AD entitlement management](/azure/active-directory/governance/entitlement-management-delegate?azure-portal=true).

### Access package example

The following diagram shows an example of the different elements in entitlement management. It shows one catalog that contains two access packages:

 -  **Access package 1**. This package includes a single group as a resource. Access is defined with a policy that enables a set of users in the directory to request access.
 -  **Access package 2**. This package includes a group, an application, and a SharePoint Online site as resources. Access is defined with two different policies:
    
     -  The first policy enables a set of users in the directory to request access.
     -  The second policy enables users in an external directory to request access.

:::image type="content" source="../media/access-package-example-dfbc8c0b.png" alt-text="Graphic showing an example of two access packages as described in the content.":::
