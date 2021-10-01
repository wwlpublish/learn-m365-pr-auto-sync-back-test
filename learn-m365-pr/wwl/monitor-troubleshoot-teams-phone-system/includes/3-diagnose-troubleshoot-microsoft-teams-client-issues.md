Besides issues on the administrative backend and network, the users Teams Client can also be the source of a problem. This unit covers different commonly used ways of troubleshooting the Teams client.
## Dial pad is missing in Teams client

The user does not see a dial pad in their Teams client. There are two possible issues:

### Check license assignment and Teams mode

The user encounters a possible license issue, when:

- The user hasn't assigned a Teams license.

- The user hasn't assigned a Calling Plan.

- The user hasn't enabled Enterprise Voice.

Possible Solution: Check and assign licenses as appropriate.

1. Navigate to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com/) and sign in as a Global Administrator.

1. Go to **Users** and select **Active Users**.

1. Find the user and select into them.

1. Select the **License and apps** tab.

1. Check they have a Phone System license, or a SKU that includes Phone System license and a Calling plan license assigned.

1. If not assigned, assign them.

Another possible solution is a wrong mode the user is operating at. Check that the user is in TeamsOnly mode. Teams can operate in multiple modes. These can be set at the tenant level or user level. These modes help manage the migration from Skype for Business to Teams. Teams Only mode is the  setting to use if you want the user to use only Teams. This enabled the user to use Phone and Federation features in Teams.

Check this for the user with the Microsoft Teams PowerShell module by running the following cmdlet:

```powershell
Get-CsOnlineUser -Identity "sip:testuser@domain.com" | Select-Object DisplayName,TeamsUpgradeEffectiveMode

```

> [!NOTE]
> The “sip:” prefix is required on the identity on with this cmdlet.

Check the output for their TeamsUpgradeEffectiveMode status, if it is not "TeamsOnly" set it to Teams only with the following cmdlet:

```powershell
Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity user@domain.com

```

The above cmdlet assigns the "UpgradeToTeams" policy to user user@domain.com. This effectively upgrades the user to Teams only mode.

### The OnlineVoiceRoutingPolicy value isn't set correctly for the user.

Using PowerShell, remove and re-add the Voice Routing Policy.

Use the following cmdlet from the Microsoft Teams PowerShell module to remove the voice routing policy from the user:

```powershell
Grant-CsOnlineVoiceRoutingPolicy -Identity user@domain.com -PolicyName $Null

```

The following cmdlet re-adds the voice routing policy to the user:

```powershell
Grant-CsOnlineVoiceRoutingPolicy -Identity user@domain.com -PolicyName Policy

```

## User information isn't updated in Microsoft Teams

After user attributes are updated in Microsoft Teams, such as display name, telephone number, or manager, users continue to see the old information in the Teams client.

Teams has a caching scheme that is designed for capacity and performance optimization. The Teams service caches general user information for up to three days. The Teams client also caches general user information locally. Some data, such as display name and telephone number, can be cached up to 28 days in the client. Profile photos can be cached up to 60 days.

If this is causing real issues to some users, they can clear their local Teams client cache.

## Collect Teams client logs

When troubleshooting Teams client issues, you may wish to collect client logs to review yourself or for Microsoft support to review.

### About client logs

There are three client log files that the Windows, Mac, and Linux clients can generate:

- Debug logs

- Media logs

- Desktop logs

The logs are text-based and are read from the bottom-up because newer entries are appended to the file.

Debug logs show the following data flows:

- Authentication

- Connection requests to middle-tier services

- Call/conversation

Media logs contain diagnostic data about audio, video, and screen sharing in Teams meetings. They are required for support cases that are linked to call-related issues.

Desktop logs, also known as bootstrapper logs, contain log data that occurs between the desktop client and the browser

When creating a support request with Microsoft Support, they will require the debug logs. Media or Desktop logs are only required if specifically requested by Microsoft support.

### How to collect client log files

It’s important to collect logs as soon as an issue occurs. Media logging is turned off by default. To enable Media logging, users must turn on the option in the Teams client. Go to Settings > General, and select Enable logging for meeting diagnostics (requires restarting Teams).

- Windows: Right-click on the Teams icon in the system tray and choose Collect support files or Ctrl + Alt + Shift + 1 in the client.

- Mac: Select the Help menu and choose Collect support files or Option + Command + Shift + 1 in the client.

To collect logs for Browser: Keyboard shortcut: Ctrl + Alt + Shift + 1 The files will be available in %userprofile%\Downloads

## Troubleshooting dynamic emergency address using client debug logs

Dynamic emergency calling provides the capability to configure and route emergency calls, provide the correct emergency calling address based on the current network location of the Teams client.

You can use  the Teams client diagnostic logs for Dynamic address validation and troubleshooting.

1. Sign out and exit the Teams client and sign in again, this causes Teams client to perform the lookup of the emergency address for the current network/site.

1. Get the client logs from a Teams client by pressing CTRL+ALT+Shift+1 simultaneously on the Windows Desktop client.

1. Windows file location: “%userprofile%\Downloads\MSTeams Diagnostics Log <timestamp>.txt”

1. Open the MsTeams Diagnostics Log <timestamp>.txt file in notepad or another text editor.

1. Search in the text log for "ipaddr," this is the public IP address the client is reporting

1. Search for "EndPointNetwork" to see if client’s public IP address is trusted.

    - If it returns as Unknown, then there is no match for the Trusted IP of the Teams client, and you need to review the configuration:
        ```console
        callingService: [setLocationInfo] set with [locationInfoType=1][content={“endpointNetwork”:”Unknown”,”networkSiteId”:null,”enableLocationBasedRouting”:false,”siteAddress”:null,”subnetId”:null}][context=locationResponse][mediaOptimization]
        
        ```

    - If it returns as Trusted, the public IP address does match an IP configured in Teams Admin Center
        ```console
        callingService: [setLocationInfo] set with [locationInfoType=1][content={“endpointNetwork”:”Trusted”,”networkSiteId”:” Test1LAN”,”enableLocationBasedRouting”:false,”siteAddress”:”Test1LAN”,”subnetId”:”192.168.10.0″}][context=locationResponse][mediaOptimization]

        ```
1. if it returns as Trusted, the public IP address does match an IP configured in Teams Admin Center

1. If Trusted, search for the following in the log file to validate them:

    - "emergencyCallingPolicy”

    - "emergencyCallRoutingPolicy”

    - "Longitude" / "Latitude"

## Analyze reverse number lookup issues

When you receive PSTN calls in your Teams client Reverse Number Lookup (RNL) will show the display name of the calling party instead of the actual phone number.

The following order will be used to check for a match in sequence with the last match being the one shown.

1. SIP Invite From Header

1. Azure Active Directory

1. Outlook contacts

1. Teams contacts

This display name will also show up in your Activity Feed, Call History, and Voicemail.

If a display name is not being shown, or the display name is not what you would expect, check the following in sequence until you have found the issue.

1. Check the users personal Teams contacts or Outlook contacts for a match. This is the most common reason for an "incorrect" display name appearing.

1. Review Azure Active Directory user and contacts for a match with PowerShell

    ```powershell
    Get-User |ft DisplayName, *phone*Get-Contact |ft DisplayName, *phone*
    
    ```

3. Review the output for a match. If a match is found, correct the display name. If no match is found, add, or edit a contact as appropriate.

1. If using Direct Routing, Check SIP logs for the SIP Invite From Header and check what it is displaying.

