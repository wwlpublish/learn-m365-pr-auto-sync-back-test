The **Defender for Office 365 Message Disposition** report (formerly the ATP Message Disposition report) displays the actions that were taken on email messages that had malicious URLs or files.

> [!NOTE]
> Microsoft Defender for Office 365 must be enabled, and Safe Links policies and Safe Attachments policies must be configured for data to appear in this report.

To view this report, go to the Security &amp; Compliance Center and then select **Reports &gt; Dashboard &gt; Defender for Office 365 Message Disposition.**

:::image type="content" source="../media/atp-message-disposition-report-widget-60f35ed3.png" alt-text="screenshot of the message disposition report tile.":::


Select the **Defender for Office 365 Message Disposition** tile to open it in a new browser window. This window will display a more detailed view of the report. Below the chart, you'll see a list of detected messages and the actions that were taken. These actions were based on the policies that were defined for your organization.

### Report view for the Defender for Office 365 message disposition report

The following views are a sample of the views available for the Defender for Office 365 Message Disposition report:

 -  **View data by: Message.** The chart contains the following information:
    
     -  Block access
     -  Messages replaced
     -  Messages monitored
     -  Replaced by Dynamic Email Delivery<br><br>If you select **Filters**, you can modify the report with the following filters:
        
         -  Start date and End date
         -  The same message disposition values that are available in the chart, and the additional Messages passed value.

    :::image type="content" source="../media/atp-file-types-report-message-view-974b956e.png" alt-text="screenshot of the file types report message view.":::


 -  **View data by: File.** The chart contains the following information:
    
     -  Malicious Excel attachments
     -  Malicious Flash attachments
     -  Malicious PDF attachments
     -  Malicious PowerPoint attachments
     -  Malicious URLs
     -  Malicious Word attachments
     -  Malicious executable attachments
     -  Others<br><br>If you select **Filters**, you can modify the report with the following filters:
        
         -  Start date and End date
         -  The same message disposition values that are available in the chart, and the additional Messages passed value.

    :::image type="content" source="../media/atp-file-types-report-file-view-47c3624e.png" alt-text="screenshot of the file types report file view.":::


> [!NOTE]
> When you hover over a particular day (data point), you can see the breakdown of types of malicious files that were detected by Safe Attachments and anti-malware protection in EOP.
