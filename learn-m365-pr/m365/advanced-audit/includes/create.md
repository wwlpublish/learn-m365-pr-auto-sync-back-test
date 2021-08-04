You must be assigned the Organization Configuration role in the Microsoft 365 Defender portal to create or modify an audit log retention policy. This can be accomplished by adding the admin to the Organization Manager role group using the Microsoft 365 Defender portal or Security & Compliance Center PowerShell.

Once you have the appropriate permissions, audit log retention policies can be created using the Microsoft 365 compliance center or Security & Compliance PowerShell.

> [!NOTE]
> Both the Exchange admin center and the Microsoft 365 Defender portal have a role group named Organization Manager. They are not the same.

> [!Important]
> The Security & Compliance Center PowerShell is the administrative interface that enables you to manage the features that are available in the Microsoft 365 Defender portal and the Microsoft 365 compliance center from the command line.

## Connect to Security & Compliance Center PowerShell

Connecting to Security & Compliance PowerShell is required to configure audit log retention policies using PowerShell. The instructions below assume the following tasks have already been completed.

- You have already been granted the permissions required to connect to the Security & Compliance Center PowerShell.
- Windows PowerShell has been configured to run scripts.
- Windows Remote Management (WinRM) has been enabled.
- WinRM has been configured to allow Basic authentication.

Here are the steps to connect to Security & Compliance PowerShell:

1. Open **Windows PowerShell** and issue the following command:

    ```PowerShell
    $UserCredential = Get-Credential
    ```

    Type the **username** and **password** when the Windows PowerShell credential request dialog box appears.

1. Run the following command:

    ```PowerShell
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    For Microsoft 365 Germany, use the `ConnectionUri` value: <https://ps.compliance.protection.outlook.de/powershell-liveid/>.

    For Microsoft 365 Government Community Cloud High (GCC High), use the ConnectionUri value: <https://ps.compliance.protection.office365.us/powershell-liveid/>.

1. Run the following command:

    ```PowerShell
    Import-PSSession $Session -DisableNameChecking
    ```

Watch this demonstration of how to connect to Security & Compliance Center PowerShell.

>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Asf5]

## Grant permission to create audit log retention policies

You must be assigned the Organization Configuration role in the Microsoft 365 Defender portal to create or modify an audit log retention policy. Here are the instructions for granting these permissions using the Security & Compliance PowerShell.

1. Connect to Security & Compliance Center PowerShell using an account that already has access.
1. Use the `Add-RoleGroupMember` cmdlet to add a user to the Organization Management role group. This example shows AlexW being added to the role group:

    ```PowerShell
    Add-RoleGroupMember -Identity "Organization Management" -Member AlexW
    ```

1. Confirm the user has been added to the Organization Management group in Security & Compliance Center. Here is an example:

    ```PowerShell
    Get-RoleGroupMember -Identity "Organization Management"
    ```

    The image below is an example of the confirmation received that AlexW user is a member of the Organization Management role group. AlexW can now create or modify audit log retention policies.

    :::image type="content" source="../media/role-group.png" alt-text="User confirmation screen":::

## Create audit log retention policy in Microsoft 365 compliance center

Audit log retention policies can be created using the Microsoft 365 compliance center.

1. Sign into the Microsoft 365 compliance center using an account with the appropriate rights.
2. Open the **Audit** solution.
3. Select **Create Policy**, then complete the **Create Retention Policy** form. The table below provides information needed to complete the form.

|  Field |  Description |
|---|---|
|  Name | The name of the audit log retention policy. This name must be unique in your organization.  |
|  Description | Provides information about the policy, such as the record type or workload, users specified in the policy, and the duration.  |
|  Users | Select one or more users to apply the policy to. If you leave this box blank, then the policy will apply to all users. If you leave Users blank, you must select a Record Type.  |
|  Record Type | The audit record type the policy applies to. If you select more than one record type, you can't select activities because the policy will apply to all activities for the selected record types. Also, if you leave Record Type blank, you must select a User.  |
|   Operations| This option is only visible if you select a Record Type. Use this box to choose activities from the record type you selected. You can choose specific activities to apply the policy to. If you do not choose specific activities, the policy will apply to all activities of the selected record type.  |
|  Duration | The amount of time to retain the audit log activities that meet the policy criteria.|
| Priority  | This value determines the order in which audit log retention policies are processed. A higher value indicates a higher priority. For example, a policy with a priority value of 5 would take priority over a policy with a priority value of 0. Custom audit log retention policies take precedence over the default policy for your organization.  |

There is no visual feedback indicating the audit retention policy is created. The list of audit log retention policies is available via the PowerShell cmdlet *Get-UnifiedAuditLogRetentionPolicy*. An example of how to use this cmdlet is provided later in this course.

### Create audit log retention policy in Microsoft 365 compliance center

Watch this video on how to create an audit log retention policy using Microsoft 365 compliance center.
>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Asf6]

## Create audit log retention policy in PowerShell

Audit log retention policies can be created using the Security & Compliance Center PowerShell.

1. Connect to Security & Compliance PowerShell.
2. Run the PowerShell command which will create an audit log retention policy. The sample provided uses the settings below.

    ```PowerShell
    New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "Six-month retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration SixMonths -Priority 10
    ```

    |  Property | Value  |
    |---|---|
    |  Name |  Microsoft Teams Audit Policy |
    |  Description | Six-month retention policy for all Microsoft Teams activities  |
    |  RecordTypes | MicrosoftTeams  |
    |  RetentionDuration | SixMonths  |
    |  Priority | 10  |

### Create audit log retention policy in PowerShell

Watch this demonstration of how to create an audit log retention policy in PowerShell.
>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4AvrG]

## View audit log retention policies using PowerShell

Custom audit log retention policies are viewed using the `Get-UnifiedAuditRetentionPolicy` cmdlet in Security & Compliance Center PowerShell. There is no way to view the default audit log retention policy. Here is a sample PowerShell command to view the settings for the audit log retention policies in your organization. This command sorts the policies from the highest to lowest priority.

```PowerShell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration 
```

### View audit log retention policies using PowerShell

Watch this demonstration on how to view your audit log retention policies.
>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4AkzK]

## Learn more

- [Manage audit log retention policies](/microsoft-365/compliance/audit-log-retention-policies?azure-portal=true)
- [Security & Compliance Center PowerShell](/powershell/exchange/office-365-scc/office-365-scc-powershell?azure-portal=true)
- [New-UnifiedAuditLogRetentionPolicy cmdlet reference](/powershell/module/exchange/new-unifiedauditlogretentionpolicy?azure-portal=true)
- [Get-UnifiedAuditLogRetentionPolicy cmdlet reference](/powershell/module/exchange/policy-and-compliance-audit/get-unifiedauditlogretentionpolicy?azure-portal=true)
