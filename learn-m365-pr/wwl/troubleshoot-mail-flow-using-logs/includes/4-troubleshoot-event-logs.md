Microsoft Exchange Server generates different event information related to transport services in the Event Viewer. You can use the Event Viewer to view those events and troubleshoot any potential transport issues. Regularly examining the event logs can help Messaging administrators fix problems before they cause an issue or persist too long.

It’s important to properly size the logs so they can preserve more data. Backing up the log files is also critical, especially when historical analysis is needed for troubleshooting issues that persisted earlier.

Event logs can be viewed in the Event Viewer or by running the **Get-EventLog** cmdlet. The **Get-EventLog** cmdlet isn't specific to Exchange Server, but it can be used to gather information about Exchange Server from the event logs.

For example, you would run the following PowerShell command to return the 10 most recent event log entries that have a source of MSExchange Common:

```powershell
Get-EventLog –LogName Application –Source “MSExchange Common” –EntryType Error –Newest 10
```

You can modify the command to return events that contain specific error numbers or words. You can also return data from multiple computers. The following command returns the 10 most recent events from multiple Exchange servers (LON-EX1 and LON-EX2):

```powershell
Get-EventLog –LogName Application –Source “MSExchange Common” –EntryType Error –Newest 10 –ComputerName LON-EX1,LON-EX2
```

You can retrieve all warning and error events quickly from a specific server’s Application log by using the following command:

```powershell
Get-EventLog –ComputerName LON-EX1 –LogName Application –Source –EntryType Error,Warning
```

Furthermore, by running the **Set-Eventloglevel** cmdlet, you can configure a different event log level for a specified event category, such as: Lowest, Low, Medium, High, and Expert. The syntax for the **Set-Eventloglevel** cmdlet is:

```powershell
Set-Eventloglevel -Identity <ECIdParameter> -Level <Lowest | Low | Medium | High | Expert>
```

Besides the Application Logs in the Event Viewer, Exchange Server records specific events to the crimson channel logs under **Applications and Services Logs > Microsoft > Exchange**.

Event log categories for Exchange included in the crimson channel include: ActiveMonitoring, Compliance, DxStoreHA, ESE, HighAvailability, MailboxAssisants, MailboxDatabaseFailureItems, ManagedAvailability, PushNotifications, and Troubleshooters.

Event logs in the Application log that are related to transport issues include the following sources:

 -  **Source MSExchangeADAccess**. Includes events about Active Directory access.
 -  **Source MSExchangeSubmission, MSExchangeDelivery**. Includes events about mail submission and mail delivery services, such as information about mail submission or mail delivery service status (started or stopped).
 -  **Source MSExchangeAntimalware**. Includes events about logging the status of the anti-malware agent.
 -  **SourceMSExchangeTransport**. Includes events about logging the status of the configuration update, configuration of the connectors, authentication failures, TLS certificate validation errors, DNS failure during the send process, and routing issues.
 -  **MS Exchange Messaging Policies**. Includes information about messaging policies features, such as encryption, federation, and certificate validation.
 -  **MSExchange Store Driver Delivery and MSExchange Store Driver Submission**. Includes events about failures in mail delivery and submission processing.
 -  **MSExchangeTransportLogSearch**. Includes information about Active Directory access, insufficient permissions, message tracking log corrupted, and the Transport Log Search service failing to start.
