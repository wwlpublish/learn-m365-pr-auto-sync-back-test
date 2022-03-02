To see how an organization might approach defining segments and policies, consider the following example.

### Contoso's departments and plan

Contoso has five departments: HR, Sales, Marketing, Research, and Manufacturing. In order to remain compliant with industry regulations, some departments are not supposed to communicate with other departments, as listed in the following table:

|   Segment |Can talk to   |  Cannot talk to |  
|---|---|---|
|  HR | All other departments    |  (no restrictions) |
| Sales  | HR & Marketing  |Research & Manufacturing   |
|Marketing |  All other departments   |   (no restrictions)  |
| Research |  HR & Marketing   |  Sales & Manufacturing |
| Manufacturing  |  HR & Marketing |  Research & Sales |

With this in mind, Contoso's plan includes three information barrier policies:

- A policy designed to prevent Sales from communicating with Research (and another policy to prevent Research from communicating with Sales)
- A policy designed to allow Manufacturing to communicate with HR and Marketing only

It is not necessary to define policies for HR or Marketing.

### Contoso's defined segments

Contoso will use PowerShell cmdlets and the Department attribute in Azure Active Directory to define segments, as follows:

|  Department | Segment definition  |
|---|---|
|  HR |  `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Sales  | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'" ` |
|  Marketing |  `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'" `|
|  Research |  `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Manufacturing  |  `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

With the segments defined, Contoso proceeds to define policies.

### Contoso's information barrier policies

Contoso defines three policies, as described in the following tables:

|  Policy | Policy definition  |
|---|---|
| Policy 1: Prevent Sales from communicating with Research  |  `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Manufacturing","Research" -State Inactive`
>In this example, the information barrier policy is called **Sales-Research**. When this policy is active and applied, it will help prevent users who are in the Sales segment from communicating with users in the Research segment. This is a one-way policy; it won't prevent Research from communicating with Sales. For that, Policy 2 is needed.

|  Policy | Policy definition  |
|---|---|
| Policy 2: Prevent Research from communicating with Sales |  `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Manufacturing","Research" -SegmentsBlocked "Sales" -State Inactive`

>In this example, the information barrier policy is called **Research-Sales**. When this policy is active and applied, it will help prevent users who are in the Research segment from communicating with users in the Sales segment.

|  Policy | Policy definition  |
|---|---|
| Policy 3: Allow Manufacturing to communicate only with HR and Marketing |  `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "Manufacturing","HR","Marketing" -State Inactive`

>In this case, the information barrier policy is called **Manufacturing-HRMarketing**. When this policy is active and applied, Manufacturing can communicate only with HR and Marketing. Note that HR and Marketing are not restricted from communicating with other segments.

With segments and policies defined, Contoso applies the policies by running the `Start-InformationBarrierPoliciesApplication` cmdlet.
