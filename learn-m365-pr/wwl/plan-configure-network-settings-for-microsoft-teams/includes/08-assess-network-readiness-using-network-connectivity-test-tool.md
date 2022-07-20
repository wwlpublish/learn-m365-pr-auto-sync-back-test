You can use the following tool to assess network readiness for Microsoft Teams. The results from the tools can be used as part of a network assessment to determine if the customer network is most optimal for Microsoft Teams.

* Microsoft 365 connectivity test tool
* Microsoft Teams network assessment tool

## Microsoft 365 network connectivity test tool

The Microsoft 365 connectivity test tool is a proof of concept (POC) network assessment tool that runs basic connectivity tests against your Microsoft 365 tenant and makes specific network design recommendations for optimal Microsoft 365 performance. 

The tool is run locally and gathers more data for deeper insights. The tool can help identify the root cause of the problem. The reports include recommended network performance improvement activities.

The network insights in the Microsoft 365 Admin Center are based on regular in-product measurements for your Microsoft 365 tenant, which are aggregated each day. In comparison, the network insights from the Microsoft 365 network connectivity test are run locally and at one time in the tool. You can use the insights from both Microsoft 365 network connectivity dashboard and Microsoft 365 connectivity test tool for comprehensive network analysis.

### Run the Microsoft 365 network connectivity test tool

The network insights from the Microsoft 365 network connectivity test are run locally and one time in the tool.

1. From the desired machine, browse to the [Microsoft 365 network connectivity test tool](https://connectivity.office.com?azure-portal=true).

2. Sign in to your Microsoft 365 tenant.
  
    All test reports are shared with your administrator and uploaded to the tenant while you are signed in.

3. Specify location and select **Run test**.

    You can type in your location by city, state, and country or you can have it detected from the web browser. When you select the run test button, we show the running test page and identify the office location.

    :::image type="content" source="../media/network-connectivity-run-test-page.png" alt-text="Screenshot of Connectivity test tool." lightbox="../media/network-connectivity-run-test-page.png":::

4. Download the advanced tests client application.

    You will be prompted to download the advanced client test application from the web site after the web browser tests have completed. Open and run the file when prompted. The application requires .NET Core installed.

5. Start the advanced tests client application.

    Once the client application starts, the web page will update to show this result. Test data will start to be received to the web page. The page updates each time new data is received and you can review the data as it arrives.

6. Advanced tests completed and test report upload.

    When the tests are completed, the web page and the advanced tests client will both show that. The test report will be uploaded to your tenant.

### Network connectivity test results

The results are shown in the **Summary** and **Details** tabs.

#### Summary

The summary tab shows a map of the detected network perimeter and a comparison of the network assessment to other Microsoft 365 customers nearby. It also allows for sharing of the test report. Here's what the summary results view looks like:

:::image type="content" source="../media/network-connectivity-test-results-summary.png" alt-text="Screenshot of Network connectivity test tool summary results." lightbox="../media/network-connectivity-test-results-summary.png":::

#### Detailed report

The details tab shows the details results and thresholds for different network insights.

- A green circle check mark indicates the result was compared favorably to a threshold.

- A red triangle exclamation point indicates the result exceeded a threshold indicating a network insight.

The details tab includes the following sections:

- Location information

- Exchange Online

- SharePoint Online

- Microsoft Teams

- Connectivity

- Network path

For Microsoft Teams, the test results include:

- **Media connectivity (audio, video, and application sharing)**: This tests for UDP connectivity to the Microsoft Teams service front door. If this is blocked, then Microsoft Teams may still work using TCP, but audio and video will be impaired.

- **Packet loss**: Shows the UDP packet loss measured in a 10-second test audio call from the client to the Microsoft Teams service front door. The result should be lower than **1.00%** for a pass.

- **Latency**: Shows the measured UDP latency, which should be lower than **100ms**.

- **Jitter**: Shows the measured UDP jitter, which should be lower than **30ms**.

    :::image type="content" source="../media/network-connectivity-detail-view.png" alt-text="Screenshot of Network connectivity test tool example test results for Teams." lightbox="../media/network-connectivity-detail-view.png":::

### Share network connectivity test results

You can share with others by selecting on of the sharing options in the **Share** dropdown menu.

- **Open share settings**: Sharing with other users who sign in to the same Office 365 tenant.

- **Copy link**: Sharing with anyone using a ReportID link.

    :::image type="content" source="../media/network-connectivity-test-results-page.png" alt-text="Screenshot of Sharing a link to your test results." lightbox="../media/network-connectivity-test-results-page.png":::

This sharing is enabled by default and can be disabled by administrator from **the Microsoft 365 Admin Center** > **Health** > **Network Connectivity** >  **Settings** > **Sharing and user-submitted reports**.

For more information, see:

- [Microsoft 365 network connectivity test tool](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool?azure-portal=true)

- [Assessing Microsoft 365 network connectivity](/microsoft-365/enterprise/assessing-network-connectivity?azure-portal=true)

## Microsoft Teams network assessment tool

Microsoft Teams Network Assessment Tool provides the ability to perform a simple test of network performance and network connectivity to determine how well the network would perform for Microsoft Teams calls.

The tool tests the connectivity to various Teams servers deployed in the Microsoft Azure network, including:

* **Network performance**: Test the connection to a Microsoft Teams relay by streaming packets to the nearest edge site and back for a configurable amount of time. The tool collects and outputs loss, jitter, and round-trip time during this packet exchange.

* **Network connectivity**: Verify network and network elements between the test location and the Microsoft Network are correctly configured to enable communication to the IP addresses and ports needed for Microsoft Teams calls.  

    The Microsoft Network Assessment Tool provides an ability to verify network connectivity between the user location and a Microsoft relay server. The relay connectivity checker verifies network connectivity to the load-balancer relay (VIP), AND one relay instance (DIP) forwarded to by the load-balancer relay. The checker tests connectivity via UDP, TCP (Pseudo-TLS/Full-TLS), and HTTPS transport protocol. The checker tests connectivity to port 3478 (control port) of the load-balancer relay, and ports 3478-3481 of the relay instance. The checker also checks whether the load-balancer relay is QoS (Quality of Service) enabled, which means the load-balancer redirects packets to relay instance ports 3479-3481 (instead of 3478) depending on modality (audio = 3479, video = 3480, screenshare/data = 3481). 

### Run the Microsoft Teams network assessment tool

1. Download the tool from [Microsoft Teams Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=103017&azure-portal=true).

2. From a command prompt, execute the tool by the following commands:

    * For network connectivity, run ```NetworkAssessmentTool.exe```
    
    * For network performance, run ```NetworkAssessmentTool.exe /qualitycheck```
    

