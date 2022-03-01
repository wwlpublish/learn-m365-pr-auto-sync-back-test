Wireless networking uses radio waves to connect wireless devices to other network devices. Wireless networks generally consist of wireless network devices, access points (APs), and wireless bridges that conform to 802.11x wireless standards.

:::image type="content" source="../media/wireless-network-diagram-0b4ee712.jpg" alt-text="Diagram showing the relationship of IPv4.":::


### Wireless Network Topologies

There are two types of wireless network topologies:

 -  **Infrastructure**. Infrastructure wireless networks consist of wireless local area networks (LANs) and cellular networks, and require the use of a device, such as an access point (AP), to allow communication between client wireless devices. You can manage infrastructure wireless networks centrally.
 -  **Ad hoc**. Ad hoc networks can connect wireless devices dynamically in a peer-to-peer configuration without the use of any infrastructure devices.

#### 802.11x wireless standards

The 802.11 standard has been evolving since 1997. There have been many improvements in transmission speed and security of the 802.11 technology since then. A letter of the alphabet designates each new standard, as the following table shows.

:::row:::
  :::column:::
    **Specification**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    802.11a
  :::column-end:::
  :::column:::
    This is the first extension to the original 802.11 specification. It provides up to 54 megabits per second (mbps) and operates in the 5 gigahertz (GHz) range. It isn't compatible with 802.11b.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    802.11b
  :::column-end:::
  :::column:::
    This specification provides 11 mbps and operates in the 2.4 GHz range.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    802.11e
  :::column-end:::
  :::column:::
    This specification defines Quality of Service and multimedia support.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    802.11g
  :::column-end:::
  :::column:::
    This specification is for transmission over short distances at speeds up to 54 mbps. It is backward compatible with 802.11b, and operates in the 2.4 GHz range.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    802.11n
  :::column-end:::
  :::column:::
    This specification adds multiple-input and multiple-output, thereby providing increased data throughput at speeds up to 100 mbps. It vastly improves speed over previous specifications, and it supports both 2.4 GHz and 5 GHz ranges.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    802.11ac
  :::column-end:::
  :::column:::
    This specification builds on 802.11n to attain data rates of 433 mbps. 802.11ac operates only in the 5 GHz frequency range.
  :::column-end:::
:::row-end:::


Guest devices that don't support the 802.11x wireless standards won't be able to see a company's guest network that's built upon these standards.

### Wireless security

Wireless security has been the biggest consideration by organizations planning a wireless implementation. Because wireless traffic travels across open airwaves, it is susceptible to interception by attackers. Therefore, organizations utilize several security technologies to address these concerns. Most Wi-Fi devices support multiple security standards. The following table describes the current security methods available for wireless networks.

:::row:::
  :::column:::
    **Security method**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Wired Equivalent Privacy (WEP)
  :::column-end:::
  :::column:::
    WEP is the oldest form of wireless security. Some devices support different versions: WEP 64-bit key, WEP 128-bit key, WEP 256-bit key. The security issues surrounding WEP are well documented, and you should avoid using WEP unless it is the only alternative.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Wi-Fi Protected Access (WPA)
  :::column-end:::
  :::column:::
    Developed to replace WEP, WPA has two variations:*WPA-Personal* is for home and small business networks, and is easier to implement than WPA Enterprise. It involves providing a security password, and uses a technology called Temporal Key Integrity Protocol. The password and the network SSID generate constantly changing encryption keys for each wireless client.*WPA-Enterprise* is for corporate networks. It involves the use of a Remote Authentication Dial-In User Service (RADIUS) server for authentication.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    WPA2
  :::column-end:::
  :::column:::
    This is an improved version of WPA that has become the Wi-Fi security standard. WPA2 employs Advanced Encryption Standard (AES), which employs larger encryption key sizes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    WPA3
  :::column-end:::
  :::column:::
    WPA3 improves upon WPA2, and is relatively new. It addresses issues with using brute-force attacks to match passwords and unencrypt data. Malicous users with the WiFi password cannot see the contents of traffic by other clients. The Easy Connect feature makes connecting IoT devices easier.WPA-Enterprise increases encryption to 192 bits.
  :::column-end:::
:::row-end:::


The security methods that a given wireless device supports depends on the vendor and the device’s age. All modern wireless devices should support WPA2.

### Wireless Driver Model

Windows 10 introduces a new Wireless Driver Interface (WDI) driver model. This feature allows for a universal WLAN driver package that supports native functionality in the various versions of Windows. Such a driver is called a Universal Windows driver. This driver works on OneCore Universal App Platform (UAP) based editions of Windows, such as Windows for desktop editions (Home, Pro, Enterprise, and Education) and Windows IoT Core (IoT Core).

A Universal Windows driver calls a subset of the interfaces that are available to a Windows driver. For example, the cellular and Wi-Fi connections can be managed using the same networking stack. That allows for easy configuration of metered connections, where you want to avoid large data transfers when possible, and monitoring data usage on a per-connection basis. It also offers greater reliability, with the capability to recover quickly when a device hangs for firmware-related reasons. The new driver model also supports MAC address randomization to increase security and privacy.

Why would you want to randomize your MAC address? When you are not connected to Wi-Fi, your PC sends a signal to look for Wi-Fi networks in the area to help you get connected. The signal contains the unique physical hardware (MAC) address for your device. Some places, for example shopping malls, stores, or other public areas, might use this unique address to track your movement in that area. If your Wi-Fi hardware supports it, you can turn on random hardware addresses to make it harder for people to track you when your PC scans for networks and connects.
