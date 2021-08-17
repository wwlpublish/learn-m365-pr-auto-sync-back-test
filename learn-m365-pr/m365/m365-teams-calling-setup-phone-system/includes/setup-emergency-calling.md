Users in your organization might need to make emergency calls at any point in time. With Phone System's emergency calling capabilities, you can decide what happens when users in your organization make emergency calls.  For example, you can ensure that a security team is notified when an emergency call is made.

In this unit, you'll learn about how you to set up emergency calling for your organization.

## Manage emergency addresses

To implement emergency calling, you should understand the following concepts:

- **Emergency address** -  A physical address of a place of business for the organization. For example, 123 South Corner Street, Redmond, WA, 98052.
- **Place** -  Refers to a building, floor, or wing. This is associated with the emergency address to provide a more precise location within a building.
- **Emergency location** -  A civic address, along with an optional place. If your organization has more than one physical locations, you'll probably require more than one emergency location. For each emergency address you create, a unique location ID is automatically generated for it.
- **Registered address** -  An emergency address assigned to a Calling Plan user. Sometimes this referred to as an address of record, or a static emergency address. This is not supported if you're using Direct Routing.

> [!NOTE]
> Depending on whether you're using Teams Calling Plans or Direct Routing, there are some considerations you'll need to be aware of for emergency calling. Use the **Considerations for Calling Plans** and **Considerations for Direct Routing** links in the **Learn more** section for more information.

### Emergency address validation

Before you can assign emergency addresses to your users or network identifiers (such as subnets), you'll need to make sure that the emergency address is marked as **validated**. This way, you can make sure that the address is legitimate, and that it can't be changed after it has been assigned.

You can define emergency addresses using PowerShell and the Teams admin center. However, the admin center provides another benefit. When you define an emergency address using the address search feature in Microsoft Teams admin center, the address is automatically marked as validated. Once an address has been validated, you can't modify it. For example, if a street name or number has changed you'll need to create a new address to reflect those changes.

### Emergency address geo codes

An emergency address can have a geo code, which consists of latitude and longitude values. These are used in some countries to help with routing emergency calls with dynamic locations.

When you define an emergency address using the address search feature in the Microsoft Teams admin center, a geocode will automatically be generated for the address.  Alternatively, you can use PowerShell to link geo codes with addresses, but using the Teams admin center will ensure your address is formatted, validated, and has the appropriate geo codes linked to it.

### Add an emergency location for your organization

You can add an emergency location using either the Teams admin center or through PowerShell. For instance, to add a new emergency location using PowerShell, you can run the **New-CsOnlineLisCivicAddress** cmdlet.

```PowerShell
New-CsOnlineLisCivicAddress -HouseNumber 1031 -StreetName Greenstreet -StreetSuffix Street -PostDirectional NE -City Redmond -StateorProvince Washington -Country US -PostalCode 98052 -Description "Headquarters" -CompanyName Contoso
```

You use the different parameters such as **-StreetName** or **-PostalCode**, to specify the relevant details of your address.

> [!NOTE]
> Exactly when you add emergency locations, varies between countries and regions. For example, if your organization is located in the United States, you associate emergency locations when you assign phone numbers to users. In the UK this would be done when you get the phone numbers from your service provider, from Office 365, or Microsoft 365.

### Add a place for an emergency location

You can add a place using either the Teams admin center or through PowerShell. For instance, you can add a new place using PowerShell by running the **New-CsOnlineLisLocation** cmdlet:

```PowerShell
New-CsOnlineLisLocation -CivicAddressId b78gg9ab-br33-5ec4-7d51-0e14459hc3 -Location "Office 01, 1st Floor"
```

You use the **-CivicAddressId** parameter to specify the ID for the address you want to add a place for, which you can get using the **Get-CsOnlineLisCivicAddress**.

### Assign an emergency location and place

You can assign an emergency location and place using either the Teams admin center or PowerShell. For example, you can use the **Set-CsOnlineVoiceUser** cmdlet to assign an emergency location and place for a user:

```PowerShell
Set-CsOnlineVoiceUser -Identity bsmith@contoso.com -LocationID c7c5a17f-00d7-47c0-9ddb-3383229d606b
```

You provide the following parameters:

| Parameter  |Description  |
|---------|---------|
| **Identity**     | The ID of the user        |
| **LocationID**     |  The ID of the emergency location to assign. Can get fetched using **Get-CsOnlineLisLocation**. This includes the place you've specified already  |

## Security desk notification

You might want your security desk to be notified of emergency calls. You can take advantage of security desk notifications for emergency calls. You use Teams emergency calling policies to configure notification rules, such as who should be notified, and how.  Through emergency calling policies, you can ensure that a group chat is started with each security desk member, and that emergency caller's location is shared through an important notification message. Alternatively, you can also configure a policy that ensures that each security desk member is dialed into a conference. You create and manage emergency calling policies using either the Microsoft Teams admin center or PowerShell.  

### Create custom emergency calling policies

Emergency calling policies can be assigned to users or network sites. For users, you can use the existing global (**Org-wide default**) policy to apply emergency calling settings across the board, or you can create a custom policy that will override the global default for its assigned users.  For network sites, you'll have to create a new custom policy. Emergency calling policies assigned to network sites always override the user assigned emergency calling policies. So if a user that is assigned with an emergency calling policy visits a network site that has a different policy, the site's policy is applied.

To create a custom policy using PowerShell, you can run the **New-CsTeamsEmergencyCallingPolicy** cmdlet:

```PowerShell
New-CsTeamsEmergencyCallingPolicy -Identity TestEmergencyCallingPolicy -Description "Test emergency calling policy" -NotificationGroup "security-desk@contoso.com" -NotificationMode NotificationOnly
```

You provide the following parameters:

|Parameter  |Description  |
|---------|---------|
| **Identity**     | Name of your policy        |
| **Description**     | A short description for your policy        |
| **NotificationGroup**     | The email address of the group that should be notified        |
| **NotificationMode** | The notification mode to use can be ConferenceMuted, ConferenceUnmuted if you want to use conference mode |

### Edit custom emergency calling policies

You can also modify existing policies. You can quickly make changes to an existing policy using PowerShell by running the **Set-CsTeamsEmergencyCallingPolicy** cmdlet. For example, to modify the notification group for a policy, you can run the following:

```PowerShell
Set-CsTeamsEmergencyCallingPolicy -Identity TestEmergencyCallingPolicy  -NotificationGroup "new-security-desk@contoso.com "
```

You provide the following parameters:

|Parameter  |Description  |
|---------|---------|
| **Identity**     | The name of the policy you want to modify        |
| **NotificationGroup**     | The new notification group value you want to use        |

### Assign emergency calling policies to users or network sites

After you've created your policies, you can assign them to users individually, through batch assignment for large-scale assignment, or you can assign your policies to network sites.

To assign users to your policy, you can use the **Grant-CsTeamsEmergencyCallingPolicy** cmdlet:

```PowerShell
Grant-CsTeamsEmergencyCallingPolicy -Identity user@contoso.com -PolicyName TestEmergencyCallingPolicy
```

You provide the following parameters:

|Parameter  |Description  |
|---------|---------|
|**Identity**	| The user to assign the policy to |
|**PolicyName**	| The name of the policy you want to assign |

Network sites are associated with network regions, which allows you to assign the same policy across an entire site or region. You can use the **Set-CsTenantNetworkSite** cmdlet to assign your policy to a network site:

```PowerShell
Set-CsTenantNetworkSite -Identity "ContosoSite1" -NetworkRegionID "RegionWashington" -Description "Main Contoso site" 
```

|Parameter  |Description  |
|---------|---------|
|**Identity**	| Identifier for your network site |
|**NetworkRegionID**	| Identifier for the network region that the network site is associated with |
|**Description**	| Description of the network site |

### Create emergency call routing policies

If you have deployed Phone System with Direct Routing, you can take advantage of emergency call routing policies. Emergency call routing policies help you determine whether enhanced emergency services should be enabled for users, how calls should be routed, and which numbers should be used to call emergency services (such as 911 for the United States).

Emergency call routing policies can be assigned to users or network sites. For users, you can use the existing global (**Org-wide default**) policy to apply settings across the board, or you can create a custom policy that will override the global default for its assigned users.  For network sites, you'll have to create custom policies. Emergency call routing policies assigned to network sites always override the user assigned emergency call routing policies.

You can manage emergency call routing policies using either the Microsoft Teams admin center or PowerShell. For instance, to create an emergency call routing policy using PowerShell, you can use the **New-CsTeamsEmergencyCallRoutingPolicy** cmdlet:

1. Create a new emergency number object (such as 911, or 112) using the **New-CsTeamsEmergencyNumber** cmdlet:

    ```powershell
    $emergencynumber = New-CsTeamsEmergencyNumber -EmergencyDialString "911" -EmergencyDialMask "111;222" -OnlinePSTNUsage "Local" -CarrierProfile "Local"
     ```

    The parameters you provide are:

    - **EmergencyDialString**: The emergency phone number to use.
    - **EmergencyDialMask**: A number that you want translated into the emergency dial number when it's dialed.
    - **OnlinePSTNUsage**: The online public switched telephone network usage.

1. Create your new emergency call routing policy:

    ```powershell
    New-CsTeamsEmergencyCallRoutingPolicy -Identity "ecrpolicy" -Tenant $tenant -EmergencyNumbers @{add=$emergencynumber} -AllowEnhancedEmergencyServices:$true -Description "test emergency call routing policy"
    ```

    The parameters you provide are:

    - **Identity**: The name for this policy
    - **Tenant**: The appropriate tenant to use
    - **EmergencyNumbers**: The emergency number object to use
    - **AllowEnhancedEmergencyServices**:  whether or not to enable enhanced emergency services

### Edit a custom emergency call routing policy

You can also modify existing policies. You can quickly make changes to an existing policy using PowerShell by running the **Set-CsTeamsEmergencyCallRoutingPolicy**. For example, to temporarily disable enhanced emergency services, you can do the following:

```PowerShell
Set-CsTeamsEmergencyCallRoutingPolicy -Identity "ecrpolicy" -Tenant $tenant -AllowEnhancedEmergencyServices:$false
```

The parameters here specify the following:

|Parameter  |Description  |
|---------|---------|
|**Identity**	|The name of the policy to edit|
|**Tenant**	|The appropriate tenant to use|
|**AllowEnhancedEmergencyServices**	|Set to false to disabled enhanced emergency services|

### Assign emergency call routing policies to user and network sites

After you've created your policies, you can assign them to users individually, through batch assignment for large-scale assignment, or you can assign your policies to network sites.

To assign users to your policy, you can use the **Grant-CsTeamsEmergencyCallRoutingPolicy**:

```PowerShell
Grant-CsTeamsEmergencyCallRoutingPolicy -Identity mgreen@contoso.com -PolicyName ecrpolicy
```

You provide the following parameters:

|Parameter  |Description  |
|---------|---------|
|**Identity**	| The user to assign the policy to|
|**PolicyName**	| The name of the policy you want to assign |

To assign your emergency call routing policy to a network site, you use the **Set-CsTenantNetworkSite** cmdlet:

```PowerShell
Set-CsTenantNetworkSite -identity "ContosoSite" -EmergencyCallRoutingPolicy ecrpolicy
```

You use the **-identity** parameter to specify your target site, and you use the **-EmergencyCallRoutingPolicy** parameter to assign your desired policy.

## Dynamic emergency calling

Dynamic calling enables you to configure and route emergency calls to notify the appropriate Public Safety Answering Point or security team, based on what is the current location of the user's Microsoft Teams client. Dynamic emergency calling is available for both Calling Plan and Direct Routing deployments. At a high level, you can carry out the following steps to configure dynamic emergency calling:

- Check if your clients are supported
- Assign emergency address to users and network identifiers
- Configure network settings to find the location of the user's Teams client and dynamically fetch their emergency location and emergency calling policies
- Configure Location Information Service, by providing it with your network identifiers and emergency locations
- Configure your emergency call routing (available for Direct Routing only) and emergency calling policies
- Enable your users and sites, by assigning the calling policies to them
- Test your emergency calling configuration

Use the **Plan and Configure dynamic emergency calling** link in the **Learn more** section as a step-by-step guide on configuring dynamic emergency calling for both Teams Calling Plans and Direct Routing.

## Learn more

- [Plan and configure dynamic emergency calling](/microsoftteams/configure-dynamic-emergency-calling)
- [Emergency call routing](/microsoftteams/what-are-emergency-locations-addresses-and-call-routing#emergency-call-routing)
- [Configure Direct Routing](/microsoftteams/direct-routing-configure)
- [Considerations for Calling Plans](/microsoftteams/what-are-emergency-locations-addresses-and-call-routing#considerations-for-calling-plans)
- [Considerations for Direct Routing](/microsoftteams/what-are-emergency-locations-addresses-and-call-routing#considerations-for-direct-routing)
