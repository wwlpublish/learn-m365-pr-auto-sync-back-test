This module examined how message administrators must configure and modify message transport settings within their Exchange organization. This task includes the configuration of different transport options, managing connectors and domains, and overall message moderation.

You learned that some transport options that are valid for entire Exchange organizations are set at the organization level. These transport settings apply only to those servers in the organization running Exchange Server. Some of these settings can be modified in the Exchange Admin Center. However, to obtain full access to all the transport settings, you must use the **Get-TransportConfig** and **Set-TransportConfig** cmdlets in the Exchange Management Shell (EMS).

This module examined how Exchange supports two types of SMTP domains: accepted domains and remote domains. An accepted domain is a domain from which the Exchange organization receives and processes messages. A remote domain doesn't manage which email messages are accepted or rejected in your organization. Instead, they define settings for message delivery to SMTP domains that are external to your Exchange Server organization.

The module then examined connectors, which are a collection of instructions that customize the way your email flows to and from your Exchange Server or Exchange Online organization.
