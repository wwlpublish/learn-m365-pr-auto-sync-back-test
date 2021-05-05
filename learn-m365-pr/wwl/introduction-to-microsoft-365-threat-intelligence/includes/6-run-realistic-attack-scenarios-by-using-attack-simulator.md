One of the key tools in Microsoft 365 Threat Intelligence is the Attack Simulator, which can be used to run realistic attack scenarios in your organization. If you are a member of your organization's security team, you can use the Attack Simulator to help identify vulnerable users before a real attack impacts your organization.

To access Attack Simulator, navigate to the Security &amp; Compliance Center and select **Threat management** &gt; **Attack simulator**.

Organizations must meet the following prerequisites to run the Attack Simulator:

 -  The person running the Attack Simulator must be a Microsoft 365 Global administrator or Security administrator.
 -  The organization has Microsoft 365 Threat Intelligence, with Attack simulator visible in the Security &amp; Compliance Center (go to Threat management &gt; Attack simulator).
 -  The organization's email is hosted in Exchange Online. Attack simulator is not available for on-premises email servers.
 -  Multi-factor authentication (MFA) is turned on for at least the Microsoft 365 Global and Security administrators who will be using Attack Simulator (ideally, multi-factor authentication/conditional access is turned on for all users in the organization).

### Simulated Attacks

The following list identifies the attack simulations that are currently available in the Attack Simulator. Additional simulations will be added to Office 365 over time.

 -  **Spear Phishing (Credentials Harvest).** Phishing is a generic term for a broad suite of attacks classed as a social engineering style attack. This attack is focused on spear phishing, a more targeted attack that is aimed at a specific group of individuals or an organization. Typically, a customized attack with some reconnaissance performed and using a display name that will generate trust in the recipient, such as an email message that looks like it came from an executive within your organization. This attack focuses on letting you manipulate who the message appears to have originated from by changing the display name and source address. When spear-phishing attacks are successful, cybercriminals gain access to users' credentials.
 -  **Spear Phishing (Attachment).** This is another form of spear phishing simulation focused on exploiting an attachment to an email.
 -  **Password Spray Attack.** A password spray attack against an organization is typically used after a bad actor has successfully enumerated a list of valid users from the tenant, utilizing their knowledge of common passwords used. It is utilized widely as it is a cheap attack to run, and harder to detect than brute force approaches. This attack focuses on letting you specify a common password against a large target base of users.
 -  **Brute Force Password (Dictionary Attack).** A brute-force password attack against an organization is typically used after a bad actor has successfully enumerated a list of key users from the tenant. This attack focuses on letting you specify a set of passwords against a single user.
