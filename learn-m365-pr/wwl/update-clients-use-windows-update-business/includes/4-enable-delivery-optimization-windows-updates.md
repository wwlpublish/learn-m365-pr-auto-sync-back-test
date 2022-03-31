Windows deployments, including updates, can contain packages with very large files that can consume a large amount of network resources on the devices receiving them. You can use Delivery Optimization or Branch Cache for your Windows devices to reduce bandwidth consumption when those devices download applications and updates. Delivery Optimization works in conjunction with Windows Update, Windows Update for Business, and Windows Server Update Services (WSUS).

### Use Delivery Optimization

Delivery Optimization works in conjunction with Windows Update, Windows Update for Business, and Windows Server Update Services (WSUS). Download packages supported for Delivery Optimization include:

 -  Windows updates and drivers
 -  Windows Store and Store for Business files
 -  Microsoft Defender definition updates
 -  Office Click-to-Run updates
 -  Win32 apps for Intune
 -  Office installations and updates (ver 2004 and later)
 -  MSIX apps (HTTP downloads only) (ver 2004 and later)

### Configure Delivery Optimization in Intune

To set up Delivery Optimization in Intune, configure Delivery Optimization as part of your device configuration profiles. After you create a profile, you then assign or deploy that profile to your Windows devices.

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  Select **Devices** &gt; **Configuration profiles** &gt; **Create profile**.
3.  Enter the following properties:
    
     -  Platform: Select **Windows 10 and later**.
     -  Profile: Select **Delivery Optimization**.
4.  Select **Create**. Delivery Optimization has several options for controlling how updates are facilitated. Some of the options include: **Download mode**
    
     -  **Not configured**: End users update their devices using their own methods, which may be to use the Windows Updates or Delivery Optimization settings available with the operating system.
     -  **HTTP only, no peering (0)**: Get updates only from the internet. Don't get updates from other computers on your network (peer-to-peer).
     -  **HTTP blended with peering behind the same NAT (1)**: Get updates from the internet and from other computers on your network.
     -  **HTTP blended with peering across a private group (2)**: Peering occurs on devices in the same Active Directory Site (if it exists) or the same domain. When this option is selected, peering crosses your Network Address Translation (NATs) IP addresses.
     -  **HTTP blended with Internet peering (3)**: Get updates from the internet and from other computers on your network.
     -  **Simple download mode with no peering (99)**: Gets updates from the internet, directly from the update owner, such as Microsoft. It doesn't contact the Delivery Optimization cloud services.
     -  **Bypass mode (100)**: Use Background Intelligent Transfer Service (BITS) to get updates. Don't use Delivery Optimization.
    
    **Bandwidth** Select how Intune determines the maximum bandwidth that Delivery Optimization can use across all concurrent download activities. Settings include:
    
     -  Maximum upload/download bandwidth
     -  Percentage of max foregroud/background download bandwidth, for during and outside business hours
    
    **Caching** Select size limits, battery level, and whether to allow peer caching over VPN. Settings include:
    
     -  Minimum RAM and disk size required for peer caching
     -  Minimum battery level % required to upload
     -  Maximum cache size type
     -  VPN peer caching
5.  After choosing a configuration, assign the profile, and complete the creation of the profile.

Delivery Optimization can also be configured with Group Policy. You will find the Delivery Optimization settings in Group Policy under **Configuration\\Policies\\Administrative Templates\\Windows Components\\Delivery Optimization**. You can also manage Delivery Optimization using Microsoft Endpoint Configuration Manager.

### Branch Cache

BranchCache is a bandwidth-optimization feature. You can use Branch Cache with WSUS or with Microsoft Endpoint Configuration Manager. Each client has a cache and acts as an alternate source for content that devices on its own network request.

BranchCache has two operating modes:

 -  **Distributed Cache mode**. This mode operates like the peer-to-peer Delivery Optimization feature in Windows.
 -  **Hosted Cache mode**. With this mode, designated servers at specific locations act as a cache for files requested by clients in its area.

Branch Cache is generally configured using Group Policy. Settings can be found under **Computer Configuration\\Policies\\Administrative Templates\\Policy definitions (ADMX files) retrieved from the local machine\\Network\\BranchCache**.
