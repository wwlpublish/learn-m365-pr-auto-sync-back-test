The condition **Document properties contain any of these values** isn't available in the Security &amp; Compliance Center. As a result, you must use Windows PowerShell to add this condition.

You can use the **New\\Set\\Get-DlpCompliancePolicy** cmdlets to work with a DLP policy. You can also use the **New\\Set\\Get-DlpComplianceRule** cmdlets with the **ContentPropertyContainsWords** parameter to add the condition **Document properties contain any of these values**.

Complete the following steps to create the DLP policy and rule for the managed property through PowerShell:

1.  Connect to the [Security &amp; Compliance Center using remote PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?azure-portal=true).
2.  Create the policy by using the **New-DlpCompliancePolicy** cmdlet and apply it to all locations:
    
    ```powershell
    <code>New-DlpCompliancePolicy -Name FCI_PII_policy -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -Mode Enable</code>
    ```
3.  Create the two rules described above by using the **New-DlpComplianceRule** cmdlet. One rule is for the **Low** value, and the other rule is for the **High** and **Moderate** values.
    
    ```powershell
    <code>New-DlpComplianceRule -Name FCI_PII_content-Low -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $false -ContentPropertyContainsWords "Personally Identifiable Information:Low" -Disabled $false -NotifyUser Owner</code>
    ```
    
    ```powershell
    <code>New-DlpComplianceRule -Name FCI_PII_content-High,Moderate -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $true -ContentPropertyContainsWords "Personally Identifiable Information:High,Moderate" -Disabled $false</code>
    ```

> [!NOTE]
> Windows Server FCI includes many built-in properties, including **Personally Identifiable Information**, which was used in this example. The possible values for each property can be different for every organization. The **High**, **Moderate**, and **Low** values used here are only an example. An organization can view the Windows Server FCI classification properties with their possible values in the file Server Resource Manager on the Windows Server–based file server.<br>

By completing these steps, the policy should have two new rules:

 -  One rule blocks access to content when the **Personally Identifiable Information** property equals **High** or **Moderate**.
 -  The second rule sends a notification about content when the **Personally Identifiable Information** property equals **Low**.

Both rules used the **Document properties contain any of these values** condition. This condition won't appear in the UI. However, other conditions, actions, and settings will appear.

The following graphic shows an external user being blocked from accessing a document with a managed property.

:::image type="content" source="../media/blocking-external-sharing-2a2496c1.jpg" alt-text="graphic shows an external user being blocked from accessing a document with a managed property":::
