In Microsoft Teams Direct Routing, Session Border Controllers (SBCs) route calls from the public switched telephone network (PSTN) to Teams.

In your clothing retailer, you're ready to begin to configure Direct Routing. To start, you'll need to configure your Session Border Controller (SBC) and connect it to the Microsoft Teams Phone.

Here, you'll learn how to configure SBCs.

## Configure the SBC

The specific steps you take to configure the Session Border Controller depend on your SBC vendor, which  provides the specific documentation. In the **Learn more** section below, the **Configure Direct Routing** link includes information about SBC from specific manufacturers.

At a high level, configuration of the SBC will generally require you to:

1. Configure the SBC license.
1. Configure LAN and WAN IP interfaces.
1. Configure the certificate used on the device itself.
1. Configure the ports to use for signaling and media.
1. Configure the Session Initiation Protocol (SIP) options and secure real-time transport protocol (SRTP).
1. Configure the codecs to be used.
1. Configure the routing needed for routing calls from Microsoft Teams to PSTN and from PSTN to Microsoft Teams, and any other telephony components you want to connect with the SBC.

## Connect the SBC

After the SBC is configured, you connect it with the Microsoft Teams Phone, using either the Microsoft Teams admin center, or PowerShell. For example, you can connect it through PowerShell by running the **New-CsOnlinePSTNGateway** command, using the following basic minimum parameters:

Parameter|Description|
|---------|---------|
|Fqdn|Fully qualified domain name for the session border controller. Must match one of the registered domains in your tenant. Mustn't be an `*on.microsoft.com` domain.|
|SipSignallingPort|The port that the SBC will be listening on.|
|MaxConcurrentSessions|The maximum concurrent sessions that your SBC can handle.|
|Enabled|Whether the SBC should be enabled.|
| | |

For example, you can run the command like this:

```powershell
New-CsOnlinePSTNGateway -Fqdn sbc1.contoso.com -SipSignallingPort 5068 -MaxConcurrentSessions 50 -Enabled $True
```

Here are some more common parameters to use when connecting your SBC:

|Parameter  |Description  |
|---------|---------|
|ForwardPAI|Used to verify the identity of the caller. The default value is $False. Set to $True if you want to enable it.|
|ForwardCallHistory|Whether call history information should be forwarded through the trunk. The default value is $False. Set to $True if you want to enable it.|
|SIPOptionsEnabled|Helps ensure the gateway is still alive and working. It's automatically enabled and you should keep it that way. If you set it to $False, you won't know whether the SBC has gone offline or not.|
|EnableFastFailoverTime|If outbound calls aren't answered in 10 seconds, they'll be routed to the next available trunk. If no trunk is available, the calls are dropped. Useful if you're working with slow networks. Default value is $False. Set it to $True if you want to enable it.|
|MediaBypass|Whether to enable MediaBypass. Set to $True to enable it.|
| | |

After connecting your SBC, you can verify the connection by checking whether it's in the list of paired SBCs. Run the **Get-CsOnlinePSTNGateway** command with the **Identity** parameter, specifying the fully qualified domain name of your SBC, like this:

```powershell
Get-CsOnlinePSTNGateway -Identity sbc1.contoso.com
```

You'll see output similar to this:

```powershell
Identity              : sbc1.contoso.com  
Fqdn                  : sbc1.contoso.com
SipSignalingPort      : 5067
CodecPriority         : SILKWB,SILKNB,PCMU,PCMA
ExcludedCodecs        :  
FailoverTimeSeconds   : 10
ForwardCallHistory    : False
ForwardPai            : False
SendSipOptions        : True
MaxConcurrentSessions : 100
Enabled               : True
```

Your SBC is now connected.

## Learn more

- [Configure Direct Routing](/microsoftteams/direct-routing-configure)
