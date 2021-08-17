A Private Branch Exchange (PBX) is a phone system within a business. Phone System is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 or Office 365 cloud with Microsoft Teams.

Calls between users in your organization are handled internally within Phone System, and never go to the Public Switched Telephone Network (PSTN). This also applies to calls between users in your organization located in different geographical areas, removing long-distance costs on these internal calls.

To connect Phone System to the PSTN, you can choose one of the following options:

- **Phone System with Calling Plan** An all-in-the-cloud solution with Microsoft as your PSTN carrier.
- **Phone System with your own PSTN carrier** By using Direct Routing to connect your on-premises environment to Teams.

## Phone System with Calling Plan

Phone System with Calling Plan is Microsoft's all-in-the-cloud solution that provides Private Branch Exchange (PBX) functionality and calls to the Public Switched Telephone Network (PSTN), as shown in the following diagram. With this solution, Microsoft is your PSTN carrier.

:::image type="content" source="../media/2-phone-system-calling-plan-with-pstn.png" alt-text="Phone System with Calling plan.":::

Phone System with Calling Plan might be the right solution for you if you can answer yes to the following questions:

- Is Calling Plan available in your region?
- Can you do without your current PSTN carrier?
- Can you work with Microsoft-managed access to the PSTN?

With this option:

- You get Microsoft Teams Phone with added Domestic or International Calling Plans that enable calling to phones around the world (depending on the level of service being licensed).
- You do not require deployment or maintenance of an on-premises deployment—because Calling Plan operates out of Microsoft 365 or Office 365.
- If necessary, you can choose to connect a supported Session Border Controller (SBC) through Direct Routing for interoperability with third-party PBXs, analog devices, and other third-party telephony equipment supported by the SBC.

This option requires uninterrupted connection to Microsoft 365.

## Phone System with own PSTN carrier with Direct Routing

It is possible that your system is more complex and you cannot answer yes to the three questions above for Phone System with Calling Plan. For example, you might have offices in locations where Calling Plan isn't available. Or you might need a combination solution that supports a complex, multi-national deployment, with different requirements for different geographic locations. You might need to connect Phone System to your telephony network using Direct Routing as outlined in the following diagram.

:::image type="content" source="../media/2-phone-system-with-direct-routing.png" alt-text="Phone System using Direct Routing.":::

If you answer yes to the following questions, then Phone System with Direct Routing is the right solution for you:

- You want to use Teams with Phone System.
- You need to retain your current PSTN carrier.
- You want to mix routing, with some calls going through Calling Plan, some through your carrier.
- You need to interoperate with third-party PBXs and/or equipment such as overhead pagers, analog devices, and so on.

With this option:

- You connect your own supported Session Border Controller (SBC) to Microsoft Teams Phone without the need for additional on-premises software.
- You can use virtually any telephone carrier with Microsoft Teams Phone.
- You can choose to configure and manage this option, or it can be configured and managed by your carrier or partner (ask if your carrier or partner provides this option).
- You can configure interoperability between your telephony equipment—such as a third-party PBX and analog devices—and Microsoft Teams Phone.

This option requires the following:

- Uninterrupted connection to Microsoft 365.
- Deploying and maintaining a supported SBC.
- A contract with a third-party carrier. (Unless deployed as an option to provide connection to third-party PBX, analog devices, or other telephony equipment for users who are on Phone System with Calling Plan.)

The information presented above should give you an idea of what decisions you need to make to be able to deploy the proper configuration for Phone System.

## Phone System Features

This section introduces the following Phone System key features and functionality, and the deployment decisions you'll need to consider:

- Auto attendants and call queues
- Cloud Voicemail
- Calling identity

### Auto attendants and call queues

**Auto attendants:** An auto attendant directs a caller to an appropriate person or department based on the caller's input to the provided menu options. Callers can be directed to specific people within your organization, to call queues where they wait to talk to the next available agent, or to voicemail. Different call routing options can be specified for business hours, off hours, and holidays.

Menu prompts can be created by using text-to-speech (system-generated prompts) or by uploading a recorded audio file. Speech recognition accepts voice commands for hands-free navigation, but people calling in can also use the phone keypad to navigate menus.

Each auto attendant has a specific language and time zone. If you do business in multiple languages or multiple parts of the world, you can create as many different auto attendants as you need to accommodate your callers.

For each auto attendant, you can configure an operator. While you can configure operator calls to go to a variety of destinations, the operator feature is designed to allow callers to talk to a specific person in your organization who can help them.

Auto attendants can be configured to allow callers to search your organization's directory, either by name or by extension number. Within an auto attendant, you can specify who is available for the directory search by choosing groups of users to include or exclude. (This is known as dial scope.)

Callers can reach an auto attendant either by direct phone number, if configured, or by being redirected from another auto attendant or a call queue.

**Call queues:** A call queue is analogous to a waiting room in a physical building. Callers wait on hold while calls are routed to the agents in the queue. Call queues are commonly used for sales and service functions. However, call queues can be used for any situation where the number of calls exceeds your internal capacity, such as a receptionist in a busy facility.

Call queues allow for specific routing of calls in cases where the total number of callers in the queue or the wait time exceeds the limits that you specify. Calls can be routed to specific people, voicemail, other call queues, or auto attendants.

Like auto attendants, call queues each have a language setting. You can use different call queues if you do business in multiple languages. Agents can be members of more than one queue if they're multi-lingual.

For each call queue, you can specify if agents in the queue can opt out of taking calls and if calls should be routed to them based on their presence indication in Teams.

You can assign a phone number to a call queue, however call queues do not provide separate call routing for off hours and holidays. Unless your call queue is staffed 24/7, we recommend assigning the phone number to an auto attendant that redirects to the call queue during business hours.

### Calling identity

By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call.

Depending on your requirements, there are additional considerations you might need such as:

- Phone numbers
- Dial plans and call routing
- Emergency calling
- Location-based routing for direct routing
- Network topology for cloud voice features
- Migrate your existing voice solution

These options are discussed in the **Additional considerations** section below.

## Additional considerations

Depending on your requirements, you might need:

:::image type="content" source="../media/2-additional-considerations.png " alt-text="Phone System Additional Considerations":::

|     Depending on your requirements               |     Description                                                                                                                                             |
|--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Phone numbers from Microsoft                 |     How to get and manage phone numbers from Microsoft, and how to   transfer existing numbers to Microsoft. Read this if you need to obtain phone numbers for Microsoft Calling Plan, transfer existing numbers, obtain service   numbers, and so on.                                                                                                                       |
|     Dial plans and call routing                  |     How to configure and manage dial plans that translate dialed phone   numbers into an alternate format (typically E.164 format) for call  authorization and call routing. Read this if you need to understand what dial   plans are and whether you need to specify dial plans for your organization.                                                                      |
|     Emergency calling                            |     How to manage and configure emergency calling—depending on your PSTN   connectivity option. Read this section if you're using Microsoft Calling Plan or Direct Routing and need to understand how to manage emergency calling   for your organization.                                                                                                                  |
|     Location-Based Routing for Direct Routing    |     How to use Location-Based Routing (LBR) to restrict toll bypass for   Microsoft Teams users based on their geographic location. Read this section if your organization is using Direct Routing at a location that doesn't   allow toll bypass.                                                                                                                          |
|     Network topology for cloud voice features    |     If your organization is deploying Location-Based Routing (LBR) for   Direct Routing or dynamic emergency calling, you must configure network   settings for use with these features in Microsoft Teams. Read this section if you're implementing LBR for Direct Routing, or if you are implementing dynamic emergency calling with Calling Plan or Direct Routing.    |
|     Migrate your existing voice solution         |     What you need to think about when migrating your voice solution to Teams. Read this section if you are migrating from an existing voice solution to Teams.                                                                                                                                                                                                             |

Links to more information on the topics listed in the table above are in the **Additional resources** section in the Summary.

## Combining Phone System with Teams Calling Plans and with Direct Routing

You have options to install Phone System with Teams Calling Plans or Phone System with Direct Routing. In some environments, you may deploy both scenarios. The following will help you decide when and if to use a particular system.

### Leverage Phone System with Calling Plan

First and foremost, you need to know if Calling Plan is available in your country or region. To check for Calling Plan availability in your area, see **Country and region availability for Audio Conferencing and Calling Plans** in the **Additional resources** section in the Summary.

Calling plan is a good choice as long as you don't need or want to keep an existing PSTN.

Calling plan offers you a solution where you do not need to install and maintain any equipment. Calling Plan is a solution where everything is based in the cloud.

### Leverage Phone System with Direct Routing

If Calling Plan isn't available in a particular country, then you have no choice but to use Direct Routing.
Direct Routing is the choice whenever you want to keep your existing PSTN. For example, if you have a desirable rate with your PSTN or when you want to continue with your existing equipment long enough to recoup the ROI.

### Combining Teams Calling Plans with Direct Routing

Larger enterprises often combine Teams Calling Plans and Direct Routing. For example, the main headquarters office already using an existing PSTN might stay with Direct Routing whereas a smaller regional office located in a region where they don't have a PSTN and would benefit from an all-cloud solution would use Calling Plan.

A single office might have both systems configured so that they can use Direct Routing for international calls and use the Calling Plan solution for domestic calls.
