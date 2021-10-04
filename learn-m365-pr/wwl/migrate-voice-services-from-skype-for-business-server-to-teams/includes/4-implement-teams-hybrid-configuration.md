With hybrid connectivity set up, you can have some users homed on-premises in Skype for Business Server and others in Microsoft Teams.

This type of configuration relies on shared session initiation protocol (SIP) address space functionality and is sometimes referred to as "split domain." A split domain configuration means users of a domain are split between using Skype for Business Server on-premises and Teams

To implement a Hybrid relationship between Skype for Business Server and Microsoft Teams, we will need perform several tasks:

1. Configure your on-premises Edge service to federate with Microsoft 365.

1. Configure your on-premises environment to enable shared SIP address space with Microsoft 365.

1. Enable shared SIP address space in your Microsoft 365 tenant.

## Configure your on-premises Edge service to federate with Teams

Federation allows users in your on-premises deployment to communicate with Teams users in your organization. To configure federation, run the following cmdlet in the Skype for Business Server Management Shell:

```powershell
Set-CSAccessEdgeConfiguration -AllowOutsideUsers $True -AllowFederatedUsers $True -EnablePartnerDiscovery $True -UseDnsSrvRouting

```

## Configure your on-premises environment to enable shared SIP address space with Teams

You must also configure your on-premises environment to trust Microsoft Teams and enable a shared SIP address space. This configuration means Teams has the capability to host user accounts for the same set of SIP domains as your on-premises environment, and messages can be routed between users hosted on premises and online.

First, check if you already have a hosting provider with ProxyFqdn=sipfed.online.lync.com. If one exists, then remove it by using the following command in the Skype for Business Server Management Shell:

```powershell
Get-CsHostingProvider | ?{ $_.ProxyFqdn -eq "sipfed.online.lync.com" } | Remove-CsHostingProvider

```

Then create a new hosting provider by using the New-CsHostingProvider cmdlet as follows:

```powershell
New-CsHostingProvider -Identity Office365 -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl [https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root](https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root)

```

## Enable shared SIP address space(s) in your organization

In addition to the change you made in your on-premises deployment, you'll need to make the corresponding change in your Teams organization to enabled shared SIP address space with your on-premises deployment.

To establish a remote PowerShell session with Teams, you first need to install the Teams PowerShell module. The Teams PowerShell module replaces the Skype for Business Online Connector module, which has been retired.

```powershell
Install-Module -Name MicrosoftTeams -Force -AllowClobber

```

After you install the module, you can establish a remote session with the following cmdlets:

```powershell
Import-Module MicrosoftTeams

$credential = Get-Credential

Connect-MicrosoftTeams -Credential $credential

```

To enable shared SIP address space in your organization, run the following cmdlet:

```powershell
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true

```

