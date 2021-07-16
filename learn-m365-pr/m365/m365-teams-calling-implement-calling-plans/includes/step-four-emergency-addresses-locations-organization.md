In the United States, 911 calls first go to a certified Emergency Routing Service Providers (ERSPs). The call taker at the ERSP will find out the location of the emergency and route the call to the proper Public Safety Answering Point (PSAP) that serves the caller's location who can then dispatch the proper units located closest to the location of the caller.

The caller's address must be attached to the caller's phone number. How and when this association happens can vary among country and regions. For example, in the United States, you need to associate an emergency address when you assign the phone number to the user. In the United Kingdom, you need to associate an emergency address to the phone number when you're getting the phone numbers from Microsoft 365 or Office 365, or when transferring phone numbers from your current service provider.

### Emergency address validation

Address validation ensures an address is legitimate. When you assign an emergency address to a user or to a network identifier, you must ensure that the emergency address is marked as "validated." You can define an emergency address by using the address map search feature in the Teams admin center and when you do, the address is automatically marked as validated.
You can't modify a validated address. If the address is ever changed, you must enter the new address and revalidate.

### Emergency address geo codes

Each emergency address can have a latitude and longitude (geo code) associated with it. Geo codes are used in some countries to help route emergency calls with dynamic locations.

A geo code is automatically associated with an emergency address when you define an emergency address by using the address map search feature in the Teams admin center. You can also associate geo codes with an address if you define the address by using PowerShell.
Microsoft recommends that you create emergency addresses for Calling Plan by using the map search feature in Teams admin center, which will ensure that the addresses are formatted, validated, and have the appropriate geo codes.

> [!IMPORTANT]
> To assign an emergency location to a network identifier for dynamic emergency calling, the emergency address must contain an appropriate geo code.

> [!NOTE]
> There are some differences in how you manage emergency calling depending on whether you are using Teams Calling Plans or Direct Routing for your PSTN connectivity. These considerations are described throughout this section.

### Emergency call enablement for Teams Calling Plans

Each Calling Plan user is automatically enabled for emergency calling and is required to have a registered emergency address associated with their assigned telephone number.
When the location must be associated to the telephone number depends on the country/region:

- In the United States and Canada, for example, an emergency location is required when a number is assigned to a user.
- For other countries--such as in Europe, the Middle East, and Africa (EMEA)--an emergency location is required when you get the phone number from Microsoft 365 or Office 365, or when it's transferred from another service provider or carrier.

### Dynamic emergency calling for Teams Calling Plans

Dynamic emergency calling for Teams Calling Plans provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) or to notify security desk personnel varies depending on the country of usage of the Teams user.
For Calling Plan users, dynamic location for routing emergency calls is only supported in the United States as follows. (For information about dynamic emergency calling and Direct Routing, see Considerations for Direct Routing.

- If a Teams client for a United States Calling Plan user dynamically acquires an emergency address within the United States, that address is used for emergency routing instead of the registered address, and the call will be automatically routed to the PSAP in the serving area of the address.
- If a Teams client for a United States Calling Plan user doesn't dynamically acquire an emergency address within the United States, then the registered emergency address is used to help screen and route the call. However, the call will be screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.
In the United States, you must configure the civic address that is part of the emergency locations that are assigned to network identifiers—and include the associated geo codes. For more information, see **Plan and configure dynamic emergency calling** below.

### Emergency call routing for Teams Calling Plans

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

**In Japan**, emergency calling isn't supported.

### Emergency call enablement and configuration for Direct Routing

You must define emergency calling policies for Direct Routing users by using a Teams emergency call routing policy (TeamsEmergencyCallRoutingPolicy) to define emergency numbers and their associated routing destination. (Be aware that registered emergency locations aren't supported for Direct Routing users.)

You can assign an emergency call routing policy to a Teams Direct Routing user account, a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located as follows:

- If an emergency call routing policy is associated with the site, then the site policy is used to configure emergency calling.
- If there is no emergency call routing policy associated with the site, or if the client is connected at an undefined site, then the emergency call routing policy associated with the user account is used to configure emergency calling.
- If the Teams client is unable to obtain an emergency call routing policy, then the user is not enabled for emergency calling.

### Dynamic emergency calling for Direct Routing

Teams clients for Direct Routing users can acquire a dynamic emergency address, which can be used to dynamically route calls based upon the location of the caller. For more information, see **Plan and configure dynamic emergency calling** below.

### Plan and configure dynamic emergency calling

Dynamic emergency calling for Teams Calling Plans and Direct Routing provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client.

Based on the network topology that the tenant administrator defines, the Teams client provides network connectivity information in a request to the Location Information Service (LIS). If there's a match, the LIS returns a location to the client. This location data is transmitted back to the client.
The Teams client includes location data as part of an emergency call. This data is then used by the emergency service provider to determine the appropriate Public Safety Answering Point (PSAP) and to route the call to that PSAP, which allows the PSAP dispatcher to obtain the caller's location.
For dynamic emergency calling, the following must occur:

1. The network administrator configures network settings and the LIS to create a network/emergency location map.

   For Direct Routing, additional configuration is required for routing emergency calls and possibly for partner connectivity. The administrator must configure connection to an Emergency Routing Service (ERS) provider (United States) OR configure the Session Border Controller (SBC) for an Emergency Location Identification Number (ELIN) application.

1. During startup and periodically afterwards, or when a network connection is changed, the Teams client sends a location request that contains its network connectivity information to the network settings and the LIS.

    - If there's a network settings site match – emergency calling policies are returned to the Teams client from that site. (For more information about policies, see Configure emergency policies below.

    - If there's an LIS match – an emergency location from the network element the Teams client is connected to is returned to the Teams client. The match is performed in the following order with the first matched result being returned:
      - WAP
      - Ethernet switch/port
      - Ethernet switch
      - Subnet

1. When the Teams client makes an emergency call, the emergency location is conveyed to the PSTN network.

   For Direct Routing, the administrator must configure the SBC to send emergency calls to the ERS provider or configure the SBC ELIN application.

#### Supported clients

The following clients are currently supported. Check back often to see updates to this list.

- Teams desktop client for Microsoft Windows
- Teams desktop client for Apple macOS
- Teams mobile client for Apple iOS client version 1.0.92.2019121004 and App Store version 1.0.92 and greater
- Teams mobile client for Android client and Google Play store version 1416/1.0.0.2019121201 and greater
- Teams phone version 1449/1.0.94.2019110802 and greater
- Teams Rooms version 4.4.25.0 and greater

  > [!NOTE]
  > Dynamic emergency calling including security desk notification isn't supported on the Teams web client. To prevent users from using the Teams web client to call PSTN numbers, you can set a Teams calling policy and turn off the **Allow web PSTN calling** setting. To **Additional resources**, see **Calling policies in Teams and Set-CsTeamsCallingPolicy** both found in the Learning More section below.

#### Assign emergency addresses

You can assign emergency addresses to both Calling Plan users and to the network identifiers that are required for dynamically obtaining a location. (Subnet and WiFi AP are supported. Ethernet switch/port is supported on Windows 8.1 and later at this time).

To support automated routing of emergency calls within the United States, you must ensure that the emergency locations that are assigned to network identifiers include the associated geo codes. (Emergency addresses without geo codes can't be assigned to the network identifiers that are required for dynamic locations.)

Azure Maps is used for location-based services. When you enter an emergency address by using the Microsoft Teams admin center, Teams checks Azure Maps for the address:

- If a match is found, the geo codes are automatically included.
- If a match isn't found, you'll have the opportunity to manually create an emergency address. You can use the PIN drop feature to do this.

This means that if an existing emergency location that is created for assigning to Calling Plan users is intended for a dynamic location; the same address needs to be re-created to include the geo codes. To distinguish between the two locations, you should include a different description. The new emergency location can be assigned to the users who have the old location. When fully migrated, the old location can be deleted.

You add and assign emergency addresses in the Microsoft Teams admin center or by using PowerShell. For more information, see Add an emergency location for your organization and Assign an emergency location for a user; both located in the **Additional resources** section in the Summary.

#### Configure network settings

Network settings are used to determine the location of a Teams client, and to dynamically obtain emergency calling policies and an emergency location. You can configure network settings according to how your organization wants emergency calling to function.

Network settings include sites that include a collection of subnets and these are used exclusively for dynamic policy assignment to users. For example, an emergency calling policy and an emergency call routing policy might be assigned to the "Redmond site" so that any user that roams from home or another Microsoft location is configured with emergency numbers, routing, and security desk specific to Redmond.

> [!NOTE]
> Subnets can also be defined in LIS and can be associated with an emergency location.

Keep the following definitions in mind. For more information, see **Network settings for cloud voice features** in the **Additional resources** section in the Summary.

- Trusted IP addresses contain a collection of the internet external IP addresses of the enterprise network and are used to determine if the user's endpoint is inside the corporate network. An attempt to obtain a dynamic policy or location will only be made if the user's external IP address matches an IP address in the trusted IP address. A match can be made against either IPv4 or IPv6 IP addresses and is dependent upon the format of the IP packet sent to the network settings. (If a public IP address has both IPv4 and IPv6, you need to add both as trusted IP addresses.)
- A network region contains a collection of network sites.
- A network site represents a location where your organization has a physical value, such as an office, a set of buildings, or a campus. These sites are defined as a collection of IP subnets.
- A network subnet must be associated with a specific network site. A client's location is determined based on the network subnet and the associated network site.

You configure network settings in the Microsoft Teams admin center or by using PowerShell. To **Additional resources**, see **Manage your network topology for cloud voice features in Microsoft Teams** in the **Additional resources** section in the Summary.

It can take some time (up to a couple of hours) for some changes to network settings (such as a new address, network identifier, and so on) to propagate and be available to Teams clients.

**For Calling Plan users:**

- If dynamic configuration of security desk notification is required, you must configure both trusted IP addresses and network sites.
- If only dynamic locations are required, you must configure only trusted IP addresses.
- If neither are required, configuring network settings isn't required.

**For Direct Routing users:**

- If dynamic enablement of emergency calling or dynamic configuration of security desk notification is required, then you must configure both Trusted IP addresses and network sites.
- If only dynamic locations are required, you must configure only trusted IP addresses.
- If neither are required, configuring network settings isn't required.

#### Configure Location Information Service

A Teams client obtains emergency addresses from the locations associated with different network identifiers. Both subnets and wireless access points (WAPs) are supported. Ethernet switch/port is supported on Windows 8.1 and later at this time.

For a client to obtain a location, you must populate the LIS with network identifiers (subnets, WAPs, switches, ports) and emergency locations. You can do this in the Microsoft Teams admin center or by using PowerShell.

#### Using the Microsoft Teams admin center

1. In the left navigation, go to **Locations** > **Networks & locations**.
1. Select the tab that represents the network identifier that you want to add. For example, select **Subnets, Wi-Fi access points, Switches**, or **Ports**. Then select Add.
1. Complete the fields, add an emergency location, and then select **Apply**.

    :::image type="content" source="../media/4-network-and-locations-inline.png" lightbox="../media/4-network-and-locations-expanded.png" alt-text="Porting Wizard – Adding account information.":::

#### Using PowerShell

Use the following cmdlets to add ports, switches, subnets, and WAPs to the LIS.

- Get, Set, Remove -CsOnlineLisSubnet
- Get, Set, Remove -CsOnlineLisPort
- Get, Set, Remove -CsOnlineLisWirelessAccessPoint
- Get, Set, Remove -CsOnlineLisSwitch

> [!IMPORTANT]
> If subnets are being used as part of network sites, they must be redefined in the Location Information Service to render dynamic locations.

#### Configure emergency policies

Use the following policies to configure emergency calling. You can manage these policies in the Microsoft Teams admin center or by using PowerShell.

- **Emergency call routing policy** – Applies only to Direct Routing. This policy configures the emergency numbers, masks per number if desired, and the PSTN route per number. You can assign this policy to users, to network sites, or to both. (Teams Calling Plans clients are automatically enabled for emergency calling with the emergency numbers from the country based upon their Microsoft 365 or Office 365 usage location.) To **Additional resources**, see Manage emergency call routing policies for Direct Routing.

- **Emergency calling policy** - Applies to Teams Calling Plans and Direct Routing. This policy configures the security desk notification experience when an emergency call is made. You can set who to notify and how they are notified. For example, to automatically notify your organization's security desk and have them listen in on emergency calls. This policy can either be assigned to users or network sites or both. To **Additional resources**, see Manage emergency calling policies in Teams.

#### Enable users and sites

You can assign emergency call routing policies and emergency calling policies to users and to sites. Keep in mind that emergency call routing policies apply to Direct Routing only. (Although it's possible to assign this policy to a Calling Plan user, the policy will have no effect.)

You assign policies in the Microsoft Teams admin center or by using PowerShell.

Here's some PowerShell examples.

To enable a specific user for security desk notification, use the following command:

```powershell
Grant-CsTeamsEmergencyCallingPolicy -Identity user1 -PolicyName SecurityDeskNotification
```

To assign a policy called "Contoso Emergency Calling Policy 1" to Site 1, use the following command:

```powershell
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallingPolicy "Contoso Emergency Calling Policy 1"
```

To enable a specific Direct Routing user for emergency calling, use the following command:

```powershell
Grant-CsTeamsEmergencyCallRoutingPolicy -Identity user1 -PolicyName UnitedStates
```

To assign a policy called "Contoso New York Emergency Call Routing" to Site 1, use the following command:

```powershell
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallRoutingPolicy "Contoso New York Emergency Call Routing"
```

If you assigned an emergency calling policy to a network site and to a user, and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.

#### Test emergency calling

Some Emergency Routing Service Providers (ERSPs) in the United States offer an emergency calling test bot.

- Calling Plan users in the United States can use the predefined test emergency number 933 to validate their emergency calling configuration. This number is routed to a bot, which then echoes back the caller phone number (calling line ID), emergency address or location, and whether the call would be automatically routed to the PSAP or screened first.
- Direct Routing customers in the United States should coordinate with their ERSP for a test service.

### Emergency call routing for Direct Routing

The emergency call routing policy references an online PSTN usage, which must have the appropriate Direct Routing configuration to properly route the emergency calls to the appropriate PSTN gateway(s). In particular, you must ensure that there is an OnlineVoiceRoute for the emergency dial string. For more information, see Configure Direct Routing in the **Additional resources** section in the Summary.

>[!NOTE]
>Teams clients prepend the "+" sign in front of emergency numbers in a similar manner that Skype for Business client does; that is, +911.

The ability to dynamically route emergency calls for Direct Routing users varies depending on the emergency calling network within a given country. There are two solutions available:

- Emergency Routing Service Providers (US only)
- Emergency Location Identification Number (ELIN) gateway applications

### Emergency Routing Service Providers for Direct Routing

In the United States, there are numerous certified Emergency Routing Service Providers (ERSPs) that can automatically route emergency calls based upon the location of the caller.

- If an Emergency Routing Service Provider is integrated into a Direct Routing deployment, emergency calls with a dynamically acquired location will be automatically routed to the Public Safety Answering Point (PSAP) serving that location.
- Emergency calls without a dynamically acquired location are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center based upon the updated location.

### Emergency Location Identification Number (ELIN) applications for Direct Routing

Session Border Controllers (SBCs) can include Emergency Location Identification Number (ELIN) applications. If an SBC ELIN application is integrated into a Direct Routing deployment, you must configure the emergency addresses and associated telephone numbers in the ELIN application, and then upload the ELIN records to the emergency calling database in the respective PSTN. Teams emergency locations with an ELIN identifier must match those within the ELIN application.
When an emergency call with a dynamically acquired location is routed to the appropriate SBC, the ELIN application:

- Parses the emergency location of the caller.
- Matches the location to an ELIN record.
- Substitutes the emergency caller's number with the ELIN phone number.
- Routes the call to the PSAP serving that location, and then the dispatchers obtain the location from the uploaded ELIN record.

Upon a callback to the emergency number, the ELIN application will do the reverse called number substitution to that of the original emergency caller.

## Security desk notification

Security desk notification is available with both Teams Calling Plans and Direct Routing.

You use a Teams emergency calling policy (TeamsEmergencyCallingPolicy) to configure who should be notified during an emergency call and how they are notified: chat only, conferenced in and muted, or conferenced in and muted but with the ability to unmute. You can also specify an external PSTN number of a user or group to call and join the emergency call.

An emergency calling policy can be granted to a Teams user account, assigned to a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If an emergency calling policy is associated with a network site, then the site policy is used to configure security desk notification.
- If there is no emergency calling policy associated with the site, or if the client is connected at an undefined site, then the emergency calling policy associated with the user account is used to configure security desk notification.
- If the Teams client is unable to obtain an emergency calling policy, then the user is not enabled for security desk notification.

During an emergency call, a security desk is conferenced into the call and the experience of the security desk user is controlled based upon the Teams emergency calling policy. A group chat is started with each security desk member, and the location of the emergency caller is shared via an important message notification. If a conference option is configured as part of the policy, each security desk user is additionally called as part of the conference.

For more information, see **Manage emergency calling** in the **Additional resources** section below
