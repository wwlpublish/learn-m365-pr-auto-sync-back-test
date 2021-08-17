Teams Calling deployment requires careful preparation and planning. It's important that you follow an organized approach to ensure that communications function correctly after deployment. The following sections summarize some of the more important aspects. Detailed information is available at [Plan your Teams voice solution](/microsoftteams/cloud-voice-landing-page).

## Prepare and configure Teams

Set up a Microsoft 365 or Office 365 organization. Purchase and assign the correct licenses. Configure the appropriate identities to represent users and services, and identify all tenant administrators. Assign the appropriate admin roles to tenant administrators.
For more information, read [Enable Microsoft 365 or Office 365](/microsoftteams/onboarding-checklist-enable-office-365)

## Prepare the network and topology for Direct Routing

If your organization is implementing location-based routing for Direct Routing, plan your network topology, and create the appropriate network regions, sites and subnets. A network region connects parts of your organization located in one or more geographic areas. A network site represents a physical venue for an organization, such as an office, building, or campus. Each site must belong to a network region. A network site contains one or more subnets. The network location of a client is a combination of the subnet and site for that client. This information is used to configure routing for calls.

You can define network regions, network sites, and subnets using the Teams admin center. Alternatively, you can use PowerShell. For details, read [Manage your network topology for cloud voice features in Microsoft Teams](/microsoftteams/manage-your-network-topology)

Verify that all locations can connect to Office 365 or Microsoft 365.
For more information on network requirements, see [Prepare your organization's network for Microsoft Teams](/microsoftteams/prepare-network).

## Configure Calling Plan if not using Direct Routing

Determine whether calling plans are available for each region within your organization.
Make a list of users that need to be able to make external calls, and create and assign the appropriate calling plans and licenses. Obtain phone numbers for users, either from Microsoft, or by porting existing phone numbers.

[Configure emergency locations]( /microsoftteams/what-are-emergency-locations-addresses-and-call-routing) and enable emergency call routing.
Configure caller ID for incoming and outgoing calls.
[Set up Cloud Voicemail]( /microsoftteams/set-up-phone-system-voicemail), if appropriate, and configure voicemail services, such as transcription and profanity masking.

## Set up audio conferencing

Verify that this feature is available in your country/region. A full list of country/region capabilities is available at [Country and region availability for Audio Conferencing and Teams Calling Plans]( /microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans).
Determine which business users and sites require access to audio conferencing. Consider rolling out audio conferencing on a site-by-site basis. Obtain service numbers or numbers for toll-free calling; you might be able to transfer existing toll-free numbers.
Configure the default bridge number, set up languages for conference bridge phone numbers, and configure the meeting join experience (entry/exit announcements, PIN length, and so on). Customize meeting invitations to include any additional legal or help information, and add logos to ensure invitations match corporate look and feel.

## Configure auto attendants and call queues

Determine how you are going to use these features in your organization. For example, what languages must be supported, should you allow voice inputs or only enable dialing inputs, how are calls routed during off hours and holidays, do you want to record your own messages or use the system-generated voice.
Configure the call routing flow for auto attendants. For example, should the call be transferred directly to a specific person that can receive voice calls, should the target be a voice app, voicemail, or an external number. Alternatively, should the call be directed based on dial options such as an extension number or by spelling a person's name.

For call queues, determine how to handle call overflow (if the number of calls exceeds a preconfigured limit), and call timeouts.
For each auto attendant and call queue, you require, a resource account, a free Phone System (Virtual User license for each resource account), and at least one Microsoft service number, direct routing number, or hybrid number for each resource account that you want to be directly dialable.

For details, read [Plan for Teams auto attendants and call queues]( /microsoftteams/plan-auto-attendant-call-queue).
