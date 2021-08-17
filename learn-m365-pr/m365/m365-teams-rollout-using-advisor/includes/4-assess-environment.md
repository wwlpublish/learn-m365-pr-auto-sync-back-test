Each workload plan includes a tenant readiness assessment. Use the assessment to identify aspects of your environment that might need attention before you roll out Teams. These assessments include prerequisites and best practices. Depending on your environment and configuration, each assessment test will display either a green check mark, or an orange warning triangle.

- A green check mark means your tenant passed the specific test.
- An orange warning triangle means you might have to take further action. For example, a Microsoft 365 Groups expiration policy is recommended, but not required. An orange warning will be displayed to alert you to something you should check.

## Assessment tests

The following tests are run for all workloads:

- **Vanity domain configured**. Checks whether you've added your own domain name, such as **contoso.com**. You can use the onmicrosoft.com domain, but this test will warn if you haven't added your own valid domain name.
- **Teams licenses**. To roll out Teams, you must have **Teams licenses**. This test queries the Microsoft Graph to see whether you have at least one Teams license, and is a prerequisite.
- **Exchange Online licenses**. Tests whether you have an active subscription with available Exchange Online licenses. Although Exchange isn't required for Teams, integration with Exchange provides a better Teams experience. This test queries the Microsoft Graph to see whether you have at least one license for Exchange Online.
- **SharePoint Online licenses**. Tests whether you have an active subscription with available SharePoint Online licenses. Microsoft recommends per-user SharePoint Online licenses to provide OneDrive for Business for file storage in chats. This test queries the Microsoft Graph to see whether you have at least one SharePoint Online license.
- **Guest access enabled**. Tests whether guest access is turned on. Guest access lets you invite external users to join your teams.
- **External access configured**. Tests whether external access is turned on. By default, it's turned on, with open federation.

## Assessment tests for chat, teams, channels, and apps

In addition to the assessment tests already described, the following specific tests for chat, teams, channels, and apps are also run:

- **Microsoft 365 Groups naming policy configured**. Tests whether naming standards have been configured for Microsoft 365 Groups. The Microsoft 365 Groups naming policy enables your organization to apply a consistent naming strategy to user-created teams. It applies to other Groups workloads, including Outlook, SharePoint, Planner, and Yammer.
- **Microsoft 365 Groups expiration policy configured**. Tests whether a group expiration policy has been defined for Microsoft 365 Groups. This policy enables your organization to automatically remove inactive Teams and is off by default.

## Assessment tests for meetings and conferencing

- **Audio Conferencing licenses**. Tests whether you have an active subscription with Audio Conferencing licenses. It's a prerequisite if you're deploying Audio Conferencing bridges.
- **Stream licenses**. Tests whether you have an active subscription with Microsoft Stream licenses. This subscription is required if you want to record meetings.

## Assessment tests for Skype for Business Upgrade

In addition to the assessment tests for all workloads, Skype for Business Upgrade includes assessments used in the meetings and conferencing plan.

## How to run an assessment

To run the workload tests:

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com/).
1. From the left navigation bar, select **Planning**, then **Teams advisor**.
1. The **Deploy Features** screen displays the summary results of the workload tests. To get a detailed view, select **View all**.
1. The **Assessments** blade displays the results of each individual test. When you've read each assessment, select **Close**.
1. Select **Next** to display the **Add team members** screen.
1. Select **Add** and search for the users who will be part of the **Teams Service Management team**. Select **Apply**.
1. When you've added all the team members who will assist in the rollout of the selected workload, select **Create**. A new **Deployment** team is created with a **General** and workload-specific channel. For example, **Chat, teams, channels, and apps**.

You're now ready to start collaborating on your Teams rollout.

## Learn more

- [Use Advisor for Teams to help you roll out Microsoft Teams](/microsoftteams/use-advisor-teams-roll-out)
- [Advisor for Teams assessment tests](/microsoftteams/use-advisor-teams-roll-out#assessment-tests-for-all-workloads)
