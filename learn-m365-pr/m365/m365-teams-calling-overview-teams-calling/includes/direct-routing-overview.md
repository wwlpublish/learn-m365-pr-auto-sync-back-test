Direct Routing enables Phone System to connect through your on-premises Session Border Controller (SBC) to the PSTN using your own telephony carrier.

Direct Routing enables you to connect your SBC to a telephony trunk using third-party hardware. You can configure interoperability between your on-premises telephony equipment, including PBX and analog devices, and Phone System.

:::image type="content" source="../media/4-direct-routing-overview-expanded.png" lightbox="../media/4-direct-routing-overview-inline.png" alt-text="Direct Routing overview":::

Direct Routing is useful in situations where Microsoft Calling Plan is not available. Alternatively, you can use Direct Routing and Calling Plan as part of the same hybrid solution.

You can find a list of SBC devices certified for Direct Routing online at [List of Session Border Controllers certified for Direct Routing](/microsoftteams/direct-routing-border-controllers).

Direct Routing is available Microsoft 365 and Office 365, as well as Office 365 GCC, Office 365 GCC High, and Office 365 DoD.

## When to use Direct Routing

Consider using Direct Routing if:

- You want to use Teams with Phone System.
- You need to retain your current PSTN carrier.
- You want to mix routing, with some calls going through Calling Plan, some through your carrier.
- You need to interoperate with third-party PBXs and/or equipment such as overhead pagers, and other analog devices.

## Core deployment decisions

There are many points that you need to address when considering how to deploy Direct Routing:

- Which users should be able to use Direct Routing, and which services should they be able to access. For example, should all users be able to make external calls through Direct Routing, what voice routes are required, and what voice routing policies should be configured to control PSTN usage?
- What licenses are required? Each user must have licenses assigned in Microsoft 365 or Office 365 for Phone System, Teams, and Microsoft Audio Conferencing.
- Where and how should SBCs be deployed? Does the SBC need to support multiple tenants?
For detailed information, read [Core deployment decisions](/microsoftteams/direct-routing-landing-page#core-deployment-decisions)
