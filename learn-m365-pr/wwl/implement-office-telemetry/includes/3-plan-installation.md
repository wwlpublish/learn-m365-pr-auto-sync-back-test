When planning for Office Telemetry, it's important to consider typical Telemetry deployment requirements and issues, including:

 -  **Network and Security setup.** The computers that run the Office Telemetry Processor, shared folder, and SQL database must be domain-joined. This design enables organizations to configure the appropriate security settings. If there's a firewall between the dashboard and the telemetry database, the SQL port in the firewall configuration must be enabled. The default port for SQL Server is 1433.

    > [!IMPORTANT]
    > Don't forget to check the user permission role for the Office Telemetry Dashboard. Ensure that you've added the user to the **td\_readonly** role.

 -  **Infrastructure issues.** Various telemetry infrastructure issues can affect successful deployment. Examples include a corrupt telemetry database, and connectivity issues between agent and shared folder, between the telemetry processor and the database, or between the telemetry dashboard and the database.
 -  **Unreported data.** For various reasons, there may be Office data that never goes to the shared folder. As such, this data will never be stored in the database. For example, offline machines or mobile machines that can't receive Group Policy may never be enabled for data logging or reporting back their data. ‎If computers that are running versions older than Office 2013 are overlooked, it can be assumed that all computers running Office are reporting data. However, if agents haven't been deployed, data will never be sent. Office 2013 and later have agents automatically installed, but earlier Office packages don't. Windows XP–based computers don't support the Office Telemetry Agent scheduled task; as such, they only report data at each user sign-in.
 -  **Missing data.** It's important to remember that data reporting is a background activity, and that after the random initial upload interval, Office Telemetry collects data only every eight hours. Given this data collection interval, it may take some time before all computers are reporting data.
 -  **Performance and capacity planning.** Telemetry performance can be maximized by setting data thresholds so that only essential information is reported. Thresholds can be set by using the Telemetry Dashboard Administration Tool (exe). When planning for capacity, note the following data collection upload sizes:
    
     -  **Microsoft 365 Apps for enterprise.** Typically 64 KB at each upload.
     -  **Office 2003+.** Typically 50 KB at each upload.
    
    Even with these small upload sizes, significant data collections can result in larger organizations. For example, 25,000 users reporting data over an eight-hour period can result in 11 GB of data. Make sure that all computers with installed agents have at least 11 GB of free space for temporary storage of this data.
