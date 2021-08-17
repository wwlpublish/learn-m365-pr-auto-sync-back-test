The majority of your organization's offices are connected via slow network links. You want to ensure that updates are delivered to devices without exhausting all the available bandwidth on the network. Your organization should consider using Delivery Optimization, together with Microsoft Connected Cache, to improve bandwidth usage and deliver content to devices faster and more securely. As the process manager, you'll explain how delivery of updates can be improved for the devices in the environment using these tools.

## What is Delivery Optimization?

Delivery Optimization is a service that will help you decrease the bandwidth that's used up by sharing the download process across multiple machines during deployment. You can use Delivery Optimization in conjunction with Windows Update, Windows Server Update Services (WSUS), Windows Update for Business, or Microsoft Endpoint Configuration Manager (when installation of Express Updates is enabled).

### Requirements

Here are some of the [requirements](/windows/deployment/update/waas-delivery-optimization#requirements) for Delivery Optimization:

- Devices must be able to access the internet
- Computers running Windows must be on version 1511 or higher
- All devices must be behind the same NAT
- Firewall must allow access to some host names, such as ***.do.dsp.mp.microsoft.com**

### Configure Delivery Optimization

Delivery Optimization can be set up using Group Policy under: **Configuration\Policies\Administrative Templates\Windows Components\Delivery Optimization**. Your team can configure many settings as indicated below:

:::image type="content" source="../media/6-delivery-optimization.png" alt-text="Delivery Optimization settings":::

How your team configures these settings depends on the relevant scenario. For example, if you have sites with 30 or more devices, you would set the **Minimum Peer Caching Content File Size** to at least one megabyte. Similarly, if your team has a large number of mobile devices as part of its environment, then it would allow uploads while on battery for mobile devices, by configuring the appropriate setting.

## Microsoft Connected Cache

Microsoft Connected Cache is a service that you use to cache content on-premises. Your team installs the service on a server on-premises. Devices then use the server to get the content they need, instead of issuing requests to Microsoft over the internet. The cache server responds much faster and more securely than a server over the internet. You can use Delivery Optimization and Microsoft Connected Cache together to get some of the content from peers, and other portions from the cache server. If the cache server fails, the devices get their content from peers or over the internet if necessary.

### Requirements

Microsoft Connected Cache [requirements](/mem/configmgr/core/plan-design/hierarchy/microsoft-connected-cache) include:

- A distribution point on-premises that runs Windows Server 2012 or later
- Computers must run Windows 10 version 1709 or later
- Access to Microsoft cloud services over the internet

### Configure Microsoft Connected Cache

You use Configuration Manager to set up Microsoft Connected Cache with the following process:

1. Go to the **Administration** workspace in the Configuration Manager console.
1. Select a distribution point that is on-premises.
1. Enable it to be used as a Microsoft Connected Cache server in the distribution point's properties.
1. Select a local drive to use for the cache.
1. Specify disk space to use for the cache.
1. For client settings in Configuration Manager, in the **Delivery Optimization** group, set *Enable devices managed by Configuration Manager to use Microsoft Connected Cache servers for content download* to **Yes**.
