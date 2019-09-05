# Learning Path: Protect Identity and Access Management with Microsoft 365 

The core foundation of cybersecurity is to identify quickly and accurately authorized users and provide them with proper access to the information and tools they need to do their jobs. Microsoft 365 provides sophisticated tools to protect the identity of your authorized users so you can authenticate their credentials and manage their access to your resources, all without hindering user productivity and collaboration.   

In this learning path, you will: 

•	Describe the identity and access management capabilities in Microsoft 365 

•	Explain how maximize protection with the identity management features in Microsoft 365 

•	Explain how to strengthen authentication using Microsoft 365 

•	Describe how to use Microsoft 365 capabilities to protect the most targeted users  

•	Describe how to use Microsoft 365 to promote organization-wide identity protection practices 

# Introduction to identity and access management  


Azure Active Directory is a component of Microsoft 365, with technologies that help ensure that only your approved users have appropriate access to your data.  Learn how these tools help you to identify, authenticate, and authorize who has access to your resources. 

In this module, you will: 

•	Describe how identity security has evolved with technologies 

•	Explain how user identity is vulnerable to attacks 

•	Explain why identity is core to security  

•	Describe a modern identity and access management strategy 

 
## The evolution of identity security  

In the past, IT secured the perimeter around the physical corporate network, like guards protecting the walls of a castle.  With today’s mobile devices, cloud computing, and Internet of Things (IoT), identity and access management must secure on-premises and cloud identities and manage access to sensitive information inside and outside the corporate network. 

Microsoft first addressed identity and access management with Windows NT Domains to consolidate on-premises accounts. Later it developed Active Directory, smartcard authentication, and support for third party multi-factor authentication (MFA).  

Threats such as sophisticated credential theft, social engineering, and password database compromises, have increased risk to your users’ identities. 

![Evolution of identity and access management](../media/icon1.png)

Microsoft 365 takes a comprehensive approach:  

Azure Active Directory (Azure AD) for unified identity management to manage single sign-in at scale  

Passwordless authentication, such as integrated phone authentication (Microsoft Authenticator) and biometrics (Windows Hello), for user convenience and productivity 

Hardware credential isolation, such as trusted platform module (TPM) and security keys for simple and secure authentication on shared devices. 

# Today’s threat landscape 

Cybersecurity attacks have become more sophisticated. Passwords alone are no longer failproof protection against unauthorized access. Hackers use phishing attacks to steal users’ credentials, then bypass network controls and expand access throughout the organization’s network.  Single factor authentication, such as passwords, isn’t enough to deter modern attacks. 

![Password Risk Data](../media/icon2.png)

The risks to your data are clear: 

81% of security breaches are caused by identity theft.  Cloud, mobile, and Internet of Things (IoT) assets are frequently outside enterprise firewalls. Identity and access controls are inconsistent across platforms, services, and devices. Once users are outside your network perimeter, they are potentially at risk for attack. 

73% of users use the same password for multiple accounts because they must remember credentials for multiple apps and devices. If a user’s identity is breached for one account, it’s only a matter of time before hackers move laterally throughout your network.  If one of your users is hacked on a non-corporate account, it might lead to a vulnerability in their work identity. 
 
Users tend to value productivity over security; 80% of employees admit using non-approved SaaS apps for work, which may introduce vulnerabilities into your network. 

# Identity challenges for today’s organizations  

The new threat landscape requires a shift from securing perimeters to protecting identities.

![New Threat Landscape](../media/icon3.png)  

•	Users need constant access using different technologies across multiple mobile devices, cloud apps, and services. 
 
•	Users suffer from an increase in identity attacks because of a lack of visibility and control over their technology. 
 
•	Organizations must comply with evolving data privacy regulations and must constantly monitor their security practices to remain compliant. 
 
•	Users want to stay productive using a simple authentication experience. 

 
# A modern identity and access management strategy 

Christina, a division VP at Contoso, travels frequently to visit the five offices that she manages across the US, UK, Canada, and parts of China. She handles highly sensitive information via connecting to corporate assets from unknown wireless networks. Classic security protocols assumed a castle under siege approach from hackers, but Christina is out in the field and needs the same protection as though she were working in her corporate office.  Her company needs security that understands her typical behavior as a user and detects when her user or device risk is elevated. If Christina’s user credentials or device are compromised, how can IT automatically enforce additional layers of authentication to keep the organization safe? 

## Identity is the new perimeter 

Identity is the new central defense and point of control that secures your organization’s data across multiple applications, locations, and devices while delivering a comprehensive identity and access management strategy.   

![Identity](../media/icon4.png)

The corporate network remains the initial defense system, but now there’s an additional layer of protection, a personal set of armor, tied directly to your users’ personal data and behaviors.   

![Identity as protection](../media/icon5.png)

Using identity as the new control plane ensures that each time users attempt to access data from the network, their personal and device data are reviewed and authenticated.  

![Business Scenario 1](../media/icon6.png)

Suppose Christina attempts to access corporate resources via her registered device.  Azure AD monitors her typical user data and validates her device based on your policy configuration to determine that this access would have a low business impact (LBI) to the network.  

![Business Scenario 2](../media/icon7.png)

Suppose Christina attempts to access the network on a device through an anonymous IP address that is outside of her expected location. Based on your policy configuration, Microsoft 365 can detect an elevated medium business impact (MBI) and require Christina to independently confirm and authenticate her identity through an alternate method, such as multi-factor authentication.   

If the device itself is compromised, as shown above, Microsoft 365 will judge it not healthy enough to access the network.  

Microsoft 365 responds to the detected access risk: 

•	Microsoft Defender can detect and remediate health threats (such as malware) on the device.  

•	Microsoft Intune can send remediation instructions to help the Christina help herself remove the problem. 


Summary 

Today’s sophisticated attacks on corporate resources require protection that can automatically recognize anomalous conditions and remediate security risks. Conditional access helps ensure that users can securely access the resources they need to stay productive. 


Check your knowledge 

Question 1 

Why do today’s security analysts sometimes describe identity security as “the new control plane?”  

Unlike the days of single organizational identities, workers today use many devices and cloud apps with multiple identities and passwords. 
Explanation: As users now access data through multiple devices and identities, the network perimeter is no longer the first line of defense. 

In the time of mainframes and local identities, IT was not concerned about identity management, but with the advent of cloud computing it’s become significant. 
Explanation: IT has always been concerned with identity security. Cloud computing and proliferation of mobile devices have made identity and access control critical.  

Before cloud computing, all user credentials resided on-premises; now they all live in a public cloud.  
Explanation: Not all organizations store user credentials in a public cloud. Regardless of where credentials reside, passwords are not the most reliable protection against network breaches. 

Question 2 

Why is user identity vulnerable to attacks in today’s digital landscape?  

Sophisticated attackers can exploit software vulnerabilities by inserting malicious code in webpages and thereby gain access to credentials stored on users’ devices. 
Explanation: Users don’t always store credentials on their devices, but smart hackers use social engineering techniques to trick users into divulging credentials. 

Most organizations now store workforce credentials in the cloud where they are increasingly vulnerable to attack. 
Explanation: Regardless of where credentials are stored, attackers target weak or duplicate passwords that are the most vulnerable to compromise. 

Because users access organization data through mobile devices and cloud apps, they must remember numerous passwords, and hackers can exploit this weakness.  
Explanation: Because users find it difficult to remember numerous personal and work passwords, they tend to use weak or duplicate passwords that are vulnerable to identity theft and brute force attacks. 

 

Question 3 

Which of these describes a modern identity and access management strategy?  

Prioritize hardening the on-premises network security perimeter while requiring periodic password changes. 
Explanation: Requiring regular password changes is best practice but it doesn’t fully address phishing attacks and the user experience. 

Protect internal and external user identity while improving user experience and productivity. 
Explanation: Users value productivity over identity protection and prefer a simple authentication experience. 

Create and enforce a single strong access policy for all users. 
Explanation: A modern access management strategy avoids a one-size-fits-all approach, preferring to customize policy based on user role and need to access. 

