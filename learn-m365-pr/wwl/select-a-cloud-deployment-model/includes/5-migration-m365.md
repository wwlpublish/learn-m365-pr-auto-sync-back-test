Once you've chosen the right deployment model for your organization, it's time to start planning your migration. The two different service models require different approaches - *migration* for cloud-only deployments and *coexistence* for hybrid deployments.

- Migration is moving everything from an old system to a new system, with the intent of eventually removing the old system. In the context of your cloud deployment, you move your data and applications from local resources up into the cloud, to infrastructure provided by your CSP. For example, if you have a free, web-based mail service and decide to move to the more secure email system in Microsoft 365, you’ll need to migrate all users’ email accounts from the free online service to Exchange Online in Microsoft 365. After that migration, users access their old email and inboxes through Outlook, and the data is stored in Exchange Online; there's nothing left in the old system to use.

- Coexistence means two different systems, one on-premises and one in the cloud, connect and work together at the same time (or *coexist*) as a single service (such as email). For example, in contrast to the example above, you've chosen to go with a hybrid environment where your Microsoft 365 subscription extends your existing Microsoft Exchange servers. You'll link the on-premises Windows Server Active Directory and Exchange Server to their online Azure Active Directory and Exchange Online counterparts. 

## Migration considerations

When you're planning your migration, the following considerations can help guide your plans.

|What you need to migrate|Strategies/considerations|
|-|-|
|Office 2013 or older to Office 365 ProPlus|Reasons to upgrade to Microsoft 365 licenses: <br><br>- After April 2023, accessing Office 365 services (like Exchange Online, SharePoint) won't be supported if you're using Office 2013.<br><br>- Office 2010 is only supported until 2020 and Office 2007 isn’t supported at all.| 
|Office Server versions to equivalent Office 365 services|	Reasons to upgrade to Office 365 services:<br><br>- Office Server 2013 and Office Server 2016 products (like Exchange Server and SharePoint Server) don’t take advantage of the cloud-based services and enhancements.<br><br>- Some Office Server 2010 products have a specified end-of-support date.<br><br>- Office Server 2007 products are no longer supported. To help with migration from this version, hire a Microsoft partner. You can then roll out the new functionality and work processes to your users and decommission the on-premises servers running Office 2007 server products when you no longer need them.|
|Windows 7 and Windows 8.1 on your devices to Windows 10 Enterprise|	Perform an in-place upgrade to Windows 10 Enterprise.|

These migrations bring your organization closer to the modern workplace: a secure and integrated environment that unlocks teamwork and creativity in your organization through Microsoft 365.
