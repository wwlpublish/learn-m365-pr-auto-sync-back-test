In an elevation of privilege scenario, once attackers have compromised one or more accounts, they then work to increase their power. In Microsoft 365, they usually want to acquire Global Administrator privileges. Specific service privileges are also desirable if the targeted data is in that product or service.

Another common pivot at this point is for the hacker to create a new account and promote that new account to a global administrator. By doing so, the attacker can now 'hide in plain sight'. In other words, the attacker will have an account that no one else is using. Usually, these accounts aren't noticed unless other administrators are regularly reviewing the global administrator account population.

### Preventing an elevation of privilege attack

In an elevation of privilege attack, user accounts are at the center of the attack pattern. As such, attackers target protection controls just as they do with an account breach. To counter these attacks, it's recommended that you implement Azure AD Multi-Factor Authentication. It's especially important to implement multifactor authentication on admin accounts and accounts with access to sensitive content.

Besides multifactor authentication, one of the best protections you can employ is to keep the number of global administrators small. It's recommended that organizations have a minimum of two and a maximum of five global admins for any size of tenant. By doing so, you keep the target area small, which makes it difficult for an attacker to hide. It's also recommended that you regularly review your global admins and their activity, including auditing and alerts.

In the event a breach of this nature occurs, you should carefully determine everything the attacker may have done to your data or to further entrench themselves in your tenancy. Look for new accounts, accounts that have had recent changes (such as promotion to a global administrator), global configuration changes, and every interaction with data from the affected accounts.

Once you've successfully regained control of the breached accounts, you can usually reverse the changes that were made. You can then determine what, if any, communication steps should be taken if data was removed or deleted. Pay careful attention to:

 -  Document access control lists
 -  Mailbox delegate permissions
 -  Mailbox forwarding rules
 -  Mail transport rules

Enabling multifactor authentication on the affected accounts is recommended.

## **Knowledge check**

Choose the best response for the following question. Then select “Check your answers.”<br>