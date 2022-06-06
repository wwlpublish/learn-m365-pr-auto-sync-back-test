Organizations in various industries must abide by rules defined by regulatory bodies, such as the Securities and Exchange Commission (SEC). One such rule, SEC Rule 17a-4, affects how organizations deal with data retention. It requires that after a policy for retention is turned on, it can't be turned off or made less restrictive.

To meet this regulatory requirement, Microsoft 365 provides a feature known as Preservation Lock. It locks a retention policy or retention label policy so that no one—not even an administrator—can turn off the policy, delete the policy, or make it less restrictive.

You apply Preservation Lock after a retention policy or retention label policy is created. Preservation Lock locks a retention policy or retention label policy so that no one, including global administrators, can turn off the policy, delete the policy, or make it less restrictive. This configuration enables organizations to meet regulatory requirements. It also helps them safeguard against rogue administrators.

When a retention policy is locked:

 -  No one can disable the policy or delete it.
 -  Locations can be added but not removed.
 -  The retention period can be extended but not decreased.

When a retention label policy is locked:

 -  No one can disable the policy or delete it.
 -  Locations can be added but not removed.
 -  Labels can be added but not removed.

In summary, a locked policy can be increased or extended, but it can't be reduced or turned off.

> [!WARNING]
> Before you lock a retention policy or retention label policy, it's critical that you understand the effect that it will have on your organization. You should also confirm whether it's required for your organization to meet regulatory requirements. Administrators won't be able to disable or delete locked policies after the preservation lock is applied.

Configure Preservation Lock after you've created a retention policy, or a retention label policy that you publish or auto-apply.

> [!NOTE]
> Locking a label policy doesn't prevent an administrator from reducing the retention period in a label that's included in the locked policy. That requirement, with other restrictions, can be met when you configure a label to mark items as a [regulatory record](/microsoft-365/compliance/records-management?azure-portal=true).

### How to lock a retention policy or retention label policy

You must use PowerShell to implement the Preservation Lock feature in Microsoft 365. This feature can't be enabled through the Microsoft 365 UI.

> [!NOTE]
> This limitation was purposely built into Microsoft 365. Because administrators can't disable or delete a policy for retention after this lock is applied, Microsoft wanted to safeguard against accidental configuration. To do so, it didn't include this feature in the Microsoft 365 UI. Instead, Microsoft 365 requires an admin to enter a specific PowerShell command to enable Preservation Lock.

All policies for retention and with any configuration support Preservation Lock.

1.  [Connect to Security and Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell?azure-portal=true).
2.  Find the name of the policy that you want to lock by running **Get-RetentionCompliancePolicy**. For example:
    
    :::image type="content" source="../media/retention-policy-preservation-lock-get-retentioncompliancepolicy-9c5e1522.png" alt-text="Screenshot of a Security and Compliance Center PowerShell session that shows the results of running the Get Retention Compliance Policy command.":::
    
3.  To place a Preservation Lock on your policy, run the **Set-RetentionCompliancePolicy** cmdlet with the name of the policy, and the **RestrictiveRetention** parameter set to true:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" -RestrictiveRetention $true
    
    ```
    
    For example:
    
    :::image type="content" source="../media/retention-policy-preservation-lock-restrictiveretention-4af32856.png" alt-text="Screenshot of a PowerShell session showing the Set Retention Compliance Policy command with the Restrictive Retention parameter set to True.":::
    
    
    When prompted, read and acknowledge the restrictions that come with this configuration by entering **Y**:
    
    :::image type="content" source="../media/retention-policy-preservation-lock-confirmation-prompt-b7706eca.png" alt-text="Screenshot of a PowerShell session showing the prompt to confirm that you want to lock a retention policy.":::
    
4.  A Preservation Lock is now placed on the policy. If you want to confirm this setting, run **Get-RetentionCompliancePolicy** again. However, you must specify the policy name and include the **\|F1** parameter to display the policy settings:
    
    ```powershell
    Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
    
    ```
    
    In the list of parameters that are displayed for this policy, the **RestrictiveRetention** should be set to True. For example:
    
    :::image type="content" source="../media/retention-policy-preservation-lock-locked-policy-1856c33b.png" alt-text="Screenshot of a PowerShell session showing the Get Retention Compliance Policy command being run for a policy and showing all policy settings.":::
    

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”