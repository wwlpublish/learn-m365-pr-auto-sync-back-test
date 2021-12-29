Once an organization establishes directory synchronization, it may occasionally experience issues with the synchronization or with individual objects syncing. As a result, Messaging administrators must know how to troubleshoot and resolve common sync issues to maintain a healthy sync environment. This unit examines several common sync issues and how to troubleshoot and resolve them.

### Sync fails completely

When an organization's directory synchronizations aren't working, it’s often the result of a backend configuration or communication problem, and less likely a problem with user or group objects. The following list identifies some common issues that cause synchronization to fail:

 -  **The sync service is stopped.** Synchronization relies on the Microsoft Azure AD Sync (ADSync) service. If the service isn’t running, then the sync won’t run. Use your standard troubleshooting steps to validate the status of the service; that is, check the account that it uses to be sure the password hasn’t expired, check to see if the service account is still valid, enabled, and not locked out, and try to start the service. The service depends on the Windows Management Instrumentation service, so you should check that service too. Then, check the System event log for errors related to the service, especially when you try to start it and it fails.
 -  **Connector credentials are invalid.** You can use the Synchronization Services Manager to look at the Connectors tab. You should have at least one connector for your on-premises Active Directory forest and one connector for Azure Active Directory (represented by the \*.onmicrosoft.com domain). Each of the connectors has credentials specified. If one of the accounts gets locked out, disabled, or has a similar problem, then the entire sync might fail to run.
 -  **Configuration is set incorrectly.** For configuration issues related to syncs, the most common issues include:
    
     -  A server is enabled for Staging mode. If this situation occurs, synchronization will fail.
     -  The scheduler is suspended. In this case, the sync won’t run on a schedule.
     -  The sync cycle interval is set to a large number of hours. The default is to sync every 30 minutes, but if the configuration is set to sync every 90 hours, it might appear to not be syncing at all. You can review your existing settings by running the Get-ADSyncScheduler command on the sync server. The following table displays sample output after running this command.

:::row:::
  :::column:::
    **Sync configuration parameter**
  :::column-end:::
  :::column:::
    **Configuration parameter value**
  :::column-end:::
  :::column:::
    **Notes**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    AllowedSyncCycleInterval
  :::column-end:::
  :::column:::
    00:30:00
  :::column-end:::
  :::column:::
    Sync every 30 minutes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    CurrentlyEffectiveSyncCycleInterval
  :::column-end:::
  :::column:::
    00:30:00
  :::column-end:::
  :::column:::
    Sync every 30 minutes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    CustomizedSyncCycleInterval
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    Null by default.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    NextSyncCyclePolicyType
  :::column-end:::
  :::column:::
    Delta
  :::column-end:::
  :::column:::
    Next sync is delta sync.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    NextSyncCycleStartTimeinUTC
  :::column-end:::
  :::column:::
    5/30/2017 3:35:20 PM
  :::column-end:::
  :::column:::
    Next sync date/time in UTC.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PurgeRunHistoryInterval
  :::column-end:::
  :::column:::
    7.00:00:00
  :::column-end:::
  :::column:::
    Keep run history for seven days.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SyncCycleEnabled
  :::column-end:::
  :::column:::
    True
  :::column-end:::
  :::column:::
    Sync is enabled.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MaintenanceEnabled
  :::column-end:::
  :::column:::
    True
  :::column-end:::
  :::column:::
    Built-in process to update both certificates and keys and to purge logs.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    StagingModeEnabled
  :::column-end:::
  :::column:::
    False
  :::column-end:::
  :::column:::
    Server is in active mode.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SchedulerSuspended
  :::column-end:::
  :::column:::
    False
  :::column-end:::
  :::column:::
    Scheduler is active.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SyncCycleInProgress
  :::column-end:::
  :::column:::
    False
  :::column-end:::
  :::column:::
    Sync isn't in progress.
  :::column-end:::
:::row-end:::


### Single user object doesn't sync

When you have a functional sync but you have a single object that doesn’t sync, it typically means there’s a problem with that object. The following common issues result in a single object that fails to sync:

 -  **Duplicate objects in Azure Active Directory.** A duplicate object is any object that has one or more attribute values that match the attribute values of the user object that isn’t syncing. For example, imagine that you have two users. One is named Ana Cantrell. The other is named Anastasia Rojas. Both go by the first name “Ana”. Ana Cantrell has a user account in Azure Active Directory. Anastasia doesn’t. Ana’s user account in Azure Active Directory has a user principal name (UPN) of Ana@Adatum.com. When you try to sync Anastasia’s account, it attempts to use her on-premises UPN of Ana@Adatum.com. However, that UPN already exists, so the sync of the object fails. Or, if you're running a new version of Azure Active Directory, the object will sync but it will require you to fix the duplicate data before using it. You can fix these scenarios by using unique values for the core attributes such as proxyAddresses and UserPrincipalName.
 -  **The object is filtered out.** When you sync objects, you can either sync all objects, or you can sync some objects. There are a few ways to sync a partial set of objects. You can use attribute-based filtering, group-based filtering (although only supported in non-production environments), and OU-level filtering. If an object isn’t syncing and you don’t see errors, you should look at the filtering configuration to find out if the object is in scope. With attribute-based filtering, you can view the **cloudFiltered** attribute. If it’s set to True, then the object won’t sync. If the attribute is empty (null), then it will sync.
 -  **Invalid characters are present on the object.** In this scenario, invalid characters are present on the user object. These invalid characters are often represented in a phone number. You can use the Microsoft IdFix tool to scan and fix these attribute issues before the sync.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.