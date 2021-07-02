When installing Office Professional 2016 or Microsoft 365 Apps for enterprise, the Office Telemetry Dashboard comes pre-installed with the suite. For earlier versions of Office, the dashboard must be manually deployed as an add-on. The Office Telemetry Dashboard Getting Started worksheet provides a step-by-step installation guide and links to supporting documents that described in detail how to configure all the required Office Telemetry components.

> [!NOTE]
> The Office Telemetry Dashboard Getting Started spreadsheet can be found by starting the Office Telemetry Dashboard in the Office 2016 Tools folder. This spreadsheet comes with two worksheet tabs, the Getting Started worksheet and the Telemetry Dashboard Guide worksheet.

Complete the following steps to install and configure Office Telemetry:

1.  **Prepare the database.** The first step is to deploy SQL Server (Express or full version), or to connect to an existing SQL Server installation. If a new database is necessary, the Getting Started worksheet provides download links for the SQL Server Express Edition. When configuring the database, Mixed Mode authentication can't be selected because the Office Telemetry Dashboard doesn't support SQL Server authentication.
2.  **Set up the Office Telemetry Processor.** The second step is to set up the Office Telemetry Processor, which reads information that Office Telemetry Agents store in the shared folder. It then connects and adds records to the Office Telemetry database. The Office Telemetry Processor setup wizard installs the processor, sets up the share, and makes the database connection.
3.  **Deploy Office Telemetry Agents.** The third step is to deploy any required agents for versions that are older than Office 2013. The Getting Started worksheet provides download links for x86 and x64 Office Telemetry Agents. Agents can be deployed by using scripts, Group Policy, electronic software distribution, or the application virtualization management features of Configuration Manager.
4.  **Configure Office Telemetry Agents.** The fourth step is to configure Office Telemetry Agents and enable data logging. The Getting Started worksheet provides a download link for the Office 2016 Administrative Template files. The office16.admx file and the language-specific office16.adml file should be imported into the Active Directory domain for use with Group Policy Management tools. The Office Telemetry Group Policy settings cover the following options:
    
     -  Enabling data collection.
     -  Enabling data upload to the shared folder.
     -  Location or Universal Naming Convention (UNC) path of the shared folder the client will use to store its data.
     -  Any applications or solutions to ignore during data collection.
     -  Custom tags to use to help during data viewing. These tags can include user location, department, and Active Directory security group.
     -  Enabling privacy settings.
    
    When the Group Policy settings have been deployed to Office clients, the telemetry configuration is complete and data collection will begin. The final two steps listed below are post-configuration steps that are included in the Getting Started worksheet.
5.  **Connect the dashboard to the database.** The fifth step in the Getting Started worksheet is to connect the dashboard to the database. This step creates and populates other worksheets. It's also required to enable viewing of the data.
6.  **Configure required privacy settings.** The final configuration step is to optionally configure any required privacy settings. By default, data collection includes full file names, file paths, and document titles. However, this information can be obscured if an organization doesn't want to make it available for some of its administrators. If the **Turn on privacy settings** in Telemetry Agent Group Policy setting is enabled, file names, file paths, and titles will be obscured. For example, a document named Merger\_Contoso.docx will be recorded as Me\*\*\*\*\*\*\*\*.docx in the shared folder, and the document's location and title will be \[location\]\*\*\*\*\*\*\*\* and \*\*\*\*\*\*\*\*.

:::image type="content" source="../media/configure-office-telemetry-62ef5135.jpg" alt-text="graphic shows the required steps to configure Office Telemetry":::
