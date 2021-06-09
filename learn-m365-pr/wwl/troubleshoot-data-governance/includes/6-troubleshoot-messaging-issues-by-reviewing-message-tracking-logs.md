Organizations can use the message tracking log to discover more details on email messages and senders. Another way to retrieve statistics about data loss prevention (DLP) policies can be found in the Reports section in the Security &amp; Compliance Center.

### Review message tracking logs

DLP data is integrated into the message tracking logs. It's displayed using existing data formats and conventions. As a Microsoft 365 administrator, you can find out what happened to an email message by running a message trace in either the Security and Compliance Center (SCC) or the Exchange admin center (EAC). After running the message trace, you can view the results in a list, and then view the details about a specific message.

Message tracing enables organizations to determine whether a targeted email message was received, rejected, deferred, or delivered by the service. You can also see what events occurred to the message before it reached its final status. Getting detailed information about a specific message lets you:

 -  efficiently answer your user’s questions.
 -  troubleshoot mail flow issues.
 -  validate policy changes.
 -  reduce, if not eliminate, the need to contact Microsoft technical support for assistance.

> [!CAUTION]
> Message trace data is only available for the past 90 days. If a message is older than 10 days, the results can only be viewed in a downloadable .CSV file.

**Additional reading.** For more information about message tracing in Exchange Online and the Security &amp; Compliance Center, see the following resources:

 -  [Trace an email message.](https://docs.microsoft.com/exchange/monitoring/trace-an-email-message/trace-an-email-message?azure-portal=true)
 -  [Message trace in the Microsoft 365 Security &amp; Compliance Center](https://support.office.com/article/Message-trace-in-the-Office-365-Security-Compliance-Center-3e64f99d-ac33-4aba-91c5-9cb4ca476803?azure-portal=true)

### Data logging format

Message tracking logs contain data from the agents involved in processing the mail flow content. For DLP, the transport rule agent (TRA) invokes deep message content scanning and applies the policies defined as part of the Exchange Transport Rules (ETRs). The existing AgentInfo Event adds DLP-related entries in the message tracking log.

The agent name will be the Transport Rule Agent in the AgentInfo event. A single AgentInfo event is logged per message, and it describes the DLP processing applied to the message. The CustomData field of the message tracking log entry field is where the DLP data logged by the transport rule agent will appear. This field may contain multiple entries: one data classification and client information line for each data classification found in the message, one rule line for each rule that applies to the message, and one health monitoring line for each rule that exceeds the load or execution-time threshold.

The following image is an example of the DLP log entry. The output has been formatted to display strings in separate lines with new lines between.<br>:::image type="content" source="../media/dlp-log-entry-ff76c7b7.png" alt-text="screenshot of a DLP log entry":::


The Transport Rule Agent requires grouping of the:

 -  rule ID
 -  DLP Policy ID (optional)
 -  last modified date
 -  action
 -  severity
 -  mode
 -  detected data classification (optional)
 -  sender override (optional) based on rule ID (indicated by “TRA=ETR” in the log line)

The Transport Rule Agent also requires the data classification ID, count, and confidence level of classifications to be grouped by classification name (indicated by “TRA=DC” in the log line).<br>

Other groupings include:

 -  data classification ID
 -  sender override (optional)
 -  override justification (optional) based on data classification ID for all classifications that were detected on the client (indicated by “TRA=CI” in the log line).

The Transport Rule Agent also requires the following properties be grouped by rule ID for all rules that exceed the load or execution Wall or CPU clock thresholds (indicated by “TRA=ETRP” in the log line):

 -  rule ID
 -  load Wall clock (optional)
 -  load CPU clock (optional)
 -  execution Wall clock (optional)
 -  execution CPU clock (optional)

**Additional reading.** For more information, see [View DLP policy detection reports](https://docs.microsoft.com/exchange/view-dlp-policy-detection-reports-exchange-2013-help?azure-portal=true).

### DLP reports in the Security &amp; Compliance Center

With DLP reports, you can quickly view the number of DLP policy matches and rule matches over time, and the number of false positives and overrides. For each report, you can filter those matches by location, time frame, and even narrow it down to a specific policy, rule, or action.

With the DLP reports, you can get business insights. This information enables organizations to:

 -  Focus on specific time periods and understand the reasons for spikes and trends.
 -  Discover business processes that violate your organization’s compliance policies.
 -  Understand any business impact of the DLP policies.

:::image type="content" source="../media/dlp-policy-matches-window-35667bf1.png" alt-text="screenshot of the DLP Policy Matches window in the SCC":::


**Additional reading.** For more information, see the [Data loss prevention reports](https://support.office.com/article/view-the-reports-for-data-loss-prevention-41eb4324-c513-4fa5-91c8-8fbd8aaba83b?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”