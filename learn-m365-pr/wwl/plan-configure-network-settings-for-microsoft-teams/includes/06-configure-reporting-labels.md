Call analytics shows call and meeting quality for individual users in Teams. Location-enhanced Call Analytics reports contain the location names instead of just an IP subnet, making the reports easier to understand and use for remediating any potential issues.

The Reporting labels page in the Microsoft Teams admin center lets you provide a text file containing a list of physical locations and their associated network subnets. This file is used by **Call Analytics** for generating reports. 

## Prepare data file

The report labels and locations data you provide is a single data structure – there's currently no interface available to make individual edits to the data. 

The file must be either a .tsv file (columns are separated by a TAB) or a .csv file (columns are separated by a comma). The following table shows the format of the data file: 

  
  | Column name        | Data type | Example                   | Guidance              |
  |--------------------|-----------|---------------------------|-----------------------|
  | NetworkIP          | String    | 192.168.1.0               | Required              |
  | NetworkName        | String    | USA/Seattle/SEATTLE-SEA-1 | Required  |
  | NetworkRange       | Number    | 26                        | Required              |
  | BuildingName       | String    | SEATTLE-SEA-1             | Required  |
  | OwnershipType      | String    | Contoso                   | Optional              |
  | BuildingType       | String    | IT Termination            | Optional              |
  | BuildingOfficeType | String    | Engineering               | Optional              |
  | City               | String    | Seattle                   | Recommended           |
  | ZipCode            | String    | 98001                     | Recommended           |
  | Country            | String    | US                        | Recommended           |
  | State              | String    | WA                        | Recommended           |
  | Region             | String    | MSUS                      | Recommended           |
  | InsideCorp         | Bool      | 1             | Required              |
  | ExpressRoute       | Bool      | 0             | Required              |
  | VPN                | Bool      | 0                         | Optional              |


This table below is an example, which you can follow in order to create your data file. A productive data file should not contain column headers (for example, Network, Network Name, etc.). The headers in the below table are used here for informational purposes only. You can download a sample template [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/locations-template.zip?raw=true?azure-portal=true).

|Network|Network Name|Network Range|Building Name|Ownership Type|Building Type|Building Office Type|City|Zip Code|Country|State|Region|Inside Corp|Express Route|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|10.0.128.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.130.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.131.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.132.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|


## Configure reporting labels

1. Sign in to **Teams admin center**.
2. Select **Locations** > **Reporting labels**.
3. On the **Reporting labels** page, select **Upload data**.
4. In the **Upload data** pane, select **Select a file**, and then browse to and upload your edited .csv or .tsv file.
4. Select **Upload**.

Once the file is uploaded successfully, you can see the update in the locations summary pane. 

:::image type="content" source="../media/configure-reporting-labels.png" alt-text="Configuration of reporting labels":::

 

 

 
