A PBX is a phone system within an organization. Phone System provides PBX capabilities, but without you needing to deploy complex and expensive equipment. Phone System allows you to replace your existing on-premises PBX system with a set of features delivered from Microsoft 365 or Office 365 that is tightly integrated into your cloud experience.

You can connect Phone System to the PSTN in two ways:

- Purchase a Microsoft Calling Plan. Review [Which Calling Plan is right for you?](/microsoftteams/calling-plan-landing-page) for more details.
- Use your existing telephony infrastructure for on-premises PSTN connectivity.

> [!TIP]
> For your Teams users, you can connect your on-premises telephony infrastructure to Phone System by using Direct Routing.

You can use Phone System to support the services described in the following table. 

| Service         | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| Auto attendants | Used to create a menu system for your  organization. Enables callers to move through the system to locate and place  or transfer calls to organization users or specific departments. |
| Call queues     | Provides greetings that are used when  someone calls in to a phone number in your organization. Includes the ability  to automatically put calls on hold and the ability to find the next available  call agent to handle the call. |
| Voicemail       | Enables licensed users to access voicemail  that has been left by callers. |


> [!NOTE]
> After you assign a Phone System license and a phone number to a user, Cloud Voicemail is automatically set up and provisioned.

## Verify Phone System set up and configuration

If you need to troubleshoot Phone System issues, you should be familiar with how to set it up. You’ll need to complete the following high-level steps to set up Phone System.

1. Ensure that Phone System is available in your country or region. Verify availability by reviewing the [Country and region availability for Audio Conferencing and Calling Plans](/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans) document. 
2. Buy an assign Phone System and Calling Plan licenses. The steps to assign a Phone System and Calling Plan license to a single user are the same as assigning a Microsoft 365 or Office 365 license.
3. Get phone numbers for your users, as described in the preceding unit of this module.
4. Get service phone numbers for audio conferencing, call queues, and auto attendants.
5. Set up your Calling Plans by following the guidance in the [Set up Calling Plans](/microsoftteams/set-up-calling-plans) document.
6. Set up audio conferencing, if needed. 
7. Set up a Cloud call queue, if needed. Review the [Create a call queue](/microsoftteams/create-a-phone-system-call-queue) document.
8. Set up a Cloud auto attended, if needed.
9. Assign service phone numbers for audio conferencing, call queues, and auto attendants.
10. Set up Communications Credits for your organization if you’d like to use toll-free numbers with Microsoft Teams.

## Implement auto attendant and call queues

An auto attendant directs callers to an appropriate person or department based on the caller's input to the provided menu options. A call queue is like a waiting room, but for phone calls. Callers wait on hold while calls are routed to the agents in the queue. 

> [!TIP]
> Call queues are often used for sales or service functions.

Auto attendant and call queue often work together. The best way to avoid issues with auto attendant and call queues is to plan carefully the call flow, as displayed in the following example.

:::image type="content" source="../media/attendant-queue-call-routing.png" alt-text="A diagram that displays how calls are handled with auto attendants and call queues.":::

In the preceding example: 

- The zero (0) key redirects callers to an operator. The operator for that auto attendant has been configured as a Person in the organization, Adele Vance. 
- The one (1) key redirects callers to the sales call queue. This call queue is connected to a team that contains the sales team assigned to the queue.
- The two (2) key redirects callers to the support call queue. This call queue is connected to a team that contains the support team assigned to the team.
- The support call queue has a direct phone number via an intervening auto attendant. Having an auto attendant answer the support line allows for separate off hours and holiday call routing.
- The three (3) key redirects users to another auto attendant for the company directory. The company directory auto attendant allows callers to call individuals in the organization by dialing their name or extension.

It’s a good idea to create diagrams like this one to map out your call routing. Make sure you include the following elements:

- Which auto attendants can external users access directly with a phone number?
- What are the out of office hours and holiday routing requirements for your auto attendants?
- The membership for each call queue. 

> [!TIP] 
> You can add users individually to a call queue, or map the queue to different kinds of groups. Mapping a queue to a group provides the most versatile experience.

### Create auto attendants and call queues

Review the following video to learn more about creating an auto attendant.

Create an auto attendant: 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWEnCG?autoplay=false] 

Review the following video to learn more about creating a call queue.

Create a call queue: 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWCF23?autoplay=false] 

### Troubleshoot auto attendant and call queues 

If you experience auto attendant or call queuing issues, you should:

- Verify resource accounts are allocated a Phone System license
- Verify enterprise voice is enabled
- Verify call queues are allocated a Direct Routing number
- Verify your call routing plan 
- Review the configuration of your auto attendants and call flow
- Gather Microsoft Teams logs for further analysis

> [!NOTE]
> Review the [Use log files to monitor and troubleshoot Microsoft Teams](/microsoftteams/log-files) document to learn how to enable and retrieve debug, media, and desktop logs.