Exchange Server uses monitoring and management concept called Workload Management. An Exchange workload is an Exchange Server feature, protocol, or service that’s been explicitly defined for the purposes of Exchange system resource management.

Each Exchange Server workload consumes system resources. You can manage these workloads in the following ways:

 -  **Monitor system resources**. Messaging administrators should monitor the resources used by each Exchange Server workload. Examples of system resources that can be monitored include:
    
     -  CPU usage
     -  Memory consumption
     -  Mailbox database operations
     -  Network utilization
     -  Active Directory requests

    If server resources are highly used, Exchange Server progressively slows down the lowest priority workloads. Priorities are defined by the classification assigned to each workload: Urgent, Customer Expectation, Internal Maintenance, and Discretionary. Urgent classification has the highest priority and Discretionary classification has the lowest priority. System resource thresholds, which measure utilization, have three levels: Underloaded, Overloaded, and Critical.

 -  **Control how individual users consume resources**. This method of managing workloads introduces different types of workload usage by users, including:
    
     -  **Burst allowances**. Exchange Server allows users to have greater resource consumption for short periods of time without throttling.
     -  **Recharge rate**. Exchange server uses a resource budget system, where administrators set a rate where users’ budgets are recharged in defined periods of time. For example, a value of 300,000 milliseconds means that users’ budgets are recharged on five minutes of usage per hour.
     -  **Traffic shaping**. Exchange Server delays the user whenever a user reaches the configured limit for the defined time interval. This type of workload usage prevents users from overloading the performance of the server. Users’ business tasks usually aren't affected because the delays are short and almost undetectable.
     -  **Maximum usage**. Exchange Server temporarily blocks users from completing their tasks when they've reached their threshold in resource usage. Users are unblocked the moment their budget is recharged.

Exchange workload management, which was previously known as User Throttling, is configured in the Exchange Management Shell. Messaging administrators can create or change workload management policy settings by using various PowerShell cmdlets. These settings can be configured at the organizational level and applied to all Exchange Servers in the organization. They can also be configured at the individual Exchange Server level and applied only to that server.

The PowerShell cmdlets used to manage resource policies include:

 -  New-ResourcePolicy
 -  Remove-ResourcePolicy
 -  Get-ResourcePolicy
 -  Set-ResourcePolicy

The cmdlets used to manage workload management policies include:

 -  New-WorkloadManagementPolicy
 -  Remove-WorkloadManagementPolicy
 -  Get-WorkloadManagementPolicy

The cmdlets used to manage workload policies include:

 -  New-WorkloadPolicy
 -  Remove-WorkloadPolicy
 -  Get-WorkloadPolicy
 -  Set-ResourcePolicy

The cmdlets used to manage and assign throttling policies include:

 -  New-ThrottlingPolicy
 -  Get-ThrottlingPolicy
 -  Set-ThrottlingPolicy
 -  Remove-ThrottlingPolicy
 -  Get-ThrottlingPolicyAssociation
 -  Set-ThrottlingPolicyAssociation

### Workload management examples

To display current workload management policies, you should use the following cmdlet:

```powershell
Get-WorkloadManagementPolicy
```

To change the default workload management policy for your organization’s Outlook Web App workload, you should run the following command:

```powershell
New-WorkloadPolicy OrgOWAWorkloadPolicy -WorkloadType OWA -WorkloadClassification Discretionary -WorkloadManagementPolicy GlobalOverrideWorkloadManagementPolicy
```

To create a workload management policy for Outlook on the Web for a specific server, you should complete the following steps:

1.  Create a custom workload management policy that will later be applied to a specific server (see step \#3) by running the following command:
    
    ```powershell
    New-WorkloadManagementPolicy LondonWorkloadManagementPolicy
    ```
2.  Create a new Outlook Web App workload policy by running the following command:
    
    ```powershell
    New-WorkloadPolicy LondonOWAWorkloadPolicy -WorkloadType OWA -WorkloadClassification Discretionary -WorkloadManagementPolicy LondonWorkloadManagementPolicy
    ```
3.  Apply the custom workload management policy you created in step \#1 to a specific server by running the following command:
    
    ```powershell
    Set-ExchangeServer -WorkloadManagementPolicy LondonWorkloadManagementPolicy -Identity EXCH1
    ```

It's recommended that you never modify the default throttling policy. Changes to the default policy can be overwritten by future Exchange updates. Instead, you should create custom throttling policies that contain customized settings.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.