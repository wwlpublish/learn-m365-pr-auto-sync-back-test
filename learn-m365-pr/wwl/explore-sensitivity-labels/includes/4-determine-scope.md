When you create a sensitivity label, you're asked to configure the label's scope. A label's scope determines two things:

 -  The label settings you can configure for that label.
 -  Where the label will be visible to users.

This scope configuration lets you have sensitivity labels that are just for documents and emails, but they can't be selected for containers. Similarly, sensitivity labels that are just for containers can't be selected for documents and emails. The following image displays a new option that's currently in preview for defining a label's scope. This feature enables you to select the scope for Azure Purview assets.

:::image type="content" source="../media/sensitivity-labels-scopes-75ffb444.png" alt-text="screenshot showing Azure Purview assets option to define a label scope":::


By default, the **Files & emails** scope is always selected. The other scopes are selected by default when the features are enabled for your tenant:<br>

 -  **Groups & sites.** [Enable sensitivity labels for containers and synchronize labels](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites?azure-portal=true).<br>
 -  **Azure Purview assets (preview).** [Automatically label your content in Azure Purview](/azure/purview/create-sensitivity-label?azure-portal=true).<br>

If you change the defaults so not all scopes are selected, you see the first page of the configuration settings for scopes you haven't selected. However, you can't configure the settings. For example, if the scope for files and emails isn't selected, you can't select the options on the next page.

:::image type="content" source="../media/sensitivity-labels-unavailable-settings-c1f0167d.png" alt-text="screenshot showing sensitivity label settings window with unavailable settings":::


For these pages that have unavailable options, select **Next** to continue. Or, select **Back** to change the label's scope.

### Label priority (order matters)

When an organization creates sensitivity labels in its admin center, they appear in a list on the **Sensitivity** tab on the **Labels** page. The order in which the labels appear in this list is important because it reflects their priority. You want your most restrictive sensitivity label, such as Highly Confidential, to appear at the bottom of the list, and your least restrictive sensitivity label, such as Public, to appear at the top.

Only one sensitivity label can be applied to an item, such as a document, email, or container. If you set an option that requires your users to provide a justification for changing a label to a lower classification, the lower classifications are identified by the order of the labels in this list. However, this option does not apply to sublabels.

The ordering of sublabels is used with [automatic labeling](/microsoft-365/compliance/apply-sensitivity-label-automatically?azure-portal=true), though. When you configure labels to be applied automatically or as a recommendation, multiple matches can result for more than one label. To determine the label to apply or recommend, the label ordering is used: The last sensitive label is selected, and then if applicable, the last sublabel.

:::image type="content" source="../media/sensitivity-label-sublabel-options-a6621794.png" alt-text="screenshot of Labels window showing the options to move labels up or down in order of priority":::


### Sublabels (grouping labels)

With sublabels, you can group one or more labels below a parent label that a user sees in an Office app. For example, under Confidential, your organization may use several different labels for specific types of that classification. In this example, the parent label Confidential is simply a text label with no protection settings, and because it has sublabels, it can't be applied to content. Instead, users must choose Confidential to view the sublabels, and then they can choose a sublabel to apply to content.

Sublabels are simply a way to present labels to users in logical groups. Sublabels don't inherit any settings from their parent label. When you publish a sublabel for a user, that user can then apply that sublabel to content. However, they can't apply just the parent label.

> [!CAUTION]
> Don't choose a parent label as the default label, or configure a parent label to be automatically applied (or recommended). If you do, the parent label won't be applied to content.

The following image shows how sublabels display for users.

:::image type="content" source="../media/sensitivity-label-grouped-labels-4d165c9b.png" alt-text="screenshot of label window showing list of sublabels in order":::


### Editing or deleting a sensitivity label

If you delete a sensitivity label from your admin center, the label isn't automatically removed from content. Any protection settings associated with that label continue to be enforced on content in which that label was applied.

If you edit a sensitivity label, the version of the label that was applied to content is what's enforced on that content.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”