Information barriers (IBs) are policies that an admin can configure to prevent individuals or groups from communicating with each other. 

IB policies also prevent lookups and discovery. If you attempt to communicate with someone you shouldn't be communicating with, you won't find that user in the people picker. The information barriers can be used in some of the following cases:

- When a team must be prevented from communicating or sharing data with a specific other team.

- When a team must not communicate or share data with anyone outside of that team.

Here's an example. Alex belongs to the Banking segment and Bill belongs to the Financial advisor segment. Alex and Bill can't communicate with each other because the organization's IB policy blocks communication and collaboration between these two segments. However, Alex and Bill can communicate with Lee in HR.

:::image type="content" source="../media/information-barriers-example.png" alt-text="Example showing information barriers preventing communication between segments":::

## How information barriers work in Teams

Information barriers are supported in Microsoft Teams, SharePoint, and OneDrive. In Microsoft Teams, IB policies are triggered when the following Teams events take place:

- **Members are added to a team**: Whenever you add a user to a team, the user's policy must be evaluated against the IB policies of other team members. If the user's policy blocks them from being added to the team, the user won't show up in search.

    :::image type="content" source="../media/information-barriers-add-members.png" alt-text="Screenshot of searching for a new member to add to a team and finding no matches":::

- **A new chat is requested**: Each time that a user requests a new chat with one or more other users, the chat is evaluated to make sure that it isn't violating any IB policies. If the conversation violates an IB policy, then the conversation isn't started. Here's an example of a 1:1 chat.

	:::image type="content" source="../media/information-barriers-one-one-chat.png" alt-text="Screenshot showing blocked communication in 1:1 chat":::

- **A user is invited to join a meeting**: When a user is invited to join a meeting, the IB policy that applies to the user is evaluated against the IB policies that apply to the other team members. If there's a violation, the user won't be allowed to join the meeting.

    :::image type="content" source="../media/information-barriers-meeting.png" alt-text="Screenshot showing user blocked from meeting":::

- **A screen is shared between two or more users**: When a user shares a screen with other users, the sharing must be evaluated to make sure that it doesn't violate the IB policies of other users. If an IB policy is violated, the screen share won't be allowed. Here's an example of screen share after the policy is applied. The screen share and call icons aren't visible.

	:::image type="content" source="../media/information-barriers-after-screen-share-policy.png" alt-text="Screenshot showing user share with blocked settings" lightbox="../media/information-barriers-after-screen-share-policy.png":::

- **A user places a phone call in Teams**: Whenever a user starts a voice call (via VOIP) to another user or group of users, the call is evaluated to make sure that it doesn't violate the IB policies of other team members. If there's any violation, the voice call is blocked.

- **Guests in Teams**: IB policies apply to guests in Teams, too. You can define IB policies once guests are discoverable in your organization's global address list.

When admins create or update information barrier policies, the service automatically searches the members to ensure that the Team members are not violating any policies. If there are any new violations, the following actions are taken:  

- **1:1 chat**: If a chat between two participants violates a policy, the chat is set to read-only and no new messages can be sent.

- **Group chat**: If participants in a group chat violate a changed or new policy, the affected participants are removed from the chat and they can see the conversation history in read-only.

- **Team**: Any users who have been removed from the group are removed from the team and won't be able to see or participate in existing or new conversations.

## Workflow

There are several steps to configuring information barrier policies for Microsoft Teams. When a team is created, a SharePoint site is provisioned and associated with Microsoft Teams for the files experience. Information barrier policies aren't honored on this SharePoint site and files by default. To enable information barriers in SharePoint and OneDrive, see [Use information barriers with SharePoint](https://docs.microsoft.com/sharepoint/information-barriers?azure-portal=true#prerequisites).

| Phase | What's involved |
|--------|------------------|
| [Make sure prerequisites are met](https://docs.microsoft.com/microsoft-365/compliance/information-barriers-policies?azure-portal=true#prerequisites) | - Verify that you have the [required licenses and permissions](https://docs.microsoft.com/microsoft-365/compliance/information-barriers?azure-portal=true#required-licenses-and-permissions)<br/>- Verify that your directory includes data for segmenting users<br/>- Enable scoped directory search for Microsoft Teams<br/>- Make sure audit logging is turned on<br/>- Make sure no Exchange address book policies are in place<br/>- Use PowerShell <br/>- Provide admin consent for Microsoft Teams |
| Part 1: Segment users in your organization | - Determine what policies are needed<br/>- Make a list of segments to define<br/>- Identify which attributes to use<br/>- Define segments in terms of policy filters |
| Part 2: Define information barrier policies | - Define your policies (do not apply yet)<br/>- Choose from two kinds (block or allow) |
| Part 3: Apply information barrier policies | - Set policies to active status<br/>- Run the policy application<br/>- View policy status |

### Prerequisites for information barriers

The following prerequisites must be in place to implement information barriers:

- **Required licenses for information barriers**: Information barriers is an advanced compliance feature and requires according licenses. The feature is available for users with one of the following licenses:

	- Microsoft 365 E5/A5

	- Office 365 E5/A5

	- Office 365 Advanced Compliance

	- Microsoft 365 Compliance E5/A5

	- Microsoft 365 Insider Risk Management

- **Permissions for information barrier policies**: To define or edit information barrier policies, administrators must be assigned to one of the following roles:

	- Microsoft 365 global administrator

	- Office 365 global administrator

	- Compliance administrator

	- IB Compliance Management


- **Directory data**: Make sure that your organization's structure is reflected in directory data.

- **Scoped directory search**: This setting must be turned on.

- **Audit logging**: To look up the status of a policy application, audit logging must be turned on.

- **No address book policies**: Make sure no Exchange address book policies are in place.

- **PowerShell with the Security &amp; Compliance Center module**: Information barriers can be configured using PowerShell and connecting the Security and Compliance center module to your Microsoft 365 tenant.

- **Admin consent for information barriers in Microsoft Teams**: Use the following procedure to enable information barrier policies to work as expected in Microsoft Teams.

	1. Run the following PowerShell cmdlets:

		```powershell
		# Login with the Azure Resource Manager PowerShell to your tenant:
		Login-AzureRmAccount
		# Save the information barrier service app id to a variable:
		$appId="bcf62038-e005-436d-b970-2a472f8c1982"
		# Get a service principal in Azure for the app id:
		$sp=Get-AzureRmADServicePrincipal -ServicePrincipalName $appId
		# If a service principal could not be retrieved, create a new one:
		if ($sp -eq $null) { New-AzureRmADServicePrincipal -ApplicationId $appId }
		# Start the process to grant consent, by running:
		Start-Process https://login.microsoftonline.com/common/adminconsent?client_id=$appId 
		```

	2. When prompted, sign in using your work or school account for Office 365.

	3. In the **Permissions requested** dialog box, review the information, and then select **Accept**.

### Part 1: Segment users in your organization

During this phase, you determine what information barrier policies are needed, make a list of segments to define, and then define your segments. When segmenting users, there are two important rules:

- A user must be in only one segment.

- Each segment must have only one information barrier.

A segment is defined by certain directory attributes.
To assign users to a segment, you use the cmdlet ```New-OrganizationSegment``` with the ```UserGroupFilter``` parameter:

1. Open PowerShell and connect with the Security & Compliance Center PowerShell module to your tenant.  

2. Run the following cmdlet and replace **segment-name** with a meaningful name and both **attribute** and **attribute-value** with the desired directory attribute to filter segment members for.

	```powershell
	New-OrganizationSegment -Name "segment-name" -UserGroupFilter "attribute -eq 'attribute-value'"	
	```  

	For example, to define a segment named Sales, using the Department attribute, use this command:

	```powershell
	New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'
	```

3. Repeat this process for each segment you want to define.
 
### Part 2: Define information barrier policies

After creating segments, you can create the policies that restrict the segments from communication. There are two types of policies:

- **Block** policies prevent one group from communicating with another group.

- **Allow** policies allow a group to communicate with only certain other, specific groups.

#### **Scenario 1:** Block communications between segments

To block segments from communicating with each other, you need two policies: one for each direction. Each policy blocks communication one way only. Use the ```New-InformationBarrierPolicy``` cmdlet with the ```SegmentsBlocked``` parameter:

```powershell
New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"
```

For example, to block communications between Sales and Research departments, use this command:

```powershell
## Prevent Sales from communicating with Research
New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive

## Prevent Research from communicating with Sales
New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive
```

#### **Scenario 2:** Allow a segment to communicate with other segment

To allow one segment to communicate with other segment, use the ```New-InformationBarrierPolicy``` cmdlet with the ```SegmentsAllowed``` parameter:

```powershell
New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"
```

For example, to allow the Research segment to communicate with only HR and Manufacturing, use this command:

```powershell
New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive
```

### Part 3: Apply information barrier policies

Information barrier policies are not in effect until you set them to active status, and then apply the policies.

1. Use the ```Get-InformationBarrierPolicy``` cmdlet to see a list of policies that have been defined. Note the status and identity (GUID) of each policy.

2. To set a policy to active status, use the ```Set-InformationBarrierPolicy``` cmdlet with an ```Identity``` parameter, and set the ```State``` parameter to ```Active```:

	```powershell
	Set-InformationBarrierPolicy -Identity GUID -State Active
	```  

3. Run the following cmdlet to start information barriers in your tenant:

	```Start-InformationBarrierPoliciesApplication```

After you run ```Start-InformationBarrierPoliciesApplication```, allow 30 minutes for the system to start applying the policies. The system applies policies user by user. The system processes about 5,000 user accounts per hour.

For more information, see:

- [Information barriers in Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams?azure-portal=true)

- [Define policies for information barriers](/microsoft-365/compliance/information-barriers-policies?azure-portal=true)

- [Attributes for information barrier policies](/microsoft-365/compliance/information-barriers-attributes?azure-portal=true)

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”