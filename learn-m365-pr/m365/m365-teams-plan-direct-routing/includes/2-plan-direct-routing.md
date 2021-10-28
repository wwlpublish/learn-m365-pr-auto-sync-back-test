There are seven steps in the planning process for Direct Routing. It's important to carefully consider your decisions at each step to ensure that users have a good experience when you migrate. Let's examine the first five steps:

:::image type="content" border="false" source="../media/1-direct-routing-planning-steps.png" alt-text="Diagram shows seven steps for Direct Routing planning. These are, Self-deployed vs. hosting, Licensing and endpoints, Session border controllers (SBC), Fully qualified domain names and certificates, IP ranges and ports (firewall), Voice routing, Optimize Media.":::

## Self-deployed or hosted Session Border Controller (SBC)

The first decision is whether to host the SBC yourself, or use a partner hosted service. This table summarizes the main issues.

|  |Self-deployed SBC  | Partner hosted SBC  |
|---------|---------|---------|
|Benefits     | <ul><li>Full control over SBC</li><li>Connectivity to existing PBX</li></ul>        | <ul><li>No need for purchasing, maintaining, and hosting own SBC</li></ul>        |
|Disadvantages     | <ul><li>Customer responsible for SBC configuration</li><li>Need to purchase, maintain, and host SBC</li></ul>         | <ul><li>No control over SBC configuration</li><li>Support model more complex</li></ul>        |

For each approach, you need to understand:

- Initial and ongoing costs.
- The available support. There's a certification program for SBC devices, but not for Microsoft partners. You should find out what expertise your partner organization has and the support they can provide.

## Licensing and endpoints

Users need the following additional **licenses** to use Direct Routing with Teams:

- Microsoft for Phone System.
- Microsoft Teams plus Skype for Business Plan 2, if included in your plan.

> [!IMPORTANT]
> Don't remove Skype for Business Plan 2 if it's included in your plan. Even if users are in Teams only mode, components from Skype for Business are used.

> [!NOTE]
> The Microsoft Audio Conferencing license is not required for Direct Routing, but it provides functionality for scheduled conferencing meetings, including dial in and dial out from the meeting. Without this license, you can do ad-hoc conferencing including 1:1 calls and adding in another person.

Direct Routing supports the following **endpoints**:

- Any Teams client.
- Common area phones. A common area phone is typically placed in a public area like a lobby and is available for many people to make a call. Common area phones are set up as devices rather than users and can automatically sign into a network.
- Skype for Business third-party IP phones, with some limitations.

## SBC

A SBC is the interface between Microsoft Teams Phone and Teams, and third-party systems, such as a public switched telephone network (PSTN) or legacy private branch exchange (PBX). The SBC is a powerful network device with built-in intelligence that translates signals from legacy systems to Microsoft Teams Phone. An SBC has three main functions:

- **Connectivity** - allows Teams to interconnect with other voice components.
- **Security** - acts as a firewall for Session Initiation Protocol (SIP)) traffic.
- **Media Services** - transcodes and supports voice and video calls.

This diagram shows how the SBC connects Teams and Phone System to legacy PBX and PSTN systems.

:::image type="content" border="false" source="../media/2-session-border-controller.png" alt-text="Diagram shows how the Session border controllers connect Teams and Phone System to legacy PBX and PSTN systems.":::

SBCs must go through a certification process that includes being validated in a third-party lab and daily testing in preproduction. This process is done jointly with SBC vendors. The SBC devices are certified by make, model, and firmware level, often with a required minimum firmware version.
SBCs might be physical hardware devices or software deployed in the cloud, such as Azure or AWS.

## Fully qualified domain names (FQDNs)

The SBC must have a fully qualified domain name, and there are some requirements when assigning a name.

- The default domain name assigned to a Microsoft tenant can't be used, so **contoso.onmicrosoft.com** isn't allowed.
- You must add at least one domain name to your Microsoft tenant, such as **contoso.com**. This allows you to assign a valid name to the SBC, such as **sbc1.contoso.com** or **europe.contoso.com**.
- A sub-domain name, such as **sbc1.europe.contoso.com** isn't a valid name unless you register **europe.contoso.com** as a domain name.

:::image type="content" border="false" source="../media/2-sbc-fqdn.png" alt-text="Diagram shows that the Session border controller must have a fully qualified domain name.":::

## Certificates

Mutual Transport Layer Security (MTLS) is used to communicate with SBCs, so you need to assign a digital certificate from a supported certification authority to each SBC device.

If you have only one SBC, you buy and assign the certificate to the device. With more than one SBC, you need to balance cost and security. The least costly solution is to use a wildcard certificate and assign it to all devices. The costliest, but also most secure, option is to assign one certificate to each device. In this scenario, the private key is only used for one device. Or you would assign one certificate to a batch of SBCs, as a trade-off between cost and security.

## IP ranges and ports

IP ranges and ports must be set correctly so that the SBC can communicate with the Phone System service. Be aware that the requirements for SBCs are different from the requirements for Teams clients. Also check with your SBC vendor for guidance on their NAT requirements.

This table summarizes the IP range and port number requirements for Microsoft 365 Commercial and GCC Moderate or Standard plans.

:::image type="content" border="false" source="../media/2-sbc-ports.png" alt-text="Table summarizes the IP range and port number requirements for Microsoft 365 Commercial and GCC Moderate or Standard plans." lightbox="../media/2-sbc-ports.png":::

## Device routing components

There are a number of voice configuration objects that interact to allow users to place calls. These are:

- Voice routing policy
- PSTN usage records
- Voice route
- Dial plan
- Gateway (trunk)

These objects are discussed in the following units.

## Learn more

- [Set up Audio Conferencing for Microsoft Teams](/microsoftteams/set-up-audio-conferencing-in-teams)
- [Skype for Business phones (3PIP) support with Microsoft Teams](https://aka.ms/3pip)
- [Session Border Controllers certified for Direct Routing](/MicrosoftTeams/direct-routing-border-controllers)
- [Public trusted certificate for the SBC](/MicrosoftTeams/direct-routing-plan#public-trusted-certificate-for-the-sbc)
- [SIP Signaling: FQDNs](/microsoftteams/direct-routing-plan#sip-signaling-fqdns)
