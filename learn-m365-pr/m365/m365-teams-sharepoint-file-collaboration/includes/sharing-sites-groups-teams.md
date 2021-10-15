SharePoint team sites are often used to store sensitive data, such as personal information about your customers, or business critical data. For many sites, you need to control who can access the information carefully.

Suppose you're setting up a collaboration environment using SharePoint. You want to understand how you will control access to each team, so that authorized personnel can do their jobs, but data is secured.

Here, you see how to use groups to help assign access.

## Plan for sharing in your organization

Each SharePoint team site is part of an Microsoft 365 Group, which is a single permissions group associated with a variety of services. Those services include a SharePoint site, an instance of Planner, a mailbox, and a shared calendar. When you add owners or members to the Microsoft 365 Group, they are given access to the SharePoint site along with the other connected services.

While you can manage SharePoint site permissions separately by using SharePoint groups, we recommend managing permissions for SharePoint by adding people to or removing them from the associated Microsoft 365 Group. This provides easier administration as well as giving users access to related services with which they can collaborate.

When planning for sharing in your organization, consider how you want to use the available sharing options:

- Public versus private groups and teams
- Site access requests
- Data classification
- Sharing with people outside your organization (guests)

## Public versus private groups and teams

Microsoft 365 Groups allow you to specify a privacy setting of either public or private. This setting also affects the associated team site as well as the team if the site is used with Microsoft Teams.

**Public groups** can be found by searching within your organization. Anyone can join a public group without approval workflow or notification to the group owners. This means that the files and folder in the SharePoint team site are accessible and editable by anyone in the organization. Public groups are great for broad collaboration scenarios where users from around your organization want to collaborate on or monitor a project that is not confidential to a group.

**Private groups** cannot be found through search. A user must be invited specifically by an existing group or team member or owner in order to get access. When an existing group member invites someone new, the request goes through a group owner for approval. Private groups are best for distinct project teams working on projects that are confidential to the organization.

In both public and private groups and teams, users can share individual files and folders with people outside the group without having to invite them to the group.

## Site access requests

By default, members of a SharePoint team site can invite others to become members of the site without the need for site owner approval. While we recommend that you manage team site membership through the associated Microsoft 365 Group, there may be times when you want to invite others to a team site by itself to view or edit files there.

*Example:*  You have a group of users collaborating on a project and a group of stakeholders who you want to be able to read the project files but not update them. Add the collaboration group as members of the Microsoft 365 Group and give the stakeholders view-only access to the team site.

SharePoint includes an option called **site access requests** which can be used to require new users to be approved by a site owner before they can access the site. There is also an option to disallow site access requests altogether. When this latter option is used, only site owners can invite new users to a team site.

## Data classification

Data loss prevention sensitivity labels provide a way to classify sites and documents with descriptive labels that can then be used to enforce a governance workflow. Using sensitivity labels helps your users to share information safely and to maintain your governance policies without the need for them to become experts in those policies. For example, you could configure a policy that requires all documents that discuss a confidential project have a watermark automatically included.

## Sharing with guests

With SharePoint, you can easily share files, folder, and sites with guests from outside your organization. Guest sharing is covered in detail later in this module.
