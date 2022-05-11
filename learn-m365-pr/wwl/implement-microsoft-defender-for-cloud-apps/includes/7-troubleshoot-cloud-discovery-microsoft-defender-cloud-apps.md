This unit provides a list of Cloud Discovery errors and resolution recommendations for each.

### Microsoft Defender for Endpoint integration

Organizations often integrate Microsoft Defender for Endpoint with Microsoft Defender for Cloud Apps. When an organization integrates these two Microsoft 365 Defender services and it doesn't see the results of the integration, it should refer to the following table. This table provides resolution actions to be taken for each error that can occur.

:::row:::
  :::column:::
    **Issue**
  :::column-end:::
  :::column:::
    **Resolution**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Win10 endpoint users reports don't appear in the list.
  :::column-end:::
  :::column:::
    Verify the devices you're connecting to are Windows 10 version 1809 or later.

Also verify that you waited the necessary two hours that it takes before your data is accessible.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Discovery reports are empty.
  :::column-end:::
  :::column:::
    If the endpoint device is behind a forward proxy, you can send logs from your forward proxy using a log collector.
  :::column-end:::
:::row-end:::


### Log parsing errors

You can track the processing of Cloud Discovery logs using the governance log. The following table provides resolution actions to be taken for each error that can occur.

:::row:::
  :::column:::
    **Error**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Resolution**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Unsupported file type.
  :::column-end:::
  :::column:::
    The file uploaded isn't a valid log file (for example, an image file).
  :::column-end:::
  :::column:::
    Upload a text, \*\*zip, or gzip file that was directly exported from your firewall or proxy.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    The log format doesn't match.
  :::column-end:::
  :::column:::
    The log format you uploaded didn't match the expected log format for this data source.
  :::column-end:::
  :::column:::
    Complete the following steps:

1.  Verify the log isn't corrupt.
2.  Compare and match your log to the sample format shown in the upload page.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Transactions are more than 90 days old.
  :::column-end:::
  :::column:::
    All transactions are more than 90 days old and are being ignored.
  :::column-end:::
  :::column:::
    Export a new log with recent events and reupload it.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    No transactions to cataloged cloud apps.
  :::column-end:::
  :::column:::
    No transactions to any recognized cloud apps are found in the log.
  :::column-end:::
  :::column:::
    Verify the log contains outbound traffic information.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Unsupported log type.
  :::column-end:::
  :::column:::
    When you select **Data source = Other (unsupported)**, the log isn't parsed. Instead, it's sent for review to the Microsoft Defender for Cloud Apps technical team.
  :::column-end:::
  :::column:::
    The Microsoft Defender for Cloud Apps technical team builds a dedicated parser for each data source. The most popular data sources are [already supported](/defender-cloud-apps/set-up-cloud-discovery?azure-portal=true). Each upload of an unsupported data source is reviewed and added to the pipeline for new data source parsers. New parser notifications are published as part of the Microsoft Defender for Cloud Apps [release notes](/defender-cloud-apps/release-notes?azure-portal=true).
  :::column-end:::
:::row-end:::


### Log collector errors

:::row:::
  :::column:::
    **Issue**
  :::column-end:::
  :::column:::
    **Resolution**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Couldn't connect to the log collector over FTP.
  :::column-end:::
  :::column:::
    Complete the following steps:

1.  Verify that you're using FTP credentials and not SSH credentials.
2.  Verify the FTP client you're using isn't set to SFTP.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Failed updating collector configuration.
  :::column-end:::
  :::column:::
    Complete the following steps:

1.  Verify that you entered the latest access token.
2.  Verify in your firewall the log collector is allowed to initiate outbound traffic on port 443.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Logs sent to the collector don't appear in the portal.
  :::column-end:::
  :::column:::
    Complete the following steps:

1.  Check to see if there are failed parsing tasks in the Governance log.
    
     -  If so, troubleshoot the error with the Log Parsing error table above.
     -  If not, check the data sources and Log collector configuration in the portal.
        
        1.  In the **Data source** page, verify that the name of data source is **NSS** and that it's configured correctly.
        2.  In the **Log collectors** page, verify that the data source is linked to the right log collector.
2.  Check the local configuration of the on-premises log collector machine.
    
    1.  Sign-in to the log collector over SSH and run the **collector\_config** utility.
    2.  Confirm that your firewall or proxy is sending logs to the log collector using the protocol you defined (Syslog/TCP, Syslog/UDP or FTP). Then verify that it's sending them to the correct port and directory.
    3.  Run netstat on the machine and verify that it receives incoming connections from your firewall or proxy.
3.  Verify that the log collector is allowed to initiate outbound traffic on port 443.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Log collector status: Created.
  :::column-end:::
  :::column:::
    The log collector deployment wasn't completed. Complete the on-premises deployment steps according to the deployment guide.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Log collector status: Disconnected.
  :::column-end:::
  :::column:::
    No data received in the last 24 hours from any of the linked data sources.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Failed pulling latest collector image.
  :::column-end:::
  :::column:::
    If you get this error during Docker deployment, it could be that you don't have enough memory on the host. To verify this condition, run the following command on the host:

`docker pull mcr.microsoft.com/mcas/logcollector`

If you receive the following error, contact your host machine administrator to provide more space:

`failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device`

  :::column-end:::
:::row-end:::


### Discovery dashboard errors

:::row:::
  :::column:::
    **Issue**
  :::column-end:::
  :::column:::
    **Resolution**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Discovery data was uploaded and parsed successfully but the Cloud Discovery dashboard looks empty.
  :::column-end:::
  :::column:::
    The Dashboard may be filtered on data your logs don't have. As a result, there's no data to show. Try changing the filters in the Cloud Discovery dashboard to show different types of data to see the results.
  :::column-end:::
:::row-end:::
