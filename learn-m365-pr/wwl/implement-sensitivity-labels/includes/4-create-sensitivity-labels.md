All Microsoft Purview Information Protection solutions are implemented by using sensitivity labels. To create and publish these labels, go to the **Microsoft Purview compliance** portal.

To implement sensitivity labels, an organization must first create and configure the labels that it wants to make available for apps and other services. For example, the labels it wants users to see and apply from Office apps.

Once an organization has created its sensitivity labels, it must create one or more label policies. In doing so, it will assign the appropriate sensitivity labels to each policy, and it will configure policy settings.

> [!NOTE]
> It's the label policy that publishes the labels and settings for an organization's chosen users and locations.

The global admin for an organization has full permissions to create and manage all aspects of sensitivity labels. If you aren't signing in as a global admin, see [Permissions required to create and manage sensitivity labels](/microsoft-365/compliance/get-started-with-sensitivity-labels?azure-portal=true).

### Create and configure sensitivity labels

1.  From the **Microsoft Purview compliance** portal, under the **Solutions** section in the navigation pane, select **Information protection**.
2.  On the **Information protection** page, select the **Labels** tab.
3.  On the **Labels** tab, select **+ Create a label** to start the **New sensitivity label** wizard.
    
    :::image type="content" source="../media/information-protection-page-2c9cb3ff.png" alt-text="Screenshot of the Information protection page showing the Labels tab and the Create a label option highlighted.":::
    
    
    > [!NOTE]
    > By default, tenants don't have any labels. As such, organizations must create them. The labels in the screenshot show default labels that were [migrated from Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels?azure-portal=true).
4.  In the **New sensitivity label** wizard, on the **Name and create a tooltip for your label** page, enter the label **Name**, **Display name**, **Description for users**, and optionally, the **Description for admins**.
5.  On the **Define the scope for this label** page, the options selected determine the label's scope for the settings that you can configure and where they'll be visible when they're published:
    
    :::image type="content" source="../media/scope-page-new-sensitivity-wizard-f5c8aa90.png" alt-text="Screenshot of the Define the scope for this label page in the new sensitivity label wizard.":::
    
    
    
     -  If **Files &amp; emails** is selected, you can configure settings that apply to apps that support sensitivity labels, such as Office Word and Outlook. If this option isn't selected, you'll still see the first page of these settings. However, you won't be able to configure them, and the labels won't be available for users to select in these apps.
     -  If **Groups &amp; sites** is selected, you can configure settings that apply to Microsoft 365 groups, and sites for Teams and SharePoint. If this option isn't selected, you'll still see the first page of these settings. However, you won't be able to configure them, and the labels won't be available for users to select for groups and site.
     -  For information about the **Schematized data assets** scope, see [Automatically label your content in Microsoft Purview Data Map](/azure/purview/create-sensitivity-label).
6.  Follow the configuration prompts for the label settings. Several of the settings options will trigger various settings pages. As such, it's difficult to describe all the settings pages that you may encounter, since they're dependent on which options you select. For more information about the label settings, see [What sensitivity labels can do](/microsoft-365/compliance/sensitivity-labels?azure-portal=true) from the overview information and use the help in the UI for individual settings.
7.  Repeat these steps to create more labels. However, if you want to create a sublabel, first select the parent label, then select the vertical ellipsis icon (**Actions**), and then select **Add sub label** in the menu that appears.
8.  When you've created all the labels you need, review their order and if necessary, move them up or down. To change the order of a label, select the vertical ellipsis icon (**Actions**), and then select **Move up** or **Move down** in the menu that appears. For more information, see [Label priority (order matters)](/microsoft-365/compliance/sensitivity-labels?azure-portal=true) from the overview information.

### Edit a sensitivity label

To edit an existing label, select it in the list of labels in the **Labels** tab on the **Information protection** page. Doing so will open the detail pane for that label. The following screenshot shows the detail pane for the **Confidential - Finance** label. To edit the label, select the **Edit label** button.

:::image type="content" source="../media/edit-sensitivity-label-window-7f63c938.png" alt-text="Screenshot of the edit sensitivity label window showing the properties of the Confidential Financial label.":::


This button starts the **Edit sensitivity label** wizard, which lets you change all the label settings.

> [!CAUTION]
> Don't delete a label unless you understand the effect on users. For more information, see [Removing and deleting labels](/microsoft-365/compliance/create-sensitivity-labels?azure-portal=true).

If you edit a label that's already been published in a label policy, no extra steps are needed when you finish the configuration. For example, you don't need to add it to a new label policy for the changes to become available to the same users. However, you should allow up to 24 hours for the changes to replicate to all apps and services.

Until you publish your labels, they won't be available to select in apps or for services. Publishing labels is examined in the next unit.

> [!IMPORTANT]
> On the **Labels** tab of the **Information protection** page, don't select the **Publish label** option on the menu bar (or the **Publish label** button when you edit a label, as seen in the screenshot above for the Confidential - Finance label) unless you need to create a new label policy. An organization only requires multiple label policies if its users need different labels or different policy settings. As a best practice, organizations should have as few label policies as possible. In fact, it's not uncommon for an organization to have just one label policy for the entire company.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”