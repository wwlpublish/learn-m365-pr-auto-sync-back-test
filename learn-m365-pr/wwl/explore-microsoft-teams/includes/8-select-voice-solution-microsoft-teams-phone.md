Microsoft Teams Phone is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud with Microsoft Teams. Microsoft Teams Phone works with Teams clients and certified devices. It allows organizations to replace their existing PBX system with a set of features directly delivered from Microsoft 365.

Calls between users in your organization are handled internally within Microsoft Teams Phone. They never go to the Public Switched Telephone Network (PSTN). As such, you no longer have long-distance costs on internal calls. For users making external calls, Microsoft Teams Phone provides add-on options for connecting to the PSTN.

### Microsoft Teams Phone features

With Microsoft Teams Phone, users can use Microsoft Teams to place and receive calls, transfer calls, and mute or unmute calls. Microsoft Teams Phone users can select a name in their address book and place Microsoft Teams calls to that person. To place and receive calls, Microsoft Teams Phone users can use:

 -  their mobile devices.
 -  a headset with a laptop or PC.
 -  one of many IP phones that work with Teams.

Microsoft Teams Phone administrators can manage calling options and settings from the same console used for messaging, collaboration, and so on. Microsoft Teams Phone includes the following key features:

 -  **Auto attendants**. Auto attendants allow you to set up menu options to route calls based on caller input. Auto attendants can be used to create a menu system for your organization. The menu system lets external and internal callers move through the system to locate and place or transfer calls to company users or departments in your organization.<br>
 -  **Call queues**. Call queue greetings can be used when someone calls in to a phone number for your organization. These greetings include the ability to automatically put the calls on hold and to search for the next available call agent to handle the call. The people on hold can also listen to music while on hold. You can create single or multiple call queues for your organization.<br>
 -  **Voicemail**.- Cloud Voicemail is automatically set up and provisioned for all Teams users. Cloud Voicemail is powered by Azure Voicemail services. It supports voicemail deposits to Exchange mailboxes only. It doesn't support third-party email systems. Cloud Voicemail includes voicemail transcription, which is enabled for all users in your organization by default. Your business needs may require that you disable voicemail transcription for specific users or everyone throughout the organization.<br>
 -  **Calling identity**. By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call.

### Microsoft Teams Phone solutions

Microsoft provides several Microsoft Teams Phone plans for organizations to choose from.

You might want the simplest solution—Microsoft Teams Phone with Calling Plan. This option is Microsoft's all-in-the-cloud solution that provides Private Branch Exchange (PBX) functionality and calls to the Public Switched Telephone Network (PSTN), as shown in the following diagram. With this solution, Microsoft is your PSTN carrier.

:::image type="content" source="../media/voice-solutions-simple-1d3ed40c.png" alt-text="graphic showing how the Microsoft Teams Phone with Calling Plan works":::


If you answer yes to the following, then Microsoft Teams Phone with Calling Plan is the right solution for you:

 -  Calling Plan is available in your region.
 -  You don't need to retain your current PSTN carrier.
 -  You want to use Microsoft-managed access to the PSTN.

However, your situation may be more complex. For example, you may have offices in locations where Calling Plan isn't available. Or you may need a combination solution that supports a complex, multi-national deployment, with different requirements for different geographic locations. Microsoft supports a combination of solutions:

 -  Microsoft Teams Phone with Calling Plan.
 -  Microsoft Teams Phone with your own PSTN carrier with Operator Connect.
 -  Microsoft Teams Phone with your own PSTN carrier with Direct Routing.
 -  A combination solution that uses Microsoft Teams Phone with Calling Plan, Microsoft Teams Phone with Operator Connect, and/or Microsoft Teams Phone with Direct Routing.

> [!NOTE]
> If you’re a small to medium business (300 or fewer people), Microsoft now bundles Microsoft Teams Phone with a Domestic Calling Plan. For more information, see [Microsoft Teams Phone guidance for small and medium businesses](https://docs.microsoft.com/microsoftteams/business-voice/whats-business-voicehttps://aka.ms/SkypeToTeamsWizard?azure-portal=true) to help you plan, set up, and manage your voice solution.

### Public Switched Telephone Network connectivity options

Microsoft Teams Phone provides complete PBX capabilities for your organization. However, to enable users to make calls outside your organization, you need to connect Microsoft Teams Phone to the Public Switched Telephone Network (PSTN). To connect Microsoft Teams Phone to the PSTN, you can choose one of the following options:

 -  [Microsoft Teams Phone with Calling Plan](https://docs.microsoft.com/microsoftteams/pstn-connectivity#phone-system-with-calling-planhttps://aka.ms/SkypeToTeamsWizard?azure-portal=true). An all-in-the-cloud solution with Microsoft as your PSTN carrier.<br>
 -  [Microsoft Teams Phone with your own PSTN carrier by using Operator Connect](https://docs.microsoft.com/microsoftteams/operator-connect-planhttps://aka.ms/SkypeToTeamsWizard?azure-portal=true). If your existing operator participates in the Microsoft Operator Connect program, they can manage the service for bringing PSTN calling to Teams.<br>
 -  [Microsoft Teams Phone with your own PSTN carrier by using Direct Routing](https://docs.microsoft.com/microsoftteams/pstn-connectivity#phone-system-with-direct-routinghttps://aka.ms/SkypeToTeamsWizard?azure-portal=true). Connects your on-premises environment to Teams.<br>

Organizations can choose a combination of connectivity options. By doing so, an organization can design a solution for a complex environment, or manage a multi-step migration. Most Microsoft Teams Phone features are the same regardless of the PSTN connectivity option you choose. There are some differences in functionality that may affect how you configure certain Microsoft Teams Phone features, such as call routing and emergency calling.

### Migrate your existing voice solution to Microsoft Teams

For an organization that is upgrading to Microsoft Teams, the ultimate goal is to move all users to TeamsOnly mode. Using Microsoft Teams Phone is only supported when the user is in TeamsOnly mode.

When an organization migrates its voice solution, there are four possible calling scenarios when moving to TeamsOnly mode:

 -  **A Skype for Business Online user with a Microsoft Calling Plan**. Upon upgrade, this user will continue to have a Microsoft Calling Plan.
 -  **A Skype for Business Online user with on-premises voice functionality through Skype for Business on-premises or Cloud Connector Edition.** The user’s upgrade to Teams must be coordinated with the user's migration to Direct Routing. This upgrade will ensure the TeamsOnly user has PSTN functionality.
 -  **A Skype for Business on-premises user with Enterprise Voice, who will be moving to online and keeping on-premises PSTN connectivity.** Migrating this user to Teams requires moving the user’s on-premises Skype for Business account to the cloud. This move must be coordinated with the user's migration to Direct Routing.
 -  **A Skype for Business on-premises user with Enterprise Voice, who will be moving to online and using a Microsoft Calling plan.** Migrating this user to Teams first requires moving the user’s on-premises Skype for Business account to the cloud. You must then complete one of the following tasks:
    
     -  Coordinate that move with the port of that user’s phone number to a Microsoft Calling Plan.
     -  Assign a new subscriber number from available regions.

**Additional reading**. For more information on each of these calling scenarios, see [PSTN considerations for upgrading to Teams from Skype for Business on-premises](/microsoftteams/upgrade-to-teams-on-prem-pstn-considerations?azure-portal=true).
