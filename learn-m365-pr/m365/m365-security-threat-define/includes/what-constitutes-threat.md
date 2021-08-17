
![Diagram of common weaknesses](../media/common-threats-intro.png)

Users face multiple threats—from credential theft to malware to phishing to infrastructure attacks. Examples of credential theft are Mimikatz, password spray, or breach harvesting. Examples of malware are viruses, ransomware, and the like. Phishing means gaining access to a user's computer and credentials, while infrastructure attacks include improperly secured virtual machines and resources in Azure.

![Typical attack timeline](../media/typical-attack-timeline.png)

Targeted attacks usually follow a timeline similar to the above image with:

- Research on company (Using social media, open-source intelligence sources, data from previous attacks) and preparing for the attack.
- Elevation of privilege attack (typically using credential theft, but also abuse of administrative/management tools and configuration weaknesses).
- Attackers typically extracting data for illicit purposes and going undetected for 200+ days. This is a general observation based on our incident response team's experience, which is similar to what is reported by others in the industry. Precise numbers are difficult to produce because evidence of the initial "Patient 0" host is frequently lost after such a long period of time.

Because most attacks are discovered by external parties, the variance in "time to discover" usually depends on the industry.  As an example, the retail industry usually discovers attacks more quickly as credit cards are put into the market. The loss of other intellectual property such as technical designs takes longer to be apparent.
