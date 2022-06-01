Unlike retention labels, an organization can apply more than one retention policy to the same item. Each retention policy can result in a retain action and a delete action. And even though an item may have a retention policy applied to it, the item could also be subject to these actions from a retention label.

**So what happens when an item is subject to multiple retention settings that could conflict with one another? What takes precedence to determine the outcome?**

The outcome isn't which single retention policy or single retention label wins, but how long an item is retained (if applicable) and when an item is deleted (if applicable). From all the retention settings that are applied to an item, these two actions are calculated independently from each other.

For example, let's assume you have an item that's subject to two retention policies. The first policy is configured for a delete-only action. The second policy is configured to retain and then delete. As a result, this item has just one retain action but two delete actions.

Given this scenario, what conflicts may occur? Well, the retention and deletion actions could be in conflict with one another. Similarly, the two deletion actions may have a conflicting date.

When these types of conflicts occur, the principles of retention determine the outcome.

### Principles of retention

Two simple rules always decide how long an item will be retained:

 -  Retention always takes precedence over permanent deletion.
 -  The longest retention period wins.

The following rule determines when an item will be permanently deleted:

 -  The delete action from a retention label always takes precedence over the delete action from a retention policy.

Refer to the flow in the following diagram to understand the retention and deletion outcomes for a single item. Each level acts as a tie-breaker for conflicts, from top to bottom. If the outcome is determined by the first level because there are no further conflicts, there's no need to progress to the next level, and so on.

:::image type="content" source="../media/principles-of-retention-with-conflict-test-b3b72bbd.png" alt-text="Diagram showing the four levels of the principles of retention with logic flow between each level.":::


> [!IMPORTANT]
> If you're using retention labels, ensure you know [which retention label is applied](/microsoft-365/compliance/retention?azure-portal=true) before applying the principles to determine the outcome of multiple retention settings on the same item.

Before explaining each principle in more detail, it's important to understand the difference between the retention period for an item versus the specified retention period in the retention policy or retention label.

The default configuration starts the retention period when an item is created. As such, the end of the retention period is fixed for the item. That being said, files also support the configuration to start the retention period from when the file is last modified. With this alternative configuration, every time the file is modified, the start of the retention period is reset. As such, the end of the retention period for the item is extended. Retention labels also support starting the retention period when labeled and at the start of an event.

> [!TIP]
> To apply the principles in action with a series of Yes and No questions, you can also use the [retention flowchart](/microsoft-365/compliance/retention-flowchart?azure-portal=true).

#### Explanation for the four different principles

The following list provides an explanation for each principle of retention:

1.  **Retention wins over deletion**. An item won't be permanently deleted when it also has retention settings to retain it. This principle ensures that content is preserved for compliance reasons. It also ensures the delete process can still be initiated (user-initiated or system-initiated). As a result, it may remove the content from users' main view. However, permanent deletion is suspended. For more information about how and where content is retained, see the following links for each workload:
    
    
     -  [How retention works for SharePoint and OneDrive](/microsoft-365/compliance/retention-policies-sharepoint?azure-portal=true).
     -  [How retention works with Microsoft Teams](/microsoft-365/compliance/retention-policies-teams?azure-portal=true).
     -  [How retention works with Yammer](/microsoft-365/compliance/retention-policies-yammer?azure-portal=true).
     -  [How retention works for Exchange](/microsoft-365/compliance/retention-policies-exchange?azure-portal=true).
    
    **Example:** At Contoso, an email message is subject to a retention policy for Exchange. The policy is configured to delete items three years after they're created. It also has a retention label applied that's configured to retain items five years after they're created.
    
    **Outcome:** The email message is retained for five years. Why? Because this retention action takes precedence over the deletion action. As a result, the email message is permanently deleted at the end of the five years because of the delete action that was suspended while the retention action was in effect.
2.  **The longest retention period wins**. If an item is subject to multiple retention settings that retain content for different periods of time, the item will be retained until the end of the longest retention period for the item.
    
    > [!NOTE]
    > It's possible for a retention period of five years in a retention policy or label wins over a retention period of seven years in a retention policy or label. Why? Because the five-year period is configured to start based on when the file is last modified. In comparison, the seven-year period is configured to start from when the file is created.
    
    **Example:** Contoso's Marketing department has documents in its SharePoint site that are subject to two retention policies. The first retention policy is configured for all SharePoint sites to retain items for five years after they're created. The second retention policy is configured for specific SharePoint sites to retain items for 10 years after they're created.
    
    **Outcome:** Documents in this SharePoint site for Contoso's Marketing department are retained for 10 years. Why? Because that's the longest retention period for the item.
3.  **Explicit wins over implicit for deletions**. With conflicts now resolved for retention, only conflicts for deletions remain:
    
    
     -  A retention label (regardless of how it was applied) provides explicit retention in comparison with retention policies. It does so because the retention settings are applied to an individual item rather than implicitly assigned from a container. This design means that a delete action from a retention label always takes precedence over a delete action from any retention policy.
        
        **Example:** A document at Contoso is subject to two retention policies that have a delete action of 5 years and 10 years, respectively. It's also subject to a retention label that has a delete action of seven years.
        
        **Outcome:** The document is permanently deleted after seven years. Why? Because the delete action from the retention label takes precedence.
     -  When you have retention policies only: If a retention policy for a location uses an adaptive scope or a static scope that includes specific instances (such as specific users for Exchange email), that retention policy takes precedence over a static scope that's configured for all instances for the same location.
        
        A static scope that's configured for all instances for a location is sometimes referred to as an **org-wide policy**. For example, Exchange email and the default setting of **All recipients**. Or, SharePoint sites and the default setting of **All sites**. When retention policies aren't org-wide but have been configured with an adaptive scope or a static scope that includes specific instances, they have equal precedence at this level.
        
        **Example 1:** An email message at Contoso is subject to two retention policies. The first retention policy is unscoped and deletes items after 10 years. The second retention policy is scoped to specific mailboxes and deletes items after five years.
        
        **Outcome 1:** The email message is permanently deleted after five years. Why? Because the deletion action from the scoped retention policy takes precedence over the org-wide retention policy.
        
        **Example 2:** A document in a user's OneDrive account at Contoso is subject to two retention policies. The first retention policy is scoped to include this user's OneDrive account. It has a delete action after 10 years. The second retention policy is scoped to include this user's OneDrive account. It has a delete action after seven years.
        
        **Outcome 2:** At this level, it can't be determined when this document will be permanently deleted. Why? Because both retention policies are scoped to include specific instances.
4.  **The shortest deletion period wins**. Applicable to determine when items will be deleted from retention policies and the outcome couldn't be resolved from the previous level: Content is permanently deleted at the end of the shortest retention period for the item.
    
    > [!NOTE]
    > It's possible that a retention policy that has a retention period of seven years wins over a retention policy of five years because the first policy is configured to start the retention period based on when the file is created, and the second retention policy from when the file is last modified.
    
    **Example:** A document in a user's OneDrive account at Contoso is subject to two retention policies. The first retention policy is scoped to include this user's OneDrive account. It has a delete action of 10 years after the file is created. The second retention policy is scoped to include this user's OneDrive account. It has a delete action of seven years after the file is created.
    
    **Outcome:** This document will be permanently deleted after seven years. Why? Because that's the shortest retention period for the item from these two scoped retention policies.

Items subject to eDiscovery hold also fall under the first principle of retention. They can't be permanently deleted by any retention policy or retention label. When that hold is released, the principles of retention continue to apply to them. For example, they could then be subject to an unexpired retention period or a delete action.

### Principles of retention examples that combine retain and delete actions

The following examples are more complex. They illustrate the principles of retention when different retain and delete actions are combined. To make the examples easier to follow, all retention policies and labels use the default setting of starting the retention period when the item is created. By doing so, the end of the retention period is the same for the item.

 -  **Example:** An item has the following retention settings applied to it:
    
    
     -  A retention policy for delete-only after five years.
     -  A retention policy that retains for three years and then deletes.
     -  A retention label that retains-only for seven years.
    
    **Outcome:** The item is retained for seven years. Why? Because retention takes precedence over deletion. As such, the seven year retention period is the longest retention period for the item. At the end of this retention period, the item is permanently deleted because of the delete action from the retention policies.
    
    Although the two retention policies have different dates for the delete actions, the earliest the item can be permanently deleted is at the end of the longest retention period, which is longer than both deletion dates.
 -  **Example:** An item has the following retention settings applied to it:
    
    
     -  An org-wide retention policy that deletes-only after 10 years.
     -  A retention policy scoped with specific instances that retains for five years and then deletes.
     -  A retention label that retains for three years and then deletes.
    
    **Outcome:** The item is retained for five years. Why? Because that's the longest retention period for the item. At the end of that retention period, the item is permanently deleted because of the delete action of three years from the retention label. Deletion from retention labels takes precedence over deletion from all retention policies. In this example, all conflicts are resolved by the third level.

## 

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”