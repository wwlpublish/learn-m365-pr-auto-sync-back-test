You've learned about the signs of a ransomware attack, and how to detect them. But what can be done if a ransomware attack has been spotted? It's important not to panic should the situation arise. Organizations and individuals can deal with the attack by investigating it first, and then respond appropriately.

## Investigate the attack

To investigate a ransomware attack effectively, the first step is to identify any potential entry points. These are ways that the cybercriminal might have used to gain access and carry out their attack. Entry points can include, but aren't limited to:

- Emails
- Social media accounts
- Removable devices
- Mobile devices
- Wireless networks
- Applications
- People

Potential entry points vary widely, and the attacker could have used any combination of them. Let's consider the case of an organization that has identified an attack. The security team can start an investigation by considering whether there are any entry points that don't have appropriate safeguards in place, as these are the most vulnerable to an attack. For example, they could ask the following questions:

- Are there any apps or devices that haven't been kept up-to-date?
- Do all accounts use strong passwords and multi-factor authentication (verification codes sent to the user's mobile device) when signing in?
- Have there been any suspicious social media or email interactions?
- Has anyone recently downloaded any suspicious apps?

Asking questions like these enable the organization to find possible entry points, but will also help them think about the potential *trajectory* of the attack. The trajectory is how an attack moves across your devices and network. This is because one entry point can give a cybercriminal access to other targets, so they can continue and strengthen their attack.

For example, let's consider a staff member who recently spent some time looking for a tool that could help with their latest work project. They downloaded a couple of different apps from various sites and installed them just to see if they could be useful. The reality is that one or more of these could have been malicious or compromised apps with malicious code that might have acted as an entry point for the attacker on their device.

To propagate the attack, the cybercriminal might have snooped around the device to find important assets, like files and information to hold the user hostage. Additionally, they might have successfully found vulnerabilities that could have enabled them to access the wider network the device is connected to. This would mean they could silently propagate the attack to all connected devices.

Nowadays, we're surrounded by so many devices, user accounts, and networks that it would be difficult to manually identify a complete attack trajectory. This problem is exacerbated for organizations, because they rely on a much larger scale of devices, users, and complex networks. Fortunately, there are clever antimalware tools that can identify the attack trajectory from entry points, along with any suspected attack related activities, mapped across all affected devices. A trajectory could look like this:

:::image type="content" source="../media/potential-trajectory.png" alt-text="Diagram that shows a map of devices and users in a path." border="false":::

This diagram shows how a potential trajectory could be mapped out. It represents how an attacker could get to a key user in an organization, like a global manager.

The attacker could start by compromising a user account in the Contoso-IT user group. This group can access the REDMOND-WA-DEV2 server, with administrator-level permissions. The attacker could access this server if they successfully compromise anyone in the user group. But that's only the beginning.

The server also happens to frequently be accessed by a user named Oscar. He has access to the REDMOND-WA-DEV2 server, but is also a member of another user group, called Contoso-All. As a result, Oscar has administrator privileges on another server, the REDMOND-WA-DEV server. The attacker could choose to target Oscar's account and, if successful, would then have administrator permissions on the server. This server is used on a daily basis by Samira, who is a global IT administrator. This now means the attacker could target Samira and, because she's a key user, the consequences could be serious, both for her and the organization as a whole.

The takeaway here is that a ransomware attack rarely ends where it starts, and can affect any users and devices along the way.

## Respond and recover from the attack

When the investigation has concluded, it's crucial to respond effectively to mitigate the potential damage of the attack and recover successfully. Here are some basic actions organizations and individual users can take:

:::image type="content" source="../media/phases-responding-recovering.png" alt-text="Diagram showing the main phases in responding and recovering." border="false":::

### Quarantine

It's essential to isolate any devices and other entities that have been impacted by the attack. Here are some actions that will help to quarantine compromised entities.

- Use built-in email platform capabilities to automatically label and move any malicious messages to a quarantine folder if they haven't been already.
- Disconnect infected devices, including mobile devices, from all network connections.
- In some serious situations, it might be necessary to turn off network devices, like Wi-Fi routers, and disconnect from the internet altogether.
- Organizations should consider blocking compromised entities like user accounts from accessing crucial apps and resources.

This will ensure that the attack doesn't continue to propagate itself. It also provides a clearer idea of where to concentrate efforts.

### Reset or wipe

Going back to our example organization, when the security team has isolated the compromised entities, they can try to reset or wipe them safely.

For entities like user accounts, they'll need to reset their credentials, and maybe even replace the accounts if necessary. For devices, they should follow the standard guidance for resetting or wiping. Devices like computers and mobile phones will come with tools that help to completely remove everything on the device, reinstall the operating system, or reset to *factory default* settings. Factory default is the state your device was in when you first bought it.

However, before the security team resets or erases anything, they'll need to make sure they have a working backup that is also free from any malware. We'll cover this next.

### Restore from backups

Devices will take regular backups of all the important information they contain. Sometimes, they'll even store backups in the cloud, on computers in a secure network across the internet. Either way, the team will need to locate the last known good backup. This means that they have to identify the latest available backup and scan the files using antimalware software to ensure that they're free from malware. They can then use either a standalone restoration tool - as long as it's from a trustworthy vendor - or a built-in tool to restore from this backup. The device will be restored based on the backup. This means it will effectively go back in time, and mirror the state it was in when the backup was created.

### Learn and ask for help

When everything has been restored, you can begin to think about how to prevent future attacks. For example, by making sure you keep antimalware software up-to-date or learning how to better spot suspicious emails and activities. In short, you can take the situation as a learning experience. Ransomware attacks can be complicated and stressful to deal with, so it's important to realize that there is help available. Don't be afraid to contact trusted cybersecurity professionals and authorities. They can help you to deal with a ransomware attack, and potentially recover from it - they might even be able to decrypt your locked data using sophisticated tools. You can also learn about the best measures to prevent a ransomware attack, or any other kind of cyberattack, in the future.
