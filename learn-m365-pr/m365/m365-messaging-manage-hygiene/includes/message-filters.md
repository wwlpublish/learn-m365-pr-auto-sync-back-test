Some of the most important tools to improve message hygiene are filters that prevent malicious messages from reaching users. The method you use to filter messages differ based on the source or contents of the message.

>[!NOTE]
> *Malware* includes any software that is designed to cause harm to a computer or network. *Spam* is an unsolicited message often containing advertising, but sometimes designed for fraud.

## Manage connection filters for anti-spam protection

You use connection filtering in EOP (specifically, the default connection filter policy) to identify good or bad source email servers by their IP addresses. The key components of the default connection filter policy are:

- **IP Allow list**: Skip spam filtering for all incoming messages from the source email servers by specifying IP addresses or IP address ranges to allow. 
- **IP Block list**: Block all incoming messages from source email servers that you specify by IP address or IP address range. Note that incoming messages are rejected, rather than marked as spam.
- **Safe list**: This dynamic IP allow list in the Microsoft datacenter requires no customer configuration. Microsoft identifies trusted email sources and the safe list is automatically maintained and updated.

You can manage connection filters by using the Microsoft 365 Defender portal or the **Set-HostedConnectionFilterPolicy** PowerShell cmdlet.

## Configure malware filters

Email messages are automatically protected against malware by EOP. EOP uses anti-malware policies (also known as *malware filter policies*) for malware protection.

You configure an anti-malware policy using either PowerShell or the Microsoft 365 Defender portal.

1. In the Microsoft 365 Defender portal, go to **Threat management > Policy > Anti-Malware**, and then select **New +**.
1. In the New anti-malware policy page that opens, configure these settings:
  
   - **Name**
   - **Description**
   - **Malware detection response**
   - **Common attachment types filter**
   - **Malware zero-hour auto purge**
   - **Notification**
   - **Applied to**

## Configure spam filters

Inbound email messages are automatically protected against spam by EOP. EOP uses anti-spam policies (also known as spam filter policies or content filter policies) as part of your organization's overall defense against spam. Admins can view, edit, and configure (but not delete) the default anti-spam policy.

You use either PowerShell or the Microsoft 365 Defender portal to configure your anti-spam policy.

1. In the Microsoft 365 Defender portal, go to **Threat management > Policy > Anti-spam**.
2. Select **Create a policy**.
3. Specify the **Name** and **Description** and, optionally, alter any settings from the default.

## Learn more

- [Configure connection filtering](/microsoft-365/security/office-365-security/configure-the-connection-filter-policy?azure-portal=true)
- [Configure anti-malware policies](/microsoft-365/security/office-365-security/configure-anti-malware-policies?azure-portal=true)
- [Configure anti-spam policies](/microsoft-365/security/office-365-security/configure-your-spam-filter-policies?azure-portal=true)
