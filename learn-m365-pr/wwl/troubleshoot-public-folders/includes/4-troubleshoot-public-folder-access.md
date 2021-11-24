The ability to estimate the number of connections being made to public folder mailboxes can be helpful to messaging administrators. This information is useful because deployment guidance for public folders partially revolves around connection counts.

The logging methods that are currently available don't reveal the names of the public folders that clients are connecting to. However, they do contain information about public folder mailboxes being accessed by clients.

Depending on the information you’re looking to gather, there are several types of logs you should consider. These logs are examined in the following sections.

### Autodiscover logs

The Autodiscover service is responsible for informing Outlook clients where and how to connect to a public folder mailbox. This design enables Outlook to display the public folder hierarchy tree, or to make a public sign-in connection to access content within a public folder mailbox. As such, the Autodiscover logs can be useful to administrators in determining which public folder mailboxes are being returned by the Autodiscover service. This information can be very helpful in large multi-site environments when trying to identify possible improvements in public folder mailbox or public folder locations.

To understand this better, consider the following common scenario. An administrator must determine which public folder mailboxes are being returned to the end users when they connect from different sites using Outlook. This can be a challenging task if there are many sites and users resulting in a huge data set. Rather than try to analyze the data manually, there needs to be an automated way which can get the desired outcome. This is where the Log Parser Studio (LPS) queries can be used to parse the Autodiscover logs on mailbox servers to get us the required data for further investigation and actions.

There are many different logs in Exchange Server showing similar information. Depending on the protocol used by your organization, you may make decisions on the log type to parse. Autodiscover logs provide a combined view of what public folder mailboxes users are at least trying to access one time.<br>

 -  If you have content-only public folder mailboxes in your environment that are excluded from the server hierarchy and not directly assigned to users as their default, you can determine whether some are never accessed and may contain content that's worthy of being purged.
 -  If you need a more granular view of the world along with the ability to generate some sort of heat map, you may choose to go with more protocol-specific logs. These logs provide data about each time the client creates a new connection to a public folder mailbox, and they enable you to determine whether the client learned about it through Autodiscover, or if it’s being used far more heavily by many users over time. The options are varied and up to you to choose based on your need.

Autodiscover logs should be investigated on Mailbox servers and can be found in the following default path for Microsoft Exchange 2013 and later:

 -  C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Logging\\Autodiscover

### Outlook Web App logs

The OWA logs identify which default public folder mailboxes Outlook Web App clients get sent to during connection process. The default public folder mailboxes could either be the ones that are provided randomly to the requesting OWA client, or they could be a hard-coded default public folder mailbox assigned to a specific user’s mailbox.

When users log into Outlook on the Web (OWA) in an environment with public folders, the public folder mailbox used for hierarchy information could be a static default public folder mailbox (if one has been set manually on the mailbox), or a random public folder mailbox. It should be noted that Autodiscover isn't utilized when accessing public folders using OWA. Instead, OWA uses its own function to return a default public folder mailbox to the requesting user. As such, you won't find OWA users in the previously mentioned Autodiscover logs.

All logging data for Outlook on the Web (OWA) including public folder access will be in the following folder on Exchange 2013 Client Access Servers or Exchange 2016 or 2019 Mailbox Server:<br>

 -  C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Logging\\HttpProxy\\Owa

### RPC Client Access logs &amp; MAPI Client Access on Microsoft Exchange 2013 Mailbox Servers

These logs identify which public folder mailboxes on a specific mailbox server the users are connecting to using RPC/HTTP and MAPI/HTTP protocols. These logs can be used with Microsoft Exchange 2013.

While AutoDiscover logs can provide information about public folder mailboxes Outlook is learning about and may potentially connect to, the RPC Client Access (RPC/HTTP) &amp; MAPI Client Access (MAPI/HTTP) logs provide information about actual public folder mailbox connections established by users. Both log types can be combined in LPS in single query and parsed to get some useful information on Public folder mailboxes being accessed. The default location of these logs include:

 -  MAPI Client Access: C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Logging\\MAPI Client Access
 -  RPC Client Access: C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Logging\\RPC Client Access

### MAPI/HTTP logs in Microsoft Exchange 2016 and 2019 Servers

These logs identify which public folder mailboxes your MAPI/HTTP clients are connecting to. Organizations should only use these logs with Microsoft Exchange 2016 and later.

Microsoft Exchange 2016 and 2019 include one additional folder created just to log **MAPI/HTTP** protocol traffic. Exchange 2016 and 2019 no longer include MAPI/HTTP traffic in the MAPI Client Access log. If not all of your Outlook for Windows clients are connecting to Exchange 2016 or 2019 through MAPI/HTTP, you may need to analyze both logs to get a full picture of your public folder mailbox connections until such time that all Outlook for Windows clients are using MAPI/HTTP. All MAPI/HTTP logging is now logged in to the **MapiHttp** folder. The logs reside in the following default path:

 -  C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Logging\\MapiHttp\\Mailbox

Exchange Server 2016 an 2019 use slightly different field names for MAPI/HTTP logging. As such, a query used previously with Exchange Server 2013 for parsing the MAPI/HTTP traffic in the older MAPI Client access logs will no longer work with Exchange Server 2016 or 2019.

**Additional reading.** For more information, see [Modern public folders logging and when to use it](https://techcommunity.microsoft.com/t5/exchange-team-blog/modern-public-folders-logging-and-when-to-use-it/ba-p/607122?azure-portal=true).<br>

### Identifying the public folder mailbox the client is connecting to

You can also use the **Test E-mail AutoConfiguration** tool from within the Outlook client to conduct a single user test. This tool identifies which public folder mailbox is being returned to a single end user by the Autodiscover service for hierarchy connections.

To start the **Test E-mail AutoConfiguration** tool, you should complete the following steps:

1.  Start Outlook.
2.  Hold down the Ctrl key, right-click the Outlook icon in the notification area, and then select **Test Email AutoConfiguration**.
3.  Verify that the correct email address is in the **E-mail Address** box. You don't have to provide a password if you’re running a test for the currently logged in user. If you’re testing a user account that's different from the one currently logged into the machine, then you must provide both the email address and password for that account.
4.  In the **Test Email AutoConfiguration** window, clear the **Use Guessmart** check box and the **Secure Guessmart Authentication** check box.
5.  Select the **Use Autodiscover** check box and then select **Test**.

The following screenshot displays an excerpt from the XML file that was gathered from running the **Test E-mail AutoConfiguration** tool.

:::image type="content" source="../media/auto-dfrom-outlook-bb6ff0d2.png" alt-text="screenshot displays an excerpt from the XML file that was gathered from running the Test E-mail AutoConfiguration tool.":::


As you can see in this screenshot, the **administrator@contoso.com** user account used the public folder mailbox **HOSPFM-001@contoso.com** to make a hierarchy connection.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.