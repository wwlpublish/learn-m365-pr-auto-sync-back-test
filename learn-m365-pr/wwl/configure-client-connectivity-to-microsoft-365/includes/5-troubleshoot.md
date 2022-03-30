Microsoft provides the following tools that can be used to analyze connectivity issues in Microsoft 365 deployments.

### Microsoft Message Analyzer

Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.

**Additional reading.** For more information, see [Getting Started with Microsoft Message Analyzer](/message-analyzer/getting-started-with-message-analyzer?azure-portal=true) and [Microsoft Message Analyzer Operating Guide](https://technet.microsoft.com/library/jj649776.aspx?azure-portal=true).

### Microsoft Remote Connectivity Analyzer

‎Microsoft Remote Connectivity Analyzer (RCA) is a downloadable client program that can:

 -  identify connectivity issues between email clients and an organization's Exchange Server.
 -  identify connectivity issues between email clients and Microsoft 365.
 -  troubleshoot Exchange Server and Microsoft 365 deployments.
 -  identify common problems.

Microsoft Remote Connectivity Analyzer runs a set of tests locally from a client computer. As such, it enables end users to run similar tests from client computers within the corporate network.

To install the Microsoft Remote Connectivity Analyzer tool, go to the [Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/?azure-portal=true) website, select the **Client** tab, and then select **Install Now**.

The RCA tool provides a log that shows the test steps that were both successful and unsuccessful. Additionally, the RCA tool provides a "Tell me more about this issue and how to resolve it" link that provides suggestions about how to help fix reported issues.

### Microsoft 365 Support and Recovery Assistant

‎ Microsoft 365 Support and Recovery Assistant (SaRA) is a diagnostic tool that lets users run tests to resolve many different problems. These problems include Outlook installation and activation issues, and issues that occur when you make a network connection in Microsoft Dynamics 365 or OneDrive for Business. The connectivity tests work for users after their mailboxes are moved to Microsoft 365. Furthermore, the tool generates a log file that contains the test results, which users can submit to the support team for further investigation.

The following graphic shows how SaRA and the RCA conduct similar tests, but from a different perspective. While the RCA tool connects from the Internet, SaRA runs its tests from a client machine.

:::image type="content" source="../media/rca-and-sara-connections-8957beae.jpg" alt-text="graphic shows that while the RCA connects from the Internet, SARA runs similar tests from a client machine":::
