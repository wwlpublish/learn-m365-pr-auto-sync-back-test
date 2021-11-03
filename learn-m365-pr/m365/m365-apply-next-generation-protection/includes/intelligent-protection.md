Your team is constantly working to address new security issues related to new threats. You want to improve the protection of your devices against the latest threats, but you need to do it in a way that will help you to reduce time and complexity for your team. Here, you'll learn about the next-generation protection features in Microsoft Defender for Endpoint that help you to achieve this task.

## What is Microsoft Defender for Cloud next-generation protection?

The traditional methods of protecting devices against viruses and other malware include:

- Running antivirus software on client computers and devices.
- Identifying new malware and providing users with signature files to download onto their devices.
- Scanning all files and processes against these signatures. When a match is found, the file or program is quarantined and blocked from running any code.

You're aware that this flow works well in most cases but relies on the antivirus provider responding rapidly with signatures for new threats. Users have to download the latest signatures often and, although downloads are often automated, protection for new threats is not instantaneous. You've also experienced users disregarding the warnings they receive from their antivirus software and running the dangerous code anyway. Microsoft Defender for Cloud's next-generation antivirus technologies provide automatic, instantaneous protection against new and emerging threats and close the loop holes in the traditional antivirus model.

Let's examine some of the capabilities of Microsoft Defender for Endpoint's next-generation protection.

### Cloud-delivered protection

You know that new viruses and other threats appear all the time and the tight connections between computers around the world allow them to propagate. To implement the best protection, you need to be able to identify these threats as fast as possible. You can use cloud-delivered protection to do this identification because it allows you to take advantage of:

- **Behavior-based machine learning**. New threats are identified from sequences of suspicious behavior.
- **Metadata-based machine learning**. New threats are identified by associating metadata on files with patterns from earlier malware.
- **File classification machine learning**. New threats are identified by using neural networks to classify files and comparing them to know threat patterns.
- **Smart rules**. New threats are blocked by using rules written by security experts.
- **Detonation-based machine learning**. New threats are identified by detonating unknown files.

:::image type="content" source="../media/next-generation-protection-engines.png" alt-text="Diagram showing the next generation protection engines on clients and in the cloud in Microsoft Defender Antivirus." lightbox="../media/next-generation-protection-engines.png":::

These next-generation cloud-delivered protection services are also known as the Microsoft Advanced Protection Service (MAPS).

> [!NOTE]
> Don't think of cloud-delivered protection services as protection only for files that are stored in the cloud. These services actually protect all files wherever they are stored but obtain their threat detection from cloud services.

You want to monitor for and block, potentially unwanted applications that are not considered to be viruses, malware, but might still perform actions on your users' devices, which adversely affect their security or functionality. For example, an unwanted application might be a program or software with a poor reputation. Unwanted software that you want to block includes:

- Advertising software that display ads on the desktop or within web pages.
- Bundling software that offers to install software that is not digitally signed by the same entity.
- Evasion software that circumvents security products by behaving differently in their presence.

### Block a threat at first sight

You can use Microsoft Defender for Endpoint's "block at first sight" feature to detect and block new malware within seconds of your systems' first contact with it. This feature closes the loophole that exists in the traditional antivirus model between the time a new threat appears in the wild and the time an antivirus provider makes its signature available to address the malware.

When you use block at first sight, the following happens to the suspicious files:

1. A hash of the file is checked against the cloud-delivered protection services to find out if it has previously been identified as threatening or benign.
1. If the cloud services cannot identify the hash, the file is blocked temporarily and a copy is uploaded to the cloud protection services.
1. The cloud protection services perform more analysis on to file to determine whether it is safe or dangerous to run.

You can specify how long the file is blocked for at step 2. You can also customize the message that is displayed on users' desktops while the file is temporarily blocked.

Use block at first sight to reduce the response to a new and potentially dangerous file from a few hours to a matter of seconds and prevents the file from running code before it is examined.

### Always-on protection

You can use always-on protection to scan files and processes on the protected computer and intercept threats before they can run code. Always-on protection is a type of protection that enables you to take advantage of:

- **Real-time protection**. Files are scanned as soon as they are downloaded and any processes are scanned rapidly. The user doesn't experience any significant delays caused by this scanning but remains well protected.
- **Behavior monitoring**. As well as being scanned for virus signatures, processes are scanned to detected suspicious patterns of behavior.
- **Heuristics**. Heuristics are methods of intercepting threats that are more approximate but faster than alternatives. If a heuristic identifies a file or process as a threat, the file is blocked temporarily while complete tests are run.

With always-on protection, you'll get faster protection, which closes some loopholes that malware has exploited in the past.
