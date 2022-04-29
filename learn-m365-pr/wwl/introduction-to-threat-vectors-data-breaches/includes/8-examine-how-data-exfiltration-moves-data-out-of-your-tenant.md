Once a network is compromised, an attacker can use various techniques to move data out of your tenant. Data exfiltration is the unauthorized retrieval of data from a computer or service. Data can be stolen in any number of ways. One of the most common methods is through a breach of an account that has access to the data. Another method is through system and infrastructure attacks that give the attacker local or system admin privileges to computers that store the data outside of Microsoft 365.

Attackers are motivated by various goals, including:

 -  Theft of intellectual property.
 -  The intent to blackmail you.
 -  Selling your data on the black market.
 -  Using the data to further entrench themselves in your systems.

Protecting data is complicated by the basic fact that data comes in various forms. Email, documents, instant messaging conversations, Yammer threads, even identifying your directory information can be useful to an attacker.

### Preventing data exfiltration

An organization should pursue different strategies to keep its data from being compromised. It should focus not only on the data itself, but also on the things needed to access the data, such as accounts. Protecting its service from account breaches and elevation of privilege attacks will be the first step in protecting its data.

There are many strategies an organization can pursue to protect its data, including:

 -  **Access control lists.** Establish standards for determining who should have access to specific kinds of data. Then create processes to monitor and maintain those access controls. For example, if you have sensitive financials data in a SharePoint Online site, ensure that:
    
     -  The site and document libraries are restricted to only named individuals.
     -  The site and document libraries are restricted to just the minimum privileges they need.
     -  You regularly review the access control list.
 -  **External sharing policies.** Prevent data leakage to external endpoints by configuring your tenant to restrict certain types of sharing. For example, you can configure your tenant to not allow documents to be shared with any external people. These types of policies can be restrictive, so you may need to strike a balance between risk and productivity.
 -  **Least privilege.** Users will often grant permissions to documents and document libraries that exceed the access that's required. For example, View permission versus Edit permission. Only grant the required minimum privilege to the smallest group of users that you can.
 -  **Data classification schemes.** Another key strategy is to use data classification metadata. This strategy is important when data is shared on SharePoint sites and OneDrive for Business. This process requires that you first determine a set of risk tiers (such as high business impact, medium business impact, low business impact). You must then require sites and documents to tag data in your systems with the appropriate classification. This strategy enables you to monitor sensitive data and use specific technologies to further protect high business impact data.
 -  **Data loss prevention (DLP**). The data classification scheme that's based on risk tiers (high business impact, medium business impact, low business impact) is most effective when used in combination with the DLP feature in Microsoft 365. This technology enables you to configure rules about how to handle data moving in and out of your tenant. It can prevent sensitive document content from being emailed to external parties, and prevent your users from sending social security numbers in email.

Along with these recommendations, Microsoft 365 administrators can enable auditing, alerts, and Advanced Security Management to detect suspicious behaviors or activities in the tenant.
