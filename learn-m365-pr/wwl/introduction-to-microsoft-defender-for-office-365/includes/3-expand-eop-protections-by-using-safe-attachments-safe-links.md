As email is received by an organization that's running Microsoft 365, the messages first pass through the front-line defenses provided by Exchange Online Protection (EOP). The mail is then analyzed for anything suspicious by the Safe Attachments and Safe Links features within Microsoft Defender for Office 365.

 -  **Safe Attachments.** Analyzes attachments by detonating them in a hypervisor sandbox environment. In this process, the attachment undergoes behavioral analysis to determine if it delivers a malicious payload. Infected attachments are often designed to modify a computer's registry, system settings, access rights, and so on.
 -  **Safe Links.** Checks any URLs that are embedded in the message body. The URLs are validated against a list of URLs that are known to be malicious. If URL detonation is enabled and a link that's embedded in a message or attachment points to a file on an external web server, Safe Links downloads the file to the sandbox environment. From there, it's analyzed in the same manner as a suspicious email attachment.

The following image illustrates what happens as mail flows through the EOP and Microsoft Defender for Office 365 anti-malware pipeline.

:::image type="content" source="../media/mail-flow-through-safe-attachments-and-safe-links-305003ee.png" alt-text="Diagram shows what happens as mail flows through the E O P and Microsoft Defender for Office 365 anti-malware pipeline.":::
