Compliance in Microsoft Teams is provided by the features of Microsoft 365   and includes information barriers, retention policies, and communications compliance.

Suppose that your board of directors has made you responsible for data protection regulations in Contoso. You want to investigate the features of Teams and Microsoft 365 to ensure that you can comply with the new regulations that have been brought in. In particular, you want to ensure that you can control offensive content, store all data for the required length of time, and closely guard information held in the accounts department.
Here, you'll learn about information barriers, retention policies, and communication compliance in Teams.

## Information barriers in Microsoft Teams

Information barriers (IB) are policies that an administrator configures to prevent individuals or groups from communicating with each other. These policies are useful if, for example, one department is handling information that shouldn't be shared with other departments; or a group needs to be prevented, or isolated, from communicating with anyone outside of that group.

Caleb and Rowan work for a large bank. Caleb is a financial advisor and Rowan works in the banking department. Because of investment banking policies, Caleb and Rowan shouldn't be about to share information with each other. Both Caleb and Rowan however can communicate with Amari in HR.  

:::image type="content" source="../media/2-information-barriers.png" alt-text="Information Barriers":::

In Microsoft Teams, you can use information barriers to prevent Caleb and Rowan from communicating. You configure information barrier policies in the Microsoft 365 Defender portal by using PowerShell cmdlets.

## Retention policies in Microsoft Teams

Organizations often need to ensure that data is kept for a fixed time period. For example, an internal policy might require that accounts be kept for 10 years or you may be bound by a legal requirement to keep communications with customers for two years. By contrast, many organizations are required to delete old data to ensure that it doesn't represent a liability. You also may need to reduce resource usage by deleting data that has no legal or business value.

You can implement these requirements by using retention policies. These policies consist of a set of retention or deletion rules and can be applied to content based on its location or features.

> [!NOTE]
> In the United States, you may be required to comply with Securities and Exchange Commission (SEC) Rule 17a-4, which requires that after a retention policy is turned on, it cannot be turned off or made less restrictive.

The default configuration in Teams is to retain chat, channel, and files date indefinitely, unless it's deleted manually or by a retention policy. You can configure Teams retention policies for chat and channel messages separately and you can apply a policy to your entire organization or to specific users and groups.
Use the Microsoft Purview compliance portal to create and manage retention policies. Alternatively, you can create them by using the Security & Compliance Center PowerShell cmdlets.

## Communication compliance in Microsoft Teams

If you want to recruit and keep the best employees from all communities, it's essential to create and foster a safe and inclusive culture in your workplace. Employees can inadvertently or deliberately threaten this culture by typing or sending inappropriate content that other users find offensive, threatening, or unwelcoming. If members of your company feel uncomfortable, they might leave and take their talents with them, which will have an impact on your profitability.

Inappropriate communications can also bring your company into disrepute if they're obtained by the news media and published.

To help prevent inappropriate communications in your company, Microsoft built communications compliance into Microsoft 365. You can use pre-defined compliance policies supplied by Microsoft or create your own custom policies to scan internal and external communications in Microsoft 365. Items that match policies are forwarded to reviewers so that they can take action to mitigate the problem. For example, the reviewer might delete the item and instruct the user to undertake a compliance training course.

Because Microsoft Teams is built on Microsoft 365, communications compliance policies automatically apply to Teams content including one-on-one or group chats.

## Learn more

- [Define policies for information barriers](/office365/securitycompliance/information-barriers-policies)
- [Information barriers in Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Retention policies in Microsoft Teams](/microsoftteams/retention-policies)
- [Microsoft Purview Communication Compliance](/microsoft-365/compliance/communication-compliance)
