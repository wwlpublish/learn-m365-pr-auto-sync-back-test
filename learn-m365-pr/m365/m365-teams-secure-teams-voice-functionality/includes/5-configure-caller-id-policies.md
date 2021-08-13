The Phone System in Microsoft 365 provides a default caller ID that is the user's assigned telephone number. You can either change or block the caller ID (also called a Calling Line ID) for a user. You can learn more about how to use caller ID in your organization by going to the How can caller ID be used in your organization link in the **Learn more** section below.

> [!TIP]
> You can't block incoming calls currently in Skype for Business Online.

There are settings that you can change:

> [!NOTE]
> This **is not** for on-premises organizations with Lync or Skype for Business Server.

- **Change their outgoing caller ID** You can replace a user's Caller ID, which by default is their telephone number, with another phone number. For example, you could change the user's Caller ID from their phone number to a main phone number for your business or change the user's Calling Line ID from their phone number to a main phone number for the legal department. You can change the Calling ID number to any Online service number (toll or toll-free).

  > [!NOTE]
  > If you want to use the Service parameter, you must specify a valid service number.

- **Block their outbound caller ID** You can block the outgoing Caller ID from being sent on a user's outgoing PSTN calls. Doing this will block their phone number from being displayed on the phone of a person being called.

- **Block their incoming caller ID** You can block a user from receiving Caller ID on any incoming PSTN calls.

  > [!IMPORTANT]
  > Emergency calls will always send the user's telephone number (caller ID).

By default, all of these caller ID settings are turned off. This means that the Skype for Business Online user's phone number can be seen when that user makes a call to a PSTN phone.
To learn more about these settings see **How can caller ID be used in your organization** link in the **Learn more** section below.

## Set your caller ID policy settings

> [!NOTE]
> For all of the Caller ID settings in Skype for Business Online, you must use Windows PowerShell and you can't use the Skype for Business admin center.

### Verify and start Windows PowerShell

Ensure that you're running Windows PowerShell version 3.0 or higher:

1. Select **Start Menu** > **Windows PowerShell**.
1. Check the version by typing **Get-Host** in the Windows PowerShell window.
1. If you don't have version 3.0 or higher, you need to download and install updates to Windows PowerShell. For Windows 10 1607 and up, Windows PowerShell 5.1 is installed by default. It's highly recommended that you upgrade Windows 10 to the latest version.
1. You'll also need to install the Windows PowerShell module for Skype for Business Online that enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at Windows PowerShell Module for Skype for Business Online, a link for which is in the **Learn more** section below. Restart your computer if you're prompted.

If you need to know more, see Connect to all Microsoft 365 services in a single Windows PowerShell window, a link to which is in the **Learn more** section below.

### Start a Windows PowerShell session

1. From the **Start Menu** > **Windows PowerShell**.
1. In the **Windows PowerShell** window, connect to your Microsoft 365 by running:

  > [!NOTE]
  > You only have to run the **Import-Module** command the first time you use the Skype for Business Online Windows PowerShell module.

  ```powershell
   Import-Module -Name SkypeOnlineConnector
   $credential = Get-Credential
   $session = New-CsOnlineSession -Credential $credential
   Import-PSSession $session
  ```

If you want more information about starting Windows PowerShell, see Connect to all Microsoft 365 services in a single Windows PowerShell window or Set up your computer for Windows PowerShell.

### See all of the caller ID policy settings in your organization

To view all of the caller ID policy settings in your organization, run:

```powershell
Get-CsCallingLineIdentity |fl
```

For more examples and details see the link in the **Learn more** section below for **Get-CsCallingLineIdentity** .

### Create a new caller ID policy for your organization

To create a new caller ID policy that sets the caller ID to anonymous, run:

```powershell
New-CsCallingLineIdentity  -Identity Anonymous -Description "Anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
```

> [!NOTE]
> In all cases, the "Service Number" field should not include an initial "+".

See more examples and details for **New-CsCallingLineIdentity** located in the **Learn more** section below.
To apply the new policy you created to Amos Marble, run:

```powershell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName Anonymous
```

See more on the **Grant-CsCallingLineIdentity** cmdlet in the **Learn more** section below.

If you've already created a policy, you can use the **Set-CsCallingLineIdentity** cmdlet to make changes to the existing policy, and then use the **Grant-CsCallingLineIdentity** cmdlet to apply the settings to your users.

### Set it so the incoming caller ID is blocked

To block the incoming caller ID, run:

```powershell
Set-CsCallingLineIdentity  -Identity "Block Incoming" -BlockIncomingPstnCallerID $true -EnableUserOverride $true
```

See more examples and details for **Set-CsCallingLineIdentity** in the Learn more section below.

To apply the policy setting you created to a user in your organization, run:

```powershell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Block Incoming"
```

See more on the **Grant-CsCallingLineIdentity** cmdlet in the **Learn more** section below.

### Remove a caller ID policy

To remove a policy from your organization, run:

```powershell
Remove-CsCallingLineIdentity -Identity "My Caller ID Policy"
```

To remove a policy from a user, run:

```powershell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName $null
```

## Learn more

- [How can caller ID be used in your organization](/microsoftteams/how-can-caller-id-be-used-in-your-organization)
- [More about Calling Line ID and Calling Party Name](/skypeforbusiness/what-are-calling-plans-in-office-365/more-about-calling-line-ID-and-calling-party-name)
- [Emergency calling terms and conditions](/microsoftteams/emergency-calling-terms-and-conditions)
- [Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
