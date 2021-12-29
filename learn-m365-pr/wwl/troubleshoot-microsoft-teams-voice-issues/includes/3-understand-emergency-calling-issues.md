Dynamic emergency calling is used by Microsoft Calling Plans and Phone System Direct Routing to enable emergency calls to be routed to the emergency services. As part of the call, The Teams client also includes location data. 

## Configure emergency calling

To configure dynamic emergency calling:
1.	First, check the supported clients for emergency calling.
2.	Assign emergency addresses. In the, from the left navigation select Locations > Emergency addresses.  Enter a location name and description. Select the country or region and the find the address or edit the address manually. Select Save. 
3.	The network administrator must configure the network settings and Location Information Service (LIS). The LIS returns the location, which is then sent as part of the emergency call. Direct Routing requires the session border controller to be configured to send calls to the Emergency Routing Service (ERS) provider. If you have an emergency location identification number (ELIN) application integrated with your Direct Routing deployment, you also need to associate the emergency addresses with telephone numbers. 
4.	Configure Location Information Service using the Microsoft Teams admin center or using PowerShell scripts. In the Teams admin center, in the left navigation, go to Locations > Networks & locations. You can then select a network identifier to add, such as a Subnet, Wi-Fi access points, Switches, or Ports. Complete the fields, add an emergency location, and select Apply. 
5.	Enable users and sites. Finally, assign emergency call routing policies and emergency calling policies. 

## Test emergency calling
For users located in the United States, some Emergency Routing Service Providers (ERSPs) provide a bot for testing emergency calls.

- Calling Plan users in the United States can use the predefined test emergency number 933 to validate their emergency calling configuration. This number is routed to a bot, which then echoes back the caller phone number (calling line ID), emergency address or location, and whether the call would be automatically routed to the PSAP or screened first.
- Direct Routing customers in the United States should coordinate with their ERSP for a test service.

### Troubleshoot emergency calling
Before troubleshooting emergency calling issues, always check that the client’s public IP address is added to the tenant trusted IP list. 
If you use Phone System Direct Routing and the error message "Update the TeamsEmergencyCallRouting Policy to avoid emergency call failures" is displayed, you need to update your Teams Emergency Call Routing policy. Previously, a ‘+’ was inserted before a dialed number but this was changed so that the number is sent as dialed. Update your Teams Emergency Call Routing policy to reflect this change. 
Also, check the session border controller logs. This will verify that calls are being routed to the correct SBC.

### Troubleshoot missing locations
If the dynamic emergency address is missing in Teams client settings, check the following:

- You have configured the Dynamic Emergency Address, but it is missing in **Teams Client Settings > Calls**. Check whether your organization uses both IPv6 and IPv4 IP addresses. If you are using both, enter both IPv6 and IPv4 addresses in the tenant trusted IP list. IPv6 is usually preferred, but it is recommended that both are added.
- If you’ve recently changed your network settings, and location data is not visible, it may have not yet propagated to the Teams client. It can take a couple of hours for network setting changes to appear in Teams clients.
- Check that the user has a correctly assigned E911 address with geo coordinates. Check that it has been marked as “validated”. Validation is a safety feature to ensure the address is correct. It cannot be modified after it has been assigned.

### Troubleshoot emergency phone normalization rules 

The order in which normalization rules are listed in a tenant dial plan is important. The dialed number will be matched to the logic in the first rule, and if a match is made all other normalization rules will be ignored. Only if there is not a match will the second rule be applied.

You can also use the PowerShell **Get-CsEffectiveTenantDialPlan** cmdlet to understand which tenant dial plan normalization rules are applicable to a specific user. This cmdlet takes the user’s identity as the input parameter. For example. The following returns the effective tenant dial plan for Vt1_User1.

**Get-CsEffectiveTenantDialPlan -Identity Vt1_User1**

### Troubleshoot dial mask issues 
A dial mask enables a number to be dialed, and then translated into the emergency services number. This allows users to dial numbers that are familiar to them, whilst still reaching emergency services. For each emergency number, you can specify zero or more emergency dial masks.  Dial masks are defined within emergency call routing policies.

As an example, if you add 112 as the emergency dial mask, which is the emergency service number for most of Europe, and 911 as the emergency dial string. A Teams user from Europe who is visiting may not know that 911 is the emergency number in the United States. When they dial 112, the call is automatically made to 911. To define multiple dial masks, separate each value by a semicolon. For example, 112;212.

When troubleshooting dial mask issues, do not add a ‘+’ prefix to your numbers. Also, remember that the Service Country dial plan is merged with user dial plans. User dial plans should only contain dial masks not contained in the Service dial plan. 

## Troubleshoot missing addresses and locations in outbound calls 

### Missing locations in outbound emergency calls

If you are missing the location in outbound emergency calls, check that you have a geo code (latitude and longitude) associated with it. Geo codes are used in routing emergency calls in some countries.

### Defining locations using PowerShell doesn’t work

In Microsoft Teams admin center, create emergency addresses for Calling Plan by using the map search feature. This ensures that the addresses are formatted, validated, and are associated with the correct geo code.
