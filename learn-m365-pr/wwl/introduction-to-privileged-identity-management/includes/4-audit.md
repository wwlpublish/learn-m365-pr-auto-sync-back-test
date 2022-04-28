With Azure AD Privileged Identity Management, organizations can view activities, activations, and audit history for their Azure resources. These resources include subscriptions, resource groups, and even virtual machines. Any resource within the Azure portal that uses Azure role-based access control functionality can take advantage of the security and lifecycle management capabilities in PIM.

> [!NOTE]
> If an organization has outsourced management functions to a service provider who uses [Azure delegated resource management](/azure/lighthouse/concepts/azure-delegated-resource-management?azure-portal=true), role assignments authorized by that service provider won't be shown here.

**Additional reading.** For more information, see the following article on [Azure Active Directory Reports](/azure/active-directory/reports-monitoring/overview-reports?azure-portal=true).

### View activity and activations

To see what actions a specific user took in various resources, you can view the Azure resource activity that's associated with a given activation period.

1.  Open **Azure AD Privileged Identity Management**.<br>
2.  Select **Azure resources**.<br>
3.  Select the resource you want to view activity and activations for.<br>
4.  Select **Roles** or **Members**.
5.  Select a user to display a summary of the user's actions in Azure resources by date. It also shows the recent role activations over that same time period.<br><br>:::image type="content" source="../media/rbac-user-details-262535c1.png" alt-text="screenshot showing user details with resource activity summary and role activations":::
    
6.  Select a specific role activation to see details and corresponding Azure resource activity that occurred while that user was active.
    
    :::image type="content" source="../media/export-membership-1d4deb71.png" alt-text="screenshot showing Role activation selected and activity details":::
    

### Navigate to audit history

From the Azure portal dashboard, select the **Azure AD Privileged Identity Management app**. From there, access the audit history by selecting **Manage privileged roles &gt; Audit history** in the PIM dashboard.

Resource audit gives you a view of all role activity for a resource.

1.  Open **Azure AD Privileged Identity Management**.<br>
2.  Select **Azure resources**.<br>
3.  Select the resource you want to view audit history for.<br>
4.  Select **Resource audit**.<br>
5.  Filter the history using a predefined date or custom range.<br><br>:::image type="content" source="../media/rbac-resource-audit-1422928c.png" alt-text="screenshot showing Resource audit list with filters":::
    <br>
6.  For Audit type, select **Activate (Assigned + Activated)**.<br><br>:::image type="content" source="../media/rbac-audit-activity-557d60a0.png" alt-text="screenshot showing Resource audit list filtered by Activate audit type":::
    <br>
7.  Under **Action**, select **(activity)** for a user to see that user's activity detail in Azure resources.<br><br>:::image type="content" source="../media/rbac-audit-activity-details-efa2fa1f.png" alt-text="screenshot showing User activity details for a particular action":::
    <br>

You can use the audit history to view the total activations, max activations per day, and average activations per day in a line graph. You can also filter the data by role if there's more than one role in the audit history.

### Export role assignments with child resources

An organization may have a compliance requirement where it must provide a complete list of role assignments to auditors. PIM enables the organization to query role assignments at a specific resource, which includes role assignments for all child resources. Previously, it was difficult for administrators to get a complete list of role assignments for a subscription. As such, they had to export role assignments for each specific resource. Organizations can now use Privileged Identity Management to query for all active and eligible role assignments in a subscription, including role assignments for all resource groups and resources.

1.  Open **Azure AD Privileged Identity Management**.<br>
2.  Select **Azure resources**.<br>
3.  Select the resource you want to export role assignments for, such as a subscription.<br>
4.  Select **Members**.
5.  Select **Export** to open the **Export membership** pane.
6.  Select **Export all members** to export all role assignments in a CSV file.<br><br>:::image type="content" source="../media/export-csv-b8c5cb76.png" alt-text="screenshot of a csv file showing all role assignments that were exported":::
    
