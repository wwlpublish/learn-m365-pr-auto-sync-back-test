The ability to attach files to messages in Teams chats is a feature that users can find helpful. However, if the files originate from untrustworthy sources, they can become a security risk.

Suppose, in your firm of legal advisors, you're concerned some Word documents might contain malicious macro code. You want to intercept malicious files that users exchange in Teams before they can compromise security.

Here, you'll learn how Safe Attachments can prevent malicious code from running and intercept other forms of attacks.

## What is Safe Attachments?
Safe Attachments for Microsoft Teams are a feature of  Microsoft Defender for Office 365. Safe Attachments helps detect and block files that are identified as malicious in Teams sites and document libraries.

Microsoft Teams allows people to share files and collaborate, and Microsoft Defender for Office 365 allows users to collaborate in a safer way. The Microsoft Defender for Office 365 Safe Attachments feature protects your organization according to policies that are set by your global or security administrators.

## How Safe Attachments works

When a file in Microsoft Teams has been identified as malicious, Microsoft Defender for Office 365 locks the file by integrating with the file store. The following image shows an example of a malicious file detected in a library.

:::image type="content" source="../media/advanced-threat-protection-policies.png" alt-text="Screenshot of blocked file in SharePoint document library.":::

Although the blocked file is still listed in the document library and in web, mobile, or desktop applications, people can't open, copy, move, or share the file. But they can delete the blocked file. Here's an example of what a blocked file looks like on a mobile device:

:::image type="content" source="../media/blocked-file-mobile-device.png" alt-text="Screenshot of blocked file in mobile device":::

## Enable Safe Attachments for Microsoft Teams

Safe Attachments for SharePoint, OneDrive, and Microsoft Teams is not enabled by default. Admins can turn it on using UI or PowerShell. 

### Use Microsoft 365 Defender portal
1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com?azure-portal=true) as a global administrator or security administrator.

2. In the left navigation bar, select **Policies & rules** \> **Threat policies** \> **Policies** section \> **Safe Attachments**..

    :::image type="content" source="../media/threat-policy-safe-attachments.png" alt-text="Safe attachments in Threat Policies page":::

3. In the Safe attachments page, select **Global settings**.

4. In the Global settings fly out that appears, turn on the toggle under **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams**.

    :::image type="content" source="../media/safe-attachments.png" alt-text="Turn on Safe Attachments for SharePoint, OneDrive, and Microsoft Teams":::

5. Select **Save**.

### Use PowerShell

Admins can also turn on Safe Attachments by connecting to Exchange Online PowerShell (`Connect-ExchangeOnline`) and using the following command: 

```Powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

By default, people can download a blocked file. Global admins or SharePoint admins can prevent people from downloading malicious files by connecting to SharePoint Online PowerShell (`Connect-SPOService`) and running the following command: :  

```Powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```
