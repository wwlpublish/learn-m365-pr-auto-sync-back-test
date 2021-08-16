Microsoft Teams scales from small companies to international conglomerates. If you have more than a small number of users, you need a way to manage Teams settings for them, without having to configure each user individually.

In your large multi-national company, you've configured settings for your Teams deployment to conform to your security and access best practices. However, you also want to ensure that users conform to these best practices when they call each other or external users, and when they exchange messages.

Here, you'll learn how policies can be used to impose restrictions on large numbers of users and devices across your Teams system.

## What are policies in Teams?

Policies are used across the Microsoft Teams service to ensure the experience end-users receive conforms to the needs of the organization. You can create policies that control calling, meetings, messaging, and other aspects of Teams.

After a policy is created or edited it can be assigned to the entire tenant, to a group of users, or to an individual user – this flexibility provides a powerful set of capabilities for customers of all sizes to tune the service as needed.

## Policy packages

A policy package is a collection of predefined policies and settings. When you assign a policy package to users, the policies in the package are created. You can then customize the settings of the policies in the package to meet your organization's needs.

The policy package is designed to be applied to a group of users with similar roles, such as higher education students or first-line workers. Policy packages are designed to simplify, streamline, and provide consistency when managing policies for groups of users.

Use policy packages as a starting point to assist with regulatory compliance, making changes to fit your own regulatory requirements.

## How to use policy packages in Teams

:::image type="content" border="false" source="../media/3-manage-policy-packages-overview.png" alt-text="A flow diagram showing the steps to using Policy Packages: View, Assign, and Customize":::

There are three stages you should go through to successfully use policy packages in your organization:

1. View the settings in each policy package.
1. Assign policy packages to users and groups.
1. Customize policy packages to your organization's needs.

### View the settings of a policy package

In the Teams admin center, in the left navigation select Policy packages. You'll see a list of the provided policy packages. Select the one you'd like to view.

### Assign a policy package

You can assign a policy package to an individual user, multiple users at the same time, or a large batch of users up to 5,000 at a time. For individuals, in the Teams admin center, navigate to an individual user and assign a policy package to them. For multiple users, navigate to the Policy package section of the admin center. Select the policy package you want, then Manage users, and select all the employees you'd like assigned to it.

If you need to assign a policy package to thousands of users, use the **New-CsBatchPolicyPackageAssignmentOperation** PowerShell cmdlet. More details can be found in the **Learn more** section below.

### Customize a policy package

You can edit the settings of a policy through the Policy packages page or by going directly to the policy page in the Teams admin center.

1. In the left navigation of the [Microsoft Teams admin center](https://admin.teams.microsoft.com), do one of the following:
   - Select **Policy packages**, and then select the policy package by selecting to the left of the package name.
   - Select the policy type. For example, select **Messaging policies**.
1. Select the policy you want to edit. Policies that are linked to a policy package have the same name as the policy package.
1. Make the changes that you want, and then select **Save**.

## Manage meeting policies

Use *meeting policies* to control the features that are available to participants in meetings that are scheduled by users.
Policy settings may be **per-organizer**, **per-user**, or **per-organizer and per-user**.  Per-organizer settings are inherited by all meeting participants from the organizer. Per-user settings apply only to the organizer or participant. Per-organizer and per-user settings are based on both the organizer and participants policy.

### Meeting policy settings

You manage meeting policies in the **Microsoft Teams admin center** or by using PowerShell. Meeting policy settings can be configured for **General**, **Audio & video**, **Content sharing** and **Participants & guests**.

#### General

You can change the following policy settings:

- Allow Meet now in channels
- Allow the Outlook add-in
- Allow channel meeting scheduling
- Allow scheduling private meetings
- Allow Meet now in private meetings

#### Audio and video

You can change the following policy settings:

- Allow transcription
- Allow cloud recording
- Allow IP video
- Media bit rate (Kbs)

#### Content sharing

You can change the following policy settings:

- Screen sharing mode
- Allow a participant to give or request control
- Allow an external participant to give or request control
- Allow PowerPoint sharing
- Allow whiteboard
- Allow shared notes

#### Participants & guests

You can change the following policy settings:

- Let anonymous people start a meeting
- Automatically admit people
- Allow dial-in users to bypass the lobby
- Enable live captions
- Allow chat in meetings

### Designated presenter role mode

The **Designated presenter role mode** lets you change the **Who can present?** setting in Meeting options. The **Who can present?** setting lets meeting organizers choose who can be presenters in a meeting. This is a per-user policy. This policy setting affects all meetings, including Meet Now meetings. Currently, you can only use PowerShell to configure this policy setting.

#### Meeting attendance report

The **meeting attendance report** setting controls whether meeting organizers can download the meeting attendance report. This is a per-user policy. Currently, you can only use PowerShell to configure this policy setting. To enable a meeting organizer to download the meeting attendance report, set the **AllowEngagementReport** parameter to Enabled. When enabled, the option to download the report is displayed in the Participants pane.

#### Meeting provider for Islands mode

The **meeting provider for Islands mode** controls which Outlook meeting add-in is used for users who are in Islands mode. This is a per-user policy. Specify whether users can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins to schedule meetings in Outlook.

You can only apply this policy to users who are in Islands mode and have the **AllowOutlookAddIn** parameter set to True in their Teams meeting policy. Currently, you can only use PowerShell to set this policy.

#### Video filtering

The **video filtering** setting controls whether users can customize their video background in a meeting. This is a per-user policy. Currently, you can only use PowerShell to set this policy.

To specify whether users can customize their video background in a meeting, set the VideoFiltersMode parameter to either **NoFilters**, **BlurOnly**, **BlurandDefaultBackgrounds** or **AllFilters**.

## Manage messaging policies

*Messaging policies* are used to control which chat and channel messaging features are available to users in Microsoft Teams.

### Create a custom messaging policy

1. Sign into the [Microsoft Teams admin center](https://admin.teams.microsoft.com), select **Messaging policies**.
1. Select **Add**.
1. Enter a **name** and **description** for the policy.
1. Amend the **settings** to suit your needs.
1. Select **Save**.

In this example, you want to ensure that sent messages are not deleted or altered by users in the Personnel department:

1. Create a new custom policy named **Retain sent messages**.
1. Amend the following settings:
   - Owners can delete sent messages - **off** (default)
   - Delete sent messages - **off**
   - Edit sent messages - **off**
1. Select **Save**.

### Assign a custom messaging policy to a user

1. Sign into the [Microsoft Teams admin center](https://admin.teams.microsoft.com), in the left navigation, select **Users**.
1. Select the user by selecting to the left of the **user name**.
1. Select **Edit settings**.
1. Under **Policies**, in **Messaging policy**, select the correct policy.
1. Select **Apply**.

## Policy precedence

A user can only have one effective policy for each policy type. When a user is assigned a policy directly, but is also a member of one or more groups that have been assigned a policy of the same type, the effective policy is in this order:

1. If a **policy is assigned directly** to a user, this takes precedence over other policies.
1. If the user is a **member of one or more groups** that have been assigned a policy of the same type, this takes precedence over the global policy.
1. If the user has not been assigned a policy directly or through a group, the **global policy** is used.

## Learn more

For more information about the topics covered in this unit, see:

- [Teams Policies and Policy Packages for Education](/microsoftteams/policy-packages-edu).
- [Manage policy packages in Microsoft Teams](/microsoftteams/manage-policy-packages).
- [Assign policies to your users in Microsoft Teams](/microsoftteams/assign-policies).
- [Assign a policy package to a batch of users](/microsoftteams/assign-policies#assign-a-policy-package-to-a-batch-of-users).
- [Manage meeting settings and policies](/microsoftteams/meeting-policies-in-teams).
- [Change participant settings for a Teams meeting](https://support.microsoft.com/office/change-participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e).
- [Manage messaging policies in Teams](/microsoftteams/messaging-policies-in-teams).
