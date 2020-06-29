
[Diagram of common weaknesses](../media/common-threats-intro.png)

Users face multiple threats—from credential theft (like Mimikatz, password spray, or breach harvesting) to malware (viruses, ransomware, and the like), to phishing (gaining access to a user’s computer and credentials) and infrastructure attacks (including improperly-secured virtual machines and resources in Azure).

[Typical attack timeline](../media/typical-attack-timeline.png)

Targeted attacks usually follow a timeline similar to this image with:

- Research on company (Using social media, open source intelligence sources, data from previous attacks) and preparing for the attack.
- Elevation of privilege attack (typically using credential theft, but also abuse of administrative/management tools and configuration weaknesses).
- Attackers typically exfiltrate data for illicit purposes and go undetected for 200+ days. 

This is a general observation based on our incident response team’s experience (which is similar to what is reported by others in the industry). Precise numbers are difficult to produce because evidence of the initial “Patient 0” host is frequently lost after such a long period of time. 

Because most attacks are discovered by external parties, the variance in time to discover times usually depends on industry (retail will be quick as credit cards are put into market whereas the loss of other IP like technical designs takes longer to be apparent).
