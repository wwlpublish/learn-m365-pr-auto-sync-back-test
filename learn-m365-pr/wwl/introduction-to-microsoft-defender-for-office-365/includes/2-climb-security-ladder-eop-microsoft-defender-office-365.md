Every Microsoft 365 subscription comes with security capabilities. The goals and actions that you can take depend on the focus of these different subscriptions. In Office 365 security, there are three main security services (or products) tied to your subscription type:

 -  Exchange Online Protection (EOP)
 -  Microsoft Defender for Office 365 Plan 1 (Defender for Office P1)
 -  Microsoft Defender for Office 365 Plan 2 (Defender for Office P2)

Office 365 security builds on the core protections offered by EOP. EOP is present in any subscription where Exchange Online mailboxes can be found (remember, all the security products discussed in this unit are Cloud-based).

You may be accustomed to seeing these three components discussed in this way:

:::row:::
  :::column:::
    **EOP**
  :::column-end:::
  :::column:::
    **Microsoft Defender for Office 365 P1**
  :::column-end:::
  :::column:::
    **Microsoft Defender for Office 365 P2**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Prevents broad, volume-based, known attacks.
  :::column-end:::
  :::column:::
    Protects email and collaboration from zero-day malware, phish, and business email compromise.
  :::column-end:::
  :::column:::
    Adds post-breach investigation, hunting, and response, as well as automation, and simulation (for training).
  :::column-end:::
:::row-end:::


But in terms of architecture, let's start by thinking of each piece as cumulative layers of security, each with a security emphasis. More like this:

:::image type="content" source="../media/office-365-security-41046e7a.png" alt-text="Diagram showing how Office 365 security progresses from EOP to the two Microsoft Defender for Office 365 plans.":::


Each of these services emphasizes a goal from among Protect, Detect, Investigate, and Respond. However, *all* the services can carry out *any* of the goals of protecting, detecting, investigating, and responding.

The core of Office 365 security is EOP protection. Microsoft Defender for Office 365 P1 contains EOP in it. Defender for Office 365 P2 contains P1 and EOP. The structure is cumulative. For this reason, when an organization configures Microsoft Defender for Office 365, it should start with EOP and work to Microsoft Defender for Office 365.

Though email authentication configuration takes place in public DNS, it's important to configure this feature to help defend against spoofing.

> [!IMPORTANT]
> *If you have EOP,* *you should [configure email authentication](/microsoft-365/security/office-365-security/email-validation-and-authentication?azure-portal=true)*.

If you have Office 365 E3 or below, you have EOP. However, you also have the option to buy standalone Microsoft Defender for Office 365 P1 through upgrade. If you have Office 365 E5, you already have Microsoft Defender for Office 365 P2.

### The Office 365 security ladder from EOP to Microsoft Defender for Office 365

It can be difficult at first glance to tell how Microsoft Defender for Office 365 provides an advantage over pure EOP threat management. To help determine whether an upgrade path is right for an organization, let's look at the capabilities of each product when it comes to:

 -  preventing and detecting threats
 -  investigating
 -  responding

**Let's start with Exchange Online Protection:**

:::row:::
  :::column:::
    **Prevent/Detect**
  :::column-end:::
  :::column:::
    **Investigate**
  :::column-end:::
  :::column:::
    **Respond**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Technologies include:

 -  spam
 -  phish
 -  malware
 -  bulk mail
 -  spoof intelligence
 -  impersonation detection
 -  Admin Quarantine
 -  Admin and user submissions of False Positives and False Negatives
 -  Allow/Block for URLs and Files
 -  Reports


  :::column-end:::
  :::column:::
    

Audit log search

Message Trace


  :::column-end:::
  :::column:::
    

Zero-hour auto purge (ZAP)

Refinement and testing of allowlists and blocklists


  :::column-end:::
:::row-end:::


Because these products are cumulative, if you evaluate Microsoft Defender for Office 365 P1 and decide to subscribe to it, you'll add these abilities.

**Gains with Microsoft Defender for Office 365, Plan 1 (to date):**

:::row:::
  :::column:::
    **Prevent/Detect**
  :::column-end:::
  :::column:::
    **Investigate**
  :::column-end:::
  :::column:::
    **Respond**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Technologies include everything in EOP plus:

 -  Safe attachments
 -  Safe links
 -  Microsoft Defender for Office 365 protection for workloads (ex. SharePoint Online, Teams, OneDrive for Business)
 -  Time-of-click protection in email, Office clients, and Teams
 -  anti-phishing in Defender for Office 365
 -  User and domain impersonation protection
 -  Alerts, and SIEM integration API for alerts


  :::column-end:::
  :::column:::
    

SIEM integration API for detections

Real-time detections tool

URL trace


  :::column-end:::
  :::column:::
    

Same


  :::column-end:::
:::row-end:::


So, Microsoft Defender for Office 365 P1 expands on the ***prevention*** side of the house, and adds extra forms of ***detection***.

Microsoft Defender for Office 365 P1 also adds the **Real-time detections** tool, which can be used for investigations. Having this tool is proof that you have Microsoft Defender for Office 365 P1. Why? Because it doesn't appear in Microsoft Defender for Office 365 P2.

**Gains with Microsoft Defender for Office 365, Plan 2 (to date):**

:::row:::
  :::column:::
    **Prevent/Detect**
  :::column-end:::
  :::column:::
    **Investigate**
  :::column-end:::
  :::column:::
    **Respond**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Technologies include everything in EOP, and Microsoft Defender for Office 365 P1 plus:

 -  Same


  :::column-end:::
  :::column:::
    

Threat Explorer

Threat Trackers

Campaign views


  :::column-end:::
  :::column:::
    

Automated Investigation and Response (AIR)

AIR from Threat Explorer

AIR for compromised users

SIEM Integration API for Automated Investigations


  :::column-end:::
:::row-end:::


So, Microsoft Defender for Office 365 P2 expands on the ***investigation***and***response*** side of the house. It also adds a new hunting strength - Automation.

In Microsoft Defender for Office 365 P2, the primary hunting tool is called **Threat Explorer** rather than **Real-time detections**. If you see **Threat Explorer** when you navigate to the Microsoft 365 Defender portal, you're in Microsoft Defender for Office 365 P2.

> [!TIP]
> EOP and Microsoft Defender for Office 365 are also different when it comes to end-users. In EOP and Microsoft Defender for Office 365 P1, the focus is on **awareness**. As such, those two services include the **Report message Outlook** add-in. With this feature, users can report suspicious looking emails for further analysis.

In Microsoft Defender for Office 365 P2 (which contains everything in EOP and P1), the focus shifts to further **training** for end-users. As such, the Security Operations Center has access to the powerful **Threat Simulator** tool, and the end-user metrics it provides.

### Microsoft Defender for Office 365 Plan 1 vs. Plan 2 cheat sheet

This quick-reference will help you understand what capabilities come with each Microsoft Defender for Office 365 subscription. When combined with your knowledge of EOP features, it can help business decision makers determine what Microsoft Defender for Office 365 is best for their needs.

:::row:::
  :::column:::
    **Microsoft Defender for Office 365 Plan 1**
  :::column-end:::
  :::column:::
    **Microsoft Defender for Office 365 Plan 2**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Configuration, protection, and detection capabilities:

 -  Safe Attachments
 -  Safe Links
 -  Safe Attachments for SharePoint, OneDrive, and Microsoft Teams
 -  Anti-phishing protection in Defender for Office 365
 -  Real-time detections


  :::column-end:::
  :::column:::
    Defender for Office 365 Plan 1 capabilities\--- plus ---Automation, investigation, remediation, and education capabilities:

 -  Threat Trackers
 -  Threat Explorer
 -  Automated investigation and response
 -  Attack simulation training
 -  Proactively hunt for threats with advanced hunting in Microsoft 365 Defender
 -  Investigate incidents in Microsoft 365 Defender
 -  Investigate alerts in Microsoft 365 Defender


  :::column-end:::
:::row-end:::
