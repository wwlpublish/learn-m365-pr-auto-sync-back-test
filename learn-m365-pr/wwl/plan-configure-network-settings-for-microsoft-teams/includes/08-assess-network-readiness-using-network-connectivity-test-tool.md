The Microsoft 365 connectivity test is a proof of concept (POC) network assessment tool that runs basic connectivity tests against your Microsoft 365 tenant and makes specific network design recommendations for optimal Microsoft 365 performance. 

The tool is run locally and gathers more data for deeper insights. The tool can help identify the root cause of the problem. The reports include recommended network performance improvement activities.

The network insights in the Microsoft 365 Admin Center are based on regular in-product measurements for your Microsoft 365 tenant, which are aggregated each day. In comparison, the network insights from the Microsoft 365 network connectivity test are run locally and at one time in the tool. You can use the insights from both Microsoft 365 network connectivity dashboard and Microsoft 365 connectivity test tool for comprehensive network analysis.

## Run the Microsoft 365 connectivity test tool

The network insights from the Microsoft 365 network connectivity test are run locally and one time in the tool.

1. From the desired machine, browse to the [Microsoft 365 network connectivity test tool](https://connectivity.office.com?azure-portal=true). 

2. Sign in to your Microsoft 365 tenant. 
    
    All test reports are shared with your administrator and uploaded to the tenant while you are signed in.

3. Specify location and select **Run test**.

    You can type in your location by city, state, and country or you can have it detected from the web browser. When you select the run test button, we show the running test page and identify the office location. 

    :::image type="content" source="../media/m365-mac-perf-test-tool-page.png" alt-text="Connectivity test tool":::

4. Download the advanced tests client application.

    You will be prompted to download the advanced client test application from the web site after the web browser tests have completed. Open and run the file when prompted. The application requires .NET Core installed. 

5. Start the advanced tests client application.

    Once the client application starts, the web page will update to show this result. Test data will start to be received to the web page. The page updates each time new data is received and you can review the data as it arrives.

6. Advanced tests completed and test report upload.

    When the tests are completed, the web page and the advanced tests client will both show that. The test report will be uploaded to your tenant.

## Network connectivity test results

The results are shown in the **Summary** and **Details** tabs. 

### Summary 
The summary tab shows a map of the detected network perimeter and a comparison of the network assessment to other Office 365 customers nearby. It also allows for sharing of the test report. Here's what the summary results view looks like:

:::image type="content" source="../media/m365-mac-perf-summary-page.png" alt-text="Network connectivity test tool summary results":::

### Detailed report 

The details tab shows the details results and thresholds for different network insights. 

* A green circle checkmark indicates the result was compared favorably to a threshold. 

* A red triangle exclamation point indicates the result exceeded a threshold indicating a network insight. 

The details tab includes the following sections: 

* Location information
* Exchange Online
* SharePoint Online
* Microsoft Teams
* Connectivity
* Network path

For Microsoft Teams, the test results include:

* **Media connectivity (audio, video, and application sharing)**. This tests for UDP connectivity to the Microsoft Teams service front door. If this is blocked, then Microsoft Teams may still work using TCP, but audio and video will be impaired. 

* **Packet loss**. Shows the UDP packet loss measured in a 10-second test audio call from the client to the Microsoft Teams service front door. The result should be lower than **1.00%** for a pass.

* **Latency**. Shows the measured UDP latency, which should be lower than **100ms**.

* **Jitter**. Shows the measured UDP jitter, which should be lower than **30ms**.

    :::image type="content" source="../media/m365-mac-perf-all-details.png" alt-text="Network connectivity test tool example test results for Teams":::

## Share network connectivity test results

You can share with others by selecting on of the sharing options in the **Share** dropdown menu. 

* **Open share settings**. Sharing with other users who sign in to the same Office 365 tenant.

* **Copy link**. Sharing with anyone using a ReportID link.

    :::image type="content" source="../media/m365-mac-perf-share-link.png" alt-text="Sharing a link to your test results":::

This sharing is enabled by default and can be disabled by administrator from **the Microsoft 365 Admin Center** > **Health** > **Network Connectivity** >  **Settings** > **Sharing and user-submitted reports**.

For more information, see:

* [Microsoft 365 network connectivity test tool](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool)

* [Assessing Microsoft 365 network connectivity](/microsoft-365/enterprise/assessing-network-connectivity)