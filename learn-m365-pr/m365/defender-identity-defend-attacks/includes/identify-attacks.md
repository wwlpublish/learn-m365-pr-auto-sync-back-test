As the security analyst for your organization, you understand that attacks can specifically target identities across your organization's environment. Your organization has many users and devices, and so you need to be able to monitor for these attacks. Here, you'll learn how you can use Microsoft Defender for Identity to help you to detect for threats to your organization's identities.

Attackers' attempts to obtain identity information from your organization are often indicated by observing processes and requests that perform some or all of the following tasks:

- Reconnaissance or probing the system for security and identity information.
- Attempts to compromise the credentials of users, computers, or services.
- Collection of information, such as user accounts and identities, from a relatively open, low-privilege service for possible use against more high-value assets.
- Attempts to modify the keys and directory structure for a domain.
- Unexpected exfiltration of sensitive data from a service or computer.

Attackers often perform these tasks as a series of phases. For example, the *Reconnaissance phase* is often the starting point for an attacker, followed by the *Compromise* phase to gain a foothold in your system by gaining access to a weakly protected computer, service, or user account. At this point, the compromised account can be used by the attacker in the *Collection phase* to probe and infiltrate other parts of your system by gathering information about other more valuable accounts and assets in your environment.

An attacker may take an incremental approach, taking advantage of lateral movement paths to gain access to accounts with increasing privileges until they gain rights over your entire domain. At this point, the attacker can modify the security structure of the domain, replace encryption keys, grant and deny rights to users, and read or write any data in the domain. This stage is known as the *Domain dominance* phase. Once an attacker has control, they might transfer the account and security data (keys, passwords, and so on) to an off-site location for subsequent use. This stage is the *Exfiltration* phase. At some point in the future, this information could be used to launch a larger attack on the system or steal data from the organization.

:::image type="content" source="../media/attack.png" alt-text="A diagram that shows the phases of an attack.":::

## Detect malicious activity

You can use Microsoft Defender for Identity to detect many of the events associated with attackers' actions during their tasks and raise alerts that capture the data for the observed activities. An administrator in your organization can then investigate these activities in more detail.

:::image type="content" source="../media/sa-timeline.png" alt-text="A diagram that shows the alerts timeline in Microsoft Defender for Identity." lightbox="../media/sa-timeline.png":::

## Detect reconnaissance activity

You can use Microsoft Defender for Identity to detect reconnaissance activities. Reconnaissance activity can take several different forms. For example, an attacker could mount an account reconnaissance process that attempts to guess your users' usernames in your domain by sending sign-in requests to see which credentials works.

Other types of reconnaissance activity include:

- **Active Directory scanning.** An attacker can attempt to access your directory to gain information about your domain, such as its structure, user accounts, computers, devices, group membership, connections to other domains, and so on. An LDAP attack can also target security principals stored in the directory to identify privileged accounts and services.
- **Network mapping.** In this type of reconnaissance, an attacker submits Domain Name Server (DNS) queries to try to establish the structure of your network and the names and address of devices on the network.

:::image type="content" source="../media/smb-enumeration.png" alt-text="A screenshot that shows user and IP address reconnaissance in progress." lightbox="../media/smb-enumeration.png":::

## Detect attempts to compromise credentials

A common strategy used by attackers is the brute force attack, where your environment is repeatedly hit with sign-in requests until a valid username and password combination is found. These credentials can be saved by the attacker for later use. Despite its name, an attacker can also perform a brute force attack in a subtle manner in an attempt to reduce suspicion by making their actions follow a pattern similar to actions followed by legitimate users. For example, a process attempting to guess a password can often be hidden under a large volume of real sign-in activity if your environment normally experiences a large scale of sign-ins. With Microsoft Defender for Identity, you can monitor for these types of attacks.

## Detect possible lateral movement attacks

A lateral movement attack occurs when the stolen credentials obtained from a lower priority or less-well protected account (user or server) and these credentials are used to gain access to more of your organization's sensitive accounts and services. Once an attacker has gained access to your network, the attacker could use various tools and techniques to dig deeper into the compromised environment, obtaining ever more privileges and infiltrating more of your organization's sensitive servers.

This form of attack is often possible if the two accounts share resources. For example, the hashed credentials for a sensitive user could be stored on the device of a less sensitive user. An attacker might be able to retrieve these credentials to access other resources available to the sensitive user. The link between the two accounts is called a _lateral movement path_.

## Detect outflow of sensitive items

You can also use Microsoft Defender for Identity to detect the Active Directory database being copied from a domain controller and detect data exfiltration by watching communication over your DNS.
