Microsoft Defender Antivirus helps protect your computer from spyware, malware, and viruses. Microsoft Defender Antivirus also is Hyper-V-aware, which means that can detect whether Windows is running as a virtual machine. Microsoft Defender Antivirus uses definitions to determine if software it detects is unwanted, and it alerts you to potential risks. To help keep definitions up to date, Microsoft Defender Antivirus automatically installs new definitions as they're released.

:::image type="content" source="../media/windows-10-virus-threat-0ace05bb.png" alt-text="Screenshot showing virus and threat protection status, with no current threats.":::


You can use Microsoft Defender Antivirus to run a Quick, Full, Custom, or Offline scan. If you suspect spyware has infected a specific area of a computer, you can customize a scan by selecting specific drives and folders. You also can configure the schedule that Microsoft Defender Antivirus will use.

You can choose to have Microsoft Defender Antivirus exclude processes in your scan. This can make a scan finish more quickly, but your computer will have less protection. When Microsoft Defender Antivirus detects potential spyware activity, it stops the activity, and then it raises an alert.

Alert levels help you determine how to respond to spyware and unwanted software. You can configure Microsoft Defender Antivirus behavior when a scan identifies unwanted software. You also receive an alert if software attempts to change important Windows operating system settings.

To help prevent spyware and other unwanted software from running on a computer, turn on Microsoft Defender Antivirus real-time protection.

Microsoft Defender includes automatic scanning options that provide regular scanning and on-demand scanning for malware. The following table identifies scanning options.

:::row:::
  :::column:::
    **Scan options**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Quick**
  :::column-end:::
  :::column:::
    View detailed configuration information. Checks the areas that malware, including viruses, spyware, and unwanted software, are most likely to infect.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Full**
  :::column-end:::
  :::column:::
    Checks all files on your hard disk and all running programs.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Custom**
  :::column-end:::
  :::column:::
    Enables users to scan specific drives and folders.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Microsoft Defender Offline**
  :::column-end:::
  :::column:::
    Reboots the device and runs a scan outside the Windows kernel.
  :::column-end:::
:::row-end:::


As a best practice, you should schedule a daily Quick scan. At any time, if you suspect that spyware has infected a computer, run a Full scan. When you run a scan, the progress displays on the Microsoft Defender Home page. When Microsoft Defender detects a potentially harmful file, it moves the file to a quarantine area, and it doesn't allow it to run or allow other processes to access it. Once the scan is complete, you can perform the following steps. You can select **Remove or Restore Quarantined items** and to maintain the Allowed list, and then a list of Quarantined items is available from the Settings page. Select **View** to see all items. Review each item, and then individually **Remove** or **Restore** each. Alternatively, if you want to remove all Quarantined items, select **Remove All**.

> [!NOTE]
> Don't restore software with severe or high alert ratings because it can put your privacy and your computer’s security at risk.

If you trust detected software, stop Microsoft Defender from alerting you to risks that the software might pose by adding it to the Allowed list. If you decide to monitor the software later, remove it from the Allowed list.

The next time Microsoft Defender alerts you about software that you want to include in the Allowed list, you can perform the following steps. In the **Alert** dialog box, on the Action menu, select **Allow**, and then select **Apply actions**. Review and remove software that you've allowed from the **Excluded files and locations** list on the **Settings** page.

By using Microsoft Defender Offline, you can boot and run a scan from a trusted environment, rather than running Microsoft Defender Antivirus from a fully booted Windows environment. Microsoft Defender Offline runs separate from the Windows kernel and can target malware that bypasses the Windows shell, including malware that may infect or overwrite a computer’s master boot record (MBR). Microsoft Defender Offline can be launched with a single button from the Microsoft Defender Antivirus client.

Microsoft Defender Antivirus includes 12 Windows PowerShell cmdlets that you can use to perform various tasks. The following table lists these cmdlets.

:::row:::
  :::column:::
    **Cmdlet**
  :::column-end:::
  :::column:::
    **Function**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Add-MpPreference**
  :::column-end:::
  :::column:::
    Modify Microsoft Defender Antivirus settings.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Get-MPComputerStatus**
  :::column-end:::
  :::column:::
    View status of antimalware software.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Get-MPPreference**
  :::column-end:::
  :::column:::
    View Microsoft Defender Antivirus scan and update preferences.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Get-MpThreat**
  :::column-end:::
  :::column:::
    View threat detection history.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Get-MpThreatCatalog**
  :::column-end:::
  :::column:::
    View list of known threats from the definitions catalog.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Get-MpThreatDetection**
  :::column-end:::
  :::column:::
    View active and previous detected malware threats.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Remove-MpPreference**
  :::column-end:::
  :::column:::
    Remove default actions or exclusions.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Remove-MpThreat**
  :::column-end:::
  :::column:::
    Remove an active threat.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Set-MpPreference**
  :::column-end:::
  :::column:::
    Configure Microsoft Defender Antivirus scan and update preferences.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Start-MpScan**
  :::column-end:::
  :::column:::
    Trigger a scan on the computer.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Start-MpWDOScan**
  :::column-end:::
  :::column:::
    Trigger a Microsoft Defender Offline scan.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Update-MpSignature**
  :::column-end:::
  :::column:::
    Update a computer’s antimalware definitions.
  :::column-end:::
:::row-end:::


In addition to using Windows PowerShell to trigger a Microsoft Defender Antivirus scan, you also can use the mpcmdrun.exe command from the cmd.exe environment to trigger a scan. For example, to trigger a quick scan, run the following command:

```cmd
mpcmdrun.exe -scan -scantype 1
```

To discover all command-line options for this tool, use the following command:

```cmd
mpcmdrun.exe /?
```

### Additional features in Microsoft Defender Antivirus

Microsoft Defender Antivirus includes the following additional features:

 -  **Block at First Sight**. This cloud protection feature allows Microsoft Defender Antivirus to rapidly identify and block new malware. You enable Block at First Sight through Group Policy. When you enable this feature, both cloud-based protection and Automatic sample submission will be turned on.
 -  **Detect and Block Potentially Unwanted Applications**. This feature enables you to block unwanted software during downloading and installation times. For example, you can block software that is bundled with other downloads, advertisement injection software, and driver and registry optimizers. The Detect and Block Potentially Unwanted Applications feature is available to enterprise users whose client infrastructure you manage by using Endpoint Configuration Manager or Intune.
 -  **Microsoft Defender for Endpoint**. This cloud-based online service assists organizations in detecting, investigating, and responding to advanced persistent threats. Microsoft Defender for Endpoint provides behavior-based advanced attack detection, a forensic timeline, and a unique threat intelligence knowledge base.
