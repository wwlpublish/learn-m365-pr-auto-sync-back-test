In the modern ultra-connected environment, threats evolve rapidly and need rapid responses. You can't wait until a security expert has identified a threat and published a virus signature to respond.

Suppose you're responsible for security in your organization. You're worried that your existing antivirus provider is not the fastest in the industry. On several occasions over the years, they've published virus signatures an hour or more after their competitors. Now, you want to reduce your exposure by using a technology that will respond to new threats more rapidly.

Here, you'll learn how next-generation protection features in Microsoft Defender for Endpoint result in near-instantaneous protection against new malware.

## What is Microsoft Defender next-generation protection?

The traditional method of protecting devices against viruses and other malware is:

- The client computers and devices run antivirus software.
- The antivirus software provider identifies new malware and provides signature files that users download to their devices.
- All files and processes are scanned against these signatures. When a match is found, the file or program is quarantined and blocked from running any code.

This system works well in most cases but relies on the antivirus provider responding rapidly with signatures for new threats. Users must also download the latest signatures often and, although downloads are often automated, protection for new threats is not instantaneous. The user may also decide to disregard the warnings they receive from their antivirus software and run the dangerous code anyway.

Microsoft Defender Antivirus is the next-generation protection component of Microsoft Defender for Endpoint. Next-generation antivirus technologies provide automatic, instantaneous protection against new and emerging threats that closes the loop holes in the traditional antivirus model.

Let's examine some of the methods Microsoft Defender Antivirus uses deliver next-generation protection.

## Cloud-delivered protection

New viruses and other threats appear all the time and the tight connections between computers around the world allow them to propagate. To implement the best protection, it's essential that these threats are identified fast.

The Microsoft Intelligent Security Graph is one tool that you can use to accelerate threat detection. The Security Graph analyses billions of connection events and signals everyday and uses AI pattern matching and machine learning to identify malicious communications without waiting for human involvement. It can also identify previously unknown security vulnerabilities in common software. Developers can connect to the Security Graph through its Application Programming Interface (API) to take advantage of its threat detection in their own software.

Microsoft Defender Antivirus uses the Security Graph as a source of information about new virus so it can respond to new threats very fast. 

As well as using the Intelligent Security Graph, Defender Antivirus uses other cloud sources for security information, including:

- **Behavior-based machine learning.** New threats are identified from sequences of suspicious behavior.
- **Metadata-based machine learning.** New threats are identified by associating metadata on files with patterns from earlier malware.
- **File classification machine learning.** New threats are identified by using neural networks to classify files and comparing them to know threat patterns.
- **Smart rules.** New threats are blocked by using rules written by security experts.
- **Detonation-based machine learning.** New threats are identified by detonating unknown files.

<!-- Image taken from https://docs.microsoft.com/microsoft-365/security/defender-endpoint/cloud-protection-microsoft-defender-antivirus -->

:::image type="content" source="../media/2-next-generation-protection-engines.png" alt-text="Next generation protection engines on clients and in the cloud in Microsoft Defender Antivirus":::

These next-generation cloud-delivered protection services are also known as the Microsoft Advanced Protection Service (MAPS)

> [!NOTE]
> Don't think of cloud-delivered protection services as protection only for files that are stored in the cloud. These services actually protect all files wherever they are stored but obtain their threat detection from cloud services.

## Detect and block unwanted apps

A Potentially Unwanted Application (PUA) is one that is not considered to be a virus, malware, or any other type of threat but might still perform actions on your clients that adversely affect their performance or functionality. Commonly, a PUA might be an application that places a high load on hardware but is not needed for users to do their jobs or software with a poor reputation. Other undesirable software includes:

- Advertising software that display ads on the desktop on within web pages.
- Bundling software that offers to install software that is not digitally signed by the same entity.
- Evasion software that circumvents security products by behaving differently in their presence.

To use Microsoft Defender for Antivirus to block PUAs, you must being running Windows 10 and then use Microsoft Intune, Endpoint Manager, Group Policy, or PowerShell to block the apps.

To use PowerShell to enable PUA protection, run this command:

```powershell
Set-MpPreference -PUAProtection Enabled
```

Once PUA protection is enable, you can use the `Get-MpThreat` PowerShell cmdlet to view blocking events. The information looks like this:

```powershell
CategoryID       : 27
DidThreatExecute : False
IsActive         : False
Resources        : {webfile:_q:\Builds\Dalton_Download_Manager_3223905758.exe|http://d18yzm5yb8map8.cloudfront.net/
                    fo4yue@kxqdw/Dalton_Download_Manager.exe|pid:14196,ProcessStart:132378130057195714}
RollupStatus     : 33
SchemaVersion    : 1.0.0.0
SeverityID       : 1
ThreatID         : 213927
ThreatName       : PUA:Win32/InstallCore
TypeID           : 0
PSComputerName   :
```

## Block a threat at first sight

Microsoft Defender Antivirus and Microsoft Defender for Endpoint include a "block at first sight" feature. You can use this feature to detect and block new malware within seconds of your systems' first contact with it. This feature closes the loophole that exists in the traditional antivirus model between the time a new threat appears in the wild and the time an antivirus provider makes its signature available to antivirus clients. To block threats at first sight, use the following settings in Microsoft Defender for Endpoint:

- Enable cloud-delivered protection
- Set the file-blocking level to high
- Set a specific sample submission timeout, such as 50 seconds

When these settings are configured, Microsoft Defender Antivirus takes the following steps for each new executable or script file:

1. It checks a hash of the file against the cloud-delivered protection services to find out if it has previously been identified as threatening or benign.
1. If the cloud services cannot identify the hash, Microsoft Defender Antivirus blocks the file temporarily and uploads a copy to the cloud protection services.
1. The cloud protection services perform more analysis on to file to determine whether it is safe or dangerous to run.

Your sample submission timeout setting determines how long the file is blocked for at step 2. You can also customize the message that is displayed on users desktop while the file is temporarily blocked.

Block at first sight reduces the response to a new and potentially dangerous file from a few hours to a matter of seconds and prevents the file from running code before it is examined.

## Always-on protection

Microsoft Defender for Endpoint and Microsoft Defender Antivirus use always-on protection to scan files and processes on the protected computer and intercept threats before they can run code. Always-on protection includes:

- **Real-time protection.** Files are scanned as soon as they are downloaded and any processes are scanned rapidly. The user doesn't experience any significant delays caused by this scanning but remains well protected.
- **Behavior monitoring.** As well as being scanned for virus signatures, processes have their behavior tracked to spot suspicious patterns of behavior.
- **Heuristics.** Heuristics are methods of intercepting threats that are more approximate but faster than alternatives. If a heuristic identifies a file or process as a threat, Defender Antivirus can temporarily block it while complete tests are run.

These methods results in fast protection, which closes some loopholes that malware has exploited in the past.

To enable always-on scanning, you can use Local Group Policy on an individual computer, or use Group Policy Objects (GPOs) in Active Directory to configure multiple computers in your organization:

1. In the Local Group Policy Editor, or in the editor for the GPO, navigate to **Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time Protection**.
1. Configure the real-time protection settings as appropriate, for example:

    | Setting | Description |
    | --- | --- |
    | Turn on behavior monitoring | Processes are monitored for suspicious patterns of activity. |
    | Scan all downloaded files and attachments | All files and attachments downloaded from the internet or email are scanned automatically. |
    | Turn on raw volume write notifications | Raw volume writes will be included in behavior monitoring |
    | Define the maximum size of downloaded files and attachments to be scanned | Files larger than this size in kilobytes will not be scanned. |
    | Configure monitoring for incoming and outgoing file and program activity | Configure whether behavior monitoring should be run for incoming files, outgoing files, or both.
    | | |

1. Select **OK**.
1. To configure scanning, navigate to **Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Scan**.
1. Configure scanning settings as appropriate, for example:

    | Setting | Description |
    | --- | --- |
    | Turn off real-time protection | Disable all real-time protection features |
    | Turn on behavior monitoring | Monitor process behavior for suspicious activity |
    | Turn on heuristics | Intercept threats by using heuristic methods |
    | | |

1. Select **OK**.