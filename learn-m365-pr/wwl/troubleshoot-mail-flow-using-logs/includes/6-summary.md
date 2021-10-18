This module examined how to troubleshoot mail flow issues using message tracking logs, protocol logs, and event logs. Event, protocol, and tracking logs are excellent resources for Messaging administrators when they must troubleshoot messaging issues. For example, you learned that logs can prove useful when:

 -  a service availability or message transport persists, even after initial service availability or message transport troubleshooting has been completed.
 -  an administrator wants to access historical data about an issue.

The module began with an overview of message tracking logs. You learned that message tracking logs and message traces can be useful to conduct forensics analysis on specific messages. They can also help troubleshoot the send and receive connectors that processed a message. You learned how to run a message trace using both the Exchange admin center and Windows PowerShell.

The module then explored how protocol logging provides a source of information where Messaging administrators can view the SMTP conversations that occur:

 -  as part of message delivery between messaging servers.
 -  between Exchange Server services in the transport pipeline.

You learned that protocol logging can be enabled on SMTP Send and SMTP Receive connectors to log the activity of each connector. These logs show the SMTP commands sent between the source and destination, and the IP addresses of the source and destination. You also learned how to activate and deactivate protocol logging,

The module concluded by examining how to troubleshoot potential transport issues using Event logs. You learned how to use the Event Viewer and Windows PowerShell to view events and troubleshoot any potential transport issues. You also learned that regularly examining the event logs can help Messaging administrators fix problems before they cause an issue or persist too long.
