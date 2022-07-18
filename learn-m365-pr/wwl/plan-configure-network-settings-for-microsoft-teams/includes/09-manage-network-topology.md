If your organization is deploying **Location-Based Routing for Direct Routing** or **dynamic emergency calling**, you must configure network settings for use with these cloud voice features in Microsoft Teams. Depending on the cloud voice feature and capability that you're deploying, you configure some or all these settings, including:

* **Network region** - A network region contains a collection of network sites. It interconnects various parts of a network across multiple geographic areas. For example, if your organization has many sites located in India, you may choose to designate "India" as a network region. Each network site must be associated with a network region.

* **Network site** - A network site represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets. Each network site must be associated with a network region.

* **Network subnet** - Each subnet must be associated with a specific network site. A client's location is determined based on the network subnet and the associated network site. You can associate multiple subnets with the same network site but you can't associate multiple sites with the same subnet.

* **Trusted IP addresses** - Trusted IP addresses are the internet external IP addresses of the enterprise network. They determine whether the user's endpoint is inside the corporate network before checking for a specific site match.

You configure network settings on the Network topology page of the Microsoft Teams admin center or by using Windows PowerShell.

## Configure network settings 


### Configure network sites  

You define network regions, network sites, and subnets on the **Network sites** tab of the Network topology page. 

1.	In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then select the **Network sites** tab.

2.	Select **+ Add**, and then enter a name and description for the site.
 
3.	To associate the site with a network region, select **+ Add network region**, select an existing region or select **Add** to add a region, and then select **Link**.

4.	To enable Location-Based Routing for the site, turn on **Location based routing**.

5.	To assign emergency services policies to the site, do one or both of the following:

    * If your organization uses Calling Plans, Operator Connect, or Direct Routing, under **Emergency calling policy**, select the policy that you want.
    * If your organization deployed Direct Routing, under **Emergency call routing policy**, select the policy that you want.

6.	To associate a subnet to the site, under **Subnets**, select **Add subnets**. Specify the IP version, IP address, network range, add a description, and then select **Apply**. Each subnet must be associated with a specific site.

7.	Select **Save**.

    :::image type="content" source="../media/network-topology.png" alt-text="Screenshot of adding network topology.":::

You can also use the following PowerShell cmdlet to configure network sites:

* To define network regions, use the cmdlet ```New-CsTenantNetworkRegion```. 

* To define network sites, use the cmdlet ```New-CsTenantNetworkSite```. 

* To define network subnets, use the cmdlet ```New-CsTenantNetworkSubnet```. 

### Configure trusted IP addresses

You manage external trusted IP addresses on the **Trusted IPs** tab on the Network topology page of the Microsoft Teams admin center. You can add an unlimited number of external trusted IP addresses.

1.	In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then select the **Trusted IPs** tab.

2. Select **Add**.

3. In the **Add trusted IP address** pane, specify the IP version, IP address, network range, add a description, and then select **Apply**.

    :::image type="content" source="../media/network-trusted-ip.png" alt-text="Screenshot of adding trusted I P.":::

You can also use the following PowerShell cmdlet to configure trusted IP addresses:

* To define external subnets and assign them to the tenant, use the cmdlet ```New-CsTenantTrustedIPAddress```.


### Configure roaming policies

In addition to managing video and media settings with meeting policies, you can dynamically control the use of **IP Video** and **Media bit rate** used by the Microsoft Teams client by using the Teams Network Roaming Policy. 

This policy enables you to assign settings to network sites. The Teams client will dynamically pick up the settings based on which network site it connects to. 

When the Teams client signs in from a network site with a roaming policy assigned, that policy will be used. If there is no policy assigned, the values set in the meeting policy will be used.
 
1.	In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then select the **Roaming policies** tab.

2. Select **+ Add**.

3. In the **Add network roaming policy** pane, configure the desired settings, and then select **Apply**.

    * **IP video** - This setting controls whether video can be turned on in meetings hosted by a user and in 1:1 and group calls started by a user.

    * **Media bit rate(Kbs)** - This setting determines the total average media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user.

    :::image type="content" source="../media/network-roaming-policy.png" alt-text="Screenshot of adding a roaming policy.":::

4. Then, you can assign the roamig policy by editing a network site from the **Network sites** tab.

You can also use the following PowerShell cmdlet to configure roaming policies:

* ```Get-CsTeamsNetworkRoamingPolicy```
* ```New-CsTeamsNetworkRoamingPolicy```
* ```Set-CsTeamsNetworkRoamingPolicy```
* ```Remove-CsTeamsNetworkRoamingPolicy```

After you've configured the policy, assign it to one or more network sites by using the ```Set-CsTenantNetworkSite``` cmdlet.

For more information, see [Configure network settings using PowerShell](/microsoftteams/manage-your-network-topology?azure-portal=true#configure-network-settings-using-powershell).

