Sensitivity labels from the Microsoft Information Protection framework let you **classify** and **protect** your organization's data, while making sure that user productivity and their ability to collaborate isn't hindered. Sensitivity labels allow Teams admins to regulate access to sensitive organizational content created during collaboration within teams. 

Organizations can use sensitivity labels to:

* Provide protection settings that include encryption and content markings.

* Protect content in Office apps across different platforms and devices.

* Protect content in third-party apps and services by using Microsoft Cloud App Security.

* Protect containers that include Teams, Microsoft 365 Groups, and SharePoint sites.

* Extend sensitivity labels to Power BI.

* Extend sensitivity labels to assets in Azure Purview.

* Extend sensitivity labels to third-party apps and services.

* Classify content without using any protection settings.

## Label scopes

When you create a sensitivity label, you're asked to configure the label's scope which determines two things:

* Which label settings you can configure for that label

* Where the label will be visible to users

You can apply the sensitivity labels to the following scopes:

* Files & emails: email and Office files

* Groups & sites: Microsoft Teams sites, Microsoft 365 groups, and SharePoint sites

* Azure Purview assets (preview)

    :::image type="content" source="../media/sensitivity-labels-scopes.png" alt-text="Scope options for sensitivity labels":::

## Sensitivity label settings for groups & sites (containers)

Sensitivity labels can be applied to item level (files and emails) or container level, such as Microsoft Teams sites, Microsoft 365 groups, and SharePoint sites. For container-level classification and protection, you can use the following label settings:

* Privacy (public or private) of teams sites and Microsoft 365 groups

* External user access

* External sharing from SharePoint sites

* Access from unmanaged devices

* Authentication contexts (in preview)

### Privacy and external user access settings

Configure the **Privacy** and **External users access** settings.
    
* **Privacy**: Keep the default of **Public** if you want anyone in your organization to access the team site or group where this label is applied.
    
    Select **Private** if you want access to be restricted to only approved members in your organization.
    
    Select **None** when you want to protect content in the container by using the sensitivity label, but still let users configure the privacy setting themselves.
    
    The settings of **Public** or **Private** set and lock the privacy setting when you apply this label to the container. Your chosen setting replaces any previous privacy setting that might be configured for the team or group, and locks the privacy value so it can be changed only by first removing the sensitivity label from the container. After you remove the sensitivity label, the privacy setting from the label remains and users can now change it again.

* **External user access**: Control whether the group owner can add guests to the group.

    :::image type="content" source="../media/edit-sensitivity-label-site-group-privacy.png" alt-text="Privacy and external user access settings" lightbox="../media/edit-sensitivity-label-site-group-privacy.png":::

### Device external sharing and device access settings

To configure the **Control external sharing from labeled SharePoint sites** and **Use Azure AD Conditional Access to protect labeled SharePoint sites** setting.

* **Control external sharing from labeled SharePoint sites**: Select this option to then select either external sharing for anyone, new and existing guests, existing guests, or only people in your organization.

* **Use Azure AD Conditional Access to protect labeled SharePoint sites**: Select this option only if your organization has configured and is using **Azure Active Directory Conditional Access**. Then, select one of the following settings:

    * **Determine whether users can access SharePoint sites from unmanaged devices**: This option uses the SharePoint feature that uses Azure AD Conditional Access to block or limit access to SharePoint and OneDrive content from unmanaged devices.
        
    * **Choose an existing authentication context**: Currently in preview, this option lets you enforce more stringent access conditions when users access SharePoint sites that have this label applied. These conditions are enforced when you select an existing authentication context that has been created and published for your organization's Conditional Access deployment. If users don't meet the configured conditions or if they use apps that don't support authentication contexts, they are denied access.

        :::image type="content" source="../media/edit-sensitivity-label-site-group-sharing.png" alt-text="Device external sharing and device access settings" lightbox="../media/edit-sensitivity-label-site-group-sharing.png":::

When you apply this sensitivity label to a supported container, the label automatically applies the classification and protection settings to the connected site or group. Content in these containers however, do not inherit the labels for the classification and settings such as visual markings, or encryption.

* Make sure you've enabled sensitivity labels for Office files in SharePoint and OneDrive, so that users can label their documents in SharePoint sites or team sites.  

    :::image type="content" source="../media/sensitivity-labels-sharepoint-onedrive.png" alt-text="Enabled sensitivity labels for Office files in SharePoint and OneDrive":::

* You can automatically assign that label to files and emails when it matches conditions that you specify. For more information, see [Apply a sensitivity label to content automatically](/microsoft-365/compliance/apply-sensitivity-label-automatically?azure-portal=true).

    :::image type="content" source="../media/sensitivity-labels-auto.png" alt-text="Automatically assign that label to files and emails when it matches conditions":::

## Enable sensitivity labels for groups & sites

Configuration options for Site and group settings don't display until you enable this capability. Follow the steps to enable the feature in Azure AD.

1. Open a **Windows PowerShell** window on your computer.

2. Connect to Azure AD with admin credentials.

    ```PowerShell
    Import-Module AzureADPreview
    Connect-AzureAD
    ```

3. Fetch the current group settings for the Azure AD organization.

    ```PowerShell
    $Setting = Get-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ).id
    ```

    > [!NOTE]
    > If no group settings have been created for this Azure AD organization, you must first create the settings. Follow the steps in [Azure Active Directory cmdlets for configuring group settings](/azure/active-directory/enterprise-users/groups-settings-cmdlets?azure-portal=true) to create group settings for this Azure AD organization.

4. Enable the feature:

    ```PowerShell
    $Setting["EnableMIPLabels"] = "True"
    ```

5. Then save the changes and apply the settings:

    ```PowerShell
    Set-AzureADDirectorySetting -Id $Setting.Id -DirectorySetting $Setting
    ```

    > [!NOTE]
    > If you were using sensitivity labels before September 2019, you will also need to synchronize your sensitivity labels to Azure AD. For instructions, see [How to enable sensitivity labels for containers and synchronize labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites?azure-portal=true#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

## Create and publish sensitivity labels

The global admin can create and manage sensitivity labels from Microsoft 365 compliance center. See the instructions from [Create and publish sensitivity labels](/microsoft-365/compliance/create-sensitivity-labels?azure-portal=true).  

1. Go to **Microsoft 365 compliance center** > **Information protection**.

2. On the **Information protection** page, select **+ Create a label** to start the New sensitivity label wizard.

3. On the **Name and create a tooltip for your label** page, provide information.

4. On the **Define the scope for this label** page, select **Groups & sites** or other scopes.

    The options selected determine the label's scope for the settings that you can configure and where they will be visible when they are published

5. Follow the prompts in the wizard for the label settings to complete the creation.

    :::image type="content" source="../media/edit-sensitivity-label-site-group-define.png" alt-text="The site and group settings tab":::

Once you created a sensitivity label, you need to [publish the sensitivity label by creating a label policy](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels?azure-portal=true#publish-sensitivity-labels-by-creating-a-label-policy). The users who are assigned a sensitivity label policy that includes this label will be able to select it for sites and groups.

Only these site and group settings take effect when you apply the label to a team, group, or site. Other label settings, such as encryption and content marking, aren't applied to the content within the team, group, or site.

## Use sensitivity labels with Teams

Admins can create a sensitivity label that, when applied during team creation, allows users to create teams with a specific privacy (public or private) setting.

For example, the admin creates a sensitivity label named "Confidential" with the policy that any team that's created with this label must be a private team. When a user creates a new team and selects the **Confidential** label, the only privacy option that's available to the user is **Private**. Other privacy options such as Public and Org-wide are disabled for the user.

:::image type="content" source="../media/sensitivity-labels-confidential-example.png" alt-text="Screenshot of Confidential sensitivity label":::

When the team is created, the sensitivity label is visible in the upper-right corner of channels in the team.

:::image type="content" source="../media/sensitivity-labels-channel.png" alt-text="Screenshot of sensitivity label in team channel window":::

A team owner can change the sensitivity label and the privacy setting of the team at any time by going to the team, and then clicking **Edit team**.

:::image type="content" source="../media/sensitivity-labels-edit-team.png" alt-text="Screenshot of Edit My Team channel page":::

> [!NOTE]
> Microsoft 365 no longer supports the old classifications for new Microsoft 365 groups and SharePoint sites after you enable sensitivity labels for containers. However, existing groups and sites that support sensitivity labels still display the old classification values until you convert them to use sensitivity labels. For more information, see [Azure Active Directory classification and sensitivity labels for Microsoft 365 groups](/microsoft-365/compliance/migrate-aad-classification-sensitivity-labels?azure-portal=true).

For more information, see:

* [Learn about sensitivity labels](/microsoft-365/compliance/sensitivity-labels?azure-portal=true)

* [Sensitivity labels for Microsoft Teams](/MicrosoftTeams/sensitivity-labels?azure-portal=true)

* [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites?azure-portal=true)

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”