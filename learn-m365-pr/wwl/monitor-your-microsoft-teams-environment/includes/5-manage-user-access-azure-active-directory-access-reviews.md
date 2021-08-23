Access to groups and applications for employees and guests changes over time. To reduce the risk associated with stale access assignments, administrators can use Azure Active Directory (Azure AD) to create access reviews for group members or application access.

Azure Active Directory (Azure AD) access reviews enable organizations to efficiently manage group memberships without needing administrative oversight. You can ensure that users and guest have appropriate access. With Access Reviews, you can:

* Schedule regular reviews or perform ad-hoc reviews to see who has access to specific resources, such as applications and groups

* Track reviews for insights, compliance, or policy reasons

* Delegate reviews to specific admins, business owners, or end users who can self-attest to the need for continued access

* Use the insights to efficiently determine if users should continue to have access

* Automate review outcomes, such as removing users’ access to resources


‎:::image type="content" source="../media/planning-review.png" alt-text="Diagram that shows the access reviews flow.":::


## Key benefits

The key benefits of enabling Access Reviews are:

* **Control collaboration**. Access Reviews allows organizations to manage access to all the resources its users' need. When their users share and collaborate, organizations can be assured that the information is among authorized users only.

* **Manage risk**. Access Reviews provide organizations a way to review access to data and applications, lowering the risk of data leakage and data spill. This includes capabilities to regularly review external partner’s access to corporate resources. 

* **Address compliance and governance**. With Access Reviews, you can govern and recertify the access lifecycle to groups, apps, and sites. You can control track reviews for compliance or risk-sensitive applications specific to your organization. 

* **Reduce cost**. Access Reviews are built in the cloud,  and natively work with cloud resources such as groups, applications, and Access Packages. Using Access Reviews is less costly than building your own tools or otherwise upgrading your on-premises toolset.

## Create Access Reviews for group members

### Prerequisites

* Azure AD Premium P2
* Global administrator or User administrator
* Microsoft 365 and Security group owner (Preview)

### Create one or more access reviews

1. Sign in to the Azure portal and open the [Identity Governance page](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade/?azure-portal=true).

2. Select **Create an access review** to create a new access review.

3. In **Step 1: Select what to review** section, select **Teams + Groups**.

4. In **Step 2: Select which Teams + Groups** section, select one of the two options: 

   - **All Microsoft 365 groups with guest users**. Select this option if you would like to create recurring reviews on all your guests across all your Microsoft Teams and Microsoft 365 groups in your organization. You can choose to exclude certain groups by selecting on ‘Select group(s) to exclude’.

   - **Select teams + groups**. Select this option if you would like to specify a finite set of teams and/or groups to review. After selecting on this option, you will see a list of groups to the right to pick from.

5. Next, in Step 3 you can select a scope for the review. Your options are
   - **Guest users only**. Selecting this option limits the access review to just the Azure AD B2B guests in your directory.
   - **Everyone**. Selecting this option scopes the access review to all user objects associated with the resource.

	If you selected All Microsoft 365 groups with guests in Step 2, then your only option is to review guests in Step 3.

	‎:::image type="content" source="../media/teams-groups.png" alt-text="Teams and groups":::

6. Select on **Next: Reviews**.

7. In the **Select reviewers** section, select either one or more people to perform the access reviews. You can choose from:

    - **Group owner(s)** (Only available when performing a review on a Team or group)
    - **Selected user(s) or groups(s)**
    - **Users review own access**
    - **Managers of users**.
    If you choose either **Managers of users** or **Group owners**  you also have the option to specify a fallback reviewer. Fallback reviewers are asked to do a review when the user has no manager specified in the directory or the group does not have an owner.

8. In the **Specify recurrence of review** section, you can specify a frequency such as **Weekly, Monthly, Quarterly, Semi-annually, Annually**. You then specify a **Duration**, which defines how long a review will be open for input from reviewers. For example, the maximum duration that you can set for a monthly review is 27 days, to avoid overlapping reviews. You might want to shorten the duration to ensure that your reviewers input is applied earlier. Next, you can select a **Start date**, and **End date**.

	‎:::image type="content" source="../media/new-access-review.png" alt-text="new access review":::


9. Select the **Next: Settings** button at the bottom of the page.

10. In the Upon completion settings,** you can specify what happens after the review completes.

    If you want to automatically remove access for denied users, set Auto apply results to resource to Enable. If you want to manually apply the results when the review completes, set the switch to Disable.
    
    Use the If reviewers don't respond list to specify what happens for users that are not reviewed by the reviewer within the review period. This setting does not impact users who have been reviewed by the reviewers manually. If the final reviewer's decision is Deny, then the user's access will be removed.

    - **No change** - Leave user's access unchanged
    - **Remove access** - Remove user's access
    - **Approve access** - Approve user's access
    - **Take recommendations** - Take the system's recommendation on denying or approving the user's continued access

    Use the Action to apply on denied **guest** users to specify what happens to guests if they are denied.
    - Remove user’s membership from the resource will remove denied user’s access to the group or application being reviewed, they will still be able to sign in to the tenant.
    - Block user from signing-in for 30 days, then remove user from the tenant will block the denied users from signing in to the tenant, regardless if they have access to other resources. If there was a mistake or if an admin decides to re-enable one’s access, they can do so within 30 days after the user has been disabled. If there is no action taken on the disabled users, they will be deleted from the tenant.

11. You can send notifications to other users or groups (Preview) to receive review completion updates. This feature allows for stakeholders other than the review creator to be updated on the progress of the review. To use this feature, select **Select User(s) or Group(s)** and add an extra user or group upon you want to receive the status of completion.

12. In the **Enable review decision helpers**, choose whether you would like your reviewer to receive recommendations during the review process.

13. In the Advanced settings section, you can choose the following
    - Set **Justification required** to **Enable** to require the reviewer to supply a reason for approval.
    - Set **email notifications** to **Enable** to have Azure AD send email notifications to reviewers when an access review starts, and to administrators when a review completes.
    - Set **Reminders** to **Enable** to have Azure AD send reminders of access reviews in progress to reviewers who have not completed their review. These reminders will be self half-way through the duration of the review.
    - The content of the email sent to reviewers is autogenerated based on the review details, such as review name, resource name, due date, etc. If you need a way to communicate other information such as other instructions or contact information, you can specify these details in the **Additional content for reviewer email** section. The information that you enter is included in the invitation and reminder emails sent to assigned reviewers. The section highlighted in the image below shows where this information is displayed.

	‎:::image type="content" source="../media/upon-completion-settings-new.png" alt-text="Upon completion settings options":::


14. Select on **Next: Review + Create** to move to the next page

15. Name the access review. Optionally, give the review a description. The name and description are shown to the reviewers.

16. Review the information and select **Create**.


## Allow  group owners to create and manage access reviews (Preview)

Prerequisite role: Global or User Administrator

1. Sign in to the Azure portal and open the [Identity Governance page](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade/?azure-portal=true).

1. In the left menu, under **Access reviews**, **settings**.

1. On the Delegate who can create and manage access reviews page, set the **(Preview) Group owners can create and manage for access reviews of groups they own** setting to **Yes**.
   

## Review access to groups 

Once you have specified the settings for an access review, select **Start**. The access review will appear in your list with an indicator of its status.

By default, Azure AD sends an email to reviewers shortly after the review starts. If you choose not to have Azure AD send the email, be sure to inform the reviewers that an access review is waiting for them to complete. 

You can start the Access Review process from the notification email or by going directly to the site [https://myapps.microsoft.com](https://myapps.microsoft.com?azure-portal=true). There are two ways that you can approve or deny access:

* You can approve or deny access for one or more users 'manually' by choosing the appropriate action for each user request.
* You can accept the system recommendations.

	‎:::image type="content" source="../media/perform-access-review.png" alt-text="Open access review listing the users to review":::




