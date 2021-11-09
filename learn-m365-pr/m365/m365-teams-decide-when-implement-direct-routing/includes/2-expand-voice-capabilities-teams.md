Microsoft Teams offers several ways of communicating, including file sharing, chat, video calls, and voice calls. When you want to expand Teams to include voice call and public switched telephone network (PSTN) capabilities, Direct Routing is one option.

Suppose you want to start your assessment of Teams telephony functionality. In your clothing retailer, you want to find out if you can reduce telephony costs by moving to Direct Routing from your third-party private branch exchange (PBX) system. It's important that users don't have to change their phone numbers if you decide to take that step.

Here, you'll learn about the business-case for Direct Routing.

## What is Direct Routing?

Direct Routing allows you to connect Teams to your existing telephone system infrastructure. It works with Phone System, Microsoft's technology for call control and private branch exchange (PBX) capabilities.

Direct Routing is the right option if your organization wants to use an existing telephony provider to deliver voice capability in Teams. You can use it to enable users to make phone calls outside your organization.

Direct Routing is only available in Teams; you can't use it with Skype for Business.

## Is Direct Routing right for my organization?

Direct Routing may be right for your organization if:

- You want to use your existing PSTN infrastructure with Microsoft Teams.
- You want to keep your users' existing telephone numbers, also known as direct inward dials (DIDs).
- You have a contract with your existing telephony service provider.
- Microsoft Calling Plan isn't available in your country (see below).
- You want to use Teams Calling Plans and Direct Routing.
- You want a controlled migration of non-Microsoft endpoints to Microsoft Teams.

## What other options are available?

:::image type="content" source="../media/2-teams-direct-routing.png" alt-text="Direct Routing and Teams" lightbox="../media/2-teams-direct-routing.png":::

Teams Calling Plans is an alternative to Direct Routing. It's available in many, but not all countries. If Teams Calling Plans isn't available in your country, Direct Routing is the alternative.

## What infrastructure do I need?

To implement Direct Routing, you must have a certified Session Border Controller (SBC). The SBC connects your PSTN infrastructure to the Microsoft Teams Phone System.

:::image type="content" source="../media/2-teams-direct-routing-architecture.png" alt-text="Direct Routing Architecture" lightbox="../media/2-teams-direct-routing-architecture.png":::

As you can see from the diagram, the SBC can also be used to link to other services, such as a third-party PBX. The SBC might be a piece of software, or virtual controller, hosted in Azure.

## Learn more

- [Country and region availability for Audio Conferencing and Calling Plans](/MicrosoftTeams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)
