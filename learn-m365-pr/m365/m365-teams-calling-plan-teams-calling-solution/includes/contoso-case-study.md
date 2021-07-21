In this section, we will look at some of the aspects of a Contoso Case Study. We will look at some of the questions they had to answer and the decisions that resulted from that analysis. For more information, see **Contoso case study: Teams voice migration overview** in the **Additional resources** section in the Summary.

In this case study, Contoso is a multi-national corporation, which is implementing a Teams voice solution. The goal is to migrate their on-premises users to Teams for unified communication, collaboration, and voice. Contoso migrated their Skype for Business enterprise voice users to Phone System using Microsoft Calling Plan, Direct Routing, or a combination of both.

## Phone System

For the several locations around the world that Contoso has, they started the decision process with the following questions.

|     Question                                                                                    |     Answer                                                   |
|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
|     Do we need to retain functionality provided by our on-premises   deployment?                |     No                                                       |
|     Do we need to interoperate with third-party PBX systems and other   telephony equipment?    |     No                                                       |
|     Do we need to retain our current third-party carrier?                                       |     Yes (regulated countries) and No (in other countries)    |
|     Do we need to get the ROI on SBCs deployed?                                                 |     Yes (for some locations) and No (for other locations)    |
|     Is Microsoft PSTN Calling Plans available in this region?                                   |     Yes (for some locations) and No (for other locations)    |

Based on this analysis, Contoso has decided to:

- Move the users that are located in a region where PSTN calling plans are available to Phone System with Teams Calling Plans.
- Move the users that are not located in a region where PSTN calling plans is available, users located in a site where the ROI on the SBCs has yet to be met, and users that resided in a country that has telephony regulations to Phone System with Direct Routing.

The following diagram shows how this deployment was migrated to both Teams Calling Plans and Direct Routing:

:::image type="content" source="../media/3-contoso-phone-system-calling-plans.png" alt-text="Contoso Phone System with Teams Calling Plans":::

:::image type="content" source="../media/3-contoso-direct-routing.png" alt-text="Contoso Phone System with Direct Routing":::

## Location-based Routing

Location-Based Routing (LBR) is a feature that restricts toll bypass based on policy and the user's physical location at the time of placing or receiving a call. Contoso has an office in a country where it is illegal to bypass the Public Switched Telephone Network (PSTN) provider to decrease long-distance calling costs. The main office has an Internet connection that is used by the main office and by the second office. This office has its own Session Border Controller (SBC) connected to a PSTN carrier.

Contoso determined that Teams follows a scenario on when a call can be placed, when it can be received, when a PSTN call can be transferred to a Teams user, and when you can transfer another Teams user to the PSTN call.

For the SBC in the remote office, Contoso reviewed the list of certified SBCs and determined that the SBC deployed is certified for Direct Routing but is not certified for Media Bypass. To support LBR, Direct Routing needs to be configured to the SBC on-site, there needs to be a local Internet egress, and the SBC needs to be configured for Media Bypass. Based on this information, Contoso decided the following:

- To delay the enablement of Teams LBR until the existing SBC is certified for Media Bypass.
- Contoso decided to use the main site SBC for the Direct Route to Microsoft 365. The main site SBC will be the proxy SBC for the remote site.
- Contoso used a third-party consultant based in the remote country to assist with certification of the LBR configuration with the telephony company in country.
- To support users working from outside of the office to place PSTN calls, the company issued mobile phone was provided to their employees.

The following diagrams show the before and after deployments for a country with telephony regulations that require Location-Based Routing:

:::image type="content" source="../media/3-lbr.png " alt-text="Local Media Optimization LBR":::

### Configuration

To configure the network components in Teams, Contoso completed the below steps to configure Location-Based Routing:

- Define Network regions - One network region was defined.
- Define Network sites - Two network sites were defined. One site for each office location in the region.
- Define Network subnets - Each floor within an office location has their own subnet for the wired and wireless network. This configuration resulted in 20 subnets for Contoso.
- Define trusted IP addresses - The external facing IP addresses for the SBC were added to the trusted IP address.

## Emergency Calling

In Microsoft 365, a Calling Plan user is automatically enabled for emergency calling. But only Calling Plan users in the United States can use dynamic locations for routing emergency calls.

For Direct Routing, additional configuration is required for routing emergency calls and possibly for partner connectivity. The administrator must configure connection to an Emergency Routing Service Provider (ERSP) (United States) OR configure the Session Border Controller (SBC) for an Emergency Location Identification Number (ELIN) application.

Contoso has offices in the United States and outside of the United States:

- In the United States, Contoso Calling Plan users can use dynamic locations for routing emergency calls.
- Outside of the United States, Contoso has some sites that use Teams Calling Plans and some sites that are connected to Phone System through Direct Routing.

As such, three possible Emergency calling plans will be used:

- Calling Plan user in the United States
- Calling Plan user outside of the United States
- Users who connect to Phone System using Direct Routing

### Calling Plan user in the United States

In the United States, the phone number needs to be associated with the caller's emergency location. Based on this requirement, Contoso has decided to associate the location with the telephone number. Dynamic emergency calling for Teams Calling Plans provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) or to notify security desk personnel varies depending on the country of usage of the Teams user.

For Calling Plan users, dynamic location for routing emergency calls is only supported in the United States as follows:

- If a Teams client for a United States Calling Plan user dynamically acquires an emergency address within the United States, that address is used for emergency routing instead of the registered address, and the call will be automatically routed to the PSAP in the serving area of the address.
- If a Teams client for a United States Calling Plan user doesn't dynamically acquire an emergency address within the United States, then the registered emergency address is used to help screen and route the call. However, the call will be screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.

In the United States, you must configure the civic address that is part of the emergency locations that are assigned to network identifiers—and include the associated geo codes.

### Emergency call routing

When a Teams Calling Plan user dials an emergency number, how the call is routed to the PSAP depends on the following:

- Whether the emergency address is dynamically determined by the Teams client.
- Whether the emergency address is the registered address associated with the user's phone number.
- The emergency calling network of that country.

**In the United States:**

- If a Teams client is located at a tenant-defined dynamic emergency location, emergency calls from that client are automatically routed to the PSAP serving that geographic location.
- If a Teams client isn't located at a tenant-defined dynamic emergency location, emergency calls from that client are screened by a national call center to determine the location of the caller before transferring the call to the PSAP serving that geographic location.
- If an emergency caller is unable to update their emergency location to the screening center, the call will be transferred to the PSAP serving the caller's registered address.

**In Canada, Ireland, and the United Kingdom**, emergency calls are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center.

**In France, Germany, and Spain**, emergency calls are routed directly to the PSAP serving the emergency address associated with the number regardless of the location of the caller.

**In the Netherlands**, emergency calls are routed directly to the PSAP for the local area code of the number regardless of the location of the caller.

**In Australia**, emergency addresses are configured and routed by the carrier partner.

**In Japan**, emergency calling is not supported.

## Considerations for Direct Routing

Here are some reasons you would consider selecting Direct Routing:

- If Teams Calling Plans isn't available in your country or region, then your only option is Direct Routing.
- You would use Direct Routing if you retain your PSTN carrier or you make use of third-party PBXs or other equipment such as pager or analog equipment.
- With Direct Routing, you can configure an on-premises PSTN connectivity with Microsoft Teams client. Direct Routing is only supported with Microsoft Teams.

### Emergency call enablement and configuration

You must define emergency calling policies for Direct Routing users by using a Teams emergency call routing policy (TeamsEmergencyCallRoutingPolicy) to define emergency numbers and their associated routing destination. (Note that registered emergency locations aren't supported for Direct Routing users.)

You can assign an emergency call routing policy to a Teams Direct Routing user account, a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located as follows:

- If an emergency call routing policy is associated with the site, then the site policy is used to configure emergency calling.
- If there is no emergency call routing policy associated with the site, or if the client is connected at an undefined site, then the emergency call routing policy associated with the user account is used to configure emergency calling.
- If the Teams client is unable to obtain an emergency call routing policy, then the user isn't enabled for emergency calling.

### Dynamic emergency calling

Teams clients for Direct Routing users can acquire a dynamic emergency address, which can be used to dynamically route calls based upon the location of the caller. For more information, see Configure dynamic emergency calling.

### Emergency call routing policy

The emergency call routing policy references an online PSTN usage, which must have the appropriate Direct Routing configuration to properly route the emergency calls to the appropriate PSTN gateway(s). In particular, you must ensure that there is an OnlineVoiceRoute for the emergency dial string. For more information, see Configure Direct Routing.

> [!NOTE]
> Teams clients prepend the "+" sign in front of emergency numbers in a similar manner that Skype for Business client does; that is, +911. This behavior will be modified in the coming months so that Teams emergency calls will no longer be sending a "+" preceding the number; that is, 911.

The ability to dynamically route emergency calls for Direct Routing users varies depending on the emergency calling network within a given country. There are two solutions available:

- Emergency Routing Service Providers (US only)
- Emergency Location Identification Number (ELIN) gateway applications

## Security desk notification

Security desk notification is available with both Teams Calling Plans and Direct Routing.

You use a Teams emergency calling policy (TeamsEmergencyCallingPolicy) to configure who should be notified during an emergency call and how they're notified: chat only, conferenced in and muted, or conferenced in and muted but with the ability to unmute. You can also specify an external PSTN number of a user or group to call and join the emergency call.
An emergency calling policy can be granted to a Teams user account, assigned to a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If an emergency calling policy is associated with a network site, then the site policy is used to configure security desk notification.
- If there is no emergency calling policy associated with the site, or if the client is connected at an undefined site, then the emergency calling policy associated with the user account is used to configure security desk notification.
- If the Teams client is unable to obtain an emergency calling policy, then the user isn't enabled for security desk notification.

During an emergency call, a security desk is conferenced into the call and the experience of the security desk user is controlled based upon the Teams emergency calling policy. A group chat is started with each security desk member, and the location of the emergency caller is shared via an important message notification. If a conference option is configured as part of the policy, each security desk user is additionally called as part of the conference.

The information above has shown you how the IT department at Contoso was  able to determine how to deploy Phone System for their environment.
