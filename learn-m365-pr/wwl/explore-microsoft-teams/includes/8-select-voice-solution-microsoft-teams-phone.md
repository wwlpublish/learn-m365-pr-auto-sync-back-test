Microsoft Teams Phone is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud with Microsoft Teams. Microsoft Teams Phone works with Teams clients and certified devices. It allows organizations to replace their existing PBX system with a set of features directly delivered from Microsoft 365.

Calls between users in your organization are handled internally within Microsoft Teams Phone. They never go to the Public Switched Telephone Network (PSTN). As such, you no longer have long-distance costs on internal calls. For users making external calls, Microsoft Teams Phone provides add-on options for connecting to the PSTN.

### Microsoft Teams Phone features

With Microsoft Teams Phone, users can use Microsoft Teams to place and receive calls, transfer calls, and mute or unmute calls. Microsoft Teams Phone users can select a name in their address book and place Microsoft Teams calls to that person. To place and receive calls, Microsoft Teams Phone users can use:

 -  their mobile devices.
 -  a headset with a laptop or PC.
 -  one of many IP phones that work with Teams.

Microsoft Teams Phone administrators can manage calling options and settings from the same console used for messaging, collaboration, and so on. The following sections introduce the key features in Microsoft Teams Phone.

#### Auto attendants

Auto attendants allow you to set up menu options to route calls based on caller input. Menu options for an auto attendant - such as "For Sales, press 1; For Services press 2" - let an organization provide a series of choices that guide callers to their destination quickly, without relying on a human operator to handle incoming calls. Menu prompts can be created by using text-to-speech (system-generated prompts) or by uploading a recorded audio file. Speech recognition accepts voice commands for hands-free navigation, but people calling in can also use the phone keypad to navigate menus.

Each auto attendant has a specific language and time zone. If an organization does business in multiple languages or multiple parts of the world, it can create as many different auto attendants as it needs to accommodate its callers.

An operator can be configured for each auto attendant. While an organization can configure operator calls to go to various destinations, the operator feature is designed to allow callers to talk to a specific person in the organization who can help them.

An auto attendant can be configured to allow callers to search the organization's directory, either by name or by extension number. Within an auto attendant, an organization can specify who's available for the directory search by choosing groups of users to include or exclude. This feature is known as *dial scope*.

Callers can reach an auto attendant either by direct phone number, if configured, or by being redirected from another auto attendant or a call queue. Auto attendants can redirect calls, based on callers' input, to one of the following destinations:

 -  **Operator**. The operator defined for the auto attendant. Defining an operator is optional. The operator can be defined as any of the other destinations in this list.

    > [!TIP]
    > It's recommended that organizations define an Operator, even though this feature is optional. Auto attendants can redirect calls to the operator if the caller doesn't make a selection on menus, repeatedly selects invalid options, or dials by name or number repeatedly fail. If an operator isn't defined, the auto attendant will drop the call.

 -  **Person in the organization**. A person in the organization who can receive voice calls. This person can be an online user or a user hosted on-premises using Skype for Business Server.
 -  **Voice app**. Another auto attendant or a call queue. When this destination is chosen, you must choose the resource account associated with the auto attendant or call queue.
 -  **Voicemail**. The voice mailbox associated with a Microsoft 365 group that you specify. You can choose if you want voicemail transcriptions and the system prompt that says: "**Please leave a message after the tone."** In the Microsoft 365 admin center, you must also enable the **Let people outside the organization email this team** setting for the Microsoft 365 group that you specify.
 -  **External phone number**. Any phone number. See [external transfer technical details](/microsoftteams/create-a-phone-system-auto-attendant?tabs=general-info#external-phone-number-transfers---technical-details?azure-portal=true).
 -  **Announcement (Audio file)**. Play an audio file. A recorded announcement message you upload that's saved as audio in .WAV, .MP3, or .WMA format. The recording can be no larger than 5 MB. The system plays the announcement, and then returns to the auto attendant menu.
 -  **Announcement (Typed)**. Type in a text message that you want the system to read. You can enter up to 1000 characters. The system plays the announcement, and then returns to the auto attendant menu.

> [!WARNING]
> When a call is redirected to a **Person in the organization**, that person must be voice enabled. For details on enabling voice, see [Assign Teams add-on licenses to users](/microsoftteams/teams-add-on-licensing/assign-teams-add-on-licenses?azure-portal=true).

#### Call queues

A call queue is analogous to a waiting room in a physical building. Callers wait on hold while calls are routed to the agents in the queue. Call queues are commonly used for sales and service functions. However, call queues can be used for any situation where the number of calls exceeds an organization's internal capacity, such as a receptionist in a busy facility.

Call queues allow for specific routing of calls in cases where the total number of callers in the queue or the wait time exceeds the limits that an organization specifies. Calls can be routed to specific people, voicemail, other call queues, or auto attendants. Like auto attendants, call queues each have a language setting. Different call queues can be used if an organization does business in multiple languages. Employees can be members of more than one queue if they're multi-lingual. For each of its call queues, an organization can specify the following options:

 -  Persons in the queue can opt out of taking calls.
 -  Calls should be routed to persons based on their presence indication in Teams.

A phone number can be assigned to a call queue. However, call queues don't provide separate call routing for off hours and holidays. Unless a call queue is staffed 24/7, it's recommended that organizations assign a phone number to an auto attendant that redirects to the call queue during business hours.

To configure auto attendants and call queues, organizations need the following resources:

 -  A [Resource Account](/microsoftteams/manage-resource-accounts?azure-portal=true) for each auto attendant and each call queue.
 -  A free Microsoft Teams Phone Resource Account license for each resource account that will be directly dialable from Teams users or external phone numbers.
 -  At least one [Microsoft service number](/microsoftteams/getting-service-phone-numbers?azure-portal=true), Operator Connect number, Direct Routing number, or a hybrid number for each resource account the organization wants to be directly dialable from external phone numbers. The service number may be a toll or toll-free number.

> [!NOTE]
> Resource accounts are disabled for sign-in and must remain so. Chat and presence aren't available for these accounts.

#### Voicemail

Cloud Voicemail is automatically set up and provisioned for all Teams users. Cloud Voicemail is powered by Azure Voicemail services. It supports voicemail deposits to Exchange mailboxes only. It doesn't support third-party email systems. Cloud Voicemail includes voicemail transcription, which is enabled for all users in your organization by default. Your business needs may require that you disable voicemail transcription for specific users or everyone throughout the organization.<br>

#### Calling identity

By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call.

**Additional reading**. For more information, see [Plan for Teams auto attendants and call queues](/microsoftteams/plan-auto-attendant-call-queue?azure-portal=true).

### Microsoft Teams Phone solutions

Microsoft provides several Microsoft Teams Phone plans for organizations to choose from.

You might want the simplest solution—Microsoft Teams Phone with Calling Plan. This option is Microsoft's all-in-the-cloud solution that provides Private Branch Exchange (PBX) functionality and calls to the Public Switched Telephone Network (PSTN), as shown in the following diagram. With this solution, Microsoft is your PSTN carrier.

:::image type="content" source="../media/voice-solutions-simple-1d3ed40c.png" alt-text="Graphic showing how the Microsoft Teams Phone with Calling Plan works.":::


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

 -  [Microsoft Teams Phone with Calling Plan](/microsoftteams/pstn-connectivity#phone-system-with-calling-plan?azure-portal=true). An all-in-the-cloud solution with Microsoft as your PSTN carrier.<br>
 -  [Microsoft Teams Phone with your own PSTN carrier by using Operator Connect](/microsoftteams/operator-connect-plan?azure-portal=true). If your existing operator participates in the Microsoft Operator Connect program, they can manage the service for bringing PSTN calling to Teams.<br>
 -  [Microsoft Teams Phone with your own PSTN carrier by using Direct Routing](/microsoftteams/pstn-connectivity#phone-system-with-direct-routing?azure-portal=true). Connects your on-premises environment to Teams.<br>

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

**Additional reading**. For more information on each of these calling scenarios, see [PSTN considerations for upgrading to Teams from Skype for Business on-premises](/microsoftteams/upgrade-to-teams-on-prem-pstn-considerations?azure-portal=true).<br>
