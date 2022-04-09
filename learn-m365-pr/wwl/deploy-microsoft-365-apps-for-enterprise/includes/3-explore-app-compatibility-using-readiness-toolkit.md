Most of today’s businesses have some version of Microsoft Office already implemented. These versions include established Office applications such as Microsoft Word, Excel, and Outlook. Many companies have also added macros and add-ins to customize their Office applications. While these macros and add-ins are designed to improve worker productivity, they can create problems for administrators who are planning their Microsoft 365 Apps for enterprise deployment strategy. These problems can be compounded based on the workers’ roles.

To help administrators work through these issues, Microsoft provides the Readiness Toolkit for Office add-ins and Microsoft Visual Basic for Applications (VBA) macros and add-ins. This toolkit can help identify compatibility issues with the VBA macros and add-ins that an organization uses with Office. The Readiness Toolkit includes the Readiness Report Creator, which creates an Excel report with VBA macro compatibility. This report includes add-in readiness information to help your organization assess its readiness to move to Microsoft 365 Apps for enterprise.

The Readiness Toolkit can be downloaded for free at the Microsoft Download Center. It’s recommended that you always download and use the most current version. The Readiness Toolkit checks if you're using the most current version when you run a report. It will then prompt you to download the most current version, if necessary. You don't have to uninstall the older version of the Readiness Toolkit before installing the most current version.

> [!NOTE]
> The Readiness Toolkit doesn't repair or fix the code in your VBA macros. If you create an advanced report, the report provides guidance, when available, for remediating your VBA macro code.

### The Readiness Report Creator

The Readiness Toolkit includes a tool called the Readiness Report Creator. Selecting this tool starts a wizard that creates the Readiness report. There's also a standalone executable that can run from the command line or be used with scripts. This executable is useful if you want to collect readiness information from users throughout your enterprise in a more automated manner. The Readiness Report Creator can scan for VBA macros in Office versions as far back as Office 2003. It can scan the following types of files:

 -  Word
 -  Excel
 -  PowerPoint
 -  Outlook
 -  Access
 -  Project
 -  Visio
 -  Publisher

It can also scan for certain types of add-ins used with Office. Add-ins for all Office applications are identified, but web add-ins aren't included.

**Additional reading.** For more information, see[ File extensions analyzed for VBA macros](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#BKMK_FileExt?azure-portal=true).

After the Readiness Report Creator has finished running, the Toolkit generates an Excel spread sheet with an overview of all the files scanned during the assessment.

The following image shows the overview page of the Readiness Report Creator.

:::image type="content" source="../media/office-readiness-report-a210c46b.png" alt-text="screenshot of the Office Readiness report":::


The Excel spread sheet that’s created by the Readiness Toolkit includes the following workbook tabs:<br>

 -  **Overview.** This tab provides access to reports that assess the results of the VBA macros and add-ins found on the company’s devices. You can review each report by selecting the View VBA/Add-in Report buttons located inside this tab.
 -  **VBA Overview.** This tab displays a pie chart of each VBA found on all scanned files, and it includes a readiness assessment. You can define the filters in this tab by Office version and bit version.
 -  **VBA Summary.** This tab displays the raw data table that's used to generate the reports in the VBA Overview tab.
 -  **VBA Results.** This tab displays information on each file scanned by the Readiness Report Creator. If multiple issues are found in a scanned file, there's a separate row for each issue.
 -  **VBA Remediation.** This tab provides proposed changes to VBA macro code found during the scan.
 -  **VBA References.** This tab lists any references that were identified in VBA macro code and in the VBA project. These references are used to call external DLLs, linked files, and ODBC connections for use by the VBA code.
 -  **Add-in Summary.** This tab displays a high-level overview of the add-ins found by the report. The data at the top of the worksheet should give you a quick assessment of:
    
     -  how many add-ins will likely be compatible with Microsoft 365 Apps.
     -  how many add-ins you must do more research on.
 -  **Add-in Details.** This tab displays metadata information about the add-ins found (for example, publisher and version number), the total number of installs of each add-in, and the readiness status.
 -  **By computer name.** This tab displays information similar to what’s on the Add-in Details worksheet. But while the Add-in Details worksheet displays the total number of installs for each add-in, this tab lists every computer in which the add-ins are installed.

### Configure the readiness report

Before an organization's Enterprise Administrator creates a readiness report, they must first determine the type of information to be collected. For example, the admin may ask questions such as:

 -  Are the files local, or do they belong to a network share?
 -  Because the Readiness Toolkit can't scan web documents, is there a previous readiness report to compare the results to?
 -  Is the Office Telemetry Dashboard being used to assess the organization's add-compatibility?

Questions such as these will help determine the type of report that an organization wants to generate.

> [!TIP]
> Before installing and using the Readiness Toolkit, see the [Requirements and limitations of the Readiness Toolkit.](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#creating-a-readiness-report?azure-portal=true)

The following image shows the Readiness Toolkit web UI.

:::image type="content" source="../media/readiness-toolkit-19e44296.png" alt-text="screenshot of the Readiness Toolkit web user interface":::


To configure the organization's readiness report, the Enterprise Administrator must:

 -  Select the information that will be used to create the report.
 -  Specify a location to save the report.
 -  Choose whether to create a basic report or an advanced report.

### Choose the information that will be used to create your report

To create a readiness report, you must first select what information to use to create the report. The following table lists the possible options and an explanation of each option. It also specifies which type of readiness report is created with each option.

:::row:::
  :::column:::
    **Option**
  :::column-end:::
  :::column:::
    **Explanation**
  :::column-end:::
  :::column:::
    **Report created**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Most recently used Office documents and installed add-ins on this computer

  :::column-end:::
  :::column:::
    The Readiness Report Creator only scans Office documents that are in the user's list of most recently used files. This design allows you to narrow the focus of the scan to documents that a user regularly accesses.

In addition, the Readiness Report Creator looks for any add-ins for Office that are installed on the computer on which the Readiness Report Creator is run.

  :::column-end:::
  :::column:::
    VBA and Add-in

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office documents in a local folder or network share.

  :::column-end:::
  :::column:::
    The Readiness Report Creator scans the Office documents in the folder or network share that you specify. The Readiness Report Creator automatically scans the specified location, and all the subfolders in that location.

Note: With this option, the Readiness Report Creator doesn't look for add-ins installed on the computer on which the Readiness Report Creator is run.

  :::column-end:::
  :::column:::
    VBA only

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Previous readiness results saved together in a local folder or network share.

  :::column-end:::
  :::column:::
    This option allows you to create a consolidated report comprised of individual readiness results from multiple standalone computers.

For example, you might want to run the Readiness Report Creator on all the computers in the Finance department, saving the results of each scan to a network share. Then, you can use this option to create a consolidated report for the Finance department.

For more information, see [Getting readiness information for multiple users in an enterprise](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#BKMK_Enterprise?azure-portal=true).

  :::column-end:::
  :::column:::
    VBA only, or VBA and Add-in, depending on what readiness results are being used.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Add-in data from Office Telemetry Dashboard.

  :::column-end:::
  :::column:::
    If you're already using Office Telemetry Dashboard to assess add-in compatibility, you can use the information that you've already collected to create a readiness report. You just need to provide the Readiness Report Creator with the appropriate information to access the database for Office Telemetry Dashboard.

With this option, the Readiness Report Creator doesn't look for VBA macros. GRANT SELECT access on the database is required for the user to run this option.

  :::column-end:::
  :::column:::
    Add-in only

  :::column-end:::
:::row-end:::


### Choose between a basic and advanced report

After you select what information to use to create your report and specify a location to save your report, you must choose whether to create a basic report or an advanced report. It’s recommended that organizations create an advanced report. This option provides additional information to help assess the compatibility of their VBA macros and add-ins with Microsoft 365 Apps.

For example, in an advanced report, the following extra information is displayed:

 -  **Remediation advice for any issues found in the organization's VBA macros**. This information is shown in a separate worksheet in the report.
 -  **Readiness status for add-ins**. For example, the report may indicate the software provider has a supported version of the add-in for Microsoft 365 Apps.

    > [!NOTE]
    > The readiness status for add-ins is derived from telemetry-based computations and explicit support statements from ISVs.

The Readiness Report Creator contacts Microsoft when it creates the report. This step provides the most up-to-date remediation advice and readiness status. In doing so, some information about an organization's VBA macros and add-ins is sent to Microsoft.

**Additional reading.** For more information about the information that's sent to Microsoft, see [Examples of the information sent to Microsoft when creating an advanced report](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#BKMK_InfoSent?azure-portal=true).

### Readiness report limitations

There's a few limitations about the Readiness Report Creator that you should know about:

 -  The Readiness Report Creator can't scan password protected files. If you try to scan one of these files, the file shows up as "Password protected" in the report.
 -  By default, the Readiness Report Creator can't scan files that are saved in a SharePoint document library, in OneDrive, or in some other type of cloud-based storage location. If you try to scan one of these files, the file shows up as "Cloud-based" in the report. For a possible workaround, see [How to scan cloud-based files](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps#how-to-scan-cloud-based-files?azure-portal=true).
 -  The Readiness Report Creator lists each issue with an Office document in a separate row in an Excel worksheet. Therefore, the Readiness Report Creator can only return 1,046,575 results. If you expect to exceed these limits, it's recommended that you narrow the scope of your report, such as to a specific department.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”