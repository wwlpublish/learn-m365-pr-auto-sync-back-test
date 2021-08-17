In some ways, the easiest way to think about Zero Trust is to assume everything is on the open internet, even resources we think are safe in our “walled gardens.” With Zero Trust, we move from the world of implicit assumptions that are made based on single elements to explicit verification of all elements of access.

Many organizations harden their external access points by requiring Multi-Factor Authentication (MFA) or certifications to access their VPN. However, in Microsoft's investigations it has seen time and time again that either because of new exploits, or because of exceptions made to reduce friction with demanding (and sometimes VIP) workers, the assumption that “if they are on my network, it’s OK” isn't good enough.

A successful Zero Trust strategy requires flexible access to applications, systems, and data while maintaining security for both users and the resources they need to do their jobs. The five steps that organizations should follow to secure their identity infrastructure include:

1.  **Strengthen your credentials**. If users in your identity system are using weak passwords and not strengthening them with MFA, it isn’t a matter of if or when you get compromised—just how often you'll be compromised.
2.  **Reduce your attack surface area**. To make life harder for hackers, eliminate using older, less secure protocols, limit access entry points, and exercise more significant control of administrative access to resources.
3.  **Automate threat response**. Reduce costs and risks by reducing the time criminals have to embed themselves into your environment.
4.  **Increase your awareness**. Use auditing and logging of security-related events and related alerts to help detect patterns that may indicate internal attacks or attempted or successful external penetration of your network.
5.  **Enable user self-help**. Reduce friction by enabling your users to stay productive, even as you remain vigilant.

**Additional reading.** For more information, see [Five steps to securing your identity infrastructure](/azure/security/fundamentals/steps-secure-identity).<br>

### Move from a model of implicit trust to one of explicit verification

To implement a Zero Trust model—and assuming that all users, applications, and machines are on the internet—you must move from a model of implicit trust to one of explicit verification, where:

 -  Rather than assuming you have a user that's in a high assurance session (for example, MFA) because of the network, the claim must be verified explicitly.
 -  Instead of assuming the user has a valid machine because of the network, the device must be verified explicitly.
 -  Instead of allowing access to file shares because the user's on the network, data must be explicitly classified and encrypted.

To determine the overall risk of each session, a robust Zero Trust strategy must consider the full context of the session, which includes:

 -  The identity of the user.
 -  The state of the user's device.
 -  The apps being used.
 -  The sensitivity of the data the user is trying to access.

A Zero Trust model then applies holistic policies that define when to allow, block, or restrict access. These policies control access by requiring extra authentication challenges such as MFA, limiting functionality such as downloads, or applying compliance controls such as terms of use. This way, a hacker trying to gain access using stolen credentials on an unknown device will be blocked, as will a verified user running a healthy device trying to access data they don't have permission to see. This strategy not only protects against external threats, but it also helps create guardrails so well-meaning employees can use organizational resources responsibly.

### Zero Trust using Azure AD conditional access

Azure Active Directory (Azure AD) provides the strong, adaptive, standards-based identity verification required in a Zero Trust framework. While Azure AD provides intrinsically strong authentication (including automatic adaptive protection against many attacks), it also allows admins to express their access requirements in simple terms. Virtually every aspect of each sign-in (including associated user or session risk) is available to define the conditions under which access policies are applied. A framework of controls such as extra authentication factors, terms of use, limited access, and other session semantics regulates access. These controls guarantee that organizations are “secure at access” in their Zero Trust approach.

### Zero Trust Assessment tool

Different organizational requirements, existing technology implementations, and security stages all affect how a Zero Trust security model implementation is planned and executed. The Zero Trust Assessment tool will help you determine where you are in your journey across your identities, devices, apps, infrastructure, network, and data. It will also tell you which maturity stage you're at (Traditional, Advanced, or Optimal). The assessment will provide recommendations on how to progress to the next stage.

To take the Zero Trust assessment, see the [Zero Trust Assessment tool](https://info.microsoft.com/ww-landing-Zero-Trust-Assessment.html?azure-portal=true).

**Additional reading.** To learn more about Microsoft's own implementation of a Zero Trust security model, see [Implementing a Zero Trust security model at Microsoft](https://www.microsoft.com/itshowcase/implementing-a-zero-trust-security-model-at-microsoft?azure-portal=true).
