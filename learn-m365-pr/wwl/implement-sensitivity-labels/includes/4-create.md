All Microsoft Information Protection solutions are implemented by using sensitivity labels. To create and publish these labels, go to the Microsoft 365 compliance center. You can also use the older portal, Microsoft 365 Security &amp; Compliance Center (SCC).

As previously discussed, creating sensitivity labels is a three-step process:

1.  Create the sensitivity labels that you want to make available for apps and other services. For example, the labels you want users to see and apply from Office apps.
2.  Configure the protection settings you want associated with each label. For example, you may want your higher sensitivity content to have a watermark and encryption
3.  Publish the sensitivity labels by using a label policy. It's the label policy that publishes the labels and settings for your chosen users and locations.

Steps 1 and 2 are examined in greater detail in the following section. Step 3 is covered in the next unit.

### Create and configure sensitivity labels

Complete the following steps to create and configure sensitivity labels:

1.  Whether you're using the Microsoft 365 compliance center or the SCC, navigate to sensitivity labels:
    
     -  In the Microsoft 365 compliance center, navigate to **Solutions &gt; Information protection.** If you don't immediately see this option, first select **Show all**.
     -  In the Security &amp; Compliance Center, navigate to **Classification &gt; Sensitivity labels.**
2.  On the **Labels** page, select **+ Create a label** to start the **New sensitivity label** wizard.
    
    The following image shows this step in the Microsoft 365 compliance center.<br><br>:::image type="content" source="../media/create-sensitivity-label-full-354f79f0.png" alt-text="screenshot showing the sensitivity label window in the Microsoft 365 compliance center":::
    

    > [!NOTE]
    > By default, Microsoft 365 tenants don't have any labels. As a result, you must create them. The labels in the prior image show default labels that were migrated from Azure Information Protection.

3.  On the **Define the scope for this label** page, the options selected determine the label's scope for the settings that you can configure and where they'll be visible when they're published.
    
    :::image type="content" source="../media/sensitivity-label-scope-options-5b86e312.png" alt-text="screenshot of the Define the scope for this label page":::
    
    
     -  If you select the **Files &amp; emails** option, you can configure settings in this wizard that apply to apps that support sensitivity labels, such as Office Word and Outlook. If you don't select this option, the wizard displays the first page of these settings. However, you can't configure them and the labels won't be available for users to select in these apps.
     -  If you select the **Groups &amp; sites** option,you can configure settings in this wizard that apply to Microsoft 365 groups, and sites for Teams and SharePoint. If you don't select this option, the wizard displays the first page of these settings. However, you can't configure them and the labels won't be available for users to select for groups and site.
4.  Follow the prompts in the wizard for the label settings. For more information about the label settings, see [What sensitivity labels can do](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?azure-portal=true) and use the help in the wizard for individual settings.
5.  Repeat these steps to create more labels. However, if you want to create a sublabel, first select the parent label and select .**.. for More actions**, and then select **Add sub label.**
6.  Once you've created all the labels you need, review their order and if necessary, move them up or down. To change the order of a label, select **... for More actions**, and then select **Move up** or **Move down**. For more information, see [Label priority (order matters)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?azure-portal=true) from the overview information.

To edit an existing label, select it, and then select the **Edit label** button, as seen in the following image.

:::image type="content" source="../media/edit-sensitivity-label-full-small-28cab907.png" alt-text="screen shot of the Label page showing the detail pane for a label with the Edit label button circled":::


This button starts the **Edit sensitivity label** wizard, which lets you change all the label settings in step 4.

Don't delete a label unless you understand the impact for users. For more information, see the [Removing and deleting labels](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels?azure-portal=true) section.

> [!NOTE]
> If you edit a label that's already published by using a label policy, no extra steps are needed when you finish the wizard. For example, you don't need to add it to a new label policy for the changes to become available to the same users. However, allow up to 24 hours for the changes to replicate to all apps and services.<br>

Until you publish your labels, they won't be available to select in apps or for services. The next unit in this module examines how to create a label policy and publish it so that the sensitivity labels assigned to the policy become available for use.

> [!IMPORTANT]
> On this **Labels** tab, do not select the **Publish labels** tab (or the **Publish label** button when you edit a label) unless you need to create a new label policy. Multiple label policies are needed only if users need different labels or different policy settings. Aim to have as few label policies as possible—it's not uncommon to have just one label policy for the entire organization.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”