When new documents are added to SharePoint, OneDrive, or Teams, it can take some time for the document to be crawled and indexed. It takes additional time for a DLP policy to scan the content and apply rules to protect any sensitive content. This means that if external sharing is turned on, external users can access your sensitive content.

What can you do to protect content containing sensitive information during the time before a DLP policy has a chance to scan it and apply protections? You run a PowerShell cmdlet that will in essence mark content as sensitive by default. This cmdlet prevents external users from accessing newly added files until at least one Office DLP policy has had a chance to scan the file. An attempt by an external user to access a file that has been configured to be sensitive by default will receive a "Due to organizational policies, you can't access this resource" message.

> [!NOTE]
> This cmdlet applies to newly added files in all SharePoint sites and OneDrive accounts. It doesn't block sharing if an existing file is changed.

Follow the steps below to set files sensitive by default:

1. Ensure that you have at least one DLP policy turned on for content located in SharePoint, OneDrive, and Teams.
1. Download the latest version of SharePoint Online Management Shell.
1. Connect to SharePoint as a global admin or SharePoint admin.
1. Run the following command:

    ```powershell
    {
    Set-SPOTenant -MarkNewFilesSensitiveByDefault BlockExternalSharing
    }
    ```

1. To disable this feature, run the following command:

    ```powershell
    {
    Set-SPOTenant -MarkNewFilesSensitiveByDefault AllowExternalSharing
    }
    ```

### Recommended DLP policy structure

A DLP policy designed to prevent the release of sensitive information to external users should contain the following conditions and actions:

- Conditions
  - Content that contains sensitive information types (for example, credit card numbers). Select all sensitive information types that apply to your particular policy
  - AND
  - Detects when content is sent in  Teams chat or channel message, email message, or shared in a SharePoint or OneDrive document that is shared with people outside of my organization.

:::image type="content" source="../media/7-dlp-sensitive-conditions-inline.png" lightbox="../media/7-dlp-sensitive-conditions-expanded.png" alt-text="DLP policy conditions.":::

- Actions
  - Restrict access to the content for external users

:::image type="content" source="../media/7-dlp-sensitive-actions-inline.png" lightbox="../media/7-dlp-sensitive-actions-expanded.png" alt-text="DLP policy actions.":::

- Notifications
  - Notify users with email and policy tips
  - Send incident reports to the Administrator
