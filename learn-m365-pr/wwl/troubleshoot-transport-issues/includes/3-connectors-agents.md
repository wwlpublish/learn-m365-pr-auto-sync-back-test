Exchange Server uses different types of connectors to enable inbound and outbound mail flow between Exchange servers and the transport pipeline’s various components. Receive and send connectors that are configured improperly can inhibit mail flow and cause messages to become stuck in the transport pipeline. Send and receive connectors can also be responsible for messages that are rejected for exceeding the maximum message size.

Both connector types provide detailed logs for troubleshooting. These logs are located on different places in the file system, depending on the server and connector type. The folder SmtpReceive contains logs of receive connectors, and SmtpSend contain logs of send connectors.

The following transport service logs can be helpful when troubleshooting mail flow issues:

 -  Front-End Transport service on Mailbox servers:
    
     -  %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd\\ProtocolLog\\SmtpReceive
     -  %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd\\ProtocolLog\\SmtpSend
 -  Transport service on Mailbox servers:
    
     -  %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\ProtocolLog\\SmtpReceive
     -  %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\ProtocolLog\\SmtpSend
 -  Mailbox Transport Delivery service on Mailbox servers:
    
     -  %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\ProtocolLog\\SmtpReceive\\Delivery
 -  Mailbox Transport Submission service on Mailbox servers:
    
     -  %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\ProtocolLog\\SmtpSend\\Submission
 -  Transport service on Edge Transport servers:
    
     -  %ExchangeInstallPath%TransportRoles\\Logs\\Edge\\ProtocolLog\\SmtpReceive
     -  %ExchangeInstallPath%TransportRoles\\Logs\\Edge\\ProtocolLog\\SmtpSend

### Transport agents

Transport agents process messages when they pass through the transport pipeline. These software components are located, by default, on your Exchange server, for which they provide built-in functionality. However, you can also create your own transport agents or install agents created by third-parties. Issues with one or more transport agents can inhibit mail flow in the transport pipeline.

Some of the common transport agents include:

 -  **Transport rule agent**. The transport rule agent is responsible for evaluating transport rules for every message that traverses the transport pipeline. It’s important to note that too many transport rules can slow down mail delivery, and certain rules may block delivery altogether.
 -  **Malware agent**. Exchange Server 2013 first introduced the Malware agent, which is enabled by default on Exchange Mailbox servers. This agent scans messages for viruses and other malware as the messages pass through the transport pipeline. If you have other software that conducts malware scanning on email, you should consider disabling the built-in malware agent to improve performance.
 -  **DLP policy agent**. The data loss prevention (DLP) policy agent evaluates an organization’s DLP policies, and it uses transport rules to take necessary action when it detects sensitive information. Large numbers of DLP policies can slow down mail delivery, so you should only deploy the policies that your organization requires, and you should verify they're properly configured.
