Most of today’s businesses have some version of Microsoft Office already implemented, using established Office applications such as Microsoft Word, Excel, and Outlook. Many companies have added macros and add-ins to customize these applications to improve the productivity of their workers. These add-ins and macros can create problems for administrators who are determining their Microsoft 365 Apps for enterprise deployment strategy. These problems can be compounded based on the workers’ role.

The Readiness Toolkit for Office add-ins and VBA can help you identify compatibility issues with your Microsoft Visual Basic for Applications (VBA) macros and add-ins that you use with Office. The Readiness Toolkit includes the Readiness Report Creator, which creates an Excel report with VBA macro compatibility. This report includes add-in readiness information to help your organization assess its readiness to move to Microsoft 365 Apps for enterprise.

The Readiness Toolkit can be downloaded for free at the Microsoft Download Center. It’s recommended that you always download and use the most current version. The Readiness Toolkit checks if you're using the most current version when you run a report, and it will prompt you to download the most current version if necessary. You don't have to uninstall the older version of the Readiness Toolkit before installing the most current version.

> [!NOTE]
> The Readiness Toolkit doesn't repair or fix the code in your VBA macros. If you create an advanced report, the report provides guidance, when available, for remediating your VBA macro code.

### Creating the readiness report

The Readiness Toolkit includes a tool called the Readiness Report Creator. Selecting this tool starts a wizard that creates the Readiness report. There's also a standalone executable that can run from the command line or be used with scripts. This executable is useful if you want to collect readiness information from users throughout your enterprise in a more automated manner. The Readiness Report Creator can scan for VBA macros in Word, Excel, PowerPoint, Outlook, Access, Project, Visio, and Publisher files, for Office versions as far back as Office 2003. It can also scan for certain types of add-ins used with Office. Add-ins for all Office applications are identified, but web add-ins aren't included.

**Additional reading.** For more information, see[ File extensions analyzed for VBA macros](https://docs.microsoft.com/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#BKMK_FileExt?azure-portal=true).

After the Readiness Report Creator has finished running, the Toolkit will generate an Excel spread sheet with an overview of all the files scanned during assessment.

The following image shows the overview page of the Readiness Report Creator.

:::image type="content" source="../media/office-readiness-report-a210c46b.png" alt-text="screenshot of the Office Readiness report":::


The Excel spread sheet that’s created by the Readiness Toolkit includes the following workbook tabs:<br>

 -  **Overview.** This tab provides access to reports that assess the results of the VBA macros and add-ins found on the company’s devices. You can review each report by selecting the View VBA/Add-in Report buttons located inside this tab.
 -  **VBA Overview.** This tab displays a pie chart of each VBA found on all scanned files, and it includes a readiness assessment. You can define the filters in this tab by Office version and bit version.
 -  **VBA Summary.** This tab displays the raw data table that's used to generate the reports in the VBA Overview tab.
 -  **VBA Results.** This tab displays information on each file scanned by the Readiness Report Creator. If multiple issues are found in a scanned file, there's a separate row for each issue.
 -  **VBA Remediation.** This tab provides proposed changes to VBA macro code found during the scan.
 -  **VBA References.** This tab lists any references that were identified in VBA macro code and in the VBA project. These references are used to call external DLLs, linked files, and ODBC connections for use by the VBA code.
 -  **Add-in Summary.** This tab displays a high-level overview of the add-ins found by the report. The data at the top of the worksheet should give you a quick assessment of how many add-ins will likely be compatible with Microsoft 365 Apps and how many add-ins you must do more research on.
 -  **Add-in Details.** This tab displays metadata information about the add-ins found (for example, publisher and version number), the total number of installs of each add-in, and the readiness status.
 -  **By computer name.** This tab displays information similar to what’s on the Add-in Details worksheet. But while the Add-in Details worksheet displays the total number of installs for each add-in, this tab lists every computer in which the add-ins are installed.

### Configuring the readiness report

Before creating a readiness report, an organization's Enterprise Administrator must first determine the type of information they want to collect. For example, the admin may ask questions such as:

 -  Are the files local, or do they belong to a network share?
 -  Because the Readiness Toolkit can't scan web documents, is there a previous readiness report to compare the results to?
 -  Is the Office Telemetry Dashboard being used to assess the organization's add-compatibility?

Questions such as these will help determine the type of report that an organization wants to generate.

> [!TIP]
> Before installing and using the Readiness Toolkit, see the [requirements and limitations of the Readiness Toolkit.](https://docs.microsoft.com/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#creating-a-readiness-report?azure-portal=true)

The following image shows the Readiness Toolkit web UI.

:::image type="content" source="../media/readiness-toolkit-19e44296.png" alt-text="screenshot of the Readiness Toolkit web user interface":::


After selecting the information that will be used to create the organization's report, the Enterprise Administrator must specify a location to save the report and choose whether to create a basic report or an advanced report.

It’s recommended that organizations create an advanced report, which provides additional information to help assess the compatibility of their VBA macros and add-ins with Microsoft 365 Apps. For example, in an advanced report, the following extra information is displayed:

 -  Remediation advice for any issues found in the organization's VBA macros. This information is shown in a separate worksheet in the report.
 -  Readiness status for add-ins. For example, the report may indicate the software provider has a supported version of the add-in for Microsoft 365 Apps.

    > [!NOTE]
    > The readiness status for add-ins is derived from telemetry-based computations and explicit support statements from ISVs.

To provide you with the most up-to-date remediation advice and readiness status, the Readiness Report Creator contacts Microsoft when it creates the report. Some information about your VBA macros and add-ins is sent to Microsoft.

**Additional reading.** For more information about the information that's sent to Microsoft, see [Examples of the information sent to Microsoft when creating an advanced report](https://docs.microsoft.com/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#BKMK_InfoSent?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”