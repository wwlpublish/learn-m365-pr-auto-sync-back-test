Cloud Discovery analyzes your traffic logs against the Microsoft Defender for Cloud Apps catalog of over 25,000 cloud apps. The apps are ranked and scored based on more than 90 risk factors. This design provides you with ongoing visibility into cloud use, Shadow IT, and the risk Shadow IT poses into your organization.

### Snapshot and continuous risk assessment reports

Organizations can generate the following types of reports in Cloud Discovery:

 -  **Snapshot reports**. Provides ad-hoc visibility on a set of traffic logs you manually upload from your firewalls and proxies.
 -  **Continuous reports**. Analyze all logs that are forwarded from your network using Microsoft Defender for Cloud Apps. They provide improved visibility over all data, and automatically identify anomalous use using either the Machine Learning anomaly detection engine or by using custom policies that you define. These reports can be created by connecting in the following ways:
    
     -  **Microsoft Defender for Endpoint integration**. Microsoft Defender for Cloud Apps integrates with Microsoft Defender for Endpoint natively, to simplify rollout of Cloud Discovery, extend Cloud Discovery capabilities beyond your corporate network, and enable machine-based investigation.
     -  **Log collector**. Log collectors enable you to easily automate log upload from your network. The log collector runs on your network and receives logs over Syslog or FTP.
     -  **Secure Web Gateway (SWG).** If you work with both Microsoft Defender for Cloud Apps and one of the following SWGs, you can integrate the products to enhance your security Cloud Discovery experience:
        
         -  [Zscaler integration](/defender-cloud-apps/zscaler-integration?azure-portal=true)
         -  [iboss integration](/defender-cloud-apps/iboss-integration?azure-portal=true)
         -  [Corrata integration](/defender-cloud-apps/corrata-integration?azure-portal=true)
         -  [Menlo Security integration](/defender-cloud-apps/menlo-integration?azure-portal=true)

        When Microsoft Defender for Cloud Apps and a Secure Web Gateway are integrated together, they provide seamless deployment of Cloud Discovery, automatic blocking of unsanctioned apps, and risk assessment directly in the SWG's portal.

 -  **Reports created using the Cloud Discovery API**. Use the Cloud Discovery API to automate traffic log upload and generate an automated Cloud Discovery report and risk assessment. You can also use the API to [generate block scripts](/defender-cloud-apps/api-discovery-script?azure-portal=true) and streamline app controls directly to your network appliance.

### Log process flow: From raw data to risk assessment

The process of generating a risk assessment consists of the following steps.

1.  **Upload**. Web traffic logs from your network are uploaded to the portal.
2.  **Parse**. Defender for Cloud Apps parses and extracts traffic data from the traffic logs with a dedicated parser for each data source.
3.  **Analyze**. Traffic data is analyzed against the Cloud App Catalog to identify more than 25,000 cloud apps and to assess their risk score. Active users and IP addresses are also identified as part of the analysis.
4.  **Generate report**. A risk assessment report of the data extracted from log files is generated.

The process takes between a few minutes to several hours depending on the amount of data processed.

> [!NOTE]
> Discovery data is analyzed and updated four times a day.

### Using traffic logs for Cloud Discovery

Cloud Discovery uses the data in your traffic logs. The more detailed your log, the better visibility you get. Cloud Discovery requires web-traffic data with the following attributes:

 -  Date of the transaction
 -  Source IP
 -  Source user - highly recommended
 -  Destination IP address
 -  Destination URL recommended (URLs provide higher accuracy for cloud app detection than IP addresses)
 -  Total amount of data (data information is highly valuable)
 -  Amount of uploaded or downloaded data (provides insights about the usage patterns of the cloud apps)
 -  Action taken (allowed/blocked)

Cloud Discovery can't show or analyze attributes that aren't included in your logs. For example, Cisco ASA Firewall standard log format doesn't have the number of uploaded bytes per transaction, Username, and Target URL (only target IP). Therefore, these attributes won't be shown in Cloud Discovery data for these logs, and the visibility into the cloud apps will be limited. For Cisco ASA firewalls, it's necessary to set the information level to 6.

To successfully generate a Cloud Discovery report, your traffic logs must meet the following conditions:

1.  [Data source is supported](/defender-cloud-apps/set-up-cloud-discovery#supported-firewalls-and-proxies?azure-portal=true).
2.  Log format matches the expected standard format (format checked upon upload by the Log tool).
3.  Events aren't more than 90 days old.
4.  The log file is valid and includes outbound traffic information.

### Create snapshot Cloud Discovery reports

It's important to upload a log manually and let Microsoft Defender for Cloud Apps parse it before trying to use the automatic log collector. For information on how the log collector works and the expected log format, see [Using traffic logs for Cloud Discovery](/defender-cloud-apps/create-snapshot-cloud-discovery-reports#log-format?azure-portal=true).

You should download a sample log file if you don't have a log yet, and you want to see an example of what your log should look like. Follow the procedure below to see what your log should look like.

To create a snapshot report:

1.  Collect log files from your firewall and proxy, through which users in your organization access the Internet. Make sure to gather logs during times of peak traffic that are representative of all user activity in your organization.
2.  In the **Microsoft Defender for Cloud Apps** portal, select **Discover** in the navigation pane, and then select **Create snapshot report**.
3.  On the **Create new Cloud Discovery snapshot report** page, enter a **Report Name** and an optional **Description.**
    
    :::image type="content" source="../media/new-snapshot-report-59f843b2.png" alt-text="Screenshot of the New Snapshot Report window.":::
    
4.  Select the **Source** from which you want to upload the log files.
5.  Verify your log format to make sure that it's formatted properly according to the sample log you can download. Under **Verify your log format**, select **View log format** then select **Download sample log**. Compare your log with the sample provided to make sure it's compatible.
    
    :::image type="content" source="../media/cloud-discovery-verify-log-file-c6731b8c.png" alt-text="Screenshot of the Verify your log format window.":::
    
    
    The FTP sample format is supported in snapshots and automated upload. In comparison, syslog is supported in automated upload only. Downloading a sample log will download a sample FTP log.
6.  Upload traffic logs that you want to upload. You can upload up to 20 files at once. Compressed and zipped files are also supported.
    
    :::image type="content" source="../media/upload-traffic-logs-1b2674f7.png" alt-text="Screenshot of the Upload traffic logs window.":::
    
7.  Select **Upload logs**.
8.  After the upload finishes, the status message will appear at the top-right corner of your screen letting you know that your log was successfully uploaded.
9.  After you upload your log files, it will take some time for them to be parsed and analyzed. After processing of your log files completes, you'll receive an email to notify you that it's done.
10. A notification banner will appear in the status bar at the top of the Cloud Discovery dashboard. The banner updates you with the processing status of your log files.
    
    :::image type="content" source="../media/notification-banner-cloud-discovery-3ef9ec14.png" alt-text="Screenshot of the notification banner.":::
    
11. After the logs are uploaded successfully, you should see a notification letting you know that the log file processing completed successfully. At this point, you can view the report either by selecting the link in the status bar, or by selecting the **Settings (cog) i**con in the upper right corner of the screen, and then selecting **Settings** in the menu that appears.
12. On the **Settings** page, under **Cloud Discovery** in the navigation pane, select **Snapshot reports**, and then select the desired snapshot report.
    
    :::image type="content" source="../media/snapshot-report-management-3bfd9b34.png" alt-text="Screenshot of the Snapshot reports view.":::
    

### Configure automatic log upload for continuous reports

Log collectors enable you to easily automate log upload from your network. The log collector runs on your network and receives logs over Syslog or FTP. Each log is automatically processed, compressed, and transmitted to the portal. FTP logs are uploaded to Microsoft Defender for Cloud Apps after the file finished the FTP transfer to the Log Collector. For Syslog, the Log Collector writes the received logs to the disk. Then the collector uploads the file to Defender for Cloud Apps when the file size is larger than 40 KB.

After a log is uploaded to Defender for Cloud Apps, it's moved to a backup directory. The backup directory stores the last 20 logs. When new logs arrive, the old ones are deleted. Whenever the log collector disk space is full, the log collector drops new logs until it has more free disk space. You'll receive a warning on the **Log collectors** tab of the **Upload logs automatically** settings when this scenario occurs.

Before setting up automatic log file collection, verify your log matches the expected log type. You want to make sure Defender for Cloud Apps can parse your specific file. For more information, see [Using traffic logs for Cloud Discovery](/defender-cloud-apps/create-snapshot-cloud-discovery-reports#log-format?azure-portal=true).

> [!NOTE]
> If the logs are being forwarded in their original format, Microsoft Defender for Cloud Apps provides support for forwarding logs from your SIEM server to the Log Collector. However, it's recommended that you integrate the log collector directly with your firewall and/or proxy.

The log collector compresses data before it's uploaded. The outbound traffic on the log collector will be 10% of the size of the traffic logs it receives. If the log collector encounters issues, you'll receive an alert after data wasn't received for 48 hours.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”