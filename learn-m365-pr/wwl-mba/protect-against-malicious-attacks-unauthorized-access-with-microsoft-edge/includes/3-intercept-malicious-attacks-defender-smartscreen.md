Microsoft Defender SmartScreen is a service that Microsoft Edge uses to help keep you safe while you browse the web. Microsoft Defender SmartScreen provides an early warning system against websites that might engage in phishing attacks or attempt to distribute malware through a focused attack.

## Benefits of Microsoft Defender SmartScreen

Microsoft Defender SmartScreen provides several benefits, which are summarized in the following list. These benefits are described in detail in the Microsoft Defender SmartScreen documentation. The benefits are:

- Anti-phishing and anti-malware support
- Reputation-based URL and app protection
- Operating system integration
- Improved heuristics and diagnostic data
- Management through Group Policy and Microsoft Intune
- Blocking URLs associated with potentially unwanted applications (PUAs)

## Understand how Microsoft Defender SmartScreen works

A number of inputs contribute to Microsoft Defender SmartScreen warnings. Data is received from many sources, including user feedback, data providers, and intelligence models. This data is used to help identify potentially malicious content. Microsoft Defender SmartScreen also checks downloaded apps or app installers to see if they're malicious. In both scenarios, Microsoft Defender SmartScreen warns users appropriately about suspicious content.

### Site analysis

Microsoft Defender SmartScreen determines whether a site is potentially malicious by:

- Analyzing visited webpages for indications of suspicious behavior.
- Checking the visited sites against a dynamic record of reported phishing sites.

### File analysis

Microsoft Defender SmartScreen determines whether a downloaded app or app installer is potentially malicious based on many criteria, such as download traffic, download history, past anti-virus results, and URL reputation.  Notifications will surface based on the following criteria:

- Files with a known safe reputation will download without any notification.
- Files with a known malicious reputation show a warning to let the user know that the file is unsafe and has been reported as malicious. The next screenshot is an example of a warning for a malicious file.

    ![Microsoft Defender SmartScreen blocking a known malicious threat](../media/ms-edge-smartscreen-known-malicious.png)

- Files that are unknown show a warning to let the user know that the download doesn't have a known footprint and advise caution. The next screenshot is an example of a warning for an unknown file.

    ![Microsoft Defender SmartScreen warning against an unknown threat](../media/ms-edge-smartscreen-unknown-malicious.png)

Watch the video below to see how Microsoft Defender SmartScreen within Edge in action.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4FjtS]

As you just saw in the video, SmartScreen in Microsoft Edge protects from various types of threats, from phishing to malware to unauthorized applications.
