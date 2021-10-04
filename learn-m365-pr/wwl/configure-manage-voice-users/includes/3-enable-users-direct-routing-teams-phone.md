
Before you can enable Direct Routing for users, you'll need to have configured it at the organization level. This will include configuring an on-premises Session Border Controller (SBC) or using settings provided by a telephony provider offering a Direct Routing service, and then configuring voice routing, emergency calling, and if required, high-availability functionality. These configuration tasks were covered in the earlier module **Configure and deploy Direct Routing**.

After configuring your organization to support Direct Routing, you will then need to perform the following tasks to enable functionality for users:

1. Assign required licenses for Teams with Direct Routing

1. Enable a user for enterprise voice services

1. Assign a telephone number to a user

1. Enable voicemail for a user

1. Assign a voice routing policy to a user

## Assign Teams Licenses

To use Direct Routing, you'll first need to assign the following licenses to a user:

- Microsoft Teams

- Microsoft 365 Phone System

- Skype for Business Plan 2

- Optionally, Audio Conferencing, or Audio Conferencing Pay Per Minute

These licenses are including in Microsoft Enterprise E5 (with Phone System) and Microsoft Business Voice SKUs.

You can use the Microsoft 365 admin center or PowerShell to assign licenses to users in your organization. You must be a Global admin or User management admin to manage licenses.

> [!WARNING]
> After assigning licenses, you will need to wait before assigning numbers to users. Because of the latency between Microsoft 365 and Microsoft Teams, it can take up to 24 hours for a user to be assigned a Calling Plan after you assign a license.

## Enable a user for voice and voicemail services with Direct Routing

After you have assigned the correct licenses, the next step is to configure the user's online phone settings. You'll perform these steps using Teams PowerShell module.

To establish a remote PowerShell session with Teams, you first need to install the Teams PowerShell module.

After you install the module, you can establish a remote session with the following cmdlet:

```powershell
Connect-MicrosoftTeams

```

You will typically enable Enterprise Voice functionality and assign a number available to you from your voice provider. As you enable this for a user, you can also enable voicemail at the same time.

To enable a user for Enterprise Voice functionality, configure a phone number for the user and enable voicemail, use the following cmdlet:

```powershell
Set-CsUser -Identity "<User name>" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true -OnPremLineURI tel:<phone number>

```

It's recommended, but not required, that the phone number used is configured as a full E.164 phone number with country/region code.

It is supported to configure phone numbers with extensions, which will be used to look up users when the lookup against the base number returns more than one result. This allows companies to configure phone numbers with the same base number and unique extensions.

The example below shows how to assign a user the number with a unique extension:

```powershell
Set-CsUser -Identity "spencer.low@contoso.com" -OnPremLineURI "tel:+14255388701;ext=1001" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true

```

The following cmdlet shows how to assign the same number with a different extension to another user:

```powershell
Set-CsUser -Identity "stacy.quinn@contoso.com" -OnPremLineURI "tel:+14255388701;ext=1002" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true

```

If the user’s phone number is managed on premises, use on-premises Skype for Business Management Shell or Control Panel to configure the user's phone number. Then enable the user for enterprise voice services and voicemail using the following cmdlet:

```powershell
Set-CsUser -Identity "<User name>" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true

```

## Assign a voice routing policy

After configuring a phone number for the user and enabling the user for voicemail, you will then assign a voice routing policy to the user. This will provide the capability for the user to dial out and receive calls by associating them with specific Direct Routing configuration:

```powershell
Grant-CsOnlineVoiceRoutingPolicy -Identity "<User name>" -PolicyName "No Restrictions”

```

