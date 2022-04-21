Message transport coexistence is automatically achieved if you have multiple Exchange Servers in your deployment. Coexistence occurs because a server automatically fails over to another server if it fails.

Consider the following issues when you are troubleshooting mail routing during coexistence:

 -  Send connectors are organization-wide, which means they're used by all Exchange Servers in the organization. If email isn't sent through the Send Connectors, verify the Send Connectors’ source servers are properly configured. In a coexistence scenario, Send Connectors may include both old and new versions of Exchange as source servers.
 -  Receive connectors are server-wide, which means that each server has its own set of receive connectors that must be configured separately. In a coexistence scenario, you must ensure that all receive connectors are configured properly on each Exchange Server before you switch the SMTP traffic from the old to the new versions of Exchange.
 -  Verify that A records and PTR records are properly configured during in a coexistence scenario. Determine which public IP address will be used for Exchange servers after previous versions of the Exchange servers are decommissioned. Then determine whether to use the same public IP address and reroute the SMTP traffic internally or assign a new public IP address where email will be routed to Exchange 2019.
 -  Verify that Exchange Online Protection services or any third-party SMTP gateways are reconfigured to send mail to Exchange servers and to receive mail from Exchange.
 -  Verify that firewalls allow SMTP traffic to and from Exchange servers.
 -  All third-party applications and devices that were using the old Exchange Server version to send email used receive connectors created and configured specifically for those applications and devices. New receive connectors must be created, configured, and tested for those applications and devices on Exchange before you uninstall the older Exchange versions.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.