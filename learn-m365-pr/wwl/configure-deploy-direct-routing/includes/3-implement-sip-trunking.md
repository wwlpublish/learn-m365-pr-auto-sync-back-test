There are multiple ways of implementing a Direct Route. One is to obtain a SIP Trunk directly from a SIP Trunk provider and they host the SBC on your behalf.  The other method also outlined in this module is to implement an SBC or SBA and then interface to the SIP trunk. Organizations will use a SIP trunk from an organization should they want to simplify the installation and have no requirement for a Session Border Controller. SIP Trunk providers will supply the SBC as part of the service and is a simplified way of doing things. The reason why you would choose an SBC is to provide more granularity and control, to provide linkage to third-party applications such as contact center and compliance recording, or if you want to manage the migration seamlessly from one solution to another while keeping the SBC upstream from Teams and the existing telephone system.

> [!NOTE]
> SIP trunk provider's tenant is used when doing direct route to the SIP trunk providers SBC.  The SIP trunk provider's domain must be added to the domain for it to function properly. 

## Add a domain

Before you can continue configuring your Direct Routing setup, you must make sure you have your desired custom domains added to your tenant. Without a custom domain in your tenant, you will not be able to accept the signaling and will ultimately reject the information from the SIP trunk provider.  If you didn't already do this, follow these steps to add, set up, or continue setting up a custom domain in your tenant.

### Verify global admin rights

You can only add new domains if you signed into the Microsoft 365 admin center as a Global Administrator. 

To validate the role you have, sign into the Microsoft 365 admin centre ([https://portal.office.com](https://portal.office.com/)), go to Users > Active Users, and then verify that you possess the Global Administrator role. 

### Add the SBC domain and verify

Perform the following steps to add a new custom domain to your tenant:
1. Navigate to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com/).

1. Select **Show all**, open **Settings** and select **Domains**.

1. Select **Add domain** to add a new domain. 

1. On the **Add a domain** page, enter the FQDN of the SBC provided by SIPCOM in your information pack. 

1. Select **Use this domain**. 

1. In the next step, you will need to verify the domain. Select **Add a TXT record instead.** 

1. Select **Next** and note the TXT value generated to verify the domain name. 

1. Provide the details to sip trunk provider and await confirmation the TXT records have been added before continuing. 

1. Once sip trunk provider has provided confirmation the TXT record has been created, select **Verify**. 

1. On the next page make, make sure to uncheck all the options and select **Continue**. 

1. Once you completed adding the domain select **Done**. 

There must be a user for every domain in which is a trusted domain. After you register the domain names, you need to activate it by adding at least one user for each domain. These will need to have the newly added domain after the @ see below for an example.

For example: [test@sbc1.customers.adatum.biz](mailto:test@sbc1.customers.adatum.biz) 

The user’s created for each domain would need a single E3 / E5 license assigned to activate the domain. Once the domain is activated then the license can be removed from each respective user.

> [!IMPORTANT]
> Do not delete these accounts for the duration of your Teams direct routing service.

## Office 365 Voice Routing

Office 365 voice routing is comprised of three configuration items: voice routing policy, PSTN usage, and voice route.

- **Voice Routing Policy**: This item is granted to users (via the Grant-CsOnlineVoiceRoutingPolicy cmdlet) and dictates what calls the user can make.

- **PSTN Usage**: Global configuration item to map a voice routing policy to a voice route.  It serves no other purpose.

- **Voice Route**: Voice routes, based on a number pattern to match (using regular expressions), route calls to a specified gateway (in the OnlinePstnGatewayList array).  There are also priority options to control which routes should be higher priority than others; this is useful for failover configuration.

## Customer tenant SBC pairing

Most sip trunk providers provide a pair of Session Border Controllers (SBCs) the SBCs will be configured independently within the PowerShell to update the configuration.

In the context of an Office 365 Customer Teams tenant, pairing allows the Office 365 Customer Teams tenant administrator to include an SBC path in their routing configuration for outgoing calls. It also allows the Teams Core to find the correct Office 365 Customer Teams tenant destination for call delivery of incoming calls. Ultimately the SBC Pairing provides disaster recovery and load balancing.

### Create a new usage

Online PSTN usages are string values that are used for call authorization. An online PSTN usage links an online voice policy to a route. The Set-CsOnlinePstnUsage cmdlet is used to add or remove phone usages to or from the usage list. This list is global so it can be used by policies and routes throughout the tenant.

You create a new usage by using the **Set-CsOnlinePstnUsage** command in PowerShell, with the following parameters:

- **Identity** - The scope where these settings should be applied. It's always set to global.

- **Usage** - The name of the usage. For example, @{Add= "UnrestrictedPSTNUsage"} means that you want to add a usage named "UnrestrictedPSTNUsage".

You configure a single usage to cover all locations call routing by running the following command from the Microsoft Teams PowerShell module or through the GUI as in the Design Direct Routing call flows section:

```powershell
Set-CsOnlinePstnUsage -Identity Global -Usage @{add="UnrestrictedPstnUsage"}

```

With this command, you've configured a usage for all local or international numbers, which means you don't restrict calling into the PSTN.

### Create multiple voice routes

You then create multiple voice routes and associate them with all local and international usage. In this example, you will create a voice route for making calls to the US offices and use "sbc1.siptrunkprovider.com" for the SBC and set the route to priority one.  This is different to previous sections of this module in that we are providing a high availability configuration of multiple SBCs that can be used to allow inbound and outbound calling should it be required.

After you've created a usage, you associate it with a voice route. You create a voice route using the **New-CsOnlineVoiceRoute** command from the Microsoft Teams PowerShell module, with the following parameters:

- **Identity** - The name of the route. This can be the same name as the usage

- **NumberPattern** - Number patterns to match. You can use “.*” to match all number patterns.

- **OnlinePstnGatewayList** - The name of your SBC.

- **Priority** - The priority position of this route should have.

- **OnlinePstnUsages**- The usage you want to associate with this voice route.

```powershell
New-CsOnlineVoiceRoute -Identity "UnrestrictedPstnUsage" -NumberPattern ".*" -OnlinePstnGatewayList sbc1.siptrunkprovider.com -OnlinePstnUsages "UnrestrictedPstnUsage"

```

This cmdlet defines how/where calls with matching number patterns are routed. The example shown will route all numbers the same way.

### Create a voice routing policy

For the final step, you create a voice routing policy and link it with your usage:

```powershell
New-CsOnlineVoiceRoutingPolicy "No Restrictions" -OnlinePstnUsages "UnrestrictedPstnUsage"

```

### Assign voice routing policy

For the final step, assign the policy to a user by using the following cmdlet:

```powershell
Grant-CsOnlineVoiceRoutingPolicy -Identity Ken Myer -PolicyName "No Restrictions”

```

### User Configuration and assign telephone number

The user you assigned the voice routing policy to also needs to have a phone number assigned. You will learn about that in a later module.

When you're done, you've successfully configured the SIP trunk into Microsoft Teams, enabled users for the sip service, and assigned a telephone number to the end user.

## Confirm domain is activated

With the user account created, Microsoft 365 needs to update the domain URL map before the remaining configuration can be completed.

You can do this via the Microsoft Teams PowerShell module by using the following cmdlet, to validate the domain URL map:

```powershell
Get-CsTenant | select DomainUrlMap

```

View the results and ensure the SBC domain is present.  If the domain is not present retry again in 60 minutes.

