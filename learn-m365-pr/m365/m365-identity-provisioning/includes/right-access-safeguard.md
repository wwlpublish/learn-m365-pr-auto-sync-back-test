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

[Adding or managing guest users](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations) 

 