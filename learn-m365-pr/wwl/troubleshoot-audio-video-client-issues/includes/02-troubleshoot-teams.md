When users experience calling problems, an organization's Teams administrator must quickly diagnose and fix the problems. Troubleshooting problems within Microsoft Teams may include a wide array of possible areas that must be investigated. Issues can be examined in the log files and various tools. 

## Resources from Microsoft

Common problems are documented in the Teams Troubleshooting section of the Microsoft Teams documentation. If there's a problem, refer to this documentation for details of symptoms, causes, and how it can be resolved.

* For initial troubleshooting steps, see [Troubleshoot for end users](https://support.microsoft.com/office/troubleshoot-6fa7c08a-6fd4-47a0-b275-90a5f60f1df9?azure-portal=true).

* For common Teams issues, see [Information about Teams known issues](/microsoftteams/troubleshoot/teams-welcome?azure-portal=true).

* Self-help diagnostics in Microsoft 365 admin center.

* Use **Help** from Teams client to report a problem.

## Check client connectivity

If you're experiencing connectivity issues with the Teams client, the most likely causes are firewall or proxy settings. Verify the necessary URLs, IP addresses, and ports are opened in the organization's firewall or proxy server. The following services require specific URLs and ports to be opened in the firewall:

* Authentication
* Microsoft Teams Client Connectivity
* Collaboration
* Media
* Shared Services
* Third-party Integration
* Skype for Business Interoperability
* Skype for Business Client Interoperability

**Additional reading**. For more information on the URLs and IPs required for Microsoft Teams, see [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?azure-portal=true).

For more information on Microsoft Teams networking requirements, see [Prepare your organization's network for Microsoft Teams](/microsoftteams/prepare-network?azure-portal=true).


## Self-help diagnostics

Self-help diagnostics won't make changes to your tenant. They provide insight into known issues and the instructions that you’ll need to fix the issues quickly.

Teams-specific diagnostic scenarios that cover top support topics and the most common tasks for which administrators request configuration help, are available in Support section of Microsoft 365 admin center

1.	Sign into **Microsoft 365 admin center**. In the navigation pane, select **Show all** > **Support** > **New service request**. 

2.	Describe the issue briefly. As you type search terms, a type-ahead query assists you to find the topics that you’re searching for. The system determines whether a diagnostic scenario matches your issue. Select the closest scenario that matches the issue.

    :::image type="content" source="../media/admin-self-help-diagnostics.png" alt-text="Screenshot of Self-help page in Microsoft 365 admin center.":::

3. Select **Run Tests** to find the best way to solve the issue. 

    :::image type="content" source="../media/help-teams-diagnostic.png" alt-text="Screenshot of selecting run tests from the diagnostics tool.":::

4.	After the diagnostic checks finish and the configuration issue is found, the system provides the steps to resolve the issue.

    :::image type="content" source="../media/help-teams-actions.png" alt-text="Screenshot of suggestted action plan from the diagnostic tool.":::

> [!NOTE]
> If a diagnostic detects an issue, and you've implemented a fix based on the results, consider rerunning the diagnostic to ensure the issue is completely resolved.

For more details on the diagnostics that are currently available, with brief scenario descriptions, see [Scenario descriptions and shortcut commands](/microsoftteams/troubleshoot/teams-administration/admin-self-help-diagnostics?azure-portal=true#what-scenarios-are-currently-covered)

## Monitor usage and feedback

It's important to know how users are using Teams and what their experience is with Teams, using the reports available in Teams admin center

* Teams reports in the Microsoft Teams admin center to get insights into how Teams is used in your organization. 

* Customer feedback and problems reported using Teams client 

    :::image type="content" source="../media/help-teams.png" alt-text="Screenshot of Select Help option in Teams client.":::


## Tools for monitoring and troubleshooting

The following tools are designed to help organizations monitor and troubleshoot call quality in Microsoft Teams:

* **Log files**: Log files are created automatically and provide information to help troubleshoot specific issues.

* **Call Analytics**: Call analytics provide detailed information about the devices, networks, and connectivity related to  specific calls and meetings for each user in Teams. Teams administrators and helpdesk agents use this information to troubleshoot call quality and connection problems in a specific call.

* **Call Quality Dashboard**: Call Quality Dashboard (CQD) provides a network-wide view of call quality across an organization. Call Quality Dashboard (CQD) is designed to help Microsoft Teams administrators, Skype for Business administrators, and network engineers optimize a network.

* **Direct Routing Health Dashboard**: Health Dashboard for Direct Routing monitors the connection between a Session Border Controller (SBC) and the Direct Routing interface.
