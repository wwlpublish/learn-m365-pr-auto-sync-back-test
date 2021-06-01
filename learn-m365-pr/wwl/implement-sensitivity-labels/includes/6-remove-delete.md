In a production environment, it's unlikely that you'll need to delete sensitivity labels or remove sensitivity labels from a label policy. It's more likely that you may need to do one or either of these actions during an initial testing phase. Make sure you understand what happens when you do either of these actions.

### Removing a label from a label policy

Removing a label from a label policy is less risky than deleting it, because you can always add it back to a label policy later if needed:

 -  When you remove a label from a label policy so that the label is no longer published to the originally specified users, the next time the label policy is refreshed, users no longer see that label to select in their Office app. However, if the label has been applied to documents or emails, the label isn't removed from that content. Any encryption that was applied by the label remains and the underlying protection template remains published.
 -  For labels that are removed but have previously been applied to content, users who are using built-in labeling for Word, Excel, and PowerPoint will still see the applied label name on the status bar. Similarly, labels that are removed that were applied to SharePoint sites still display the label name in the **Sensitivity** column.

### Deleting a label

When you delete a label, you take into account the following considerations:

 -  **If the label applied encryption.** When a label applied encryption, the underlying protection template is archived so that previously protected content can still be opened. Because of this archived protection template, you won't be able to create a new label with the same name. Although it's possible to delete a protection template by using PowerShell, you shouldn't do it unless you're sure you don't need to open content that was encrypted with the archived template.
 -  **For desktop apps.** The label information in the metadata remains. However, because a label ID to name mapping is no longer possible, users won't see the applied label name displayed (for example, on the status bar). As a result, they'll assume the content isn't labeled. If the label applied encryption, the encryption remains and when the content is opened, users still see the name and description of the now archived protection template.
 -  **For Office on the web.** Users don't see the label name on the status bar or in the Sensitivity column. The label information in the metadata remains only if the label didn't apply encryption. If the label applied encryption, and you've enabled sensitivity labels for SharePoint and OneDrive, the label information in the metadata is removed and the encryption is removed.

> [!NOTE]
> When you delete a sensitivity label or remove a sensitivity label from a label policy, the changes can take up to 24 hours to replicate to all users and services.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”