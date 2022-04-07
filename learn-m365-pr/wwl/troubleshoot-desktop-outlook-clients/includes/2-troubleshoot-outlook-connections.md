You can connect a variety of client apps to Exchange Online, including the Microsoft Outlook desktop client for Windows, Exchange Active Sync clients, POP and IMAP email apps, and others. If you can't connect to Exchange Online, it might be because of a client-side issue, such as the way Outlook is configured, or a server-side issue, such as a client access rule. It's important that you know how to manage client connections, and how to troubleshoot connectivity failures from all causes.

## Review Outlook client configuration information

If your users are experiencing connectivity issues while using Microsoft Outlook, a good starting point is to review client configuration information. You can:

- Review connectivity with Connection Status
- Verify communications with troubleshooting logs

### Review Connection Status

To access Connection Status information, use the following procedure:

1. Open **Outlook** on the user's computer.
1. Press and hold the **CTRL** key.
1. In the Taskbar corner overflow area, right-click **Microsoft Outlook** and then click **Connection Status**.
1. In the **Outlook Connection Status** dialog box, review the displayed information.
1. Click **Close** when you're done.

The screenshot displays the Outlook Connection Status dialog box. Four lines are displayed relating to the same user's connectivity to Exchange Online, all of which display as Established.

:::image type="content" source="../media/outlook-connection-status.png" alt-text="A screenshot that displays the Outlook Connection Status dialog box. ":::

Connection Status enables you to review the connected accounts, listed by SMTP Address. Information displayed includes:

- SMTP address
- Display name
- Server name
- Status
- Protocol
- Authentication
- Encryption
- Number of requests and failed requests

You can then review the information and identify any connectivity issues displayed. If status is *Disconnected*, you must investigate the underlying network cause for that connection failure.

### Enable and review troubleshooting logs

To access troubleshooting logging information, use the following procedure:

1. Open **Outlook**.
1. On the menu, select **File** and then click **Options**.
1. In the **Outlook Options** dialog box, in the navigation pane, select **Advanced**, and then under the **Other** heading, select the **Enable troubleshooting logging** check box.
1. Click **OK**, and then restart Outlook.
1. You will receive a prompt that **Logging is turned on**. Do not disable logging when prompted.

Perform typical tasks, to record data in the logs. To find the logs, open File Explorer and navigate to the **C:\Users\username\AppData\Local\Temp** folder.

> [!WARNING]
> When you've finished collecting data, disable logging and restart Outlook. 

> [!IMPORTANT]
> Important: Some of the Outlook logs are readable with any text editor. Others, such as the calendar logs and advanced ETW logs, are in a format that can only be analyzed by Microsoft personnel. In certain situations, Outlook logging can be used to locate connectivity related issues, when they are reviewed by Microsoft support engineers. More details about Outlook logging can be found in the How to enable global and advanced logging for Microsoft Outlook link in the Learn more section below.

Although some of the logs can be opened in a text editor, the ETL log files require Microsoft support to interpret. For more information about advanced logging, see the link in the Learn more section below.

If you've checked your Outlook client configuration and troubleshooting logs and haven't found the problem, your next subject to investigate might be server-side Client Access Rules.

## Troubleshoot Client Access Rules

The issue that prevents Outlook from connecting to Exchange Online might not be on the client side. On the server, one feature that can stop users connecting is Client Access Rules. Exchange Online uses Client Access Rules to control access from different types of client apps or activities. For example, by using Client Access Rules, an administrator can:

- Allow or block access to Exchange ActiveSync clients (perhaps by specific IP addresses).
- Allow or block access to Exchange Web Services (perhaps for users in specific departments, cities, or countries).
- Allow or block access to an offline address book (perhaps for specific users based on their usernames).
- Prevent client access using federated authentication.
- Prevent client access using Exchange Online PowerShell.
- Block access to the classic Exchange admin center (perhaps by country or region).

Client Access Rules are useful for controlling clients and enforcing secure connections, but when they are configured wrongly, they can prevent an authorized user from gaining access to their mailbox and doing their job.

A rule consists of:

- **Conditions**. Determines to which client connections a rule applies.
- **Exceptions**. Determines exceptions to the defined conditions.
- **Action**. Choose between AllowAccess and DenyAccess.
- **Priority**. If multiple rules apply, then the rule with the lowest numerical value has a higher priority and takes precedence.

Typically, an Exchange Online administrator creates Client Access Rules by using the Exchange Online PowerShell. Similarly, if you suspect a Client Access Rule might be the cause of a failure to connect to Exchange Online, you must use Exchange Online PowerShell to review and, if necessary, reconfigure the rules.

To use Exchange Online PowerShell, you must first install the required PowerShell module. Use the following procedure:

1. Open an elevated Windows PowerShell window.
1. Change the execution policy for scripts to remote signed by running: `set-executionpolicy remotesigned`.
1. Then install the required module by running the following commands:

    1. install-module powershellget -force
    1. install-module -name ExchangeOnlineManagement

1. Acknowledge any prompts by responding **Y**.
1. Next, connect to your Exchange Online environment: `connect-exchangeonline -userprincipalname name`, where *name* is your administrative account, for example: `Admin@Contoso.com`.

After you've installed the required module, you can use the appropriate cmdlets to review and manage the Client Access Rules. If you suspect that a Client Access Rule is preventing access in a given situation, review the configured rules by running the following cmdlet: `Get-ClientAccessRule`.

You can then review settings for a specific rule by running: `Get-ClientAccessRule 'name' | fl`.

The key information in the returned output is what the rule controls, and whether the rule's action is AllowAccess or DenyAccess. If you need to change a Client Access Rule, use the following syntax:

``` powershell
Set-ClientAccessRule -Identity "<RuleName>" [-Name "<NewName>"] [-Priority <PriorityValue>] [-Enabled <$true | $false>] -Action <AllowAccess | DenyAccess> [<Conditions>] [<Exceptions>]
```

For example, if you wanted to update the IP range for a rule called **Allow IMAP4** that controlled IMAP4 protocol access, you could use the following command:

``` powershell
Set-ClientAccessRule -Identity "Allow IMAP4" -AnyOfClientIPAddressesOrRanges @{Add="172.16.0.0/16"}
```

> [!TIP]
> Remember that if there are multiple rules in use, especially if the rules control access from the same client protocol, then Action and Priority should be checked carefully. 

## Troubleshoot autodiscover issues

When a user attempts to set up Outlook to connect to their Exchange Online mailbox, they might receive the following error message:

An encrypted connection to your mail services is not available.

You might then decide to troubleshoot the problem using the Microsoft Remote Connectivity Analyzer:

1. In a web browser, open a connection to:  `https://testconnectivity.microsoft.com`.
1. On the **Office 365** tab, select the **Outlook Connectivity** test.
1. Define the following information:

    - Email address
    - Authentication type (Modern or Basic)
    - If Modern is used, then enter the **Modern Authentication (OAuth) credentials** and click Sign in.
    - Select **Use Autodiscover to detect server settings**.
    - Choose the appropriate Service Selection (typically **Office 365**)

1. Select the **I understand that I must use the credentials of a working account from my Exchange domain to be able to test it remotely** check box, and then click **Perform Test**.

The screenshot displays the Outlook Connectivity test dialog box. The administrator has entered the required information before running the test.

:::image type="content" source="../media/outlook-connectivity.png" alt-text="A screenshot that displays the Microsoft Remote Connectivity Analyzer":::

You receive the following error:

**The Autodiscover service couldn't be contacted successfully by any method.**

These two messages could be the result of several problems, including that the Autodiscover CNAME record for your domain doesn't exist or isn't set up correctly.

> [!TIP]
> Be sure you selected the appropriate authentication method.

If you suspect that the problem lies with Autodiscover, you can check the AutoDiscover status for Outlook by running the **Test Email AutoConfiguration** tool. Use the following procedure:

1. Open **Outlook**.
1. Press and hold the **CTRL** key.
1. In the Taskbar corner overflow area, right-click **Microsoft Outlook** and then click **Test Email Autoconfiguration**.
1. In the **Test Email Autoconfiguration** dialog box, enter the user's password, and then click **Test**.
1. When the test is complete, you can review the results on the **Results**, **Log**, and **XML** tabs.
1. Close the dialog box when you've finished analyzing results.

The screenshot displays the results from the Test Email AutoConfiguration test. The Results tab displays information about the Protocol, Server, Login Name, and other details recorded during the test.

:::image type="content" source="../media/test-email-autoconfiguration.png" alt-text="A screenshot that displays the Test Email AutoConfiguration dialog box.":::

If this test is unsuccessful, or displays errors relating to Autodiscover, then attempt to connect Outlook to the user's mailbox using the default `OnMicrosoft.com` domain name. Autodiscover supports this default name. You can now investigate the problem with your custom domain name settings in DNS.

> [!TIP]
> This problem is most likely to occur during initial provisioning, or after reconfiguration of DNS settings relating to Office 365 services. 

> [!NOTE]
> Find out more about required DNS records here: [External Domain Name System records for Office 365](/microsoft-365/enterprise/external-domain-name-system-records).

## Resolve Outlook client connectivity failure to Exchange Online mailbox

There are many issues that might result in a user being unable to connect their Outlook client to Exchange Online, including Autodiscover issues and Client Access Rules. But if you've verified these, it's worth also considering the following possibilities:

- Azure Active Directory (Azure AD) Conditional Access policies

- Licensing issues

- Networking infrastructure

### Azure Active Directory Conditional Access policies

Conditional Access is a feature of Azure AD that provides an additional layer of security before allowing authenticated users to access data or other assets, such as apps like Exchange Online. Conditional Access checks for things such as user, device, and location to automate decisions and enforce policies for accessing cloud apps or resources. For example, a conditional access policy might state that:

**IF** a user belongs to a certain group, **THEN** they are required to provide multi-factor authentication to sign-in to Exchange Online.

Conditional Access can use a number of signals when deciding whether to grant access, including the following:

- **User or group membership**. Policies can be targeted to specific users and groups, giving administrators fine-grained control over access.
- **IP Location information**. Trusted IP address ranges can be created, then used when making policy decisions. Also, Administrators can opt to block or allow traffic from an entire countries IP range.
- **Device**. Users with devices of specific platforms or marked with a specific state can be used
- **Application**. Users attempting to access specific applications can trigger different Conditional Access policies.
- **Real-time sign-in risk detection**. Signals integration with Azure AD Identity Protection allows Conditional Access policies to identify risky sign-in behavior. Policies can then force users to perform password changes or multi-factor authentication to reduce their risk level or be blocked from access until an administrator takes manual action.

> [!NOTE]
> After the conditional access policy is applied, a determination is made as to whether to grant access, block access, or require additional verification. 

If your users can't connect to Exchange Online, it's important to verify whether they're being impacted by a conditional access policy. To check these settings, you must sign-in to the Azure Active Directory admin center, and then access **Azure AD Conditional Access** from **All** **services**. All policies are listed, but you'll only be interested in policies that display a State of On.

Open the appropriate policies, and then review the conditions and access controls. In the screenshot below, the Exchange Online policy is:

- Assigned to the All Sales Staff group
- Applies when users connect to Office 365 Exchange Online
- Applies when the users have no or low sign-in security risks
- Grants access as long as the device is marked as compliant

The screenshot displays the Exchange Online conditional access policy in the Azure Active Directory admin center. In this example, your user might be prevented from connecting to Exchange Online because:

- They don't belong to All Sales Staff
- They're signing in with a medium or high sign-in risk
- Their computer is not compliant with corporate security requirements

:::image type="content" source="../media/conditional-access.png" alt-text="A screenshot that displays a conditional access policy named Exchange Online with the properties described in the preceding text. ":::

> [!TIP]
> The solution to this problem might not be to change the policy, but rather to resolve the client computer issue or add a user to a group. 

### Licensing issues

An often-overlooked reason for failure to connect to an Exchange Online mailbox is that the user doesn't have an Exchange Online license. In some cases, this problem could be because the user hasn't been assigned an Office 365 license, or else that the assigned license doesn't include Exchange Online.

The following Office 365 service plans do not include Exchange Online:

- Office 365 Apps
- Microsoft 365 F1

In addition, some service plans don't include a desktop license for office applications, including Microsoft Outlook; for example, Microsoft 365 Business Basic. Ensure that your users have been assigned an appropriate license for their requirements.

### Networking infrastructure

If your users are experiencing connectivity issues to Exchange Online, it's always worth considering whether the underlying network is at fault. Between Microsoft Outlook and Exchange Online, there are any number of network segments, subnets, and routers. In addition, the various services require access to correctly configured DNS servers. If you suspect there might be a generic connectivity issue, you can use the Remote Connectivity Analyzer to perform tests for connectivity to Exchange Online.

The Remote Connectivity Analyzer can perform the following tests:

- **Exchange Online Custom Domains DNS Connectivity Test**. Checks the external domain name settings for your verified domain in Office 365. Looks for issues with mail delivery and Outlook client connectivity issues.
- **Exchange ActiveSync**. Simulates the steps that a mobile device uses to connect to an Exchange server using Exchange ActiveSync.
- **Exchange Web Services**. You can run the following tests for Exchange Web Services:

    - Synchronization, Notification, Availability, and Automatic Replies.
    - Service Account Access (Developers).
    - Free/Busy.

- **Outlook Connectivity**. Performs the steps Microsoft Outlook uses to connect from the internet. It tests connectivity using both the RPC over HTTP and the MAPI over HTTP protocols.
- **Internet email**:

  - Inbound SMTP E-Mail.
  - Outbound SMTP E-Mail.
  - POP Email.
  - IMAP Email.

> [!TIP]
> The Remote Connectivity Analyzer is accessed here: [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365.)

## Learn more

- [How to enable global and advanced logging for Microsoft Outlook](https://support.microsoft.com/topic/how-to-enable-global-and-advanced-logging-for-microsoft-outlook-15c74560-2aaa-befd-c256-7c8823b1aefa)
