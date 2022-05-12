Policies allow you to define the way you want your users to behave in the cloud. They enable you to detect risky behavior, violations, or suspicious data points and activities in your cloud environment. If necessary, you can integrate remediation work flows to achieve complete risk mitigation. There are multiple types of policies that correlate to the different types of information you want to gather about your cloud environment and the types of remediation actions you may want to take.

For example, if there's a data violation threat that you want to quarantine, you need a different type of policy in place than if you want to block a risky cloud app from being used by your organization.

Microsoft Defender for Cloud Apps can monitor any file type based on more than 20 metadata filters (for example, access level, file type). The Microsoft Defender for Cloud Apps engine combines three aspects under each policy:

 -  Content scan based on preset templates or custom expressions.
 -  Context filters, including:
    
     -  user roles
     -  file metadata
     -  sharing level
     -  organizational group integration
     -  collaboration context
     -  other customizable attributes
 -  Automated actions for governance and remediation.

    > [!NOTE]
    > The only governance action that's guaranteed to be applied is the action of the first triggered policy. For example, if a file policy has already applied a sensitivity label to a file, a second file policy can't apply another sensitivity label to it. For more information, see [Control](/defender-cloud-apps/control?azure-portal=true).

Once an organization enables a policy, the policy continuously:

 -  scans the organization's cloud environment.
 -  identifies files that match the content and context filters that were configured by the organization.
 -  applies the requested automated actions.

File policies detect and remediate any violations for at-rest information or when new content is created. Policies can be monitored using real-time alerts or using console-generated reports.

### Policy types

When you look at the Policy page in the Microsoft Defender for Cloud Apps portal, the various policies and templates can be distinguished by type to see which policies are available. The policies can be viewed together on the **All policies** tab, or in their respective category tabs. The available policies depend on the data source and what you have enabled in Microsoft Defender for Cloud Apps for your organization. For example, if you uploaded Cloud Discovery logs, the policies relating to Cloud Discovery are displayed.

The following table describes the types of policies can be created.

:::row:::
  :::column:::
    **Policy type**
  :::column-end:::
  :::column:::
    **Category**
  :::column-end:::
  :::column:::
    **Use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Activity policy
  :::column-end:::
  :::column:::
    Threat detection
  :::column-end:::
  :::column:::
    Activity policies allow you to enforce a wide range of automated processes using the app provider's APIs. These policies enable you to monitor specific activities carried out by various users, or follow unexpectedly high rates of a certain type of activity. [Learn more](/defender-cloud-apps/user-activity-policies?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Anomaly detection policy
  :::column-end:::
  :::column:::
    Threat detection
  :::column-end:::
  :::column:::
    Anomaly detection policies enable you to look for unusual activities on your cloud. Detection is based on the risk factors you set to alert you when something happens that is different from the baseline of your organization or from the user's regular activity. [Learn more](/defender-cloud-apps/anomaly-detection-policy?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    OAuth app policy
  :::column-end:::
  :::column:::
    Threat detection
  :::column-end:::
  :::column:::
    OAuth app policies enable you to investigate which permissions each OAuth app requested and automatically approve or revoke it. These built-in policies come with Defender for Cloud Apps and can't be created. [Learn more](/defender-cloud-apps/app-permission-policy?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Malware detection policy
  :::column-end:::
  :::column:::
    Threat detection
  :::column-end:::
  :::column:::
    Malware detection policies enable you to identify malicious files in your cloud storage and automatically approve or revoke it. This built-in policy comes with Defender for Cloud Apps and can't be created. [Learn more](/defender-cloud-apps/anomaly-detection-policy#malware-detection?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    File policy
  :::column-end:::
  :::column:::
    Information protection
  :::column-end:::
  :::column:::
    File policies enable you to scan your cloud apps for specified files or file types (shared, shared with external domains), data (proprietary information, personal data, credit card information, and other types of data) and apply governance actions to the files (governance actions are cloud-app specific). [Learn more](/defender-cloud-apps/data-protection-policies?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Access policy
  :::column-end:::
  :::column:::
    Conditional access
  :::column-end:::
  :::column:::
    Access policies provide you with real-time monitoring and control over user logins to your cloud apps. [Learn more](/defender-cloud-apps/access-policy-aad?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Session policy
  :::column-end:::
  :::column:::
    Conditional access
  :::column-end:::
  :::column:::
    Session policies provide you with real-time monitoring and control over user activity in your cloud apps. [Learn more](/defender-cloud-apps/session-policy-aad?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    App discovery policy
  :::column-end:::
  :::column:::
    Shadow IT
  :::column-end:::
  :::column:::
    App discovery policies enable you to set alerts that notify you when new apps are detected within your organization. [Learn more](/defender-cloud-apps/cloud-discovery-policies?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cloud Discovery anomaly detection policy
  :::column-end:::
  :::column:::
    Shadow IT
  :::column-end:::
  :::column:::
    Cloud Discovery anomaly detection policies look at the logs you use for discovering cloud apps and search for unusual occurrences. For example, when a user who never used Dropbox before suddenly uploads 600 GB to Dropbox, or when there are a lot more transactions than usual on a particular app. [Learn more](/defender-cloud-apps/cloud-discovery-anomaly-detection-policy?azure-portal=true).
  :::column-end:::
:::row-end:::


### Identifying risk

Defender for Cloud Apps helps you mitigate different risks in the cloud. You can configure any policy and alert to be associated with one of the following risks:

The following table describes the types of risks that can be identified.

:::row:::
  :::column:::
    **Risk**
  :::column-end:::
  :::column:::
    **What should you consider?**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Access control
  :::column-end:::
  :::column:::
    Who accesses what from where?
  :::column-end:::
  :::column:::
    Continuously monitor behavior and detect anomalous activities, including high-risk insider and external attacks, and apply a policy to alert, block, or require identity verification for any app or specific action within an app. Enables on-premises and mobile access control policies based on user, device, and geography with coarse blocking and granular view, edit, and block. Detect suspicious sign-in events, including multifactor authentication failures, disabled account sign-in failures, and impersonation events.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Compliance
  :::column-end:::
  :::column:::
    Are your compliance requirements breached?
  :::column-end:::
  :::column:::
    Catalog and identify sensitive or regulated data, including sharing permissions for each file, stored in file-sync services to ensure compliance with regulations such as PCI, SOX, and HIPAA.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Configuration control
  :::column-end:::
  :::column:::
    Are unauthorized changes being made to your configuration?
  :::column-end:::
  :::column:::
    Monitor configuration changes including remote configuration manipulation.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cloud Discovery
  :::column-end:::
  :::column:::
    Are new apps being used in your organization?
  :::column-end:::
  :::column:::
    Do you have a problem of Shadow IT apps being used that you don't know about? Rate overall risk for each cloud app based on regulatory and industry certifications and best practices. Enables you to monitor the number of users, activities, traffic volume, and typical usage hours for each cloud application.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DLP
  :::column-end:::
  :::column:::
    Are proprietary files being shared publicly?
  :::column-end:::
  :::column:::
    Do you need to quarantine files? On-premises DLP integration provides integration and closed-loop remediation with existing on-premises DLP solutions.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Privileged accounts
  :::column-end:::
  :::column:::
    Do you need to monitor admin accounts?
  :::column-end:::
  :::column:::
    Real-time activity monitoring and reporting of privileged users and admins.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Sharing control
  :::column-end:::
  :::column:::
    How is data being shared in your cloud environment?
  :::column-end:::
  :::column:::
    Inspect the content of files and content in the cloud, and enforce internal and external sharing policies. Monitor collaboration and enforce sharing policies, such as blocking files from being shared outside your organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Threat detection
  :::column-end:::
  :::column:::
    Are there suspicious activities threatening your cloud environment?
  :::column-end:::
  :::column:::
    Receive real-time notifications for any policy violation or activity threshold via text message or email. By applying machine learning algorithms, Defender for Cloud Apps enables you to detect behavior that could indicate that a user is misusing data.
  :::column-end:::
:::row-end:::


### Examples of different file policies

The following examples describe various file policies that can be created:

 -  **Publicly shared files**. Receive an alert about any file in your cloud that's publicly shared by selecting all files whose sharing level is set to **Public**.
 -  **Publicly shared filename contains the organization's name**. Receive an alert about any file that contains your organization's name and is publicly shared. Select files with a filename containing the name of your organization and which are publicly shared.
 -  **Sharing with external domains**. Receive an alert about any file shared with accounts owned by specific external domains. For example, files shared with a competitor's domain. Select the external domain with which you want to limit sharing.
 -  **Quarantine shared files not modified during the last period**. Receive an alert about shared files that no one modified recently, to quarantine them or choose to turn on an automated action. Exclude all the Private files that weren't modified during a specified date range. On Google Workspace, you can choose to quarantine these files, using the 'quarantine file' checkbox on the policy creation page.
 -  **Sharing with unauthorized users**. Receive an alert about files shared with unauthorized group of users in your organization. Select the users for whom sharing is unauthorized.
 -  **Sensitive file extension**. Receive an alert about files with specific extensions that are potentially highly exposed. Select the specific extension (for example, crt for certificates) or filename and exclude those files with private sharing level.

### Create a new file policy

Complete the following steps to create a new file policy:

1.  On the **Microsoft Defender for Cloud Apps** portal, select **Control** in the navigation pane, and then select **Policies**.
2.  On the **Policies** page, the **All policies** tab is displayed by default. Select the **Information protection** tab.
3.  In the **Information protection** tab, select **+Create policy** on the menu bar. In the drop-down menu that appears, select **File policy**.
4.  On the **Create file policy** page, you should configure the following information for the policy:
    
     -  **Policy template**. If you want to base your policy on a template, select this field to display a list of predefined templates and then select the corresponding template. If you want to create a customized policy, select **No template**. For more information on policy templates, see [Control cloud apps with policies](/defender-cloud-apps/control-cloud-apps-with-policies?azure-portal=true).
     -  **Policy name**. Assign the policy a name.
     -  **Policy severity**. If you have set Defender for Cloud Apps to send you notifications on policy matches for a specific policy severity level, this level is used to determine whether the policy's matches trigger a notification.
     -  **Category**. Link the policy to the most appropriate risk type. This field is informative only. The risk may already be preselected according to the category for which you chose to create the policy. By default, **File policies** are set to **DLP**, although you can select a different value if necessary.
     -  **Description**. Enter an optional description of the policy.
     -  **Files matching all of the following (filters)**. Create a filter for the files this policy will act on to set which discovered apps trigger this policy. Narrow down the policy filters until you reach an accurate set of files you wish to act upon. Be as restrictive as possible to avoid false positives. For example, if you wish to remove public permissions, remember to add the Public filter. Or, if you wish to remove an external user, use the "External" filter. When a policy filter is used, the **Contains** clause searches only for full words that must be separated by commas, dots, spaces, or underscores. For example:
        
         -  If you search for the words "malware" or "virus":
            
             -  It finds **virus\_malware\_file.exe.**
             -  It doesn't find **malwarevirusfile.exe**.
         -  If you search for **malware.exe:**
            
             -  It finds ALL files with either **malware** or **exe** in their filename.
         -  If you search for "malware.exe" (with the quotation marks):
            
             -  It finds only files that contain exactly "malware.exe". **Equals** searches only for the complete string. For example if you search for malware.exe, it finds malware.exe but not malware.exe.txt.
     -  **Apply to**. For this filter, select either **all files**, **all files excluding selected folders**, or **selected folders**. You can enforce your file policy over all files on the app or on specific folders. You're redirected to sign in the cloud app, and then add the relevant folders.
     -  **Select user groups**. Select either **all file owners**, **file owners from selected user groups,** or **all file owners excluding selected groups**. Then select the relevant user groups to determine which users and groups should be included in the policy.
     -  **Inspection method.** You can select either the [Built-in DLP](/defender-cloud-apps/content-inspection-built-in?azure-portal=true) or [Data Classification Services](/defender-cloud-apps/content-inspection?azure-portal=true) method. **Data Classification Services** is the recommended method. Once content inspection is enabled, you can:
        
         -  Choose to use preset expressions or to search for other customized expressions.
         -  Specify a regular expression to exclude a file from the results. This option is highly useful if you have an inner classification keyword standard that you want to exclude from the policy.
         -  Set the minimum number of content violations that you want to match before the file is considered a violation. For example, you can choose 10 if you want to be alerted on files with at least 10 credit card numbers found within its content.
         -  Unmask the last four characters of a match. When content is matched against the selected expression, the violation text is replaced with "X" characters. By default, violations are masked and shown in their context displaying 100 characters before and after the violation. Numbers in the context of the expression are replaced with "\#" characters and are never stored within Defender for Cloud Apps. You can select the option to Unmask the last four characters of a violation to unmask the last four characters of the violation itself. It's necessary to set which data types the regular expression searches: content, metadata and/or file name. By default it searches the content and the metadata.
     -  **Governance actions**. Select the action you want Defender for Cloud Apps to take when a match is detected.
5.  Once you've created your policy, you can view it in the **File policy** tab. You can always edit a policy, calibrate its filters, or change the automated actions.

A new policy is automatically enabled upon creation. As such, it starts scanning your cloud files immediately. Take extra care when you set governance actions. Improperly set actions can lead to irreversible loss of access permissions to your files.

It's recommended that you use multiple search fields to narrow down the filters. Doing so narrows down the list of files to the exact ones that you wish to act upon. The narrower the filters, the better. For guidance, you can use the **Edit and preview results** button in the **Filters** section.

File policy matches are files that are suspected to violate the policy. To view these files:

1.  In the **Microsoft Defender for Cloud Apps** navigation pane, select **Control** and then select **Policies**.
2.  On the **Policies** page, in the **Filters** section at the top of the page, select the **Type** filter to display the list of policy types. Select the appropriate type.
3.  For more information about the matches for a specific policy, select the policy.
4.  The "Matching now" files for the policy are displayed. Select the **History** tab to view the last six months of files that matched the policy.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”