A hybrid deployment includes special management and monitoring requirements. These requirements are because of the complex configuration of hybrid deployments that automatically exchange information between the Exchange Server on-premises organization and Exchange Online. The complexity of this configuration isn't visible to end users, but you must monitor specific areas of the deployment to ensure that it functions properly.

### Monitor a hybrid deployment

A Messaging administrator should complete the following tasks to monitor a hybrid deployment:

 -  **Ensure that Azure AD Connect is running reliably**. Azure AD Connect synchronizes the underlying Active Directory that supports the Exchange Server on-premises environment with Exchange Online. For example, if you configure a personal archive for a mailbox that's stored in an Exchange database on-premises, Azure AD Connect synchronizes the properties of the mailbox so that Exchange Online recognizes the archive. If Azure AD Connect isn't running, Exchange Online doesn't recognize the change and the user can't use their archive. Microsoft 365 automatically monitors your Directory Synchronization activity, and it sends a message to the technical account if Directory Synchronization doesn't occur for a day.
 -  **Manage synchronization between Exchange Server on-premises and Exchange Online.** Use the Exchange Admin Center (EAC) of the on-premises Exchange Server environment to manage Exchange Server on-premises and Exchange Online recipients so that Directory Synchronization synchronizes them correctly. If you use the Exchange Admin Center to synchronize users, distribution lists, and contacts, keep in mind that synchronization occurs in one direction only—from the Exchange Server on-premises organization to Exchange Online. For example, if you create an on-premises user mailbox, Directory Synchronization creates the user mailbox in Exchange Online. But if you create a user mailbox in Exchange Online, Directory Synchronization doesn't synchronize or create the user mailbox in AD DS.
 -  **Monitor message routing between on-premises and Exchange Online.** Message routing between Exchange Server on-premises and Exchange Online is one of the most important factors that makes a hybrid deployment successful. Make sure that the messages flow successfully and don't queue somewhere. For this reason, it’s recommended that you monitor the queues in the Exchange Server on-premises environment so that you can react quickly if messages queue for too long.
 -  **Use monitoring software to monitor the federated delegation.** Federated delegation is the basis for the information exchange between Exchange Server on-premises and Exchange Online. If federated delegation doesn't work properly, users can't retrieve any free/busy information, MailTips, or other information between the on-premises and cloud deployments. Consider testing federated delegation with the monitoring software so that you’re notified immediately if federated delegation doesn't work. Also consider using the following test cmdlets:
    
     -  Test-FederationTrust
     -  Test-FederationTrustCertificate
     -  Test-OrganizationRelationship
 -  **Verify the configuration by running the Microsoft Remote Connectivity Analyzer.** The Microsoft Remote Connectivity Analyzer (RCA) is a Microsoft tool that can verify your configuration, such as the Exchange Web Services or Exchange ActiveSync settings, and ensure that all settings are configured properly. This tool helps prevent issues that can easily be overlooked. Because a hybrid deployment uses those services to communicate between Exchange Online and on-premises, an organization should occasionally run the RCA to verify that its configuration hasn't changed in any way.
 -  **Monitor the middle-tier components.** A hybrid deployment involves not only Exchange servers but other components as well, such as the new Hybrid Agent and firewalls. As such, you must ensure that these components function correctly by monitoring any middle-tier components that are involved in the deployment. These components include Active Directory Federation Services, third-party firewalls, and other products.

### Update a hybrid deployment

There are various situations when a Messaging administrator must update their hybrid deployment by running the Hybrid Configuration wizard again, including:

 -  They add an accepted domain to their on-premises Exchange environment.
 -  They add a domain to their Microsoft 365 tenant.
 -  They update their Exchange certificate.
 -  They change their Exchange organizational settings.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.