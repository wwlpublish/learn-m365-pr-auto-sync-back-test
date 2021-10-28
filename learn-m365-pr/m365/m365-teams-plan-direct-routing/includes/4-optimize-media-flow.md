Direct Routing handles two types of traffic: media and signaling. In this unit, let's examine media bypass, where media flow is optimized for users who are in the same building and on the same network as the SBC.

:::image type="content" border="false" source="../media/1-direct-routing-planning-steps.png" alt-text="Diagram shows seven steps for Direct Routing planning. These are, Self-deployed vs. hosting, Licensing and endpoints, Session border controllers (SBC), Fully qualified domain names and certificates, IP ranges and ports (firewall), Voice routing, Optimize Media.":::

## Media bypass

The following diagrams show two scenarios. The diagram on the left shows call flow without media bypass, using Phone Service and the internet. The diagram on the right shows call flow with media bypass, where media flows directly to the SBC.

:::image type="content" border="false" source="../media/4-media-bypass.png" alt-text="The following diagrams show two scenarios. Diagram on the left shows call flow without media bypass, using Phone Service and the internet. The diagram on the right shows call flow with media bypass, where media flows directly to the Session Border Controllers." lightbox="../media/4-media-bypass.png":::

For media bypass to work, it must be enabled on the SBC; there's an on/off toggle. Also, the Teams user must have access to the public IP address of the SBC, whether or not they're on the same network, unless you're using Local Media Optimization.

> [!NOTE]
> The signaling path using SIP/TLS doesn't change; it's always through the Microsoft Cloud.

Media bypass is supported on Teams desktop clients and Teams phone devices. For endpoints that don't support media bypass, such as Skype for Business 3PIP phones and Teams web clients, the call automatically falls back to a non-bypass call. No configuration is needed, it happens automatically.

## IP ranges and ports with media bypass

When media bypass is implemented, there are additional considerations for setting IP address ranges and port numbers.

First, users inside the network need access to the public IP address of the SBC. The administrator has to configure a "hairpin", with the connection going out from the Teams client and back into the SBC's public IP address. If this isn't possible for any reason, the alternative is **local media optimization**, covered later in this unit.

Second, media processors are still required for voice apps and web clients, in the same way as they are for non-bypass traffic. You must also configure IP addresses for them.
Finally, with media bypass, SBCs need to communicate with transport relays, so the relevant ports must be open, and the IP address ranges set.  

This diagram summarizes the requirements for IP address ranges and ports for media bypass.

:::image type="content" border="false" source="../media/4-media-bypass-ips.png" alt-text="Diagram summarizes the requirements for IP address ranges and ports for media bypass.":::

## Local Media Optimization

Local Media Optimization controls how media traffic flows between the Teams client and the SBCs.

When Local Media Optimization is configured, the internal IP address of the SBC is used, rather than the external IP address. This means that SBCs can be behind a firewall, and not necessarily seen by Teams.

:::image type="content"  source="../media/4-local-media-optimization.png" alt-text="Diagram explains that when Local Media Optimization is configured, the internal IP address of the SBC is used, rather than the external IP address. This means that Session Border Controllers can be behind a firewall, and not necessarily seen by Teams.":::

To configure Local Media Optimization, you need to create a **proxy SBC**, with a public IP address, to communicate with Phone Service. It's deployed and configured in the same way as any other SBC for direct routing. This proxy SBC is the target for online voice routes.

In addition, a **downstream SBC** is required. This SBC doesn't have a public IP address and is paired to the Phone Service  by association to the upstream or **proxy SBC**.

## Learn more

- [Local Media Optimization for Direct Routing](/MicrosoftTeams/direct-routing-media-optimization)
- [List of Session Border Controllers certified for Direct Routing](/MicrosoftTeams/direct-routing-border-controllers)
- [Plan for media bypass with Direct Routing](/microsoftteams/direct-routing-plan-media-bypass)
