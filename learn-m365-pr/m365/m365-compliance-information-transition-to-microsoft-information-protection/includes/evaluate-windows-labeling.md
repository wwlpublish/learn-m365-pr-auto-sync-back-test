Applications like Word, Excel, PowerPoint, and Outlook deliver the user experience and underlying logic to add sensitivity labels to email, documents, or other content the organization wants to protect. The required labeling capabilities are built into the latest Office and Outlook clients for macOS, iOS, Android, and the web. Once labels are published, users on non-Windows platforms can manually label content. No further action is needed.

The story is different for Windows clients. During the transition to Microsoft Information Protection, the three options to enable labeling are:

- Azure Information Protection client (classic)
- Azure Information Protection unified labeling client
- Office built-in labeling client

Each client integrates with Office and Outlook, but the classic client and unified labeling client must be installed separately from Office. The requirement for a separate installation does come with a benefit. The classic client and unified labeling client support additional features not available in the Office built-in labeling client. Classifying and protecting files outside Office and Outlook is one example of a feature not supported in the Office built-in labeling client but available in the Azure Information Protection client (classic) and the Azure Information Protection unified labeling client. You can use different clients on different Windows devices to support different business requirements, but you cannot use more than one of the clients on the same machine.

## Azure Information Protection client (classic)

The Azure Information Protection client was the only labeling client for Windows prior to the introduction of the new Microsoft Information Protection framework and unified labeling. This client is commonly referred to as the Azure Information Protection client (classic), or just the classic client. This client downloads labels and policy settings from Azure and you configure the Azure Information Protection policy from the Azure portal. As previously noted, installation of this client is separate from your Office installation.

> [!NOTE]
> The Azure Information Protection client (classic) is scheduled to be deprecated on March 31, 2021.

## Azure Information Protection unified labeling client

The Azure Information Protection unified labeling client is one of two options for Windows clients to become aware of the functionality introduced with the transition to Microsoft Information Protection framework. It replaces the Azure Information Protection client (classic). This client downloads sensitivity labels and policy settings from the Microsoft 365 compliance center. The unified labeling client is close to feature parity with the Azure Information Protection client. Like the classic client, the unified labeling client installation process is a separate installation from Office. You must download this client from the Microsoft Download Center or other preferred source.

## Office built-in labeling client

The second way Office clients become aware of the new unified labeling support is via the Office built-in labeling client, available in Microsoft 365 Apps for enterprise (version 1910 or later). No separate installation is required which reduces deployment, maintenance, and support costs. The most frequently used features from the Azure Information Protection unified labeling client are included in the Office built-in labeling client and the list continues to grow.

## User experience comparison

The main difference the Azure Information Protection client (classic) user will see when using the unified labeling clients (either built-in or installed separately) is the "Sensitivity" button replaces the "Protect" button. The image below illustrates the differences between the classic client and the unified labeling client (and Office built-in labeling) on Windows. The experience is similar in iOS, macOS and on the web.

> [!div class="centered"]
> :::image type="content" source="../media/classic-unified-labeling-client.png" alt-text="Differences between the classic client and the unified labeling client (and Office built-in labeling) on Windows." border="false":::

## Windows labeling client guidance

The recommendation for both new and existing information protection customers is to use the Office built-in labeling when possible for the reasons listed below:

- **Cost**. It is more costly to deploy, maintain, and support add-on software than to use built-in functionality.
- **Performance**. Using a capability built into software generally performs better compared to an add-on.
- **Security**. The more software on the device, the bigger the attack surface.

While the Office built-in labeling client is the preferred choice, it will not work in every scenario. One reason you might need to deploy the unified labeling client instead of using the built-in client is your organization is running a standalone edition of Office or a version of Microsoft 365 Apps for Enterprise prior to version 1910. Another is you have a requirement to protect files outside Office. There are even some situations where existing customers might need to use the legacy Azure Information Protection client (classic) because they are using a feature not yet available in the unified labeling client

### Guidance for new customers

Use the decision tree below to help you decide which Windows client to install if you have yet to deploy an information protection solution from Microsoft.

> [!div class="centered"]
> :::image type="content" source="../media/windows-client-decision-tree.png" alt-text="Use the decision tree below to help you decide which Windows client to install if you have yet to deploy an information protection solution from Microsoft." border="false":::

### Guidance for existing Azure Information Protection customers

Use the decision tree below to help you decide which Windows client to install if you are an existing Azure Information Protection customer transitioning to Microsoft Information Protection.

> [!div class="centered"]
> :::image type="content" source="../media/windows-client-aip-decision-tree.png" alt-text="Use the decision tree below to help you decide which Windows client to install if you are an existing Azure Information Protection customer transitioning to Microsoft Information Protection." border="false":::

## Learn more

- [Use sensitivity labels in Office apps](/microsoft-365/compliance/sensitivity-labels-office-apps?azure-portal=true)
- [Azure Information Protection unified labeling client for Windows](/azure/information-protection/rms-client/aip-clientv2?azure-portal=true)
- [The difference between the AIP client and the AIP unified labeling client](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client?azure-portal=true)
- [Choose with labeling client to use for Windows computers](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers?azure-portal=true)
- [Announcing timelines for sunsetting label management in the Azure portal and AIP client (classic)](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179?azure-portal=true)
