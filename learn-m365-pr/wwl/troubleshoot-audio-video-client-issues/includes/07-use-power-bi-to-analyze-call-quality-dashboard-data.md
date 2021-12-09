The Call Quality Dashboard (CQD) also provides Teams administrators with access to Power BI reports. These reports include summary reports, help desk reports, user feedback reports, mobile device reports, and more. 

Before an organization can use the Power BI query templates (PBIX files) for Microsoft Teams Call Quality Dashboard (CQD), it must download and install the Microsoft Call Quality connector for Power BI. The installation process uses the MicrosoftCallQuality.pqx file that's included in the download.

## Install Microsoft Call Quality Power BI Connector

Complete the following steps to download and install the Microsoft Call Quality connector for Power BI:

1. Check to see if your computer already has a **\[Documents\]\\Power BI Desktop\\Custom Connectors** folder. If not, create this folder.

2. Download the [Power BI Connector for Microsoft CQD](https://www.microsoft.com/download/details.aspx?id=102291&azure-portal=true) (either a *\*.mez* or *\*.pqx* file?azure-portal=true) and place it in the **Custom Connectors** directory.

3. If the connector file is a *\*.mez* file, you'll also need to adjust your security settings as described in the [custom connector setup documentation](https://docs.microsoft.com/power-bi/desktop-connector-extensibility#data-extension-security?azure-portal=true).

If a new version of this Power BI Connector for Microsoft Teams is released, replace the old connector file in the **Custom Connectors** directory with the new file.

## Set up the Microsoft Call Quality Power BI Connector

To build a report and run queries, you must first complete the following steps to connect to the CQD data source:

1. In the **Home** tab on the **Power BI portal**, select **Get Data**.

    ‎:::image type="content" source="../media/call-quality-dashboard-power-bi-connector-data.png" alt-text="Screenshot of the Power BI portal showing the Get Data option selected":::

2. The **Get Data** window that appears, select **Online Services**, select **Microsoft Call Quality (Beta)**, and then select **Connect**.

    ‎:::image type="content" source="../media/call-quality-dashboard-power-bi-connector-services.png" alt-text="Screenshot of the Get Data window showing the Online Services tab and the Microsoft Call Quality option selected":::

3. You'll then be prompted to sign in. Use the same credentials that you used to sign into the Call Quality Dashboard.

4. You'll then be prompted to select between two **Data Connectivity modes**. Select **DirectQuery** and then select **OK**.

5. You'll receive a final prompt showing you the entire data model for Call Quality Dashboard. No data will be visible at this point, only the data model for CQD. Select **Load** to complete the setup process.

6. At this point, Power BI will load the data model onto the right side of the window. No queries will be loaded by default.

With the CQD data sources loaded, you're now ready to build a query and display data. Continue to the next section for instruction on how to build a query.

## Build queries

Microsoft Call Quality Power BI Connector enables you to build your own custom reports. You can use customizable Power BI templates that have been predefined by Microsoft as a starting point for a new report's layout, data model, and queries.

|Power BI templates  |Description  |
|---------|---------|
|CQD Teams Auto Attendant & Call Queue Historical Report.pbit     |  This template provides the following three reports:<br>- Auto Attendant – showing analytics for calls coming into your Auto Attendants.<br>- Call Queue – showing analytics for calls coming into your Call Queues.<br>- Agent Timeline – showing a timeline view of agents being active in Call Queue calls.      |
|CQD Helpdesk Report.pbit     |Integrating building and end-user personal information, this report is designed to let you drill up from a single user to find the upstream root cause of poor call quality for that user (for example, the user is in a building that's experiencing network problems).         |
|CQD Location Enhanced Report.pbit     | Reimagining CQD SPD location reports. Includes 9 reports, providing Call Quality, Building WiFi, Reliability, and Rate My Call (RMC) information with other drill-thrus by Building or by User.  Make sure you upload the building data to maximize your reporting experience.        |
|CQD Mobile Device Report.pbit     | Provides insights tuned towards mobile device users, including Call Quality, Reliability, and Rate My Call. View mobile network, WiFi network, and mobile operating system reports (Android, iOS).        |
|CQD PSTN Direct Routing Report.pbit     |Provides insights specific for PSTN calls that go through Direct Routing.          |
|CQD Summary Report.pbit     |Better visualizations, improved presentation, increased information density, and rolling dates. These reports make it easier to identifier outliers. Drill into call quality by location with an easy-to-use interactive map. 9 new reports:<br>- Quality Overall<br>- Reliability Overall<br>- RMC (Rate My Call) Overall<br>- Conference Quality<br>- P2P Quality<br>- Conference Reliability<br>- P2P Reliability<br>- Conference RMC<br>- P2P RMC         |
|CQD Teams Utilization Report.pbit     | Shows how users in your organization are using Teams and how much. Make sure you upload the building data to maximize your reporting experience.  |
|CQD User Feedback (Rate My Call) Report.pbit     | Shows Rate My Call data in a way that you can easily use to help support calling for your organization. Cross reference with feedback to identify end-user education opportunities.        |
