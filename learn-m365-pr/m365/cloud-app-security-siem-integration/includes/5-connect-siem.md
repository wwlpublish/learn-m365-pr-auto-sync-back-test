Many organizations have Already implemented an event management (SIEM) solution and they are unlikely to want to replace this solution purely for Microsoft Defender for Cloud Apps connectivity. Fortunately, when connecting Microsoft Defender for Cloud Apps to a SIEM solution you are not obliged to use Microsoft Sentinel and can connect to other non-Microsoft SIEM solutions as long as they use Common Event Format (CEF).

## Prerequisites

The following prerequisites are required to connect a 3rd party SIEM solution to Microsoft Defender for Cloud Apps:

- A SIEM solution that can receive Syslog CEF messages.
- A syslog server with the following specifications:
  - Java 8 (or more recent) in installed
  - Running Windows or Linux
  - Two CPUs
  - At least 20 GB of free disk space
  - At least 2 GB of RAM
  - Transport Layer Security (TLS) 1.2 (or more recent)
  - Firewall settings set to connect to Microsoft Defender for Cloud Apps. See **Network requirements** in the **Summary** unit for details.

> [!NOTE]
> Note that the token is bound to the admin who created it and, if that admin account is removed, the token will no longer be valid. You should plan which account is used to create the token and ensure that it is not bound to a specific individual who could leave the organization or change role. If you have implemented Azure Active Directory (Azure AD) Privileged Identity Management (PIM) ensure that the account that has created the token has sufficient access rights.

## Steps to connect a non-Microsoft security information and event management solution to Microsoft Defender for Cloud Apps

To connect a non-Microsoft security information and event management solution to Microsoft Defender for Cloud Apps, perform the following steps:

1. In Microsoft Defender for Cloud Apps, select **Settings**, and select **Security extensions**.

    :::image type="content" source="../media/../media/2-security-extensions.png" alt-text="Security extensions.":::

1. Select **SIEM agents** and select **Add agent**.

    :::image type="content" source="../media/5-add-agent.png" alt-text="Add agent.":::

1. Select **Generic SIEM** and select **Start Wizard**.
1. Enter the name and format for the agent and select **Next**.
1. Enter the IP address information for the syslog host and select **Next**.
1. Select the alert and activity types to export to your SIEM server and select **Next**.
1. Copy the token and save it.
1. Select **Finish**.
1. Unzip the file and run the extracted file on your server:

```java
java -jar mcas-siemagent-0.87.20-signed.jar \[\--logsDirectory DIRNAME\] \[\--proxy ADDRESS\[:PORT\]\] \--token TOKEN
```

> [!NOTE]
> DIRNAME is the path to the directory you want to use for local agent debug logs.
>
> ADDRESS\[:PORT\] is the proxy server address and port that the server uses to connect to the internet.
>
> TOKEN is the SIEM agent token you saved in the previous step.

The following video walks through the steps to connect Microsoft Defender for Cloud Apps to a 3rd party SIEM:
>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyyLZ]
