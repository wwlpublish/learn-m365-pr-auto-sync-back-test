Because Azure does not provide a native, full-featured firewall capability, other options must be used to restrict traffic. The following table describes the two available options and their advantages and disadvantages.

:::row:::
  :::column:::
    <b>Option </b>
  :::column-end:::
  :::column:::
    <b>Advantage </b>
  :::column-end:::
  :::column:::
    <b>Disadvantage </b>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <u><a href="https://docs.microsoft.com/azure/virtual-network/virtual-networks-acl?azure-portal=true"><span style="color: blue;">Azure network ACLs</span></a></u>
  :::column-end:::
  :::column:::
    Less costly and simpler initial configuration
  :::column-end:::
  :::column:::
    Another network ACL configuration is required if any new VMs are added to the deployment.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <u><a href="https://www.barracuda.com/products/ngfirewallvx/index?azure-portal=true"><span style="color: blue;">Barracuda NG firewall</span></a></u>
  :::column-end:::
  :::column:::
    Safelist mode of operation that requires no network ACL configuration
  :::column-end:::
  :::column:::
    Increased cost and complexity for initial setup.
  :::column-end:::
:::row-end:::


To deploy AD FS in this limited firewall case, you should complete the following high-level steps:

1.  Create a [virtual network with cross-premises connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-plan-design?azure-portal=true), using either a VPN or [ExpressRoute](https://azure.microsoft.com/services/expressroute/?azure-portal=true).
2.  Deploy domain controllers on the virtual network.
3.  Deploy domain-joined AD FS servers on the virtual network.
4.  [Create an internal load balanced set](https://docs.microsoft.com/azure/load-balancer/load-balancer-get-started-ilb-arm-ps?azure-portal=true) that includes the AD FS servers, and that uses a new private IP address within the virtual network (a DIP).
5.  Update DNS to create the FQDN to point to the private IP address (DIP) of the internal load balanced.
6.  Create a cloud service (or a separate virtual network) for the Web Application Proxy nodes.
7.  Deploy the Web Application Proxy nodes in the cloud service or virtual network: 
    1. [Create an external load balanced set](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview#fundamental-load-balancer-features?azure-portal=true) that includes the Web Application Proxy nodes. 
    2. Update the external DNS name (FQDN) to point to the cloud service public IP address (the VIP). 
    3. Configure AD FS proxies to use the FQDN that corresponds to the internal load balanced set for the AD FS servers. 
    4. Update claims-based web sites to use the external FQDN for their claims provider.
8.  Restrict access between Web Application Proxy to any machine in the AD FS virtual network. To restrict traffic, the load-balanced set for the Azure internal load balancer needs to be configured for only traffic to TCP ports 80 and 443, and all other traffic to the internal DIP of the load balanced set is dropped.

  :::image type="content" source="../media/adfs-network-alc-19cbf873.png" alt-text="graphic showing ADFS Network ACLs":::


Traffic to the AD FS servers would be permitted only by the following sources:

 *  The Azure internal load balancer.
 *  The IP address of an administrator on the on-premises network.

A disadvantage to this option is the need to configure the network ACLs for multiple devices, including internal load balancer, the AD FS servers, and any other servers that get added to the virtual network. If any device is added to the deployment without configuring network ACLs to restrict traffic to it, the entire deployment can be at risk. If the IP addresses of the Web Application Proxy nodes ever change, the network ACLs must be reset (which means the proxies should be configured to use [static DIPs](https://docs.microsoft.com/previous-versions/tn-archive/dd163570%28v=technet.10%29?azure-portal=true)).

:::image type="content" source="../media/adfs-on-azure-with-network-alc-9426b9c1.png" alt-text="ADFS On Azure With Network ACLs":::

Another option is to use the [Barracuda NG Firewall](https://www.barracuda.com/products/ngfirewall?azure-portal=true) appliance to control traffic between AD FS proxy servers and the AD FS servers. This option complies with security and high availability recommendations, and it requires less administration after the initial setup because the Barracuda NG Firewall appliance provides a safelist mode of firewall administration and it can be installed directly on an Azure virtual network. That eliminates the need to configure network ACLs whenever a new server is added to the deployment. But this option adds initial deployment complexity and cost.

In this case, two virtual networks are deployed instead of one. VNet 1 contains the proxies and VNet2 contains the STSs and the network connection back to the corporate network; VNet1 is therefore physically (albeit virtually) isolated from VNet2 and, in turn, from the corporate network. VNet 1 is then connected to VNet2 using a special tunneling technology known as Transport Independent Network Architecture (TINA). The TINA tunnel is attached to each of the VNets using a Barracuda NG firewall—one Barracuda on each of the VNets. For high-availability, it is recommended that you deploy two Barracuda firewalls on each VNet; one active, the other passive. They offer rich firewalling capabilities that enables organizations to mimic the operation of a traditional on-premises perimeter network in Azure.

:::image type="content" source="../media/adfs-on-azure-with-firewall-50076cfc.png" alt-text="AADFS On Azure With Firewall":::

**Additional reading.** For more information, see [AD FS: Extend a claims-aware on-premises front-end application to the Internet](https://msdn.microsoft.com/library/azure/jj156090.aspx?azure-portal=true).
