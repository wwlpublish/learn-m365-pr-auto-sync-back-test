Two other types of attacks worth mentioning are Password cracking and Malicious insider. These attacks are often used in the kill chain of events.

### Password cracking

In this scenario, an attacker has acquired access to an application, service, or data store that allows them to try many different password combinations for an account. Attackers use specialized software that tries thousands upon thousands of combinations in a short amount of time. If the password is short, weak, common, or the same as another account password owned by the user, the chances are good that an attacker can guess the password and compromise the account.

#### Preventing password cracking

Microsoft 365 uses Azure Active Directory (Azure AD) for authentication when federation isn't enabled. Azure AD temporarily disables an account after multiple sign-in failures. This process is referred to as smart password lockout. Keep in mind that credentials can be stored in many other places in which attackers can attempt their cracking operation. If you aren't using Azure Active Directory for authentication, it's recommended that you enable directory controls against multiple failed sign-in attempts. This process will disable an account after several failed attempts. The number of failed attempts must be determined and supported by your organization.

### Malicious insider

In this scenario, one of your approved users is conducting illicit activities in your tenant. These sorts of attacks can be the most damaging. The user usually knows a lot about your company. They also clearly understand how to maximize the negative effect on the company and its data. Motivations for a malicious insider vary, but typical ones include:

 -  Disgruntled employees looking for ways to make extra money.
 -  They want to cause issues for others before leaving the company.
 -  They want to harm specific individuals or the organization as a whole.

A malicious insider may even take steps to ensure long-term access by building in backdoor accounts or go straight to exfiltration or deleting sensitive data. Users with administrative rights are typically the most dangerous malicious insiders.

#### Preventing the malicious insider scenario

As with the other scenarios in the kill chain, you must ensure that your accounts are secure, privileges are well managed, and data is well protected.

In most cases, the attacker has achieved all the required prerequisites to execute any attack. As a result, the focus on prevention should be to ensure that you have:

 -  Processes that enable you to discern motive.
 -  Ways to identify disgruntled or unhappy employees.
 -  Ways to protect yourself from short-term vendors and contingent staff by implementing access controls and auditing.
