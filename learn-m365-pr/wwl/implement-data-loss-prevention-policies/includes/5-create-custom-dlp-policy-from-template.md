The easiest, most common way to get started with DLP policies is to use one of the templates included in the Microsoft Purview compliance portal. An organization can use one of these templates as is, or customize the rules to meet its specific compliance requirements.

Microsoft 365 includes over 40 ready-to-use templates that can help an organization meet a wide range of common regulatory and business policy needs. See [Policy templates](/microsoft-365/compliance/dlp-policy-reference?azure-portal=true) for a complete list.

Organizations can fine tune a template by modifying any of its existing rules or adding new ones. For example, you can:

 -  Add new types of sensitive information to a rule.
 -  Modify the counts in a rule to make it harder or easier to trigger.
 -  Allow people to override the actions in a rule by providing a business justification.
 -  Change who notifications and incident reports are sent to.

A DLP policy template is a flexible starting point for many common compliance scenarios. An organization can also choose the **Custom** template, which has no default rules. By doing so, the organization can configure the DLP policy from scratch to meet its compliance requirements.

### Permissions

Members of an organization's compliance team who will create DLP policies need permissions to the Microsoft Purview compliance portal. By default, the tenant admin will have access can give compliance officers and other people access by following these steps:

1.  Create a Microsoft 365 group and add the company's compliance officers to it.
2.  Create a role group on the **Permissions** page of the **Microsoft Purview compliance** portal.
3.  While creating the role group, use the **Choose Roles** section to add the **DLP Compliance Management** role to the role group.
4.  Use the **Choose Members** section to add the Microsoft 365 group you created in step 1 to the role group.

> [!NOTE]
> Use the **View-Only DLP Compliance Management** role to create the role group with view-only privileges to the DLP policies and DLP reports.

**Additional reading**. For more information, see [Permissions in the Microsoft Purview compliance portal](/microsoft-365/compliance/microsoft-365-compliance-center-permissions?azure-portal=true).

These permissions are required to create and apply a DLP policy. They aren't required to enforce policies.

### Roles and role groups for fine-tuning access controls

Microsoft 365 includes roles and role groups that organizations can test out to fine tune their access controls.

The roles that are available include:

 -  Information Protection Admin
 -  Information Protection Analyst
 -  Information Protection Investigator
 -  Information Protection Reader

The role groups that are available include:

 -  Information Protection
 -  Information Protection Admins
 -  Information Protection Analysts
 -  Information Protection Investigators
 -  Information Protection Readers

### Create the DLP policy from a template

Organizations can complete the following steps to create a DLP policy from a template:

1.  Sign in to the **Microsoft Purview compliance** portal.
2.  In the **Microsoft Purview compliance** portal, select **Data loss prevention** in the navigation pane.
3.  On the **Data loss prevention** page, select the **Policies** tab.
4.  On the **Policies** tab, select **+Create policy** in the menu bar. The **Create policy** wizard begins.
5.  In the **Create policy** wizard, on the **Start with a template or create a custom policy** page, select the category and then select the template that protects the type of sensitive information that you need. Then select **Next**.
6.  On the **Name your DLP policy** page, the name of the selected template appears in the **Name** field. You can't use this name, since a template already exists with it. Instead, you can optionally use the template name the basis for your own, custom policy name. Or, you can enter an entirely different name. In either case, enter a name and an optional description, and then select **Next**.
7.  On the **Choose locations to apply the policy** page, determine the locations that you want the DLP policy to protect. Then either accept the default scope for each selected location or customize the scope. See the following examples:
     -  **Example 1.** To include or exclude an entire location such as all **Exchange email** or all **OneDrive accounts**, switch the **Status** of that location to **On** or **Off**.
     -  **Example 2.** To include only specific **SharePoint sites** or **OneDrive accounts**, switch the **Status** to **On**, and then select the links under **Include** to choose specific sites or accounts. When you apply a policy to a site, the rules configured in that policy are automatically applied to all subsites of that site.
    
    In this example, to protect sensitive information stored in all OneDrive accounts, turn off the**Status** for both **Exchange email** and **SharePoint sites**, and leave the **Status** on for **OneDrive accounts**. Then select **Next**.
    
    :::image type="content" source="../media/choose-locations-dlp-policy-wizard-998934b8.png" alt-text="Screenshot showing the choose locations to apply the policy page in the create policy wizard.":::
    
8.  On the **Define policy settings** page, select either **Review and customize default settings from the template**, or **Create or customize advanced DLP rules**.
    
    :::image type="content" source="../media/define-policy-settings-dlp-policy-wizard-c2282620.png" alt-text="Screenshot showing the define policy settings page in the create policy wizard.":::
    
    
    A DLP policy template contains predefined rules with conditions and actions that detect and act upon specific types of sensitive information. You can edit, delete, or turn off any of the existing rules, or add new ones. To do so, select the **Create or customize advanced DLP rules**.
    
    :::image type="content" source="../media/customize-advanced-dlp-rules-dlp-policy-wizard-3d11004c.png" alt-text="Screenshot showing the advanced D L P rules page in the create policy wizard.":::
    
9.  Select **Next.**
10. On the **Test or turn on the policy** page, select whether to turn on the policy right away, or test it out first. Then select **Next**.
    
    :::image type="content" source="../media/test-turn-on-policy-dlp-policy-wizard-5b32a8f4.png" alt-text="Screenshot showing the test or turn on the policy page in the create policy wizard.":::
    
11. On the **Review your policy and create it** page, review the policy settings that you defined. If any options need to be changed, select the **Edit** option under the appropriate section and make the necessary changes. Once all settings are correct, select **Submit**.
