For Windows 10 and later, Microsoft Edge is the default browser experience, and is available for download for Windows 8.1. However, legacy web applications may still exist that were originally written for Internet Explorer 11. While Windows can run both Edge and Internet Explorer at the the same time, Internet Explorer is being retired, and it can be tedious to switch between browsers or remember which browser to use for which web application. Frequently, an organization's desire to upgrade the OS can be blocked due to older browser requirements in a critical LOB web app.

### Microsoft Edge with IE mode

To overcome the hurdle of supporting legacy web applications, Microsoft Edge introduced a feature called IE Mode. IE mode on Microsoft Edge makes it easy to use all of the sites your organization needs in a single browser. It uses the integrated Chromium engine for modern sites, and it uses the Trident MSHTML engine from Internet Explorer 11 (IE11) for legacy sites.

Only those sites that you specifically configure (via policy) will use IE mode, all other sites will be rendered as modern web sites. When a site loads in IE mode, the IE logo indicator displays on the left side of navigation bar. Alternatively, IE Mode can be configured to open with a standalone Internet Explorer 11 window. However, most users prefer when sites open directly within Microsoft Edge in IE mode.

> [!NOTE]
> Internet Explorer provided a feature called Enterprise Mode. This enabled Internet Explorer to runin a compatiblity mode for web apps that were designed for older versions of IE.

#### To enable Internet Explorer Mode in Edge using Intune

1.  In the Endpoint Manager admin center, select **Devices**, then select **Windows** platform, then select **Configuration Profiles**.
2.  Select **Create Profile**.
3.  Enter the following properties:
    
     -  **Platform**: Choose which versions of Windows to include.
     -  **Profile type**: Select **Administrative Templates**.
4.  After providing a name, on the **Configuration Settings tab**, select **All Settings**.
5.  In the Search field, enter **configure internet**. In the results, select **Configure Internet Explorer integration** on the line where **Setting type** is showing as **User**.
6.  In the dialog on the right, set the option to **Enabled**. In the drop-down box, select **Internet Explorer mode**.
7.  Assign and complete the profile.<br>

### Configure IE Mode Sites

Before you can start using either IE Mode, you must create an IE Mode site list and add the individual website domains and domain paths that need to be rendered in a mode other than the default Edge experience.

#### Enterprise Mode Site List Manager

This tool helps you create error-free XML documents with simple n+1 versioning and URL verification. We recommend using this tool if your site list is relatively small. There are two versions of this tool, both supported on Windows 8.1 and Windows 10. We recommend that you only use Enterprise Mode Site List Manager (schema v.2) because the Enterprise Mode schema has been updated to v.2 to be easier to read and to provide a better foundation for future capabilities.

When configuring a site list, all sites that have the element **&lt;open-in&gt;IE11&lt;/open-in&gt;** will now open in IE mode. Sites that have an additional compat-mode tag, such as **&lt;compat-mode&gt;IE7Enterprise&lt;/compat-mode&gt;**, will open using compatibility mode for that browser version.

You can download version 2 of the tool from here: [https://www.microsoft.com/en-us/download/details.aspx?id=49974](https://www.microsoft.com/en-us/download/details.aspx?id=49974).

#### Enterprise Mode Site List Portal

The Enterprise Mode Site List Portal is an open-source web tool on GitHub that allows you to manage your Enterprise Mode site list, hosted by the app, with multiple users. The portal is designed to use IIS and a SQL Server backend, leveraging Active Directory (AD) for employee management.

In addition to all the functionality of the Enterprise Mode Site List Manager tool, the Enterprise Mode Site List Portal helps you:

 -  Manage site lists from any device supporting Windows 8.1 or greater.
 -  Submit change requests.
 -  Operate offline through an on-premises solution.
 -  Provide role-based governance.
 -  Test configuration settings before releasing to a live environment.

Updates to your site list are made by submitting new change requests, which are then approved by a designated group of people, put into a pre-production environment for testing, and then deployed immediately, or scheduled for deployment later.

If your list is too large to add individual sites, or if you have more than one person managing the site list, we recommend using the Enterprise Site List Portal.

### Enable Enterprise Site Mode

After you have created the Enterprise Mode site list, you need to turn on the functionality and set up the system for centralized control. By allowing centralized control, you can create one global list of websites that render using IE Mode or Enterprise Mode.

Microsoft recommends that you store and download your website list from a secure web server (https://), to help protect against data tampering. After the list is downloaded, it's stored locally on your employees' computers so if the centralized file location is unavailable, they can still use Enterprise Mode.

The Enterprise Mode Site list location must also be configured. To do so, follow the same steps as above but search for the **Configure the Enterprise Mode Site List** setting. Enable the setting, and set the **Configure the Enterprise Mode Site List** field to the complete path to the site list file, such as **https://localhost:8080/ESMlist.xml**.

#### Configuring with Group Policy

You can also use Group Policy to configure clients to use IE Mode or Enterprise Mode.

 -  To configure IE Mode: Set **Computer Configuration** &gt; **Administrative Templates** &gt; **Microsoft Edge**&gt; **Configure Internet Explorer integration** to **Enabled**.
 -  If you want to use the same IE website list for both IE and Enterprise mode: Set **Computer Configuration** &gt; **Administrative Templates**&gt; **Windows Components** &gt; **Internet Explorer** &gt; **Use the Enterprise Mode IE website list** to the complete path to the file, such as **https://localhost:8080/ESMlist.xml**.
 -  Alternatively, you can also configure IE mode with a separate policy for Microsoft Edge. This additional policy allows you to override the IE site list. Set **Computer Configuration** &gt; **Administrative Templates**&gt; **Microsoft Edge** &gt; **Configure the Enterprise Mode Site List** to the complete path to the file, such as **https://localhost:8080/IEModelist.xml**.
