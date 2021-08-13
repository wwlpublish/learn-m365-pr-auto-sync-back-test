In our scenario, you want to extend Microsoft Teams to support meetings for your on-premises and work-from-home staff. Here, you'll learn about the process and steps needed to extend your Microsoft Teams service to include meetings. This includes considerations around network and bandwidth, exchange dependencies and licensing costs.

## Check your environment for pre-deployment readiness of Microsoft Teams meetings

Initially, take time to review and confirm that your environment is ready to support Teams. Review the following information and make any required changes to your environment as needed.

To get the best experience on Teams, your organization must have deployed Exchange Online and SharePoint Online, and you must have a verified domain for Microsoft 365 such as *contoso.com*.

To scale meetings across your organization, you should ensure that all user locations have internet access to connect to the Microsoft 365 Services.

At a minimum, in addition to normal web traffic, you should make sure that the following common ports and locations are opened, for all locations, for media in Teams:

- TCP ports 80 and 443 outgoing from clients that will use Teams
- UDP ports 3478 through 3481 outgoing from clients that will use Teams
- IP address ranges:
  - 13.107.64.0/18
  - 52.112.0.0/14
  - 52.120.0.0/14

## Evaluate your Network and bandwidth capabilities

Review the following before you begin your Teams meetings deployment:

- Do all your locations have internet access (so they can directly connect to Microsoft 365)?
- Do you have a verified domain for Microsoft 365 (for example, *contoso.com*)?
- Has your organization deployed Exchange Online and enabled SharePoint Online?
- Have you run the Network Assessment Tool and ensure that you meet the requirements described in media quality and network connectivity performance from both the edge segment and the client segment?

Once you've verified that you meet these network requirements, you should be ready to roll out Teams.

## Configure any Microsoft Teams meeting dependencies

For the full Teams experience, every user should be enabled for Exchange Online, SharePoint Online, and Microsoft 365 Group creation.

Users' Exchange mailboxes can be hosted online or on-premises. Integration with on-premises Exchange requires an Exchange hybrid deployment. Generally, you shouldn't have to configure any Exchange Online functionality for use with Microsoft Teams. However, for Exchange Hybrid scenarios, there are steps necessary to ensure Group memberships are synchronized between Exchange Server (on-premises) and Exchange Online. This involves enablement of group writeback functionality in Azure AD Connect along with various initialization scripts.

## Consider license costs

You manage access to Teams at the user level by assigning or removing a Microsoft Teams product license. Each user in your organization must have a Teams license before they can use Teams. You can assign a Teams license for new users when new user accounts are created or to users with existing accounts.

By default, when a licensing plan (for example, Microsoft 365 Enterprise E3 or Microsoft 365 Business Premium) is assigned to a user, a Teams license is automatically assigned, and the user is enabled for Teams. You can disable or enable Teams for a user by removing or assigning a license at any time.

## Learn more

- [Meetings and conferencing in Microsoft Teams](/MicrosoftTeams/deploy-meetings-microsoft-teams-landing-page)
- [Meetings in Microsoft Teams](/MicrosoftTeams/tutorial-meetings-in-teams?tutorial-step=4)
- [Prepare your organization's network for Teams](/microsoftteams/prepare-network)
- [Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885)
- [Media Quality and Network Connectivity Performance](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)
