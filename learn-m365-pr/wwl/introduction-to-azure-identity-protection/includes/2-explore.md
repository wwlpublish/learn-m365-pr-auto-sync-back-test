Azure Active Directory Identity Protection, which is also known as Azure Identity Protection, is a cloud-based solution that helps an organization monitor and report compromised or abused identities within its environment. Monitoring and reporting in Azure Identity Protection can be done automatically by administrators. They can define rules and conditions, manually by users, or a combination where users are given recommendations.

Azure Identity Protection offers identity protection to organizations by detecting attacks in near real time. It informs them of risks and applies controls to keep their enterprises safe. Most security breaches occur when attackers gain access to an environment by stealing a user’s identity.

Over the years, attackers have become increasingly effective in using third-party breaches and sophisticated phishing attacks. As soon as attackers gain access to even low privileged user accounts, it’s relatively easy for them to gain access to important company resources through lateral movement.

As a result, it's imperative that enterprise administrators:

 -  protect all identities, regardless of their privilege level.
 -  proactively prevent compromised identities from being abused.

Discovering compromised identities is no easy task. Azure Active Directory uses adaptive machine learning algorithms and heuristics to detect anomalies and suspicious incidents that indicate potentially compromised identities. Azure Identity Protection uses this data to generate reports and alerts that enable organizations to evaluate the detected issues and take appropriate mitigation or remediation actions.

Azure Identity Protection is more than a monitoring and reporting tool. It can enable organizations to protect their identities by configuring risk-based policies that automatically respond to detected issues when a specified risk level has been reached. These policies, along with other Conditional Access controls provided by Azure Active Directory and Enterprise Mobility + Security (EMS), can either automatically block or start adaptive remediation actions, including password resets and multi-factor authentication enforcement.

The following graphic shows that Azure Identity Protection is a technology inside Azure Active Directory that recognizes malicious activity and calculates risks based on the user activity.

:::image type="content" source="../media/azure-ad-identity-protection-3683e9b8.jpg" alt-text="graphic shows that Azure Identity Protection is a technology inside Azure Active Directory":::


### Azure Identity Protection Capabilities

Microsoft detects more than 10,000 attacker-controlled IP addresses per day. It also detects and blocks more than 10 million bogus sign-in attempts per day, resulting in 1.5 million newly protected credential pairs every day. This protection results in world-class signal and battle-tested algorithms that organizations can use to protect their identity infrastructure.

This information is also the basis for the following capabilities that Azure Identity Protection provides organizations:

 -  **Detecting vulnerabilities and risky accounts.** Azure Identity Protection uses all this data, analysis, and experience to generate user and sign-in risk scores. It can then notify an organization of the compromised users, risky logons, and configuration vulnerabilities in its environment before they can be exploited by cyber criminals.
 -  **Investigating risk events.** Azure Identity Protection helps organizations to better protect themselves by providing a combined view into risks, remediation recommendations, and in-line response options. It uses advanced machine learning to detect suspicious activities based on signals including brute force attacks, leaked credentials, sign-in from unfamiliar locations, and infected devices.
 -  **Risk-based Conditional Access policies.** Azure AD Identity Protection can be configured to trigger Risk-Based Conditional Access policies that automatically respond to threats by blocking sign-in attempts, issuing Azure Active Directory Multi-Factor Authentication challenges, or if the evidence is strong enough, requiring users to change their credentials. For example, if Azure Identity Protection’s machine learning system believes that a sign-in is coming from a new, anonymized, or bot-controlled network location, Conditional Access autoremediation can intercept the request with an adaptive two-factor challenge. When Azure Identity Protection’s threat intelligence or advanced machine-learning algorithms indicate that a user’s credentials are compromised, the risk-based Conditional Access policies can be triggered. These policies can offer either automatic remediation in the form of blocking the account or, with Multi-Factor Authentication, require a user-initiated password change.

Azure Identity Protection also helps organizations identify and remediate configuration vulnerabilities. It can then integrate with Azure AD Privileged Identity Management, Cloud App Discovery, and Multi-Factor Authentication to improve their security posture. Azure AD Identity Protection also can detect suspicious activity to include impossible sign-in attempts, such as signing on in New York and then in Sydney, Australia three hours later.

### Azure Identity Protection roles

You can assign several roles to load balance the management activities around your Azure Identity Protection implementation. Azure Identity Protection supports the following directory roles:

:::row:::
  :::column:::
    

**Role**


  :::column-end:::
  :::column:::
    

**Can do**


  :::column-end:::
  :::column:::
    

**Can't do**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Global administrator


  :::column-end:::
  :::column:::
    

Full access to Identity Protection, Onboard Identity Protection.


  :::column-end:::
  :::column:::
    


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Security administrator


  :::column-end:::
  :::column:::
    

Full access to Identity Protection.


  :::column-end:::
  :::column:::
    

Onboard Identity Protection, reset passwords for a user.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Security reader


  :::column-end:::
  :::column:::
    

Read-only to Identity Protection.


  :::column-end:::
  :::column:::
    

Onboard Identity Protection, remediate users, configure policies, reset passwords.


  :::column-end:::
:::row-end:::


### Risk Detection through Azure Identity Protection

Azure AD uses machine learning to detect anomalies and suspicious activity, using both signals detected in real time during sign-in attempts and non-real time signals related to users and their sign-in activities. Using this data, Azure Identity Protection calculates a real-time sign-in risk each time a user authenticates, and determines an overall risk level for reach user. Azure Identity Protection enables you to automatically take action on these risk detections by configuring user risk policies and sign-in risk policies.

Azure Identity Protection detects the following types of risk:

 -  **Sign-in risk.** Sign-in risk reflects the probability that a given authentication request isn’t authorized by the identity owner. There are two types of sign-in risks:
    
     -  **Real-time.** Real-time sign-in risk is detected at the time of the given sign-in attempt (such as sign-in attempts from anonymous IP addresses).
     -  **Total.** Total sign-in risk is the aggregate of detected real-time sign-in risks and any later non-real-time risk events associated with the user’s sign-in attempts (such as impossible travel).
 -  **User risk.** User risk reflects the overall likelihood that a bad actor has compromised a given identity. User risk contains all the risk activities for a given user, including:
    
     -  Real-time sign-in risk
     -  Later sign-in risk
     -  Risky user detections

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”