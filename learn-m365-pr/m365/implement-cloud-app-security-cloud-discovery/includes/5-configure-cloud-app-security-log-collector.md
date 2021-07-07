You can use Cloud App Security log collector to help automate log upload from your corporate network. The Cloud App Security log collector automatically processes, compresses, and transmits each log to the Cloud App Security portal for your review.

## Overview of traffic logs

Cloud Discovery uses the data in your traffic logs. The more information that is stored in your logs, the better understanding of your organizational apps. The following list describes the required attributes for log data ingested by Cloud App Security:

- Date of the transaction
- Source IP
- Source user - highly recommended
- Destination IP address
- Destination URL recommended

   > [!TIP]
   > URLs provide higher accuracy for cloud app detection than IP addresses

- Total amount of data
- Amount of uploaded or downloaded data
- Action taken (allowed/blocked)

## How logs are uploaded and processed

The way in which logs are uploaded varies depending on the type of log file.

> [!NOTE]
> The log collector runs on your network and receives logs over Syslog or FTP.

For Syslog files, the log collector writes the received logs to the disk. When the file size is larger than 40 KB, the log collector uploads the file to Cloud App Security. With FTP, the log collector uploads the logs to Cloud App Security as soon as the log collector receives the completed FTP upload.

After a log is uploaded, Cloud App Security moves the log to a backup directory.

> [!NOTE]
> The backup directory stores the last 20 logs.

As new logs arrive, the old logs are deleted.

> [!IMPORTANT]
> Whenever the log collector disk space is full, the log collector drops new logs until it has more free disk space. You'll receive a warning on the Log collectors tab of the Upload logs automatically settings when this happens.

## Implement a Log Collector

You can deploy a Log Collector in one of two modes, as described in the following table.

| Mode              | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| Container         | Runs as a Docker image on Windows, Ubuntu  on-premises, Ubuntu in Azure, RHEL on-premises or CentOS |
| Virtual appliance | Runs as an image over Hyper-V or VMware  hypervisor          |

> [!IMPORTANT]
> Virtual appliance mode is deprecated. You should use Container mode.

After you've deployed the log collector, you must define it in the Cloud App Security portal:

1. Open **Settings**, and select **Automatic log upload**.
2. First, define your data sources. Select the **Data sources** tab, and then select **Add data source**.
3. In the **Add data source** dialog box, enter a name, and then select the **Source** and **Receiver** **type**. The Source represents the appliance, such as a proxy or firewall. The Receiver type is the type of log file: FTP or Syslog.

   :::image type="content" source="../media/log-1.png" alt-text="A screenshot of the Add data source dialog box. The administrator has selected Cisco ASA firewall and Syslog: TCP.":::

4. Select **Add**.
5. Next, on the **Automatic log upload** page, select the **Log collectors** tab.
6. Select **Add log collector**.
7. In the **Create log collector** dialog box, enter the required information and then select **Create**:

   - Name
   - Host IP or FQDN
   - Data source(s). This is the data source you previously defined.

8. A section called **Next steps** appears. Follow the instructions provided to complete configuration. You can export the required configuration by selecting the **Export** button above the list of data sources.

   :::image type="content" source="../media/log-2.png" alt-text="A screenshot of the Create log collector dialog box. The administrator has defined the data source as matching that defined earlier in the procedure. A section labeled Next steps contains a list of collector configuration data.":::

Having completed the configuration procedure for Cloud App Security, you must now configure the log collector itself. As mentioned earlier, you can deploy in two modes: as a container, or a virtual appliance.

For example, to use a Windows computer with Docker, you would complete the process as follows:

1. Sign in to Windows as a local administrator.
2. Download the Windows Docker installer PowerShell script by running the following command in an elevated PowerShell window:

    ```powershell
    Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)
    ```

3. Set the execution policy to remote signed: `Set-ExecutionPolicy RemoteSigned`
4. Install Docker client: `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

   > [!IMPORTANT]
   > While the log collector container is installed, your computer restarts twice. You'll have to sign in again each time. Make sure the Docker client is set to use Linux containers.

5. After each restart, rerun the `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` command.
6. Next, import the configuration information from the Next steps section of the Create log collector dialog box.

   > [!TIP]
   > You can verify successful deployment on the Log collectors tab in the Cloud App Security portal. If your log collector shows as **Connected**, you have successfully completed deployment.
