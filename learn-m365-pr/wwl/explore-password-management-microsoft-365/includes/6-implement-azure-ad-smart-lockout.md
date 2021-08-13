Smart Lockout locks out bad actors who are trying to guess users’ passwords or use brute-force methods to gain access. It can recognize sign-ins coming from valid users and treat them differently than ones of attackers and other unknown sources. Smart Lockout locks out the attackers, while letting an organization's users continue to access their accounts and be productive.

By default, Smart Lockout locks the account from sign-in attempts for one minute after 10 failed attempts. After the 10th failed attempt, the account is then locked following each successive failed attempt. It's locked for one minute following the 11th failed attempt and then longer after each additional failed attempt.

Smart Lockout tracks the passwords for the three previous failed password attempts to avoid incrementing the lockout counter for the same password. If someone enters the same bad password multiple times, it won't cause the account to lock out.

> [!NOTE]
> Hash tracking functionality isn't available for customers with pass-through authentication enabled as authentication happens on-premises and not in the cloud.

Smart Lockout is always on for all Azure AD customers with these default settings that offer the right mix of security and usability. Customization of the Smart Lockout settings, with values specific to an organization, requires paid Azure AD licenses for its users.

Using Smart Lockout doesn't guarantee that a genuine user will never be locked out. When Smart Lockout locks a user account, the service tries its best to not lock out the genuine user. The lockout service attempts to ensure that bad actors can’t gain access to a genuine user account.

 -  Each Azure Active Directory data center tracks lockout independently. A user will have (threshold\_limit \* datacenter\_count) number of attempts, if the user hits each data center.
 -  Smart Lockout uses familiar location versus unfamiliar location to differentiate between a bad actor and the genuine user. Unfamiliar and familiar locations will both have separate lockout counters.

Smart Lockout can be integrated with hybrid deployments, using password hash sync or pass-through authentication to protect on-premises Active Directory accounts from being locked out by attackers. By setting Smart Lockout policies in Azure AD appropriately, attacks can be filtered out before they reach on-premises Active Directory.

### Smart Lockout integration with pass-through authentication

When using pass-through authentication, an organization must ensure that:

 -  The Azure AD lockout threshold is **less** than the Active Directory account lockout threshold. Set the values so that the Active Directory account lockout threshold is at least two or three times longer than the Azure AD lockout threshold.
 -  The Azure AD lockout duration must be set longer than the Active Directory reset account lockout counter after duration.

> [!WARNING]
> The Azure AD duration is set in seconds, while the AD duration is set in minutes.<br>

For example, if you want your Azure AD counter to be higher than AD, then Azure AD would be 120 seconds (2 minutes) while your on-premises AD is set to 1 minute (60 seconds).

> [!IMPORTANT]
> Currently, an administrator can't unlock the users' cloud accounts if they've been locked by Smart Lockout. The administrator must wait for the lockout duration to expire. However, the user can unlock by using self-service password reset (SSPR) from a trusted device or location.

### Verify on-premises account lockout policy

An organization should complete the following instructions to verify its on-premises Active Directory account lockout policy:

1.  Open the Group Policy Management tool.
2.  Edit the group policy that includes the organization's account lockout policy. For example, the **Default Domain Policy**.
3.  Browse to **Computer Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Account Policies** &gt; **Account Lockout Policy**.
4.  Verify your **Account lockout threshold** and **Reset account lockout counter after** values.

### Manage Azure AD Smart Lockout values

Based on an organization's requirements, Smart Lockout values may need to be customized. Customization of the Smart Lockout settings, with values specific to the organization, requires paid Azure AD licenses for its users.

To check or modify the Smart Lockout values for an organization, complete the following steps:

1.  Sign in to the Azure portal and navigate to **Azure Active Directory** &gt; **Authentication methods** &gt; **Password protection**.
2.  Set the **Lockout threshold**, based on how many failed sign-ins are allowed on an account before its first lockout. The default is 10.
3.  Set the **Lockout duration in seconds**, to the length in seconds of each lockout. The default is 60 seconds.

> [!WARNING]
> If the first sign-in after a lockout also fails, the account locks out again. When an account locks repeatedly, the lockout duration is increased.

### How to determine if Smart Lockout is working

When the Smart Lockout threshold is triggered, the following message will be displayed while the account is locked:

**Your account is temporarily locked to prevent unauthorized use. Try again later, and if you still have trouble, contact your admin.**
