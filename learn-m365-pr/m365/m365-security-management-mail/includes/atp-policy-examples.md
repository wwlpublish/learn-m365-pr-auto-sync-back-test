This example sets up a policy called "Domain and CEO" that provides both user and domain protection from impersonation and then applies the policy to all email received by users within the domain contoso.com. The security administrator has determined that the policy must meet these business requirements:

- The policy needs to provide protection for the CEO's email account and the entire domain.
- Messages that are determined to be impersonation attempts against the CEO's user account need to be redirected to the security administrator's email address.
- Messages that are determined to be impersonation attempts against the domain are less urgent and should be quarantined for later review.

The security administrator at Contoso might use the following values to create an anti-phishing policy that meets these needs.

|||
|-|-|
|**Name**|Domain and CEO|
|**Description**|Ensure that the CEO and our domain are not being impersonated.|
|**Add users to protect**|The CEO's email address at a minimum.|
|**Add domains to protect**|The organizational domain that includes the office of the CEO.|
|**Choose actions**|If email is sent by an impersonated user:<br> Choose **Redirect message to another email address**, and then type the email address of the security administrator. For example, securityadmin@contoso.com.<br>If email is sent by an impersonated domain: Choose **Quarantine message**.|
|**Mailbox intelligence**|By default, mailbox intelligence is selected when you create a new anti-phishing policy. Leave this setting **On** for best results.|
|**Add trusted senders and domains**|For this example, don't define any overrides.|
|**Applied to**|Select **The recipient domain is**. Under **Any of these**, select **Choose**. Select **+ Add**. Select the name of the domain (for example, contoso.com), and then select **Add**. Select **Done**.

## Learn more

- [Set up anti phishing policies](/microsoft-365/security/office-365-security/set-up-anti-phishing-policies?azure-portal=true)
- [Configure anti phishing policies](/microsoft-365/security/office-365-security/configure-atp-anti-phishing-policies?azure-portal=true)
- [Anti-spoofing protection in EOP](/microsoft-365/security/office-365-security/anti-spoofing-protection?azure-portal=true)
