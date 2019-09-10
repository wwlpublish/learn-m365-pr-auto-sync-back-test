# Implement Conditional Access 

Azure Conditional Access helps you balance security with user productivity. It automates access control decisions based on security conditions that exist at the time of an access request.  

After the first-factor authentication completes, Conditional Access enforces the policies that you have configured. Conditional Access is not a first-line defense for scenarios like denial-of-service (DoS) attacks, but can use signals from these events, such as the sign-in risk level and location of the request, to determine whether to block access. 

  ![Identity Lifecycle](../media/icon12.png)

 ## Business use case  

Christina travels frequently for her organization. In the US or Canada, she signs in early in the day. When she travels to China, she has meetings with colleagues during local Chinese business hours as well as meetings with her team back in North America. Christina frequently checks emails or downloads documents from her iPhone. Is there a security solution that knows what’s normal for Christina, and can respond to atypical behavior automatically by enforcing access policies to re-authenticate the user or restrict access? 

## Create Conditional Access policies 

A Conditional Access policy is a definition of an access scenario using the following pattern: 

  ![Identity Lifecycle](../media/icon13.png)

When this happens defines the reason for triggering your policy. This reason is characterized by a group of conditions that have been satisfied. In Conditional Access, the two assignment conditions play a special role: 

* Users: The users performing an access attempt (Who). 

* Cloud apps: The targets of an access attempt (What). 

These two conditions are mandatory in a Conditional Access policy. You can also include additional conditions that describe how the access attempt is performed. Common examples are using mobile devices or locations that are outside your corporate network.  

The combination of conditions with your access controls represents a Conditional Access policy. Start crafting your Conditional Access policies by drafting the policy requirements for your environment.  

  ![Identity Lifecycle](../media/icon14.png)


What is Azure AD B2B 

Azure AD B2B collaboration allows you to securely share your company's applications and services with guest users and external partners from any organization, while maintaining control over your own resources. Through a simple invitation and redemption process, guest users can start collaborating on the resources you allowed them to access. 
 
  ![Identity Lifecycle](../media/icon15.png)

Your guest users and external partners manage their own identities through Azure AD, social email accounts, or any identity provider. This benefits your organization because: 

* Partners use their own identities and credentials; Azure AD is not required. 

* You don't need to manage external accounts or passwords. 

* You don't need to sync accounts or manage account lifecycles. 

## Learn more 

[Adding or managing guest users](https://docs.microsoft.com/en-us/azure/active-directory/b2b/delegate-invitations) 

 

Summary 

Azure AD provides the tools and security protocols to provision identity. It helps you define roles, organize groups, and manage users throughout the access lifecycle. You can implement and automate Conditional Access to ensure that your users have the right access at the right time to the right resources.  

Knowledge check 

Question 1 

All of these are identity management capabilities of Microsoft 365 except: 

Conditional access 
Explanation: Azure AD Conditional Access enables you to verify identity, device, app, data, and risk signals before allowing access. 

Privileged identity management 
Explanation: Privileged identity management lets you require administration accounts to request access privileges for a limited duration.  

Automated investigation and response  
Explanation: Automated investigation and response is not an identity management feature; it’s a tool that automates investigation and remediation of well-known attack threats. 

Role-based access 
Explanation: Role-based access helps you manage who has access to Azure resources, what they can do with those resources, and what areas they have access to. 

Question 2 

When you plan for identity governance in Azure AD, you should: 

Determine which users and groups should have access to which resources at which time. 
Explanation: When planning for identity governance, you should determine how soon a user has access to the resources they need and how their access changes over time. 

Prioritize the right set of alerts for investigation.  
Explanation: You prioritize alerts for investigation when you set a threshold that triggers an incident response by security operations.  

Assess the risk levels and business readiness of your organization’s cloud apps. 
Explanation: You assess the risk level of cloud apps when you want to classify and protect the exposure of sensitive information. 

Question 3 

Before you deploy a Microsoft 365 identity infrastructure, you should first: 

Assign access policies to users. 
Explanation: Before you assign access policies to user, you should first categorize users so you can control who has access to resources in your organization. 

Classify data security.  
Explanation: When you plan an identity infrastructure, you should first categorize users before you provision resources with appropriate permissions.  

Categorize your users. 
Explanation: You should first categorize users so you can secure access with controls that ensure strong assurances of identity and access from safe devices. 

 