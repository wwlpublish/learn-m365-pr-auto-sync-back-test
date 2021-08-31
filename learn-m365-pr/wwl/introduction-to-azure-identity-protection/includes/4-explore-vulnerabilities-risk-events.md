A vulnerability is a weakness that can be exploited by an attacker to do unauthorized actions within a computer system. Recommended solutions enable organizations to address these vulnerabilities to improve their security posture and prevent attackers from exploiting them.

:::image type="content" source="../media/azure-identity-protection-vulnerabilities-7c6f6923.png" alt-text="screenshot of Azure Identity Protection showing the Vulnerabilities window":::


The following sections provide an overview of the vulnerabilities reported by Azure Identity Protection, along with recommendations on how to address those issues.

### Multi-factor authentication registration not configured

This vulnerability can affect the deployment of Azure AD Multi-Factor Authentication (MFA) in your organization. MFA provides a second layer of security to user authentication. It helps safeguard access to data and applications while meeting user demand for a simple sign-in process. MFA delivers strong authentication through a range of easy verification options, such as phone call, text message, mobile app notification, verification code, and third-party OATH tokens.

**Recommended Action:** It's recommended that you require Azure AD Multi-Factor Authentication for user sign-in attempts. MFA plays a key role in risk-based conditional access policies available through Azure Identity Protection.

### Unmanaged cloud apps

This vulnerability helps you identify unmanaged cloud apps in your organization. In modern enterprises, IT departments are often unaware of all the cloud applications that users in their organization are using to do their work. It's easy to see why administrators have concerns about unauthorized access to corporate data, possible data leakage, and other security risks.

**Recommended Action:** It's recommended that you deploy Cloud App Discovery to discover unmanaged cloud applications. Once you've identified these unmanaged cloud apps, it's recommended that you manage them using Azure Active Directory.

### Security alerts from Privileged Identity Management

This vulnerability helps you discover and resolve alerts about privileged identities in your organization. To enable users to carry out privileged operations, organizations need to grant users temporary or permanent privileged access in Azure AD, Azure or Office 365 resources, or other SaaS apps. Each of these privileged users increases the attack surface of your organization. This vulnerability helps you identify users with unnecessary privileged access and take appropriate action to reduce or eliminate the risk they pose.

**Recommended Action:** Microsoft recommends that your organization use Azure AD Privileged Identity Management to manage, control, and monitor privileged identities. Use PIM to manage access of these identities to resources in Azure AD and other Microsoft online services, such as Microsoft 365 and Microsoft Intune.

### Azure Active Directory risk events

Most security breaches occur when attackers gain access to an environment by stealing a user’s identity. Discovering compromised identities is no easy task. Azure Active Directory uses adaptive machine learning algorithms and heuristics to detect suspicious actions that are related to an organization’s user accounts. Each detected suspicious action is stored in a record called a risk event.

Currently, Azure Active Directory detects six types of risk events:

 -  Users with leaked credentials
 -  Sign in attempts from anonymous IP addresses
 -  Impossible travel to atypical locations
 -  Sign in attempts from infected devices
 -  Sign in attempts from IP addresses with suspicious activity
 -  Sign in attempts from unfamiliar locations

:::image type="content" source="../media/azure-identity-protection-risks-c26764c0.png" alt-text="screenshot of Azure Identity Protection showing the Risk window":::


The parameters that define each risk event type are outlined in the following table.

:::row:::
  :::column:::
    

**Detection Type**


  :::column-end:::
  :::column:::
    

**Reporting Latency**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Real-time


  :::column-end:::
  :::column:::
    

5 to 10 minutes


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Offline


  :::column-end:::
  :::column:::
    

2 to 4 hours


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Risk Level**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

High


  :::column-end:::
  :::column:::
    

High confidence and high severity risk events. These events are strong indicators that the user’s identity has been compromised, and any affected user accounts should be remediated.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Medium


  :::column-end:::
  :::column:::
    

High severity and lower confidence risk event, or low severity and high confidence risk event. These events are potentially risky, and any affected user accounts should be remediated.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Low


  :::column-end:::
  :::column:::
    

Low confidence and low severity risk event. This event may not require an immediate action, but when combined with other risk events, may provide a strong indication that the identity is compromised.


  :::column-end:::
:::row-end:::


> [!NOTE]
> The insight you get for a detected risk event is tied to your Azure AD subscription. With the Azure AD Premium P2 edition, you get the most detailed information about all underlying detections. With the Azure AD Premium P1 edition, detections that aren't covered by your license appear as the following risk event: **Sign in with additional risk detected**.

The risk event type is an identifier for the suspicious action a risk event record has been created for. The following sections introduce each of the risk event types currently being tracked in Azure Active Directory.

### Users with leaked credentials

Cybercriminals often share credentials when they compromise valid passwords of legitimate users. Criminals share credentials by posting them publicly on the dark web or paste sites or by trading or selling the credentials on the black market. The Microsoft Leaked Credentials Service acquires username / password pairs by monitoring public and dark web sites and by working with:

 -  Researchers
 -  Law enforcement
 -  Security teams at Microsoft
 -  Other trusted sources

When the service acquires username/password pairs, they're checked against the Azure AD users' current credentials. If a match is found, it means that a user's password has been compromised, and a *leaked credentials risk event* is created.

### Sign-ins from anonymous IP address

This risk event type identifies users who have successfully signed in from an IP address that has been identified as an anonymous proxy IP address. These proxies are used by people who want to hide their device’s IP address, and may be used for malicious intent.

### Impossible travel to atypical locations

This risk event type identifies two sign-in attempts that originate from geographically distant locations, where at least one of the locations may also be atypical for the user, given past behavior. Among several other factors, this machine learning algorithm considers the time between the two sign-in attempts and the time it would have taken for the user to travel from the first location to the second, indicating that a different user is using the same credentials.

The algorithm ignores obvious "false positives" contributing to the impossible travel conditions, such as VPNs and locations regularly used by other users in the organization. The system has an initial learning period of 14 days during which it learns a new user’s sign-in behavior.

### Sign in from unfamiliar locations

This risk event type considers past sign-in locations (IP, Latitude/Longitude, and ASN) to determine new or unfamiliar locations. The system stores information about previous locations from which a user has signed in and considers these “familiar” locations. The risk event is triggered when the sign-in occurs from a location that's not already in the list of familiar locations. The system has an initial learning period of 30 days. During this time, the system doesn't flag any new locations as unfamiliar locations. The system also ignores sign in attempts from familiar devices, and locations that are geographically close to a familiar location.

Azure Identity Protection also detects sign in attempts from unfamiliar locations for basic authentication/legacy protocols. Because these protocols don't have modern familiar features such as client ID, there aren't enough measurements to reduce false positives. To reduce the number of detected risk events, you should move to modern authentication.

### Sign in attempts from infected devices

This risk event type identifies sign in attempts from devices infected with malware that are known to actively communicate with a bot server. This event is determined by correlating IP addresses of the user’s device against IP addresses that were in contact with a bot server.

### Sign in attempts from IP addresses with suspicious activity

This risk event type identifies IP addresses from which a high number of failed sign-in attempts were seen across multiple user accounts over a short period of time. This match of traffic patterns of IP addresses used by attackers strongly indicates that accounts are either already compromised or are about to be compromised. This machine learning algorithm ignores obvious "*false-positives,*" such as IP addresses that are regularly used by other users in the organization. The system has an initial learning period of 14 days where it learns the sign-in behavior of a new user and new tenant.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”