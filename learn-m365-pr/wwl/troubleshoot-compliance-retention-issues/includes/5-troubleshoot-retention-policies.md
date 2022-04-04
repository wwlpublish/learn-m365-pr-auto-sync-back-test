Microsoft 365 compliance center helps you to ensure that items are retained for long enough to comply with legislation in your operational regions.

In your newspaper office, you need most items to be retained and available for five years. However, because emails received by your journalists are often relevant to legal cases, you want to ensure that these are available for at least seven years. You've set up retention policies that implement these rules, but you want to double-check the policies that apply in each mailbox.

Here, you'll learn how to investigate and diagnose the actions that are taken by retention policies created in the Microsoft 365 compliance center.

## What are compliance center retention policies?

As information technology becomes more pervasive in business, and the law is updated to enforce good management of personal and sensitive data, your requirements for data management become more complex. You must balance requirements such as:

- The need to comply with legislation by retaining emails and other documents for a minimum time.
- The need to reduce litigation risk by deleting old items that you're not required to keep.
- The need to ensure that users have up-to-date and relevant items that they need to do their jobs.

In the Microsoft 365 compliance center, you can use retention policies to manage automatic retention and deletion of old items to balance these requirements, and ensure compliance. Each policy selects locations by using a scope and takes one of three actions:

- **Retain content.** Ensure that content is available for a minimum time, or forever.
- **Delete content.** Ensure that content is purged after a specific time has expired.
- **Retain and then delete.** Retain content for a specific time, and then delete it.

You can create policies with one of two scope types:

- **Adaptive.** A policy with an adaptive scope uses a query to identify the mailboxes or other locations where it should apply. The query is run daily so new locations can be added automatically. For example, if an adaptive scope is applied to members of the Directors security group, new accounts added will automatically have the policy applied to them.
- **Static.** A policy with a static scope doesn't use a query and isn't evaluated after creation. For example, if a static scope is applied to members of the Directors security group, new accounts added don't have the policy applied to them. Instead, you must update the static policy to include them.

> [!IMPORTANT] 
> Compliance center retention policies are a feature of Microsoft 365 and apply to Exchange Online, SharePoint Online, Teams folders, and other storage locations. Exchange Online also has its own Messaging Records Management (MRM) technology, which remains available, but only applies to Exchange mailboxes and public folders. Exchange Online MRM is covered in Unit 6. Be sure to keep the difference between these tools in mind when you troubleshoot item retention.

## Compliance center retention policies in Exchange Online mailboxes

In Exchange Online, retention policies are implemented by using the **Recoverable Items** folder that you learned about in Unit 4. A timer job executes periodically and evaluates all the items in the Recoverable Items folder against the policies that have been applied.

If a **Retain content** or a **Retain and then delete** policy applies, and the item hasn't reached the minimum age, it's retained in Recoverable Items and can be recovered, if necessary, for example, for an eDiscovery case.

If a **Delete content** or a **Retain and then delete** policy applies, and the item has reached the necessary age, it's immediately purged from the Exchange Online database and is no longer recoverable.

## Diagnose the retention policies that apply

You can create multiple retention policies in compliance center and apply them to different scopes. Depending on the conditions you apply, it's possible that several different retention policies might apply to a mailbox. This situation can make it difficult to assess what retention behavior should be.

If items are not being retained or deleted as you expect, the first stage of troubleshooting is to determine which policies apply in the mailbox. You can diagnose these policies by using the **Policy lookup** tool:

1.  In the ccMicrosoft 365 ompliance enter, under **Solutions,** select **Information governance**.
1.  Select the **Policy lookup** tab.

    :::image type="content" source="../media/05-access-policy-lookup.png" alt-text="Screen shot showing how to access the policy lookup tool in Microsoft 365 compliance center.":::

1.  Under **Find policies that include a**, select **User,** and then enter the user's email address.
1.  Select **Search**. Policies that apply to the user's mailbox are displayed in the list.

    :::image type="content" source="../media/05-use-policy-lookup.png" alt-text="Screen shot showing how to use the policy lookup tool in Microsoft 365 compliance center.":::

If the wrong policies apply to a mailbox, you should review and correct the scopes for each one.

## Retry retention policies

When you apply a new policy or modify an existing one, it can take up to seven days before the policy applies in full to all the mailboxes in its scope. Often, the policy will take effect sooner, but don't start troubleshooting until seven days are up – the policy might not be complete.

After seven days, if the policy is still not working as expected, you can use the `Set-AppRetentionCompliancePolicy` cmdlet to redistribute it, which might overcome any replication issues:

``` powershell
Set-AppRetentionCompliancePolicy -Identity ContosoExecsRetentionPolicy -RetryDistribution
```

# Learn more

- [Learn about retention policies and retention labels](/microsoft-365/compliance/retention?view=o365-worldwide)
- [Learn about retention for Exchange](/microsoft-365/compliance/retention-policies-exchange)
- [Create and configure retention policies](/microsoft-365/compliance/create-retention-policies)
