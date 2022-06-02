The following table can help organizations identify whether to use a retention policy or retention label, based on capabilities.

| **Capability**                                                                                                                                       | **Retention policy**                              | **Retention label**                                                   |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | --------------------------------------------------------------------- |
| Retention settings that can retain and then delete, retain-only, or delete-only.                                                                     | Yes                                               | Yes                                                                   |
| Workloads supported:<br>\- Exchange<br>\- SharePoint<br>\- OneDrive<br>\- Microsoft 365 groups<br>\- Skype for Business<br>\- Teams<br>\- Yammer     | <br>Yes<br>Yes<br>Yes<br>Yes<br>Yes<br>Yes<br>Yes | <br>Yes, except public folders<br>Yes<br>Yes<br>Yes<br>No<br>No<br>No |
| Retention applied automatically.                                                                                                                     | Yes                                               | Yes                                                                   |
| Automatically apply different retention settings at the end of the retention period.                                                                 | No                                                | Yes                                                                   |
| Retention applied based on conditions:<br>\- sensitive info types<br>\- KQL queries and keywords<br>\- trainable classifiers<br>\- cloud attachments | No                                                | Yes                                                                   |
| Retention applied manually.                                                                                                                          | No                                                | Yes                                                                   |
| End-user interaction.                                                                                                                                | No                                                | Yes                                                                   |
| Persists if the content is moved.                                                                                                                    | No                                                | Yes, within your Microsoft 365 tenant.                                |
| Declare item as a record.                                                                                                                            | No                                                | Yes                                                                   |
| Start the retention period when labeled or based on an event.                                                                                        | No                                                | Yes                                                                   |
| Disposition review.                                                                                                                                  | No                                                | Yes                                                                   |
| Proof of disposition for up seven years.                                                                                                             | No                                                | Yes, when you use disposition review or item is marked a record.      |
| Audit admin activities.                                                                                                                              | Yes                                               | Yes                                                                   |
| Audit retention actions.                                                                                                                             | No                                                | Yes (1)                                                               |
| Identify items subject to retention:<br>\- Content Search<br>\- Data classification page, content explorer, activity explorer                        | <br>No<br>No                                      | <br>Yes<br>Yes                                                        |

**Footnote:**

(1) Some retention labels don't mark the content as a record or regulatory record. With these labels, auditing events are limited to when an item in SharePoint or OneDrive has a label applied, changed, or removed. For auditing details for retention labels, see the upcoming unit that examines auditing retention configuration and actions.

### Combining retention policies and retention labels

Organizations don't have to choose between only using retention policies or only using retention labels. Both methods can be used together. In fact, when they're used together, they complement each other for a more comprehensive solution.

The following examples are just some of the ways in which you can combine retention policies and retention labels for the same location.

For more information about how retention policies and retention labels work together and how to determine their combined outcome, see the upcoming unit that explains the principles of retention and what takes precedence.

#### Example for users to override automatic deletion

**Scenario:** By default, Contoso wants the content in every user's OneDrive account to be automatically deleted after five years. However, users must be able to override this event for specific documents. Possible solutions include:

 -  Contoso creates and configures a retention policy that automatically deletes content five years after it's last modified. It then applies the policy to all of its OneDrive accounts.
 -  Contoso creates and configures a retention label that keeps content forever. it then adds this retention label to a label policy that it publishes to all of its OneDrive accounts. Contoso explains to users how to manually apply this label to specific documents that should be excluded from automatic deletion if they weren't modified after five years.

#### **Example to retain items for a period longer than the default**

**Scenario:** By default, Contoso wants SharePoint items to be automatically retained and then deleted after five years. However, it wants documents in specific libraries to be retained for 10 years. Possible solutions include:

 -  Contoso creates and configures a retention policy that automatically retains and then deletes content after five years. It then applies the policy to all SharePoint and Microsoft 365 Groups instances.
 -  Contoso creates and configures a retention label that automatically retains content for 10 years. It then publishes this label to SharePoint site admins. By doing so, they can apply it as a default label to be inherited by all items in specific document libraries.

#### Example to delete items in a shorter time period

**Scenario:** By default, Contoso automatically deletes emails after 10 years. However, emails related to a specific project that has a prerelease code name must be automatically deleted after one year. Possible solutions include:

 -  Contoso creates and configures a retention policy that automatically deletes content after 10 years. It then applies the policy to all Exchange recipients.
 -  Contoso creates and configures a retention label that automatically deletes content after one year. Options for applying this label to relevant emails include:
     -  Contoso creates an auto-labeling policy that identifies content. It does so by using the project code name as the keyword. It then applies the policy to all Exchange recipients.
     -  Contoso publishes the label and instructs users involved in the project on how to create an automatic rule in Outlook that applies this label.
     -  Contoso publishes the label and instructs users to create a folder in Outlook for all emails related to the project. The users apply the published label to the folder, and then create an Outlook rule to move all project-related emails to this folder.

### How long it takes for retention policies to take effect

When you create and submit a retention policy, it can take up to seven days for the retention policy to be applied. First, the retention policy needs to be distributed to the locations that you selected, and then applied to content.

You can always check the distribution status of the retention policy by selecting it from the **Retention policies** page in the **Microsoft Purview compliance** portal. From the flyout pane, if you see **(Error)** included in the status, and if you see a message in the details for the locations that indicates it's taking longer than expected to deploy the policy or to try redeploying the policy, try running the **Set-AppRetentionCompliancePolic**y or **Set-RetentionCompliancePolicy** PowerShell command to retry the policy distribution:

1.  [Connect to Security &amp; Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell?azure-portal=true).
2.  Run one of the following commands:
     -  For the policy locations: **Teams private channel messages**, **Yammer user messages**,and **Yammer community messages**:
        
        ```powershell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
     -  For all other policy locations, such as: **Exchange email**, **SharePoint sites**, and **Teams channel messages**:
        
        ```powershell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

### How long it takes for retention labels to take effect

When you auto-apply retention labels based on sensitive information, keywords or searchable properties, or trainable classifiers, it can take up to seven days for the retention labels to be applied.

If the expected labels don't appear after seven days, check the **Status** of the auto-apply policy by selecting it from the **Label policies** page in the **Microsoft Purview compliance** portal. If you see the status of see **Off (Error)** included in the status, and if you see a message in the details for the locations that indicates it's taking longer than expected to deploy the policy (for SharePoint) or to try redeploying the policy (for OneDrive), try running the **Set-RetentionCompliancePolicy** PowerShell command to retry the policy distribution:

1.  [Connect to Security &amp; Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell?azure-portal=true).
2.  Run the following command:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

> [!TIP]
> Often, the policies will take effect and labels will be visible quicker than seven days. But with many potential variables that can affect this process, it's best to plan for the maximum of seven days.
