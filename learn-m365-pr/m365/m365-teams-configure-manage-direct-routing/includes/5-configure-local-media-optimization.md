Voice quality is a key requirement for most organization's telephony system. You need to ensure that the move to Direct Routing doesn't cause a drop in call quality so that productivity is improved.

Suppose that your clothing retailer has multiple sites in Singapore, Vietnam, and Indonesia. All three sites have Session Border Controllers (SBCs). You'd like to configure Local Media Optimization for better performance and voice quality.

:::image type="content" border="false" source="../media/5-diagram.png" alt-text="Multiple SBC network diagram":::

You're also aware of the following information when it comes to wide area network (WAN) connectivity:

- Connectivity between Vietnam and the Singapore site is good.
- Connectivity between Indonesia and the Singapore site is good.
- Connectivity between Vietnam and Indonesia isn't so good.

To configure media optimization, you:

1. Configure trusted IP addresses.
1. Configure the network elements.
1. Define the virtual typology.
1. Configure your SBCs and voice routing.

## Configure trusted IP addresses

Your first step is to configure trusted IP addresses. Each of your sites has an IP address that people use to connect to the internet or use their Microsoft Teams clients to connect to the service. You'll configure these as trusted IP addresses.

You can configure trusted IP addresses using either PowerShell or the Microsoft Teams admin center. To configure trusted IP address using PowerShell, run the following commands for each site:

```powershell
# Configure Vietnam site address
New-CsTenantTrustedIPAddress -IPAddress 192.0.2.110 -MaskBits 32 -Description "Vietnam site trusted IP"

# Configure Indonesia site address
New-CsTenantTrustedIPAddress -IPAddress 192.0.2.120 -MaskBits 32 -Description "Indonesia site trusted IP"

# Configure Singapore site address
New-CsTenantTrustedIPAddress -IPAddress 192.0.2.130 -MaskBits 32 -Description "Singapore site trusted IP"
```

|Parameter|Description|
|---------|---------|
|IPAddress| The IP address for each site.|
|MaskBits|The length of bits to mask.|
|Description|A friendly description for the address.|
| | |

## Configure the network elements

Now you're ready to define your regions, sites, and subnets.
The region you're working with is Asia. You need to define your region by giving it the "Asia" ID. To assign this ID, you run the **New-CsTenantNetworkRegion** command in PowerShell:

```powershell
# Define the Asia region
New-CsTenantNetworkRegion -NetworkRegionID "Asia"
```

After defining the region, you can define the sites for it. Run the **New-CsTenantNetworkSite** command to define your sites, and specify the **NetworkRegionID** as "Asia" for each site:

```powershell
# Define the Vietnam site
New-CsTenantNetworkSite -NetworkSiteID "Vietnam" -NetworkRegionID "Asia"

# Define the Indonesia site
New-CsTenantNetworkSite -NetworkSiteID "Indonesia" -NetworkRegionID "Asia"

# Define the Singapore site
New-CsTenantNetworkSite -NetworkSiteID "Singapore" -NetworkRegionID "Asia"
```

> [!NOTE]
> In these PowerShell commands, site names are case sensitive.

Next, define your subnets. You run the **New-CsTenantNetworkSubnet** command for each subnet and specify the **NetworkSiteID** for its associated site:

```powershell
# Define the subnet for Vietnam
New-CsTenantNetworkSubnet -SubnetID 192.168.1.0 -MaskBits 24 -NetworkSiteID "Vietnam"

# Define the subnet for Indonesia
New-CsTenantNetworkSubnet -SubnetID 192.168.2.0 -MaskBits 24 -NetworkSiteID "Indonesia"

# Define the subnet for Singapore
New-CsTenantNetworkSubnet -SubnetID 192.168.3.0 -MaskBits 24 -NetworkSiteID "Singapore"
```

|Parameter|Description|
|---------|---------|
|SubnetID| The subnet to configure. |
|MaskBits|The length of bits to mask.|
|NetworkSiteID|The site that your subnet is in.|
| | |

> [!NOTE]
> Your new tenant network configuration settings, like trusted IPs, subnets, and network sites, could take around two hours to be available.

## Define the virtual typology

Now you can create gateways for your proxy SBC and the downstream SBCs. You're working with the following SBCs:

- Singapore SBC (proxy SBC).
- Indonesia SBC (downstream SBC).
- Vietnam SBC (downstream SBC).

You use the **New-CsOnlinePSTNGateway** to create the gateways. For your proxy SBC, do the following:

```powershell
# Create a gateway for the proxy SBC (Singapore)
New-CsOnlinePSTNGateway -Fqdn proxysbc.contoso.com -SipSignallingPort 5067 -MaxConcurentSessions 100 –GatewaySiteID Singapore –MediaBypass $true –BypassMode Always -Enabled $true
```

For your downstream SBCs, run the following commands:

```powershell
# Create a gateway for the Vietnam downstream SBC
New-CsOnlinePSTNGateway –Identity VNsbc.contoso.com –SipSignalingPort 5061 –ProxySBC proxysbc.contoso.com –GatewaySiteID Vietnam –MediaBypass $true –BypassMode OnlyForLocalUsers –Enabled $true

# Create a gateway for the Indonesia downstream SBC
New-CsOnlinePSTNGateway –Identity IDsbc.contoso.com –SipSignalingPort 5061 –ProxySBC proxysbc.contoso.com –GatewaySiteID Indonesia –MediaBypass $true –BypassMode OnlyForLocalUsers –Enabled $true
```

|Parameter  |Description  |
|---------|---------|
|Fqdn/Identity|The fully qualified domain name of your SBC.|
|SipSignalingPort|Port to use for communicating with Direct Routing services using Transport Layer Security (TLS) protocol.|
|ProxySBC|The fully qualified domain name of the proxy SBC, if you're configuring a downstream SBC.|
|GatewaySiteID|The site ID for this gateway.|
|MediaBypass|Whether to use MediaBypass for this SBC. MediaBypass improves performance and ensures media stays between the SBC and client, and doesn't go to the Microsoft Teams Phone. |
|BypassMode|Set to "OnlyForLocalUsers", to ensure media will flow through the SBC where the user is located. |
| | |

## Configure the SBC and voice routing

The final task is for you to configure the SBCs. You'll need to configure your SBCs for Local Media Optimization, based on your SBC vendor's documentation and guidance.

Not all SBCs support Local Media Optimization. You can use link in the **Learn more** section below to find out if your SBC supports Local Media Optimization by looking up your vendor and product  specifications.

After you've configured your SBCs, you can configure voice routing as outlined in the voice routing configuration unit.

## Learn more

- [Configure SBC(s) for Local Media Optimization according to the SBC vendor specification](/microsoftteams/direct-routing-media-optimization-configure#configure-sbcs-for-local-media-optimization-according-to-the-sbc-vendor-specification)
