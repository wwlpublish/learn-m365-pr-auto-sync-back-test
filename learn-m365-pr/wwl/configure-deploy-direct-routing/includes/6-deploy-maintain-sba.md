Occasionally, a customer site using Direct Routing to connect to Microsoft Phone System may experience an internet outage.

Assume that the customer site--called a branch--temporarily cannot connect to the Microsoft cloud through Direct Routing. However, the intranet inside the branch is still fully functional and users can connect to the Session Border Controller (SBC) that is providing PSTN connectivity.

This section of the module describes how to use a Survivable Branch Appliance (SBA) to enable Microsoft Phone System to continue to make and receive Public Switched Telephone Network (PSTN) calls in the case of an outage.

## Prerequisites

The SBA is distributable code provided by Microsoft to SBC vendors who then embed code into their firmware or distribute it separately to have SBA run on a separate VM or hardware.

To get the latest Session Border Controller firmware with the embedded Survivable Branch Appliance, contact your SBC vendor. In addition, the following is required:

- The SBC needs to be configured for Media Bypass to ensure that the Microsoft Teams client in the branch site can have media flowing directly with the SBC.

- TLS1.2 should be enabled on the SBA VM OS.

## Supported Teams clients

The SBA feature is supported on the following Microsoft Teams clients:

- Microsoft Teams Windows desktop

- Microsoft Teams macOS desktop

## How it works

During an internet outage, the Teams client should switch to the SBA automatically, and ongoing calls should continue with no interruptions. No action is required from the user. As soon as the Teams client detects that the internet is up and any outgoing calls are finished, the client will fall back to normal operation mode and connect to other Teams services. The SBA will upload collected Call Data Records to the cloud and call history will be updated so that this information is available for review by the tenant administrator.

When the Microsoft Teams client is in offline mode, the following calling-related functionality is available:

- Making PSTN calls via local SBA/SBC with media flowing through the SBC

- Receiving PSTN calls via local SBA/SBC with media flowing through the SBC

- Hold and Resume PSTN calls.

## Configuration

For the SBA feature to work, the Teams client needs to know which SBAs are available in each branch site, and which SBAs are assigned to the users in that site.

 To connect your SBA to Microsoft Phone System, follow these steps

1. Create the SBAs.

1. Create the Teams branch survivability policy.

1. Assign the policy to users.

1. Register an application for the SBA with Azure Active Directory.

All configuration is done by using Skype for Business Online PowerShell cmdlets. The Teams admin center does not yet support the Direct Routing SBA feature.

Refer to your vendor documentation to configure your SBC.

### Create the SBAs

To create the SBAs, you will use the New-CsTeamsSurvivableBranchAppliance cmdlet from the Microsoft Teams PowerShell module.

This cmdlet has the following parameters:

- **Identity** - The identity of the SBA

- **Fqdn** - The FQDN of the SBA

- **Description** - Free format text

    ```powershell
    New-CsTeamsSurvivableBranchAppliance -identity CPH -Fqdn sba1.contoso.com -Description "SBA 1"
    
    ```

### Create the Teams Branch Survivability Policy

To create a policy, you use the New-CsTeamsSurvivableBranchAppliancePolicy cmdlet.

This cmdlet has the following parameters:

- **Identity** - Identity of the policy

- **BranchApplicanceFqdns** - The FQDN of the SBA(s) in the site

> [!NOTE]
> Note that the policy can contain one or more SBAs.

```powershell
New-CsTeamsSurvivableBranchAppliancePolicy -Identity CPH -BranchApplianceFqdns "sba1.contoso.com","sba2.contoso.com"

```

You can add or remove SBAs from a policy by using the Set-CsTeamsSurvivableBranchAppliancePolicy cmdlet.

For example:

```powershell
Set-CsTeamsSurvivableBranchAppliancePolicy -Identity CPH -BranchApplianceFqdns @{remove="sba1.contoso.com"}

Set-CsTeamsSurvivableBranchAppliancePolicy -Identity CPH -BranchApplianceFqdns @{add="sba1.contoso.com"}

```

### Assign a policy to a user

To assign the policy to individual users, you will use the Grant-CsTeamsSurvivableBranchAppliancePolicy cmdlet.

This cmdlet has the following parameters:

- **Identity** - Identity of the policy

- **PolicyName** - The identity of the policy

```powershell
Grant-CsTeamsSurvivableBranchAppliancePolicy -PolicyName CPH -Identity user@contoso.com

```

You can remove a policy from a user by granting the $Null policy as shown in the next example:

```powershell
Grant-CsTeamsSurvivableBranchAppliancePolicy -PolicyName $Null -Identity user@contoso.com

```

### Register an application for the SBA with Azure Active Directory

To allow different SBAs used within your tenant to read required data from Microsoft 365, you need to register an application for the SBA with Azure Active Directory.

You only need to register one application for use by all the SBAs in your tenant.

For the SBA registration, you need the following values created by the registration:

- Application (client) ID

- Client secret

For the SBA application, keep the following in mind:

- The name can be whatever you decide.

- Supported account types = Account in this organizational directory only.

- The Web Redirect Uri = [https://login.microsoftonline.com/common/oauth2/nativeclient](https://login.microsoftonline.com/common/oauth2/nativeclient).

- Implicit grant tokens = Access tokens and ID tokens.

- API permissions = Skype and Teams Tenant Admin Access -> Application permissions -> application_access_custom_sba_appliance.

- Client secret: you can use any description and expiration.

- Remember to copy the client secret immediately after creating it.

- The Application (client) ID is shown on the Overview tab.

Then configure a SBA to Azure AD follow these steps:

- Register the application.

- Set the implicit grant tokens.

- Set the API permissions.

- Create the client secret.

