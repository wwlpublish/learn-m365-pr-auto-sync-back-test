Microsoft 365 provides tools that run on-premises and in Exchange Online to support electronic discovery (eDiscovery). You use these tools to store, search, and process content stored throughout Microsoft 365. This includes emails in users' mailboxes or groups, chats in Teams, documents in SharePoint, or chats in Yammer.

As public folders might also contain valuable information required for eDiscovery, they can also be included.

## Grant access to eDiscovery

Within your organization, you'll need to add appropriate users to an eDiscovery Manager role. The role grants them access to the Microsoft Purview compliance portal. The two roles you can use to grant this access are:

- **eDiscovery Manager**.Members of this role group can view and manage their own cases. Managers can add other managers, but by default will only see cases they own.
- **eDiscovery Administrator**. People in this role group have all the permissions of eDiscovery Managers, and they can view all cases in the organization. After assigning themselves, eDiscovery Administrators can also export case data and manage cases.

These roles are controlled in the **Permissions** section of the compliance portal. Select the **eDiscovery Manager** permission and edit either the Manager or Administrator role.

:::image type="content" source="../media/ediscovery-manager.png" alt-text="Screenshot of the permissions page in the Microsoft Purview compliance portal with the e Discovery Manager selected and the assigned roles shown in an open pane." lightbox="../media/ediscovery-manager.png" border="false":::

## Creating cases in Microsoft Purview compliance portal

Microsoft Purview compliance portal allows you to manage your organization's compliance tasks—eDiscovery is just one of those activities. You'll create cases to control holds on information and search for content required for evidence in current or future legal cases.

:::image type="content" source="../media/select-compliance-center.png" alt-text="Screenshot of the Microsoft 3 65 app launcher with Compliance highlighted." border="false":::

You access the compliance portal from the Microsoft 365 app launcher by selecting **Compliance**. After you've signed in with an account that has the correct permissions, you'll see the Compliance home page. You could also go directly to this page from the link in the **Learn more** section at the end of this unit.

### Create an eDiscovery case

1. Using the navigation pane on the left, expand **Solutions**, expand **eDiscovery**, select **Advance**, and then select the **Cases** tab.

   :::image type="content" source="../media/create-ediscovery-case.png" alt-text="Screenshot of the e Discovery page in the compliance portal with the Cases tab and the Create a case button highlighted." lightbox="../media/create-ediscovery-case.png" border="false":::

2. On the Cases pane, select **Create a case**.
3. Enter the details of the case, for example "investigating a customer complaint," then select **Save**.

   :::image type="complex" source="../media/new-ediscovery-case.png" alt-text="Modal window for creating a new e Discovery case." lightbox="../media/new-ediscovery-case.png" border="false":::
	Case name is a required field, a case number is generated, and a case description is an optional field. There is a toggle that asks do you want to configure additional settings after creating this case? The case fields and the save button are highlighted.
:::image-end:::

4. After the case is created, you can add information to it.

   :::image type="content" source="../media/customer-complaint.png" alt-text="Screenshot showing a new e Discovery case. The settings tab shows case information, access/permissions, and search/analytics can be accessed. The holds tab is highlighted." lightbox="../media/customer-complaint.png" border="false":::

## Create an in-place hold to include public folders

You can instantly add hold details in the case summary screen, or access the case from the eDiscovery cases pane.

1. Select the **Holds** tab.

   :::image type="content" source="../media/select-holds-tab.png" alt-text="Screenshot of a the create a new hold dialog box. The name your hold tab is shown with a name and description field." lightbox="../media/select-holds-tab.png" border="false":::

2. Select **+ Create**, enter a Name and Description in the **Create a new hold** panel, then select **Next**.

   :::image type="content" source="../media/create-new-hold.png" alt-text="Screenshot of a the create a new hold dialog box. The choose locations tab is shown which lists the apps where the hold can be used and the users, groups, or teams it can be applied to." lightbox="../media/create-new-hold.png" border="false":::

3. On the **Choose locations** page, add the users, groups, or teams you want to include.
4. Choose specific SharePoint sites, Team sites, or Yammer networks.
5. To include all the Exchange public folders, select the toggle switch, then select **Next**.

You can't choose individual public folders, as Microsoft Purview compliance portal only allows for all the created public folders to be included in a case.

## Learn more

- [Microsoft Purview compliance portal](https://compliance.microsoft.com/?azure-portal=true)
- [Get started with eDiscovery (Premium)](/microsoft-365/compliance/get-started-with-advanced-ediscovery?azure-portal=true)
