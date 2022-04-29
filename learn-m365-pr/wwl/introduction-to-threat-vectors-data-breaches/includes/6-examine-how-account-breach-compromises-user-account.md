In the previous units, you examined several methods that attackers use to collect a user’s sign-in credentials and other sensitive information. Another less commonly used method to obtain a user’s account credentials is by using a password cracking tool.

An account breach occurs when a user’s account is compromised such that it can be used by an attacker to access network resources. When the account is an administrative account, the hacker can immediately begin scouring the network to gain access to critical data. If the breached account is a regular user, the hacker can use elevation of privilege techniques to obtain administrator privileges. Elevation of privilege is discussed in the next unit.

### Mitigating an account breach

One of the recommended methods that can be used to mitigate an account breach is to use Multi-Factor Authentication (MFA). With MFA, users must complete an extra step to sign in to services. The second authentication method can be an SMS text message, key FOB, or a phone call. These methods make it much more difficult for an attacker to steal an identity without the actual account owner knowing about it. You can protect against password cracking attempts by enabling directory controls against multiple failed sign-in attempts. For example, a user account can be automatically disabled after three failed attempts. If either solution is implemented after a breach, you should also monitor the account for a period to ensure that it hasn’t been rebreached.

> [!NOTE]
> Organizations can also classify, label, and protect their documents and emails by implementing Azure Active Directory Identity Protection, which is also known as Azure Identity Protection. This cloud-based solution offers identity protection to organizations by detecting attacks in near real time, informing them of risks, and applying controls to keep their enterprises safe. Azure Identity Protection is covered in detail later in this module.
