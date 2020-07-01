> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xsMw]

Microsoft 365 is a dynamic, hyper-scale cloud containing a variety of system components. To effectively process log data from our environment and protect logs from modification, we perform log collection and analysis using secure, centralized processing, and storage services.

## Log aggregation

All auditable events defined by the Microsoft 365 Security team are collected for analysis and retention in centralized processing and storage services. Microsoft 365 uses a custom logging agent called the Office Data Loader (ODL) to enable log aggregation. The ODL agent is included in all baseline system images to collect logs according to Microsoft 365 Security logging requirements. ODL agents are configured to upload events to the central logging service in batches every five minutes. All event log transfers occur over a TLS encrypted connection on approved ports and protocols to protect log data in transit. The ODL also scrubs end-user information from log entries before transferring logs to the central processing and storage services.

The central storage service dynamically allocates audit storage space for audit logs. Any audit processing failures are reported to Service Engineer Operations personnel and escalated to Microsoft 365 Security as appropriate.

## Log retention

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xsMx]

Microsoft 365 retains audit log data in accordance with security best practices and compliance regulations. Most types of audit log data are retained for a minimum of 90 days to support incident investigations and compliance requirements. Service teams may select alternative retention periods for specific types of log data to support the needs of their applications.

Access to this log data is limited to a small number of security team personnel. Microsoft 365 log retention and backup policies ensure log data is readily available for incident investigations, compliance reporting, and any other business requirements.
