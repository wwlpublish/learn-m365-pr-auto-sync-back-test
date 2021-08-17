The Office Telemetry Dashboard is an on-premises tool that collects inventory, usage, and health data about the Office documents and solutions, such as add-ins, used in an organization. The data is primarily designed to help an organization with application compatibility testing. Data that's collected for the Office Telemetry Dashboard is stored in a SQL Server database that's controlled by the organization. The collected data is NOT sent to Microsoft. Data collected for the Office Telemetry Dashboard is different than Office diagnostic data, which can be sent to Microsoft. The settings used to manage the Office Telemetry Dashboard have no impact on Office diagnostic data.

Office Telemetry provides inventory, usage, and monitoring tools for Office 2003 and later. Data is collected whenever a user opens, edits, or closes a monitored document type. When certain errors occur in applications in Office 2013 later, Office Telemetry can create records that include a description of the problem and a link to more information. Office Telemetry then aggregates this data in a central database for reporting and viewing. You can view data by using an Excel solution, the Office Telemetry Dashboard, and the Office Telemetry Log.

> [!NOTE]
> An advantage of installing the 32-bit version of Microsoft 365 Apps for enterprise is the added functionality of all the add-ins that are installed and its use with Office applications. With the Office Telemetry Dashboard, the use of these add-ins can be measured.

There are five components of the Office Telemetry Dashboard:

 -  **The Office Telemetry Dashboard itself.** The Office Telemetry Dashboard is an Excel workbook that is configured to connect to a database. It's installed together with Microsoft 365 Apps for enterprise, Office Professional Plus 2019, Office Professional Plus 2016, and Office Standard 2016. To view the Office Telemetry Dashboard, you must have Excel 2019 or Excel 2016 installed.
 -  **The Office Telemetry Processor.** Office Telemetry Processor runs on one or more computers and collects inventory, usage, and health data from the shared folder. It then imports the data to the database. The processor is installed as a Windows service named "Office Telemetry Processor," and the processor supports Transport Layer Security (TLS) 1.2.
 -  **The Office Telemetry Agent.** Office Telemetry agents are built into Office 2013 Professional, Office 2016 Professional, and Microsoft 365 Apps for enterprise. If you enable data collection, information about installed add-ins, the most recently used documents, and application event data is written to the Office Telemetry Logs and Office Telemetry Database. However, for Office 2003, Office 2007, and Office 2010, you must first deploy an agent. This agent collects information about add-ins and recently used documents, but it doesn't provide application event data.
 -  **SQL Server.** SQL Server must be deployed before the Office Telemetry Dashboard can be configured. An existing database isn't needed, but one of these versions of SQL Server must either be installed or accessible:
    
     -  SQL Server 2016 or SQL Server 2016 Express
     -  SQL Server 2014 or SQL Server 2014 Express
     -  SQL Server 2012 or SQL Server 2012 Express
     -  SQL Server 2008 R2 or SQL Server 2008 R2 Express Edition
     -  SQL Server 2008 or SQL Server 2008 Express Edition
     -  SQL Server 2005 or SQL Server 2005 Express Edition
 -  **A shared folder.** This folder stores data that is uploaded by Office Telemetry Agents installed on client computers. The folder must be stored on-premises and not in the cloud. It can be located on the same computer as other components.

### Telemetry operations

‎Before data collection can begin, Office Telemetry client functionality must be enabled, whether its built into Microsoft 365 Apps for enterprise (formerly Office 365 ProPlus) or deployed to previous versions of Office. The Office Telemetry client must be enabled through Group Policy or by editing the local registry. Data collection runs as a scheduled task and requires domain membership.

Office client data is first sent to a shared folder on the network (cloud storage isn't an option for this data). This folder must be accessible to all clients and users. The Office Telemetry processing service, known as the Office Telemetry Processor, runs on a domain-joined computer running Windows Server 2008 or newer. This service then reads the data and sends it to the Office Telemetry database.

> [!NOTE]
> The telemetry processor can run in test or small environments on Windows 10, Windows 8, or Windows 7. It's also possible to run the processor on a workgroup computer by using a workaround. The Office Telemetry database requires Microsoft SQL Server 2005 and newer versions. It can be run on Microsoft SQL Express editions in test or small environments.

> [!NOTE]
> A single computer can be used for each of the Office Telemetry components: database, share, and processor.

The Office Telemetry Dashboard is an Excel 2016 tool that installs automatically as part of Office Professional Plus 2016 and Microsoft 365 Apps for enterprise installations. The dashboard appears in the Tools folder under the Microsoft Office 2016 Start Menu folder. The dashboard connects to the database to enable combined views of telemetry data. Multiple users can use the dashboard to view the data.

The Office Telemetry Log is a tool for developers and experienced users who want to diagnose compatibility issues on a specific Office 2016 client. As with the dashboard, the Office Telemetry Log is also in the Office 2016 Tools folder and requires Excel 2016. It automatically installs with Office Professional Plus 2013, Office Professional 2016, and Microsoft 365 Apps for enterprise. However, unlike the dashboard, the Office Telemetry Log connects to the local data store on the client, and not the central database.

The following graphic shows the important steps involved in collecting telemetry data from clients.

:::image type="content" source="../media/collect-telemetry-data-c8286e16.jpg" alt-text="graphic shows the important steps involved in collecting telemetry data from clients":::


### Office Telemetry uses

‎A key function of Office Telemetry is to help when planning an upgrade to Microsoft 365 Apps for enterprise. By deploying agents to computers that run existing Office editions, collected data can provide inventory information, and identify the business-critical Office documents and solutions in the organization. These solutions can then be ranked for compatibility testing with the newest version of Microsoft 365 Apps for enterprise.

Collecting this data before a Microsoft 365 Apps for enterprise rollout provides the information needed to help with capacity and license planning. Data collection also helps to ensure that Microsoft 365 Apps for enterprise network and storage performance will be within acceptable limits. Office Telemetry can also be used after a Microsoft 365 Apps for enterprise rollout to:

 -  monitor performance against targets.
 -  monitor user adaption of new features.
 -  identify errors and problems with Office solutions.

### Telemetry management

‎Telemetry data collection is managed separately for each client through Group Policy settings. Office 2016 administrative templates include these settings, as part of Office16.admx and Office16.adml. They're located under the User Configuration\\Administrative Templates\\Microsoft Office 2016\\Telemetry Dashboard node.

If you can't use Group Policy, you can configure these settings on the local computer by editing the registry, or by deploying registry files. There are also several telemetry test settings that update only through the registry editor.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”