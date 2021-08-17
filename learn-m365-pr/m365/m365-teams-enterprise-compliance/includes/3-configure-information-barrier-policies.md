In most companies, communication is actively encouraged between all employees. However, in some specialized circumstances, it's necessary to prevent one department or team from communicating with another.

Suppose, in your legal firm, you have separate teams that represent plaintiffs and defendants in cases of criminal negligence. It's essential that these teams cannot exchange information so that, when lawyers from your company both prosecute and defend the same case, there is no possibility of conflicts.

Here, you'll learn how to set up information barriers between users in Microsoft Teams.

## What are information barriers?

Information barriers allow you to restrict communication between two groups of people within your Teams system. You may want to avoid a conflict of interest, safeguard internal information, or have another business need to restrict communication.

:::image type="content" border="false" source="../media/3-info-barriers-explained.png" alt-text="Information Barriers":::

To create or edit information barrier policies, you will need to be familiar with PowerShell cmdlets.

## Licenses and permissions

To use information barriers, you must have one of the following subscriptions:

- Microsoft or Office 365 E5/A5
- Office 365 Advanced Compliance
- Microsoft 365 Compliance E5/A
- Microsoft 365 Insider Risk Management

Assign the **IB Compliance Management** or **Compliance administrator** role to the person responsible for managing information barriers.

There are several steps to configuring information barrier policies:

1. Check you have the necessary licenses and have assigned permissions.
1. Segment users.
1. Define the information barrier policy.
1. Apply the information barrier policy.

## Segment users

When segmenting users, there are two important rules:

- A user must be in only one segment.
- Each segment must have only one information barrier.
To assign users to a segment, you use the cmdlet **New-OrganizationSegment** with the **UserGroupFilter** parameter:

```powershell
New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"
```

To define a segment named **HR**, using the **Department** attribute, use this command:

```powershell
New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'
```

After you run each cmdlet, details about the segment are displayed, including the type, who created or last modified it, and so on.

## Define an information barrier policy

You can either block communications between segments, or allow communication with one segment only.
To block segments from communicating with each other, you need two policies: one for each direction. Each policy blocks communication one way only. Use the **New-InformationBarrierPolicy** cmdlet with the **SegmentsBlocked** parameter:

```powershell
New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"
```

To define a policy **Sales-Research** for a user segment **Sales** to prevent **Sales** from communicating with **Research**, the PowerShell command would be:

```powershell
New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive
```

The second half policy, prevents **Research** from communicating with **Sales**:

```powershell
New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive
```

To allow one segment to communicate with only one other segment, use the **New-InformationBarrierPolicy** cmdlet with the **SegmentsAllowed** parameter:

```powershell
New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"
```

To define a policy called **Manufacturing-HR** for a segment called **Manufacturing** to allow people in Manufacturing to communicate only with people in a segment called **HR**, use this command:

```powershell
New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive
```

## Apply an information barrier policy for Microsoft Teams

You have seen how to segment users and define a policy. You now need to apply the policy. Information barrier policies do not take effect until you set them to active and apply the policy.

To set a policy to active status, use the **Set-InformationBarrierPolicy** cmdlet with an **Identity** parameter, and set the **State** parameter to **Active**:

```powershell
Set-InformationBarrierPolicy -Identity GUID -State Active
```

The GUID is displayed when you define the information policy. Use it when you want to make the information barrier policy active, as in the following example:

```powershell
Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active
```

## Learn more

To learn more about the topics in this unit, see:

- [Information barriers](/microsoft-365/compliance/information-barriers).
- [Information barriers in Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).
