## Required permissions
To define or edit information barrier policies, you must be assigned one of the following roles:
- Microsoft 365 global administrator
- Office 365 global administrator
- Compliance administrator
- IB Compliance Management 

To learn more about roles and permissions, see [Permissions in the Office 365 Security & Compliance Center](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?view=o365-worldwide?azure-portal=true).

## Workflow at a glance
There are several phases involved in implementing information barriers. First, you need to ensure that prerequisites have been met. This involves:

- Verifying that you have the required licenses and permissions.
- Verifying that your directory includes data for segmenting users.
- [Enabling scoped directory search](https://docs.microsoft.com/MicrosoftTeams/teams-scoped-directory-search?azure-portal=true) for Microsoft Teams.
- Making sure [audit logging is turned on](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off?view=o365-worldwide?azure-portal=true).
- Making sure no [Exchange address book policies](https://docs.microsoft.com/exchange/address-books/address-book-policies/remove-an-address-book-policy?azure-portal=true) are in place.
- PowerShell
   - Connect to [Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps?azure-portal=true).
   - Connect to [Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.7.0&viewFallbackFrom=azps-2.3.2?azure-portal=true).
- Providing admin consent for Microsoft Teams.

For more information, see [Prerequisites](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-policies?view=o365-worldwide#prerequisites?azure-portal=true).

## Segmenting users
Once prerequisites have been met you can move on to the next phase which is to segment users in your organization. To segment users, it is recommended that you: 

- Determine what policies are needed.
- Make a list of segments to define.
- Identify which [attributes](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-attributes?view=o365-worldwide?azure-portal=true) to use. (It is recommended to use the same attribute for all your segments. Ensure your segments do not overlap; each user should be assigned to exactly one segment.)
- Define segments in terms of policy filters

For more information, see [Part 1: Segment users](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-policies?view=o365-worldwide#part-1-segment-users?azure-portal=true).

## Defining information barrier policies
When defining information barrier policies you need to determine whether you need to prevent communications between certain segments or limit communications to certain segments. It is recommended that you use the minimum number of policies to ensure your organization is compliant with legal and industry requirements.

Once you have identified your user segments and the information barrier policies you want to define, you will choose between implementing one (or both) of the following scenarios:
- Scenario 1: Block communications between segments
- Scenario 2: Allow a segment to communicate only with one other segment

For more information, see [Part 2: Define information barrier policies](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-policies?view=o365-worldwide#part-2-define-information-barrier-policies?azure-portal=true).

## Applying information barrier policies
Currently, information barrier policies must be defined and managed by using a combination of [Office 365 Security & Compliance PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=o365-worldwide?azure-portal=true) cmdlets as illustrated below:

- Use the **Get-InformationBarrierPolicy** cmdlet to see a list of policies that have been defined and make note of the status and identity (GUID) of each policy. 

  `Get-InformationBarrierPolicy`

- Use the Set-InformationBarrierPolicy cmdlet with an Identity parameter and the State parameter set to Active. 

  `Set-InformationBarrierPolicy -Identity GUID -State Active`

- Use the Start-InformationBarrierPoliciesApplication cmdlet to apply the policy. 

  `Start-InformationBarrierPoliciesApplication`

  After you run `Start-InformationBarrierPoliciesApplication,` you will need to allow 30 minutes for the system to start applying the policies. 

For more information, see [Part 3: Apply information barrier policies](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-policies?view=o365-worldwide#part-3-apply-information-barrier-policies?azure-portal=true). 


## Learn more

 - [Permissions in the Office 365 Security & Compliance Center](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center?view=o365-worldwide?azure-portal=true)
 - [Prerequisites](https://docs.microsoft.com/en-us/microsoft-365/compliance/information-barriers-policies?view=o365-worldwide#prerequisites?azure-portal=true)
 - [Troubleshooting information barriers](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-troubleshooting?view=o365-worldwide?azure-portal=true)
 - [Edit (or remove) information barrier policies](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-edit-segments-policies?view=o365-worldwide?azure-portal=true)

