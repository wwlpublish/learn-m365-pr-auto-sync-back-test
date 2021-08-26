By enabling Azure Active Directory Identity Protection, organizations can:

 -  Get a combined view of flagged users and risk events that were detected using machine learning algorithms.
 -  Implement risk-based Conditional Access policies to automatically protect its users.
 -  Improve their security posture by acting on vulnerabilities proactively rather than just acting after cyber attacks have occurred.

Azure Active Directory Identity Protection includes three default policies that administrators can choose to enable:<br>

 -  **User risk policy.** Azure AD Identity Protection can calculate what it believes is normal for a user's behavior and use that to base decisions for their risk. User risk is a calculation of probability that an identity has been compromised. Administrators can make a decision based on this risk score signal to enforce organizational requirements. Administrators can choose to block access, allow access, or allow access but require a password change using Azure AD self-service password reset. If a risk is detected, users can do a self-service password reset to self-remediate and close the user risk event to prevent unnecessary noise for administrators.
 -  **Sign-in risk policy.** Azure AD Identity Protection analyzes signals from each sign-in, both real-time and offline, and calculates a risk score based on the probability that the sign-in wasn't performed by the user. Administrators can make a decision based on this risk score signal to enforce organizational requirements. Administrators can choose to block access, allow access, or allow access but require multi-factor authentication. If a risk is detected, users can complete multi-factor authentication to self-remediate and close the risky sign-in event to prevent unnecessary noise for administrators.
 -  **Azure AD Multi-Factor Authentication registration policy.** Azure AD Identity Protection can help organizations roll out Azure AD Multi-Factor Authentication (MFA) using a Conditional Access policy requiring registration at sign-in. Enabling this policy is a great way to ensure new users in your organization have registered for MFA on their first day. MFA is one of the self-remediation methods for risk events within Identity Protection. Self-remediation allows your users to take action on their own to reduce helpdesk call volume.

All three policies are turned Off by default. To turn on each policy required by your organization, complete the following steps:

1.  Sign into the Microsoft 365 admin center with a Global administrator account.
2.  In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Show all**.
3.  In the left-hand navigation pane, under **Admin centers**, select **Azure Active Directory**.
4.  In the **Azure Active Directory admin center**, in the left-hand navigation pane, select **All services**.
5.  On the **All services** page, select **Identity**.
6.  In the **Identity** pane, select **Azure AD Identity Protection.**
7.  On the **Identity Protection \| Overview** page, the three policies are listed in the middle pane under the **Protect** group. Select each of the three policies that your organization wants to enforce, and on its policy page, toggle the **Enforce policy** switch to **On**.
