In a production environment, it's unlikely that an organization will need to remove sensitivity labels from a label policy, or delete sensitivity labels. It's more likely that it may need to do one or either of these actions during an initial testing phase. As an enterprise administrator, you must understand what happens when you do either of these actions.

### Removing a sensitivity label from a label policy

Removing a label from a label policy is less risky than deleting it. Why? Because it can always be added back later if needed. You won't be able to delete a label if it's still in a label policy.

An organization will remove a label from a label policy so that the label is no longer published to the originally specified users. As a result, the next time the label policy is refreshed, users no longer see that label to select in their Office apps.

However, if that label is already applied, it isn't removed from the content or container. For example, users who are using built-in labeling in desktop apps for Word, Excel, and PowerPoint, still see the applied label name on the status bar. An applied container label continues to protect the Teams or SharePoint site.

### Deleting a sensitivity label

In comparison, deleting a sensitivity label can have multiple implications:

 -  **The label applied encryption**. In this case, the underlying protection template is archived so that previously protected content can still be opened. Because of this archived protection template, you won't be able to create a new label with the same name. Although it's possible to delete a protection template by using PowerShell, refrain from doing so unless you're sure you don't need to open content that was encrypted with the archived template.
 -  **Documents are stored in SharePoint or OneDrive and sensitivity labels are enabled for Office files**. When you open the document in Office for the web:
     -  You won't see the label applied in the app.
     -  The label name no longer displays in the **Sensitivity** column in SharePoint. 

    If the deleted label applied encryption and the services can process the encrypted contents, the encryption is removed. Egress actions from these services result in the same outcome. For example, download, copy to, move to, and open with an Office desktop or mobile app. Although the label information remains in the file's metadata, apps can no longer map the label ID to a display name. As such, users will assume a file isn't labeled.

 -  **Documents are stored outside SharePoint and OneDrive or sensitivity labels haven't been enabled for Office files, and for emails**. When you open the content, the label information in the metadata remains, but without the label ID to name mapping, users don't see the applied label name displayed (for example, on the status bar for desktop apps). If the deleted label applied encryption, the encryption remains and users still see the name and description of the now archived protection template.
 -  **The label applies to containers, such as sites in SharePoint and Teams**. The label is removed and any settings that were configured with that label are no longer enforced. This action typically takes between 48 to 72 hours for SharePoint sites. It can be quicker for Microsoft Teams and Microsoft 365 Groups.

As with all label changes, removing a sensitivity label from a label policy or deleting a sensitivity label takes time to replicate to all users and services.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”