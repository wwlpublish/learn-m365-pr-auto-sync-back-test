Now that you know the teams responsible for incident response, we will explore each phase of the incident response process.
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wqV5]

Preparation enables rapid response when an incident occurs and may even prevent incidents in the first place. Microsoft 365 dedicates significant resources to preparing for security incidents.

## Training

Each employee working in Microsoft 365 is provided with training appropriate to their role regarding security incident response. Initial training occurs when a new employee begins working at Microsoft, and annual refresher training takes place every year thereafter. The training is designed to provide the employee with an understanding of Microsoft's fundamental approach to security. Upon completion of the training, all employees can:

- Define a security incident.
- Explain their role and responsibility to report security incidents.
- Describe how the Microsoft 365 Security Response team responds to security incidents.
- Escalate a potential security incident to the Microsoft 365 Security Response team.
- Articulate special concerns regarding privacy, particularly customer privacy.
- Access additional information about security, privacy, and escalation contacts.

In addition to general security training, employees involved in incident response receive supplementary role-based security training.

## Maintaining the on-call engineers

All service operations teams, including the Microsoft 365 Security Response team, maintain a deep on-call rotation to ensure there are resources available 24x7x365. The on-call rotation includes backups for availability and escalation points to ensure accountability. Our on-call rotations enable Microsoft 365 to mount an effective incident response at any time or scale, including widespread or concurrent events.

On-call engineers use Secure Access Workstations to access the production environment, and their access is time-bound and scoped to the tasks required for incident response.

## Tools and resources

The Microsoft 365 Security Response team is responsible for maintaining all tools and resources associated with security incident response. These include online help resources designed to quickly inform on-call engineers of proper procedures and how to escalate potential issues quickly and securely. Incident response resources also include custom tools, scripts, and processes to help the Microsoft 365 Security Response team address a variety of security issues and attack types. On-call engineers must complete yearly training and obtain up-to-date background checks to maintain eligibility for access to incident response tools and resources.

## Incident response testing

Microsoft 365 regularly tests, reviews, and updates its incident response plan to account for changes to the environment and new security threats. Our incident response testing methodology uses real-time, unpredictable attacks from an internal team of security penetration testers that we call the Red Team. The Red Team uses a variety of techniques to attempt to compromise Microsoft systems without detection. Red Team efforts simulate real-world attacks and test the capabilities of the Microsoft 365 Security Response team.

In the context of internal penetration testing, the Microsoft 365 Security Response team is known as the Blue Team. The Blue Team uses the incident response process to detect and respond to Red Team attacks as if they were genuine security incidents. Customer data is never the target of penetration testing, but these exercises help to ensure Microsoft 365 is prepared to detect, prevent, and respond to new kinds of security threats.

 :::image type="content" source="../media/red-blue-teams-definitions.png" alt-text="Two boxes with definition of Red Team and Blue Team. Red Team: Cyber-security experts who constantly attempt to breach our own production services without detection to simulate attackers by advanced adversaries. Blue Team: Cyber defenders who use sophisticated security tools and techniques to detect and defeat the Red Team's efforts." border="false":::


In addition to ongoing internal penetration testing, Microsoft 365 conducts a variety of other incident response exercises, including ‘capture the flag' events, one-off tabletop exercises, and other impromptu or organized events. These exercises supplement ongoing internal penetration testing to ensure all teams are adequately prepared to fulfill their responsibilities in the event of a real security incident.

## Protection of evidence

The data collected during an incident response is often sensitive and must remain secure. The Microsoft 365 Security Response team is responsible for ensuring adequate encryption and information protection for all incident-related communications and documentation. This includes using secured evidence lockers for storage of forensic evidence collected during investigations. The team follows approved processes for handling forensic evidence, including chain of custody, to ensure all incident-related evidence remains secure and unmodified.

## Learn more

- [Microsoft 365 security incident management: Preparation](/compliance/assurance/assurance-sim-preparation?azure-portal=true)
