Voice routing helps you dictate how calls are routed through your Session Border Controller (SBC) or multiple SBCs.

In your clothing retailer, you've installed and configured the SBC. Now, you want to ensure that voice calls are routed to the right destination, as they are received from the Public Switched Telephone Network (PSTN)

Here, you'll learn how to manage routing in Direct Routing.

## Configure simple voice routing

To set up voice routing, you create a combination of elements including voice routing policies, routes, and usages. You set up voice routing using the Microsoft Teams admin center or PowerShell. Let's look at a basic voice routing configuration set up through PowerShell.

### Create a new usage

You create a new usage by using the **Set-CsOnlinePstnUsage** command in PowerShell, with the following parameters:

|Parameter|Description|
|---------|---------|
|Identity|The scope where these settings should be applied. It's always set to global.|
|Usage|The name of the usage. For example, @{Add= "Unrestricted"} means that you want to add a usage named "Unrestricted".|
| | |

To create a new usage, you would run:

```powershell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="Unrestricted"}
```

### Create a voice route

After you've created a usage, you associate it with a voice route. You create a voice route using the **New-CsOnlineVoiceRoute** command in PowerShell, with the following parameters:

|Parameter|Description|
|---------|---------|
|Identity|The name of the route. This can be the same name as the usage.|
|NumberPattern|Number patterns to match. You can use `.*` to match all number patterns.|
|OnlinePstnGatewayList|The name of your SBC. |
|Priority|The priority position this route should have.|
|OnlinePstnUsages|The usage you want to associate with this voice route.|
| | |

For example, to create a new voice route and associate it with the usage you created earlier, run the following command:

```powershell
New-CsOnlineVoiceRoute -Identity "Unrestricted" -NumberPattern ".*" -OnlinePstnGatewayList sbc1.contoso.com -Priority 1 -OnlinePstnUsages "Unrestricted"
```

### Create a voice routing policy

You create the voice routing policy using the **New-CsOnlineVoiceRoutingPolicy** command and associate it with the usage you created. Run the following command:

```powershell
New-CsOnlineVoiceRoutingPolicy "MyVoiceRoutingPolicy" -OnlinePstnUsages "Unrestricted"
```

"MyVoiceRoutingPolicy" is the name of your policy, and `-OnlinePstnUsages "Unrestricted"` links it with the usage you created earlier.

After completing this final step, you've configured basic voice routing.

## Configure advanced voice routing

For additional redundancy and availability, you can configure more advanced voice routing, using the following process:

### Set up multiple SBCs

Suppose that your organization has offices in the US and Canada. You could set up multiple SBCs as outlined below.

1. An SBC for making calls to the US offices (`sbc1.contoso.com`).
1. A backup SBC in case `sbc1` becomes unresponsive (`sbc1a.contoso.com`).
1. An additional SBC for making calls to all other US and Canada numbers (`sbc2.contoso.com`).

To set up all three SBCs, you run the following commands:

```powershell
New-CsOnlinePSTNGateway -Fqdn sbc1.contoso.com -SipSignallingPort 5068 -Enabled $True
New-CsOnlinePSTNGateway -Fqdn sbc1a.contoso.com -SipSignallingPort 5068 -Enabled $True
New-CsOnlinePSTNGateway -Fqdn sbc2.contoso.com -SipSignallingPort 5068 -Enabled $True
```

### Configure a usage

You configure a single usage to cover all your US and Canada call routing by running the following command:

```powershell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="US and Canada"}
```

With this command, you've configured a usage called "US and Canada".

### Create multiple voice routes

You then create multiple voice routes and associate them with your US and Canada usage. You create a voice route for making calls to the US offices. Use `sbc1.contoso.com` for the SBC and set the route to priority one.

```powershell
New-CsOnlineVoiceRoute -Identity "US Offices 1" -NumberPattern "^\+1(425|206)(\d{7})$" -OnlinePstnGatewayList sbc1.contoso.com -Priority 1 -OnlinePstnUsages "US and Canada"
```

You create a backup route using backup SBC (`sbc1a`), but set its priority to two:

```powershell
New-CsOnlineVoiceRoute -Identity "US Offices 1a" -NumberPattern "^\+1(425|206)(\d{7})$" -OnlinePstnGatewayList sbc1a.contoso.com -Priority 2 -OnlinePstnUsages "US and Canada"
```

The backup route will be used if the first SBC becomes unavailable.
Finally, you create a route for all other US and Canada numbers:

```powershell
New-CsOnlineVoiceRoute -Identity "Other US and Canada numbers" -NumberPattern "^\+1(\d{10})$" -OnlinePstnGatewayList sbc2.contoso.com  -OnlinePstnUsages "US and Canada"
```

You'll notice that priority doesn't have to be added here because it's the only route that matches the number pattern specified.

### Create a voice routing policy

For the final step, you create a voice routing policy and link it with your usage:

```powershell
New-CsOnlineVoiceRoutingPolicy "US and Canada only" -OnlinePstnUsages "US and Canada"
```

When you're done, you've successfully configured advanced voice routing.
