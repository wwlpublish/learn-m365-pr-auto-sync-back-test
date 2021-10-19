Microsoft Teams was built from the ground up to take advantage of the Microsoft cloud, leveraging Azure, and integrating with and depending on many Microsoft 365 services. For example, Teams are built on Microsoft 365 Groups. Team files are stored in SharePoint and Chat files are stored in OneDrive. User recordings of calls and meetings are also stored in SharePoint and OneDrive for Business. Azure AD Premium features like Naming policies and group expiration may be leveraged by Microsoft Teams.

In this unit, we will look at how Teams Phone services interact with other Microsoft cloud services.

## Understand how Azure and Teams Phone interact

Teams is built on Microsoft Azure as a collection of microservices. Azure hosts the backend services for all of Teams functionality. Specifically for voice, the following services are built in Azure:
- Cloud Voicemail is an Azure Service

- Auto Attendants and Hunt Groups are Azure Services

- Media Processors, Media Controllers, and Media Transport Relays are Azure Services

- Convenience recording is an Azure service

- Optionally, customer SBCs can be hosted in Azure

## Understand how Azure Active Directory and Teams Phone interact

Azure Active Directory (AAD) is Microsoft’s multi-tenant cloud-based directory and identity management service. This provides the sign-in authorization and authentication for Microsoft Teams. 

Azure Active Directory (Azure AD) business-to-business (B2B) collaboration lets you invite guest users to collaborate with you with Microsoft Teams. With Azure AD B2B collaboration, organizations can enforce Conditional Access and multifactor authentication (MFA) policies for B2B users.

Azure Active Directory is also the registration and access control point for Applications and Bots when configuring features like policy-based compliance recording or contact center integration when using Azure Active Directory. Connecting other services tied to Azure AD identities enables a unified user experience across the many different tools that business users consume during their workday.

## Understand how Exchange Online and Exchange Server interact with  Teams Phone

Teams Cloud Voicemail, also sometimes called Azure Voicemail, supports voicemail deposits to Exchange mailboxes only. It doesn't support third-party email systems.
For Office 365 Exchange Online users, Cloud Voicemail is automatically set up and provisioned for users after you assign a Phone System license to the users. Voicemail being delivered to Exchange Server mailboxes via SMTP is also supported.

Other ways Teams and Exchange Online Interact:
- Your Exchange Online contacts that have phone numbers populated will be accessible in Microsoft Teams.

- Chat and Channel Chat messages are also ingested into Exchange Online for compliance and meetings and are scheduled via the Outlook/Exchange calendar; eDiscovery is always done against Exchange Online.

- Channel chat messages are journaled to the group mailbox in Exchange Online.

- Free/Busy information from your Exchange calendar will pull though to your Teams presence.

