The ability to attach files to messages in Teams chats is a feature that users can find helpful. However, if the files originate from untrustworthy sources, they can become a security risk.

Suppose, in your firm of legal advisors, you're concerned some Word documents might contain malicious macro code. You want to intercept malicious files that users exchange in Teams before they can compromise security.

Here, you'll learn how Safe Attachments can prevent malicious code from running and intercept other forms of attacks.

## What are Safe Attachments?

Safe Attachments for Microsoft Teams is a feature of Microsoft Defender for Endpoint. Safe Attachments helps detect and block files that are identified as malicious in Teams sites and document libraries.

Microsoft Teams allows people to share files and collaborate, and Microsoft Defender for Office 365 allows users to collaborate in a safer way. The Microsoft Defender for Office 365 Safe Attachments feature protects your organization according to policies that are set by your global or security administrators.

## How Safe Attachments works

When a file in Microsoft Teams has been identified as malicious, Microsoft Defender for Office 365 locks the file by integrating with the file store. The following image shows an example of a malicious file detected in a library.

:::image type="content" source="../media/3-file-warning.png" alt-text="Safe attachments file warning":::

Safe attachments doesn't scan all files, but uses smart heuristics and threat signals to identify malicious files. You can view Microsoft Defender for Office 365 reports to show files that have been identified as malicious in Microsoft Teams, SharePoint Online, and OneDrive for Business.

## Configure a Safe Attachments policy

To start using Safe Attachments, configure a Safe Attachment policy:

1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com/) with global administrator, security administrator, Exchange Online organization management, or Exchange Online hygiene management permissions.
1. In the left navigation bar, select **Threat management** > **Policy** > **Safe Attachments**.

    :::image type="content" source="../media/3-atp-safe-attachments.jpg" alt-text="Microsoft Defender for Office 365 Safe Attachments":::

1. Select **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams**.
1. Select **Save** and review your organization's Safe Attachments policies.

It is also recommended that you run the **Set-SPOTenant** cmdlet with the **DisallowInfectedFileDownload** parameter set to **true**. This blocks all actions except Delete for detected files. People cannot open, move, copy, or share detected files. You must be a Global admin or SharePoint Online admin to run these cmdlets.

## Learn more

- [Microsoft Defender for Office 365 Safe Attachments](/microsoft-365/security/office-365-security/atp-safe-attachments)
- [Microsoft Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams](/microsoft-365/security/office-365-security/atp-for-spo-odb-and-teams)
- [Turn on Microsoft Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams](/microsoft-365/security/office-365-security/turn-on-atp-for-spo-odb-and-teams)
