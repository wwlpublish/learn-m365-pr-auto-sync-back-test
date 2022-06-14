Insider risk management templates are pre-defined policy conditions that define the types of risk indicators and risk scoring model used by the policy. Each policy must have a template assigned in the policy creation wizard before the policy is created. Insider risk management supports up to five policies for each policy template.

### Policy template prerequisites and triggering events

Depending on the template an organization chooses for an insider risk management policy, the triggering events and policy prerequisites vary.

 -  Triggering events are prerequisites that determine if a user is active for an insider risk management policy. If a user is added to an insider risk management policy but doesn't have a triggering event, the user activity isn't evaluated by the policy unless they're manually added in the **Users** dashboard.
 -  Policy prerequisites are required items so that the policy receives the signals or activities necessary to evaluate risk.

The following table lists the triggering events and prerequisites for policies created from each insider risk management policy template.

| **Policy template**                            | **Triggering events for policies**                                                                                          | **Prerequisites**                                                                                                                                                                                                                                                             |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Data theft by departing users                  | Resignation or termination date indicator from HR connector or Azure Active Directory account deletion.                     | (optional) Microsoft 365 HR connector configured for termination and resignation date indicators.                                                                                                                                                                             |
| General data leaks                             | Data leak policy activity that creates a **High severity** alert or built-in exfiltration event triggers.                   | DLP policy configured for **High severity** alerts.<br><br>or<br><br>Customized triggering indicators.                                                                                                                                                                        |
| Data leaks by priority users                   | Data leak policy activity that creates a **High severity** alert or built-in exfiltration event triggers.                   | DLP policy configured for **High severity** alerts.<br><br>or<br><br>Customized triggering indicators.<br><br>Priority user groups configured in insider risk settings.                                                                                                       |
| Data leaks by disgruntled users                | Performance improvement, poor performance, or job level change indicators from HR connector.                                | Microsoft 365 HR connector configured for disgruntlement indicators.                                                                                                                                                                                                          |
| General security policy violations             | Defense evasion of security controls or unwanted software detected by Microsoft Defender for Endpoint.                      | Active Microsoft Defender for Endpoint subscription.<br><br>Microsoft Defender for Endpoint integration with Microsoft Purview compliance portal must be configured.                                                                                                          |
| General patient data misuse                    | Defense evasion of security controls from EMR systems.<br><br>User and patient address matching indicators from HR systems. | Healthcare access indicators selected in policy or insider risk settings.<br><br>Microsoft 365 HR connector must be configured for address matching.<br><br>Microsoft Healthcare or Epic connector must be configured.                                                        |
| Security policy violations by departing users  | Resignation or termination date indicators from HR connector or Azure Active Directory account deletion.                    | (optional) Microsoft 365 HR connector configured for termination and resignation date indicators.<br><br>Active Microsoft Defender for Endpoint subscription.<br><br>Microsoft Defender for Endpoint integration with Microsoft Purview compliance portal must be configured. |
| Security policy violations by priority users   | Defense evasion of security controls or unwanted software detected by Microsoft Defender for Endpoint.                      | Active Microsoft Defender for Endpoint subscription.<br><br>Microsoft Defender for Endpoint integration with Microsoft Purview compliance portal must be configured.<br><br>Priority user groups configured in insider risk settings.                                         |
| Security policy violations by disgruntled user | Performance improvement, poor performance, or job level change indicators from HR connector.                                | Microsoft 365 HR connector configured for disgruntlement indicators.<br><br>Active Microsoft Defender for Endpoint subscription.<br><br>Microsoft Defender for Endpoint integration with Microsoft Purview compliance portal must be configured.                              |

### Prioritize content in policies

Insider risk management policies support specifying a higher priority for content. The priority depends on where the content's stored, the type of content, and how it's classified. Specifying content as a priority increases the risk score for any associated activity. It also increases the chance of generating a high severity alert. However, some activities won't generate an alert at all unless the related content contains built-in or custom sensitive info types, or it was specified as a priority in the policy.

For example, consider the scenario where a company has a dedicated SharePoint site for a highly confidential project. Data leaks for information in this SharePoint site could compromise the project and have a negative effect on its success. When a company prioritizes this SharePoint site in a Data leaks policy, risk scores for qualifying activities are automatically increased. This prioritization increases the likelihood that these activities generate an insider risk alert and raises the severity level for the alert.

When an organization creates an insider risk management policy in the policy wizard, it can choose from the following priorities:

 -  **SharePoint sites**. Any activity associated with all file types in defined SharePoint sites is assigned a higher risk score. Users configuring the policy and selecting priority Share Point sites can select SharePoint sites they have permission to access. If SharePoint sites aren't available for selection in the policy by the current user, another user with the required permissions can later select the sites for the policy. Or, the current user should be given access to the required sites.
 -  **Sensitive information types**. Any activity associated with content that contains sensitive information types are assigned a higher risk score.
 -  **Sensitivity labels**. Any activity associated with content that has specific sensitivity labels applied are assigned a higher risk score.
 -  **File extensions**. Any activity associated with content that has specific file extensions. Users configuring a data theft/leak policy that selects File extensions to prioritize in the policy wizard can define up to 50 file extensions to prioritize in the policy. Entered extensions can include or omit a '.' as the first character of the prioritized extension.

### Sequence detection

Risky activities may not occur as isolated events. These risks are frequently part of a larger sequence of events. A sequence is a group of two or more user activities performed one after the other that may suggest an elevated risk. Identifying these related activities is an important part of evaluating overall risk. When sequence detection is enabled for data theft or data leaks policies, insights from sequence information activities are displayed on the **User activity** tab within an insider risk management case.

The following policy templates support sequence detection:

 -  Data theft by departing users
 -  General data leaks
 -  Data leaks by priority users
 -  Data leaks by disgruntled users

These insider risk management policies can use specific indicators and the order they occur to detect each step in a sequence of risk. File names are used when mapping activities across a sequence. These risks are organized into four main categories of activity:

 -  **Collection**. These category signals focus on download activities by in-scope policy users. Some example activities in this category include downloading files from SharePoint sites and moving files into a compressed folder.
 -  **Exfiltration**. These category signals focus on sharing or extraction activities to internal and external sources by in-scope policy users. An example activity in this category would be sending emails with attachments from an organization to external recipients.
 -  **Obfuscation**. These category signals focus on the masking of risky activities by in-scope policy users. Some example activities in this category include renaming files on a device and removing or downgrading sensitivity labels on SharePoint files.
 -  **Clean-up**. These category signals focus on deletion activities by in-scope policy users. An example activity in this category would be deleting files from a device.

Sequence detection uses indicators that are enabled in the global settings for insider risk management. It also uses indicators that are selected in a policy. If appropriate indicators aren't selected, sequence detection won't work.

Organizations can customize individual threshold settings for each sequence detection type when configured in the policy. These threshold settings adjust alerts based on the volume of files associated with the sequence.

**Additional reading**. For more information about sequence detection management in the **User activity** view, see [Insider risk management cases: User activity](/microsoft-365/compliance/insider-risk-management-cases?azure-portal=true).

### Create a new policy

To create a new insider risk management policy, you'll use the policy wizard in the Insider risk management solution in the Microsoft Purview compliance portal.

Complete the following steps to create a new policy:

1.  In the **Microsoft Purview compliance** portal, select **Insider risk management** in the navigation pane.
2.  On the **Insider risk management** page, select the **Policies** tab.
3.  Select **Create policy** on the menu bar. This option opens the **Policy** wizard.
4.  In the **Policy** wizard, on the **Policy template** page, choose a policy category and then select the template for the new policy. These templates are made up of conditions and indicators that define the risk activities an organization wants to detect and investigate. Review the template prerequisites, triggering events, and detected activities to confirm this policy template fits your needs.
    
    > [!IMPORTANT]
    > Some policy templates have prerequisites that must be configured for the policy to generate relevant alerts. If you haven't configured the applicable policy prerequisites, see the prior section titled **Policy template prerequisites and triggering events**.
5.  Select **Next** to continue.
6.  On the **Name and description** page, complete the following fields:
     -  **Name (required)**. Enter a friendly name for the policy. This name can’t be changed after the policy is created.
     -  **Description (optional)**. Enter a description for the policy.
7.  Select **Next** to continue.
8.  On the **Users and groups** page, select **Include all users and groups** or **Include specific users and groups** to define which users or groups are included in the policy.
     -  **Include all users and groups**. This option will look for triggering events for all users and groups in your organization to start assigning risk scores for the policy.
     -  **Include specific users and groups**. This option allows you to define which users and groups to assign to the policy. Guest user accounts aren't supported.
9.  If you've chosen a priority users-based template, select **Add** or **edit priority user groups**.
10. Select **Next** to continue.
11. On the **Content to prioritize** page, you can assign (if needed) the sources to prioritize. Doing so increases the chance of generating a high severity alert for these sources. Select one of the following choices:
     -  **I want to specify SharePoint sites, sensitivity labels, and/or sensitive information types as priority content**. Selecting this option will enable detail pages in the wizard to configure these channels.
     -  **I don't want to specify priority content right now (you'll be able to do this after the policy is created)**. Selecting this option will skip the channel detail pages in the wizard.
12. Select **Next** to continue.
13. If you've selected **I want to specify SharePoint sites, sensitivity labels, sensitive information types**, and/or **file extensions as priority content** in the previous step, you'll see the detail pages for **SharePoint sites, sensitive info types, sensitivity labels** and **file extensions**. Use these detail pages to define the SharePoint, sensitive info types, and sensitivity labels to prioritize in the policy.
     -  **SharePoint sites**. Select **Add SharePoint site** and select the SharePoint sites you have access to and want to prioritize. For example, *"group1@contoso.sharepoint.com/sites/group1"*.
     -  **Sensitive info type**. Select **Add sensitive info type** and select the sensitivity types you want to prioritize. For example, *"U.S. Bank Account Number"* and *"Credit Card Number"*.
     -  **Sensitivity labels**. Select **Add sensitivity label** and select the labels you want to prioritize. For example, *"Confidential"* and *"Secret"*.
     -  **File extensions**. Add up to 50 file extensions. You can include or omit the '.' with the file extension. For example, *.py* or *py* would prioritize Python files.
    
    > [!NOTE]
    > Users configuring the policy and selecting priority Share Point sites can select SharePoint sites they have permission to access. If SharePoint sites aren't available for selection in the policy by the current user, another user with the required permissions can select the sites for the policy later. Or, the current user should be given access to the required sites.
14. Select **Next** to continue.
15. If you've selected the **General data leaks** or **Data leaks by priority users** templates, you'll see options on the **Triggers for this policy** page for custom triggering events and policy indicators. You have the choice to select a DLP policy or indicators for triggering events that bring users assigned to the policy in-scope for activity scoring.
     -  If you select the **User matches a data loss prevention (DLP) policy triggering event** option, you must select a DLP policy from the DLP policy dropdown list to enable triggering indicators for the DLP Policy for this insider risk management policy.
     -  If you select the **User performs an exfiltration activity triggering event** option, you must select one or more of the listed indicators for the policy triggering event.
        
        > [!IMPORTANT]
        > If you're unable to select a listed indicator, it's because they aren't enabled for your organization. To make them available to select and assign to the policy, enable the indicators in **Insider risk management &gt; Settings &gt; Policy indicators**.
        
        If you've selected other policy templates, custom triggering events aren't supported. The built-in policy triggering events apply and you'll continue to the final step without defining policy attributes.
16. Select **Next** to continue.
17. If you've selected the **General data leaks** or **Data leaks by priority users** templates and have selected the **User performs an exfiltration activity and associated indicators**, you can choose custom or default thresholds for the indicator triggering events that you've selected. Choose either the **Use default thresholds (Recommended)** or **Use custom thresholds for the triggering events**.
18. Select **Next** to continue.
19. If you've selected **Use custom thresholds for the triggering events**, for each triggering event indicator that you selected in Step 15, choose the appropriate level to generate the desired level of activity alerts.
20. Select **Next** to continue.
21. On the **Policy indicators** page, you'll see the indicators that you've defined as available on the **Insider risk settings &gt; Indicators** page. Select the indicators you want to apply to the policy.
    
    > [!IMPORTANT]
    > If indicators on this page can't be selected, you must select the indicators you want to enable for all policies. You can use the **Turn on indicators** button in the wizard or select indicators on the **Insider risk management &gt; Settings &gt; Policy indicators** page.
    
    If you've selected at least one **Office** or ***Device*** indicator, select the **Risk score boosters** as appropriate. Risk score boosters are only applicable for selected indicators. If you've selected a **Data theft** or **Data leaks** policy template, select one or more **Sequence detection** methods and a **Cumulative exfiltration detection** method to apply to the policy.
22. Select **Next** to continue.
23. On the **Decide whether to use default or custom indicator thresholds** page, choose custom or default thresholds for the policy indicators that you've selected. Choose either the **Use default thresholds for all indicators** or **Specify custom thresholds** for the selected policy indicators. If you've selected **Specify custom thresholds**, choose the appropriate level to generate the desired level of activity alerts for each policy indicator.
24. Select **Next** to continue.
25. On the **Review** page, review the settings you've chosen for the policy and any suggestions or warnings for your selections. Select **Edit** to change any of the policy values, or select **Submit** to create and activate the policy.

### Immediately start scoring user activity

There may be scenarios where an organization must immediately start assigning risk scores to users with insider risk policies outside of the insider risk management triggering event workflow. Use **Start scoring activity for users** on the **Policies** tab to:

 -  Manually add a user (or users) to one or more insider risk policies for a specific amount of time.
 -  Immediately start assigning risk scores to their activity.
 -  Bypass the requirement for a user to have a triggering indicator (like a DLP policy match).

You can also add a reason for adding the user to the policy. This reason will appear on the users' activity timeline. The **Users** dashboard displays users that were manually added to policies. Alerts are also created if activity meets the policy alert thresholds.

Some scenarios where an organization may want to immediately start scoring user activities include:

 -  Users are identified with risk concerns. As such, the organization wants to immediately start assigning risk scores to their activity for one or more of its policies.
 -  There's an incident that may require the organization to immediately start assigning risk scores to involved users' activity for one or more of its policies.
 -  The organization hasn't configured its HR connector yet. However, it wants to start assigning risk scores to user activities for HR events by uploading a .csv file for the users.

> [!NOTE]
> It may take several hours for new, manually added users to appear in the **Users** dashboard. Activities for the previous 90 days for these users may take up to 24 hours to display. To view activities for manually added users, navigate to the **Users** tab and select the user on the **Users** dashboard. Then open the **User activity** tab on the details pane.

To manually start scoring activity for users in one or more insider risk management policies, complete the following steps:

1.  In the **Microsoft Purview compliance** portal, select **Insider risk management** on the navigation pane.
2.  On the **Insider risk management** page, select the **Policies** tab.
3.  On the **policy** dashboard, select the policy or policies you want to add users to.
4.  Select **Start scoring activity for users**.
5.  In the **Reason** field in the **Add users to multiple policies** pane, add a reason for adding the users.
6.  In the **This should last for (choose between 5 and 30 days)** field, define the number of days to score the user's activity for the policy they're added to.
7.  To search your Active Directory for users, use the **Search user to add to policies** field. Type the name of the user you want to add to the policies. Select the user name and repeat to assign other users to the policies. The users that you selected will appear in the **Users** section of the **Add users to multiple policies** pane.
8.  To import a list of users to add to the policies, select **Import** to import a .csv (comma-separated values) file. The file must be in the following format, and you must list the user principal names in the file:
    
    ```
    user principal name
    user1@domain.com
    user2@domain.com
    
    ```
9.  Select the **Add users to policies** to accept the changes and add users to the policies, or select **Cancel** to discard the changes and close the dialog.
