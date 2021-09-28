SBCs are additional single points of failure in your environment, so it is important to plan for disaster events not to lose PSTN connectivity for the users.
### Set up multiple SBCs

In this example, your priority is to ensure that calls to your US office locations are working. Calls to all other numbers are a secondary priority. Therefore, you decide to set up your SBCs like this:

- An SBC for making calls to the US offices (sbc1.contoso.com).

- A backup SBC in case sbc1 becomes unresponsive (sbc1a.contoso.com).

- An additional SBC for making calls to all other US and Canada numbers (sbc2.contoso.com).

To set up all three SBCs, you run the following commands from the Microsoft Teams PowerShell module:

```powershell
New-CsOnlinePSTNGateway -Fqdn sbc1.contoso.com -SipSignallingPort 5068 -Enabled $True

New-CsOnlinePSTNGateway -Fqdn sbc1a.contoso.com -SipSignallingPort 5068 -Enabled $True

New-CsOnlinePSTNGateway -Fqdn sbc2.contoso.com -SipSignallingPort 5068 -Enabled $True

```

### Configure a usage

You configure a single usage to cover all your US and Canada call routing by running the following command from the Microsoft Teams PowerShell module:

```powershell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="US and Canada"}

```

With this command, you've configured a usage called "US and Canada."

### Create multiple voice routes

You then create multiple voice routes and associate them with your US and Canada usage. You create a voice route for making calls to the US offices. Use “sbc1.contoso.com” for the SBC and set the route to priority one.

```powershell
New-CsOnlineVoiceRoute -Identity "US Offices 1" -NumberPattern "^\+1(425|206)(\d{7})$" -OnlinePstnGatewayList sbc1.contoso.com -Priority 1 -OnlinePstnUsages "US and Canada"

```

You create a backup route using backup SBC (sbc1a), but set its priority to two:

```powershell
New-CsOnlineVoiceRoute -Identity "US Offices 1a" -NumberPattern "^\+1(425|206)(\d{7})$" -OnlinePstnGatewayList sbc1a.contoso.com -Priority 2 -OnlinePstnUsages "US and Canada"

```

The backup route will be used if the first SBC becomes unavailable. Finally, you create a route for all other US and Canada numbers:

```powershell
New-CsOnlineVoiceRoute -Identity "Other US and Canada numbers" -NumberPattern "^\+1(\d{10})$" -OnlinePstnGatewayList sbc2.contoso.com  -OnlinePstnUsages "US and Canada"

```

You'll notice that priority doesn't have to be added here because it's the only route that matches the number pattern specified.

### Create a voice routing policy

For the final step, you create a voice routing policy and link it with your usage:

```powershell
New-CsOnlineVoiceRoutingPolicy "US and Canada only" -OnlinePstnUsages "US and Canada"

```

### Other considerations

Location-Based Routing is a feature that lets you restrict toll bypass based on policy and the user's geographic location at the time of an inbound or outbound PSTN call. Location-Based Routing is intended to provide a mechanism to prevent toll bypass. It shouldn't be used as a mechanism to dynamically route PSTN calls based on the location of the user or unintended consequences may result.

When a Teams user is enabled for Location-Based Routing, the following applies:

- To make an outbound PSTN call, one of the following must be true:

- The user's endpoint is located in a network site that's enabled for Location-Based Routing and calls egress through the corresponding gateway that's enabled for Location-Based Routing.

- The user's endpoint is located in a network site that's not enabled for Location-Based Routing and calls egress through a gateway that's not enabled for Location-Based Routing.

Outbound calls aren't allowed in any other scenario.

- To receive an inbound PSTN call, the user's answering endpoint must be located in the same network site where the call ingresses through the gateway that's enabled for Location-Based Routing. In any other scenario, such as if the user is roaming, the call isn't allowed and is routed to the user's call forwarding settings (typically voicemail).

- To transfer a PSTN call to another Teams user, the target user's endpoint must be located in the same network site as the user who initiates the transfer. Transfers aren't allowed in any other scenario.

- To transfer another Teams user to the PSTN, the call must be transferred through a Location-Based Routing enabled gateway located at the same network site as the initial caller. Transfers aren't allowed in any other scenario.

Location-Based Routing uses the same network region, site, and subnet definitions that Skype for Business Server uses. When toll bypass is restricted for a location, an admin associates each IP subnet and each PSTN gateway for that location to a network site. A user’s location is determined by the IP subnet that the user’s Teams endpoints are connected to at the time of a PSTN call. A user may have multiple Teams clients located at different sites, in which case Location-Based Routing enforces each client’s routing separately depending on the location of its endpoint.

Further information can be found in the resources section.

### Media bypass

Media bypass enables you to shorten the path of media traffic and reduce the number of hops in transit for better performance. With media bypass, media is kept between the Session Border Controller (SBC) and the client instead of sending it via the Microsoft Phone System. To configure media bypass, the SBC and the client must be in the same location or network.

You can control media bypass for each SBC by using the `Set-CSOnlinePSTNGateway` command with the `-MediaBypass` parameter set to true or false. If you enable media bypass, this does not mean that all media traffic will stay within the corporate network. This article describes the call flow in different scenarios.

Further information can be found in the resources section.

When you're done, you've successfully configured advanced voice routing and can assign this policy to your users.

