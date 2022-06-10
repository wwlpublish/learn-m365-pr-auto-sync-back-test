
Before you can enable Direct Routing for users, you'll need to have configured it at the organization level. This will include configuring an on-premises Session Border Controller (SBC) or use settings provided by a telephony provider that offers a Direct Routing service. Followed by configuring voice routing, emergency calling, and if necessary, high-availability functionality.

After configuring your organization to support Direct Routing, you will then need to perform the following tasks to enable functionality for users:

1. Assign required licenses for Teams with Direct Routing

1. Enable a user for enterprise voice services

1. Assign a telephone number to a user

1. Enable voicemail for a user

1. Assign a voice routing policy to a user

## Assign Teams Licenses

To use Direct Routing, you'll first need to assign the following licenses to a user:

- Microsoft Teams

- Microsoft Teams Phone

- Skype for Business Plan 2

- Optionally, Audio Conferencing, or Audio Conferencing Pay Per Minute

These licenses are including in Microsoft Enterprise E5 (with Teams Phone) and Microsoft Business Voice SKUs.

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

You will typically enable Teams Phone functionality and assign a number available to you from your voice provider. As you enable Teams Phone for a user, voicemail will be automatically enabled at the same time.

To enable a user for Teams Phone functionality and assign a Microsoft Calling Plan phone number, use the following cmdlet:

```powershell
Set-CsPhoneNumberAssignment -Identity "<User name>" -PhoneNumber "<phone number>" -PhoneNumberType CallingPlan

```

Supports E.164 format like +12065551234 and non-E.164 format like 12065551234. The phone number can't have "tel:" prefixed.

Direct Routing numbers with extensions using the formats +1206555000;ext=1234 or 1206555000;ext=1234 are supported, but such phone numbers can't be assigned to a resource account.

The example below shows how to assign  Direct Routing number with a unique extension to the user:

```powershell
Set-CsPhoneNumberAssignment -Identity "spencer.low@contoso.com" -PhoneNumber "+14255551234;ext=1001" -PhoneNumberType DirectRouting

```

The following cmdlet shows how to assign the same number with a different extension to another user:

```powershell
Set-CsPhoneNumberAssignment -Identity "stacy.quinn@contoso.com" -PhoneNumber "+14255551234;ext=1002" -PhoneNumberType DirectRouting

```

If a user or resource account has a phone number set in Active Directory on-premises and synched into Microsoft 365, you can't use Set-CsPhoneNumberAssignment to set the phone number. You will have to clear the phone number from the on-premises Active Directory and let that change sync into Microsoft 365 first. Then enable the user for enterprise voice services and voicemail using the following cmdlet:

```powershell
Set-CsPhoneNumberAssignment -Identity "<User name>" -EnterpriseVoiceEnabled $true

```

## Assign a voice routing policy

After configuring a phone number for the user and enabling the user for voicemail, you will then assign a voice routing policy to the user. This policy allows the user to dial out and receive calls by associating them with specific Direct Routing configuration:

```powershell
Grant-CsOnlineVoiceRoutingPolicy -Identity "<User name>" -PolicyName "No Restrictions”

```

