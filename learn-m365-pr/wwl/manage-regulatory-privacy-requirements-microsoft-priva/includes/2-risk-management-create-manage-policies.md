Privacy Risk Management policies can help you address risk scenarios that are important to your organization. Our policy templates are centered on fostering sound data handling practices.  Alerts let admins know when policy matches are detected and might need further investigation. Email notifications and tips in Microsoft Teams help users understand which activities carry privacy risks, allows users to immediately fix issues, and points them to privacy training.

For a quick start, use a template with default settings to create new policies for data overexposure, data transfers, and data minimization and scenarios. You can also customize template settings to create policies that suit your organization's needs.

## Policy template types

Privacy Risk Management has three policy templates designed to help you address key areas of concern around protecting personal data. Each template has default settings that you can accept in the quick setup process, or customize using a guided process. When you create a new policy, your first task will be to choose one of the three templates listed below:

- **Data overexposure**: This policy identifies content items containing personal data that may be too broadly accessible by other people. When matches are found, you can set up notifications prompting content owners to quickly apply protection.

- **Data transfers**: This policy can detect personal data transfers across boundaries that you determine, which could involve transfers outside of your organization, or internal transfers across departments or geographic regions. When matches are found, you can set up notifications encouraging senders to revoke access to the content.

- **Data minimization**: This policy identifies content items containing personal data that have been untouched for long periods of time. When matches are found, you can send notifications to content owners prompting them to  take quick action to keep or delete the item.

## Quick setup: using a template with default settings

When creating a policy directly from a template, most settings will be chosen for you automatically to help you get up and running quickly. Follow these steps to create a policy with default settings using one of our templates:

1. In the [Microsoft Purview compliance center](https://compliance.microsoft.com/), find Priva Privacy Risk Management in the left navigation and select **Policies**.

2. Select **Create a policy** at the upper right corner of the screen, which displays a flyout pane listing all policy creation options.

3. Find the type of policy you want to create and in its card, select **Create**.

4. A flyout pane contains policy details. Selecting **View settings** will show the default settings. You can edit settings from here, which takes you into the guided process outlined below. To continue creating your policy using the default settings, simply enter a descriptive name, then select **Create policy**.

Your policy will be created and you'll find it listed on your **Policies** page.

The policy will start running in test mode, meaning no alerts or notifications will be generated, and you can monitor its performance. When you're ready to turn your policy on, select your policy and edit it to turn in on.

## Custom setup: guided process to choose all settings

The custom policy option is a guided process for creating a policy. You'll start by choosing a template, and then walk through each setting to customize your policy. The instructions below give details about basic settings that apply to each of the three policy types. Where the settings differ by policy type, we'll link to specific instructions.

Follow the steps below to create a policy:

1. In the [Microsoft Purview compliance portal](https://compliance.microsoft.com/), locate Priva Privacy Risk Management in the left navigation. From the drop-down menu, select **Policies**.

2. Select **Create a policy**.

3. Choose the **Custom** option to create your policy using the policy creation wizard in Privacy Risk Management.

4. Choose the type of policy: **Data overexposure,** **Data transfers,** or **Data minimization**.

5. Give your policy a descriptive name to help you identify it in your list of policies. Provide an optional description, then select **Next**.

6. The next steps allow you to define all policy settings. You can jump to descriptions within in this article for more details. Options include:
    - [**Data to monitor**](#choose-data-to-monitor): Select the type of personal data your policy will monitor.
    - [**Users and groups**](#choose-users-and-groups): Apply your policy to all users or selected users.
    - [**Locations**](#choose-locations): Apply your policy to selected areas in Microsoft 365.
    - [**Conditions**](#set-conditions): Set the conditions for your policy. These options vary depending on your policy type.
    - [**Outcomes**](#define-outcomes-user-email-notifications-and-tips): Define the outcomes when a policy match is found, such as user email notifications.
    - [**Alerts**](#set-alerts): Decide the frequency of alerts to admins when a policy match is found.
    - [**Mode**](#testing-a-policy): Choose whether or not to run your policy in test mode first.
7. When all settings are complete, review your choices, make any desired edits, and then select **Submit** to create the policy.

After a few seconds, you'll see a confirmation that the policy was created. Select **Done** on the confirmation page, which will take you to the **Policies** page where you'll see the new policy at the top of the table.

The sections immediately below provide further details about each policy setting.

## Choose data to monitor

When creating or editing a policy, we'll ask you to select which types of data the policy should monitor. There are two options:

- **Classification groups**: A searchable list of groupings of sensitive information types; for example, a group based on the Australia Health Records Act, or a group based on US personally identifiable information such as a US passport number.

- **Individual sensitive information types**: A searchable list of sensitive information types; for example, Social Security numbers or driver's license numbers.

If you select from the existing classification groups, you can't also select individual types or create your own groups. For the most flexibility, choose individual sensitive info types. To utilize the most common standards, choose from the classification groups. Learn more about each data type below.

### Classification groups

Classification groups are groupings of [sensitive information types](/microsoft-365/compliance/sensitive-information-type-entity-definitions) that are used to detect content related to personal data or specific regulations.

When you select this option on the **Data to monitor** page, you'll need to select **+Add classification groups** and choose one or more groups from the list that appears on a flyout pane.

### Individual sensitive information types

By choosing specific [sensitive information types](/microsoft-365/compliance/sensitive-information-type-entity-definitions), like Social Security numbers or driver’s license information, you can customize your own group or groups of data to look out for. You can select from the complete list of sensitive information types within Privacy Risk Management. Each information type has its own properties.

When you select this option on the **Data to monitor** page, a selector appears with **Default** listed as a name for the group of sensitive info types you'll select. Keep or edit this group name, then select **Add** to select one or more sensitive info types from the complete list within Privacy Risk Management. Each information type has its own properties and recommended settings, which you can discover by selecting the info icon to the right of the confidence drop-down menu after you've added the info type. You can also change the instance count for each sensitive info type. This setting designates the number of unique instances of each sensitive info type you want your policy to detect.

If you create more than one group, the wizard lets you select how the groups should relate (an "and" or "or" relation) and define their order of operations.

## Choose users and groups

You have two options for deciding which users a policy will cover: all users and groups, or specific users and groups.

- **All users and groups**: This option will apply the policy to all users and Office 365 Groups in your organization.

- **Specific users or groups**: This option allows you to select individual users, individual Office 365 Groups, or a mix of both.
  - **To choose users**: Select **Choose users** and on the flyout pane, search for a user by entering an email address in the search box. Or find the user from the list and select the checkbox to the left of their name. You can select up to 100 users. When done, select **Add.**
  - **To choose groups**: Select **Choose groups** and on the flyout pane, select the checkbox to the left of each group name. You can select up to ten groups. When done, select **Add**.

After designating users and groups, select **Next** to advance to the next step.

## Choose locations

In this step, you'll designate where in your Microsoft 365 environment you want the policy to look for personal data matches. The location options will depend on the policy type, and you can select more than one. Each of the locations is explained below.

- **Exchange**: The policy will identify matches in users' Exchange accounts, which include content in the body of emails and in attachments sent or received by Exchange mailboxes.

- **OneDrive**: The policy will identify matches in files stored in users' OneDrive for Business account.

- **Teams**: The policy will identify matches in users' messages in Teams channels and chats.

- **SharePoint**: The policy will identify matches in files stored in users' SharePoint sites. When you select this option, you'll choose between the following options:
    - **All SharePoint sites**: this selection will cover all sites for all users in your organization.

    - **Specific SharePoint sites**: this selection asks you to designate specific sites for the policy to apply to. You can enter the URL of a specific site directly in the URL box, then select the **+** sign to add it to your list of sites. You can also select **Choose sites**, and from the flyout pane, search for and select from the list of sites you have access to. Check the box that appears when you hover over the site you want to select. After making your selections, select **Add**.  All your chosen sites will be listed at the bottom of the **Locations** page.
    
    > [!TIP]
    > If you need help identifying the SharePoint sites in your organization, visit [Manage sites in the SharePoint admin center](/sharepoint/manage-sites-in-new-admin-center).

After you finish designating locations, select **Next**.

## Set conditions

The conditions for detecting policy matches differ based on the policy template.

- **Data overexposure**: Refer to the conditions step in the [data exposure policy custom setup instructions](risk-management-policy-data-overexposure.md#custom-setup-guided-policy-creation-process).
- **Data transfers**: Refer to the conditions step in the [data transfers policy custom setup instructions](risk-management-policy-data-transfer.md#custom-setup-guided-policy-creation-process).
- **Data minimization**: Refer to the conditions step in the [data minimization policy custom setup instructions](risk-management-policy-data-minimization.md#custom-setup-guided-policy-creation-process).

## Define outcomes: user email notifications and tips

The outcomes settings are handled on the **Outcomes** page of the policy creation wizard. On this page, you can choose to send an email notification to users when they perform an action that matches a policy's conditions.

Data transfer policies have an additional option to show tips to users in Teams when their actions generate a policy match. These tips will include links to privacy training, which you provide, and include mechanisms for remediating potential risks.

These notifications can be useful opportunities to prevent issues from escalating, and to build users' skills and confidence in adopting safe data handling practices.

Visit [User notifications in Privacy Risk Management](risk-management-notifications.md) to learn more about working with user notifications.

## Set alerts

Alerts help admins know when a user event matches a policy's conditions. Setting up alerts is optional and you control how often alerts are generated, the threshold that must be reached before an alert is generated, and the alert's severity. Alerts are displayed on the **Alerts** card on the **Policies** page. Learn more about [viewing, investigating, and remediating alerts](risk-management-alerts.md).

#### Turn on alerts

You can turn on alerts when you first create a policy, or edit the policy later to turn them on. On the **Alerts** page of the policy creation wizard, set the **Create alerts** toggle switch to the **On** position.

#### Alert frequency and thresholds
After turning on alerts, decide how often they'll be generated.

- **Alert each time when a policy match occurs**: Selecting this option could yield a high number of alerts.
- **Alert when a specific threshold is reached**: You'll set  thresholds based on the number and frequency of user events detected.

#### Alert severity level
Select a severity level of Low, Medium, or High. We suggest your organization define what each level represents for you.

## Testing a policy

When you create a policy, the default setting is to start it in test mode. This means that once the policy is created:

- No alerts will be generated. However, you'll see insights on the policy's details page when matches are detected, including the types of data detected and their locations.

- No user email notifications will be sent when policy matches are detected. However, you'll see insights on the policy's details page showing which users are associated to policy matches.

Test mode allows you to look for matches from the last 30 days of user activity. Using these insights, you can gauge the policy’s behavior and review the types of alerts that may be generated when the policy is on.

We recommend testing your policy for at least five days to help you understand the type and volume of matches it'll generate. You can [edit the policy](#edit-a-policy) while it's in test mode so that you can monitor how the changes affect its performance before turning it on. For example, you may find that the policy is too broad and its conditions need adjusting. Or you may realize based on activity it detects that alerts won't be generated in a time frame that's useful to you.

The policy's details page indicates how many days the test has been running. You'll see how many matches have been found by location, how many user events matching the policy's conditions have been detected, and the personal data types that have detected by policy matches.

> [!NOTE]
> If you toggle the **Run in test mode** switch to the **Off** position, *this will turn on your policy* when you're done creating it. This means any alerts or user notifications you set up will start generating when matches are detected.

When you're satisfied with your policy's settings and are ready to turn it on, select the blue **Turn on policy** button. The policy will now be active and will generate any alerts and user notifications you set up.

## Turn on a policy

You can set a policy to turn on as soon as you finish creating it. This isn't recommended, as it's best to monitor performance and settings by putting the policy in test mode before you turn it on (see [Testing a policy](#testing-a-policy)).

If you've created your policy in test mode, you can quickly turn it on by following these steps:

1. From your **Policies** page, find the policy and select its name to open its details page.
2. In the **Policy status** card, select **Turn on policy**.

The policy will now be active and will generate any alerts and user notifications you set up.

## Turn off a policy

You can turn off a policy at anytime by selecting **Turn off policy** at the upper-right corner of a policy's details page. When a policy is off, it won't detect matches or generate alerts or email notifications. Turning off a policy won't delete a policy. You can turn a policy back on by selecting **Turn on policy** at the upper-right corner of the policy details page.

## View details and activity from the policy details page

Each policy has a details page showing activities detected by the policy and insights to help you address risks.

After your policy has been created, select its name in the table on the main **Policies** page. The **Overview** tab of the policy details page tells you the status of your policy, provides insights into your data, and highlights policy matches. Here you can view details about specific policy matches and learn more about next steps. If your policy's running in test mode, you'll see recommended next steps on this page and a button to turn on the policy.

When the policy's on, you can continue to review its policy details page to see ongoing insights on problem areas, alert severity and trends, and corrective actions taken.

### Overview tab

On the **Overview** tab of the policy details page, you'll find details about what the policy's detecting with respect to types and locations of data and user activity. The insights on the policy's details page are described below. After turning on a policy, it can take up to 48 hours for data to come through.

#### Policy status

The policy status card will indicate whether your policy is in one of three states: **Testing**, **On**, or **Off**.

**Testing**: This section shows the number of days your policy has been in test mode, which means it's looking for policy matches based on the conditions you set but is not generating alerts or user notifications. We'll provide a recommendation when it's a good time to turn your policy on. You can turn it on anytime by selecting the **Turn on policy** button on this card.

**On**: When your policy is on, the status card displays metrics that highlight when corrective action has occurred after a policy matches generate alerts and user notifications.

- **User actions taken**: This metric shows the number of remediation actions taken by users when prompted from a notification email out of the total number of notifications sent. For example, 8/10 would represent that out of 10 user notifications sent, users performed a remediation action in 8 instances.

- **User resolution rate**: This metric is rate at which remediation actions are taken by users based on the number of notifications generated. If the percentage is low, you may want to [edit the email content](risk-management-notifications.md#preview-and-customize-email-content), or closely examine the matches to determine if the policy's detecting the intended activity.

- **Admin actions taken**: This metric shows the number of remediation actions taken by admins when an alert is generated by the policy. Learn more about [how to take actions on alerts](risk-management-alerts.md#manage-alerts).

- **Admin resolution rate**: This metric is rate at which remediation actions are taken by admins based on the number of alerts.

#### Matches by location

The **Matches by location** card displays the number of content items detected by the policy according to Microsoft 365 location.

#### User notifications

The **User notifications** card displays a bar graph showing the number of user notification emails that have been generated by the policy if you have those capabilities turned on.

#### Matches by user

The **Matches by user** card lists the top users whose actions have triggered a policy match. You'll see the number of events detected by the policy for each user, along with the number of remediation actions taken from email notifications. Select **View all users** on this card to review the complete list of users detected by the policy.

#### Matches by data type

The **Matches by data type** card displays the types of personal data detected by policy matches, and the amount of each type. The pie chart helps visually demonstrate whether a certain type of personal data, for example Social Security numbers or credit card numbers, is predominantly represented in the risk scenarios you're trying to identify.

> [!TIP]
> When taking a holistic look at the locations, types of data, and number of users involved in policy matches, you may get a better sense as to the types of training and data protection measures needed to help your organization secure the personal data it stores.

### Matched items tab

The **Matched items** tab displays a list of all the content items matching a condition set forth in the policy. From this view, you can select an item from its row to preview it in the window to the right of the item list.

In the preview window, you'll find the following tabs that provide details about each item:
- **Source**: Displays the personal data that triggered the match.
- **Details**: Displays the content owner (user in your organization) for the item, the Microsoft 365 location of the item, the number of personal data types within the item, and the specific personal data types.
- **File activities**: Displays any label or classification applied to the item.
- **Remediation history**: Displays information about remediation actions taken by users or admins on the item.

## Edit a policy

You can edit the settings for a policy at any time, whether in test mode or turned on. You can update most policy settings, including putting a policy back into test mode after you've turned it on. The only settings you can't edit are the policy template and the policy name.

To edit a policy, follow the steps below:

1. In the [Microsoft Purview compliance portal](https://compliance.microsoft.com/), locate Priva Privacy Risk Management in the left navigation. From the drop-down menu, select **Policies**.

2. Select the policy you want to edit from its row on the **Policies** page, which brings up that policy's details page.

3. On the policy details page, select the **Edit** command in the upper-right corner of the page. This action will bring you into the policy creation  in Privacy Risk Management.

4. Proceed through the steps to get to the settings you wish to change. You can edit all settings except for policy template and policy name. Select **Next** to advance to each next step.

5. On the **Finish** page, review your settings, and then select **Submit** to save the changes you made.

## Delete a policy

If you need to remove an existing Privacy Risk Management policy, find it in the list on the **Policies** page, select the action menu (vertical ellipses), and choose the **Delete policy** action. You can also open the policy's details page and select **Delete** in the upper-right corner.

You'll be asked to confirm your choice before the deletion is final and the policy is permanently removed. Deleting a policy will not affect any files previously evaluated by the policy, and issues and alerts generated by the policy will still be listed on the **Alerts** and **Issues** pages.

