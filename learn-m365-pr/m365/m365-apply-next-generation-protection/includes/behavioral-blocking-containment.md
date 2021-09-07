As a member of the security team of your organization, you're aware that some attacks don't need to use executable files to compromise devices.  You want to find out how Microsoft Defender for Endpoint can help you to detect and mitigate these attacks.

Here, you'll learn how behavioral blocking and containment can block attacks both before they start and also while they execute by examining their behavior.

## What is behavioral blocking and containment?

Antivirus software in your organization might not be able to pick up on some threats, such as:

- **Fileless malware**. This term includes both those attacks that don't store or use files on your filesystem at all and also those attacks that may use a file in one or more stages of the complete exploit. Fileless malware is categorized into three types:

  - **Type 1:** Fully fileless malware, which never needs to write a file to your disk. Malware may infect memory, firmware, or a peripheral USB device. Most antivirus products can't scan these locations.
  - **Type 2:** Indirect file activity. Malware of this type installs files on your filesystem indirectly, for example by using the command line or PowerShell.
  - **Type 3:** Files required to operate. Malware of this type has fileless persistence, but requires files to operate successfully.
- **Human-operated attacks**. This term describes attacks initiated and continued by a malicious user, which may not use files at all and so cannot be scanned and intercepted by standard anti-virus software. Human-operated attacks also change depending on what vulnerabilities an attacker discovers on the target system.

You can use behavioral blocking and containment in Microsoft Defender for Endpoint to identify threats by their behaviors and process trees both before an attack has started, and while it is going on. Behavioral blocking and containment consist of several components including:

- Client behavioral blocking
- Feedback-loop blocking
- Endpoint detection and response (EDR) in block mode

## Use client behavioral blocking

 You can use client behavioral blocking to detect suspicious behaviors on your devices, and ensure that suspicious artifacts are blocked, checked, and remediated automatically. You'll find information about suspicious actions in Microsoft Defender for Endpoint under EDR for analysis, and to help detect similar attacks on other devices. This allows you to take advantage of machine learning in the cloud, which can differentiate between malicious sequences of actions and legitimate operations in milliseconds. And it allows you to ensure that bad actors are blocked almost instantaneously.

Use client behavioral blocking to stop attacks both before they begin in addition to after they have started. Client behavioral blocking is enabled by default.

## Use feedback-loop blocking

Feedback loop blocking is the component of behavioral blocking and containment that occurs in the cloud and is part of Microsoft Defender for Endpoint. On your devices, Microsoft Defender for Endpoint detects threats with client behavioral blocking and sends their artifacts to an engine in the cloud. This engine examines the information and correlates it with signals about suspicious activity from other devices. Based on this collated information, the engine decides whether to block the action and treat it as an attack.

Use feedback-loop blocking for fast and automatic and blocking of attacks across your organization. Feedback-looping is enabled by default.

## Use EDR in block mode

You can use EDR in block mode to protect devices from malicious artifacts, even when those devices are running Microsoft Defender Antivirus in passive mode.

In passive mode, Microsoft Defender Antivirus scans all files on the device where it runs, and reports threat detections to the Microsoft Defender for Endpoint service. But Microsoft Defender Antivirus doesn't block or remediate any viruses or malware that it detects. When you turn on EDR in block mode and Microsoft Defender Antivirus is not the primary antivirus solution, it will detect and remediate malicious items.
