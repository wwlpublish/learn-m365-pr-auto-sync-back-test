Besides regular Teams recording, some organizations need compliance recording for Workforce engagement (WFE), security and surveillance, or compliance and regulatory obligations. 

Compliance recording solution in Teams enables organizations to automatically record and capture calls and online meetings for later processing and retention.

## Compliance recording solution  

The core component of the compliance recording solution is the recorder. When a communication interaction takes place, the recorders are automatically invited to participate in conversations based on the policies. 

Users under this policy are aware that their digital interactions with Teams are being recorded. Users can't disable the recording and don't have access to the recording once the interaction is complete. 

The recording becomes part of the organizational archive. The recording is available to compliance and legal personnel for eDiscovery, legal hold, and other corporate retention uses.

 The exact implementation of the recorder service will vary by partner. Compliance recording solutions are integrated with Teams as shown in the following diagram.

:::image type="content" source="../media/hp-compliance-recording-for-teams-calling-and-meetings.jpg" alt-text="The images shows the flow when a Teams meeting or call is sent and received.":::


## Configure compliance recording policy 

IT Administrators configure compliance recording policies to determine the users to be recorded and the recorder to be used for each user.

Admins can apply the compliance recording policies at the tenant, per-user, and security group levels.  

1. Create an application instance in your tenant.

   ```powershell
   PS C:\> New-CsOnlineApplicationInstance -UserPrincipalName cr.instance@contoso.onmicrosoft.com -DisplayName ComplianceRecordingBotInstance -ApplicationId fcc88ff5-a42d-49cf-b3d8-f2e1f609d511

   RunspaceId        : 4c13efa6-77bc-42db-b5bf-bdd62cdfc5df
   ObjectId          : 5069aae5-c451-4983-9e57-9455ced220b7
   TenantId          : 5b943d7c-5e14-474b-8237-5022eb8e0dc9
   UserPrincipalName : cr.instance@contoso.onmicrosoft.com
   ApplicationId     : fcc88ff5-a42d-49cf-b3d8-f2e1f609d511
   DisplayName       : ComplianceRecordingBotInstance
   PhoneNumber       :
   ```

   ```powershell
   PS C:\> Sync-CsOnlineApplicationInstance -ObjectId 5069aae5-c451-4983-9e57-9455ced220b7
   ```

2. Use ```New-CsTeamsComplianceRecordingPolicy``` cmdlet to create a Compliance Recording policy.

   ```powershell
   PS C:\> New-CsTeamsComplianceRecordingPolicy -Identity TestComplianceRecordingPolicy -Enabled $true -Description "Test policy created by tenant admin"

   Identity                        : Global
   ComplianceRecordingApplications : {}
   Enabled                         : True
   WarnUserOnRemoval               : True
   Description                     : Test policy created by tenant admin
   ```

   ```powershell
   PS C:\> Set-CsTeamsComplianceRecordingPolicy -Identity TestComplianceRecordingPolicy `
   -ComplianceRecordingApplications @(New-CsTeamsComplianceRecordingApplication -Id 5069aae5-c451-4983-9e57-9455ced220b7 -Parent TestComplianceRecordingPolicy)
   ```


3. Use ```Grant-CsTeamsComplianceRecordingPolicy``` cmdlet to assign the Compliance Recording policy to a user.

   ```powershell
   PS C:\> Grant-CsTeamsComplianceRecordingPolicy -Identity testuser@contoso.onmicrosoft.com -PolicyName TestComplianceRecordingPolicy
   ```

   ```powershell
   PS C:\> Get-CsOnlineUser testuser@contoso.onmicrosoft.com | select SipAddress, TenantId, TeamsComplianceRecordingPolicy | fl

   UserPrincipalName              : testuser@contoso.onmicrosoft.com
   TenantId                       : 5b943d7c-5e14-474b-8237-5022eb8e0dc9
   TeamsComplianceRecordingPolicy : TestComplianceRecordingPolicy
   ```