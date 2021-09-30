After you have set up your organization's configuration for Teams Phone System with Calling Plans or configured a partnership with your provider using Operator Connect, you then need to enable users to make and receive PSTN phone calls.

This allows you to selectively enable Teams Voice services for only users who need the functionality or gradually enable voice services as you train users or deploy devices.

To enable Teams Phone system for users, we'll need to perform the following tasks:

1. Assign Teams Phone System licensing

1. Assign a Teams Domestic or International Calling Plan license

1. Assign user Dial Plans

1. Assign numbers to users

1. Assign a verified emergency address location

1. Assign a calling policy to a user

## Assign Teams Licenses

To use Teams Phone System, you'll first need to assign the following licenses to a user:

- Microsoft Teams

- Microsoft 365 Phone System

- Optionally, Audio Conferencing, or Audio Conferencing Pay Per Minute

    - These licenses are including in Microsoft Enterprise E5 (with Phone System) and Microsoft Business Voice SKUs.

You will also need to assign a Calling Plan license. Plans are available with inclusive minutes:

- Domestic Calling Plan (3000 minutes per user/month for US/PR/CA, 1200 minutes per user/month for EU countries/regions)

- Domestic Calling Plan (120 minutes per user/month for each country/region - this plan isn't available in the United States)

- Domestic Calling Plan (240 minutes per user/month for each country/region - this plan isn't available in the United States)

Instead of a Calling Plan license, you can instead use Communications Credits, allowing users to consume calling minutes as needed. This must be configured before assigning it to users, following the procedures shown in the module **Configure Teams Phone System**. When you use Communication Credits, you'll need to assign the following licenses:

- Domestic and International Calling Plan

- Communications Credits

Alternatively, you can use Operator Connect. Operator Connect is another option for providing Public Switched Telephone Network (PSTN) connectivity with Teams and Phone System. You do not require Calling Plan or Communications Credits licenses when using this option, but you will need to license users with Microsoft Teams and Microsoft 365 Phone System.

You can use the Microsoft 365 admin center or PowerShell to assign licenses to users in your organization. You must be a Global admin or User management admin to manage licenses. To assign licenses through the Microsoft 365 admin center, follow these steps:

1. Navigate to the Microsoft 365 admin center at [https://admin.microsoft.com/](https://admin.microsoft.com/) and sign in as a Global Administrator or User Management Administrator.

1. In the left navigation, select **Users** and **Active users.**

1. Select the user you want to assign the license to.

1. In the edit pane, select **Licenses and apps** and then select the Calling Plan and the necessary licenses as listed above.

1. Select **Save changes.**

> [!WARNING]
> After assigning licenses, you will need to wait before assigning numbers to users. Because of the latency between Microsoft 365 and Microsoft Teams, it can take up to 24 hours for a user to be assigned a Calling Plan after you assign a license.

## Assign phone numbers and emergency locations to users

After assigning licenses to users for Teams Phone System, you'll then need to assign phone numbers and emergency locations.

In European countries/regions, the emergency location is associated with the phone number when you get it from Microsoft 365 or Office 365 or when you transfer a phone number over to Microsoft 365 or Office 365. In the United States, the emergency location is associated with the phone number when it's assigned to the user. The emergency address can be changed if the user that it's assigned to moves to a new location.

Complete the following steps to assign phone numbers to users:

To assign a phone number in the Teams Admin Center, perform the following steps in written order:

1. Navigate to the Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/)

1. Sign into the Teams admin center with an account that has the Teams Administrator role.

1. In the left navigation, select **Voice** > **Phone numbers**.

1. On the **Phone numbers** page, select an unassigned number in the list, and then select **Edit**.

1. In the **Edit** pane, under **Assigned to**, search for the user by display name or username, and then select **Assign**.

1. To assign or change the associated emergency location, under **Emergency location**, search for and then select the location.

1. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this is on.

1. Select **Save**

You can also perform these steps by using the Microsoft Teams PowerShell module.

To establish a remote PowerShell session with Teams, you first need to install the module. The Teams PowerShell module replaces the Skype for Business Online Connector module, which has been retired.

You can install the latest version of the Microsoft Teams PowerShell module with the following cmdlet in an elevated PowerShell session:

```powershell
Install-Module MicrosoftTeams

```

After you install the module, you can establish a remote session to your tenant with the following cmdlet:

```powershell
Connect-MicrosoftTeams

```

Before assigning a phone number and emergency location, you can retrieve a list of phone numbers and locations available. This makes it easier to find free numbers to assign and ensure you specify the correct location ID for emergency services.

To retrieve a list of phone numbers and their respective activation state, use the following cmdlet:

```powershell
Get-CsOnlineTelephoneNumber | ft Id,ActivationState

```

To retrieve a list of emergency locations that are validated, use the following cmdlet:

```powershell
Get-CsOnlineLisLocation -ValidationStatus Validated

```

After selecting a phone number and emergency location, use the “Set-CsOnlineVoiceUser” cmdlet in a format like the one shown below to enable the user for Teams Voice:

```powershell
Set-CsOnlineVoiceUser -Identity "<User name>" -TelephoneNumber +15555037311 -LocationID d8c4a18a-00d7-37b0-9ddb-3383d29d606b

```

## Assign calling policies and dial plans to a user

While you can assign a multitude of policies to Teams users, two important policies for Voice are dial plans and calling policies.

A dial plan is a named set of normalization rules that translate dialed phone numbers by an individual user into an alternate format (typically E.164) for purposes of call authorization and voice routing. They describe how phone numbers expressed in various formats are translated to an alternate format.

A calling policy controls the calling features that are available for the user. To assign policies and dial plans to a user, follow these steps:

1. Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Sign into the Teams admin center with an account that has the Teams Administrator role.

1. In the left navigation, select **Users**.

1. Select the user you want to assign the policy to by checking the space in front of the username.

1. Select **Edit settings**.

1. In the edit pane on the right, scroll down to **Dial plan** and select **Global (Org-wide default)** or any other policy you want to assign from the dropdown menu.

1. Still in the edit pane on the right, navigate to **Calling policy** and select **AllowCalling** or any other calling policy you want to assign from the dropdown menu.

1. Review the other policy types you can assign through this dialogue, then select **Apply**.

Using this method, you can also assign other policy types to individual users. If you want to use the Microsoft Teams PowerShell module, each policy type comes with its own set of cmdlets for managing it. The Grant-cmdlet will allow you to assign existing policies.

For a Dial Plan, use the Grant-CsTenantDialPlan cmdlet in a similar format to the example below:

```powershell
Grant-CsTenantDialPlan -Identity "<User name>" -PolicyName RedmondDialPlan

```

