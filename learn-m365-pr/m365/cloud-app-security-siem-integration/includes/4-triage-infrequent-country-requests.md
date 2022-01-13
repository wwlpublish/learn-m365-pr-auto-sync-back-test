If connections to cloud apps originate from unusual countries, this is often a sign that it could be some form of attack. Therefore, there are systems in Microsoft Defender for Cloud Apps to block unusual country requests. In most scenarios, this is a useful feature, but sometimes it might not be beneficial. Imagine a scenario where a senior business executive has gone on annual leave to a tropical island a long way from home. While they are away, one of the organizations key clients wants to place a large last-minute order. The senior business executive needs to approve an order of this size, but they are blocked from the orders app because they are in an unusual country.

You can implement Power Automate to increase the sophistication of the response to an infrequent country request, but sometimes you need more control over the response and more information from the alert. By implementing a Microsoft Sentinel playbook, which is triggered by the Microsoft Defender for Cloud Apps infrequent country request alert, you can call APIs to get information about the user account, about their out-of-office status, about the Microsoft Defender for Cloud Apps alert, or any other information that would be useful.

Once you have gathered all of the required information, you can implement logic to automatically resolve the alert in Microsoft Defender for Cloud Apps.

By using Microsoft Sentinel, you have the ability to add granular control to the infrequent country request process. For example, you can exclude automatic resolution from members of administrator groups because there is extra risk to your systems if these accounts are compromised.

The following video includes details of using Microsoft Sentinel to add sophistication to a Microsoft Defender for Cloud Apps infrequent country request alert:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyyLY]
