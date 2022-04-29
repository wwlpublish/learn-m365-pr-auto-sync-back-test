This module examined the planning aspects that must be considered when implementing directory synchronization with Microsoft 365. The module began by reviewing the four stages of deploying Azure Active Directory. You then examined how to prepare your on-premises deployment for directory synchronization.

To prepare for synchronization, you learned the importance of preparing your environment by analyzing the following features:

 -  Active Directory preparation
 -  UPN suffixes
 -  Microsoft 365 IdFix tool

With both your on-premises and cloud environments ready for synchronization, you're now ready to choose which directory synchronization tool best fits your organization's requirements. This module explored the features of each tool - Azure AD Connect and Azure AD Connect Cloud Sync.

You learned that while it's easy to implement Azure AD Connect, organizations that have a complex Active Directory implementation or special requirements must thoroughly plan the Azure AD Connect tool implementation. It has a larger footprint than Azure AD Connect Cloud Sync, but it's also the only tool that can be used in a hybrid Exchange environment. You then examined Microsoft's latest directory synchronization tool, Azure AD Connect Cloud Sync. This tool has a smaller footprint, since it uses lightweight agents to run the synchronization process. However, it doesn't currently support Exchange hybrid deployments.
