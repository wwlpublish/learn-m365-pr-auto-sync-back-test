Azure Active Directory (Azure AD) access reviews enable organizations to efficiently manage group memberships, access to enterprise applications, and privileged role assignments. With access reviews, Microsoft 365 Global admins and User Account admins can complete the following tasks:

 *  Evaluate guest user access by reviewing their access to applications and memberships of groups. Reviewers can use the insights that are provided to efficiently decide whether guests should have continued access.
 *  Evaluate employee access to applications and group memberships with access reviews.
 *  Collect access review controls into programs that are relevant for your organization to track reviews for compliance or risk-sensitive applications.
 *  Evaluate the role assignment of administrative users who are assigned to Azure AD roles such as Global Administrator or Azure subscription roles. This capability is included in Azure AD Privileged Identity Management.

The following graphic shows the purpose and circular nature of Access Reviews. In other words, inviting guests and later collaboration is always followed after a certain amount of time by a re-evaluation of the granted access rights and a removal process before everything starts over again.

:::image type="content" source="../media/access-reviews-186a2079.jpg" alt-text="graphic depicts the the purpose and circular nature of Access Reviews":::


### Prerequisites

Access reviews are available with the Premium P2 edition of Azure AD, which is included in Microsoft Enterprise Mobility + Security, E5.

**Additional reading.** For more information, see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/active-directory-editions?azure-portal=true).

### Create an access review

Global admins and User Account admins can create an access review by completing the following steps:

1.  In the Microsoft Azure dashboard, sign in to your tenant, then go to the [access reviews page](https://portal.azure.com/?azure-portal=true) and select **Programs**.
2.  Select the program that holds the access review control you want to create. **Default Program** is always present, or you can create a different program. For example, you can choose to have one program for each compliance initiative or business goal.
3.  Within the program, select **Controls**, and then select **Add** to add a control.
4.  Enter a **name** for the access review and an optional **description**. The name and description are shown to the reviewers.
5.  Set the **start date**. By default, an access review occurs once, starts the same time it's created, and it ends in one month. You can change the start and end dates to have an access review start date in the future, and you can set it to last however many days you want.
6.  To make the access review recurring, change the frequency from **One time** to **Weekly, Monthly, Quarterly, or Annually**. Then use the slider or text box to define how many days each review of the recurring series will be open for input from reviewers. To avoid overlapping reviews, the maximum duration a monthly review can be set to is 27 days.
7.  The recurring access review series can end in three ways: it runs continuously to start reviews indefinitely, until a specific date, or after a defined number of occurrences has been completed. Either you, or another user account administrator, or another global administrator can stop the series after creation by changing the date in **Settings** so that it ends on that date.
8.  Access reviews can be for the members of a group or for users who were assigned to an application. You can further scope the access review to review only the guest users who are members (or assigned to the app), rather than reviewing all the users who are members or who have access to the application.
9.  Select either one or more people to review all the users in scope, or you can select to have the members review their own access. If the resource is a group, you can ask the group owners to review. You also can require that the reviewers supply a reason when they approve access.
10. If you wish to manually apply the results when the review completes, click **Start**. Otherwise, the next section explains how to configure the review to automatically apply the results.

### Create and conduct an access review

You can have one or more users as reviewers in an access review.

1.  Select a group in Azure AD that has one or more members, or select an application connected to Azure AD that has one or more users assigned to it.
2.  Decide whether to have each user review their own access, or have one or more users review everyone's access.
3.  Enable access reviews to appear on the reviewers' access panels. As a global administrator or user account administrator, go to the [access reviews page](https://portal.azure.com/?azure-portal=true).
4.  Start the access review. For more information, see [Create an access review](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-create-access-review?azure-portal=true).
5.  Ask the reviewers to give input. By default, they each receive an email from Azure AD with a link to the access panel, where they [perform their access review](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review?azure-portal=true).
6.  If the reviewers haven't given input, you can ask Azure AD to send them a reminder. By default, Azure AD automatically sends a reminder halfway to the end date to reviewers who haven't yet responded.
7.  After the reviewers give input, stop the access review and apply the changes. For more information, see [Complete an access review](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-complete-access-review?azure-portal=true).

### Configuring an access review with auto-apply

1.  Expand the menu for **Upon completion settings** and then enable **Auto apply results to resource**.
2.  In cases where users were not reviewed by the reviewer within the review period, you can have the access review either take the system's recommendation (if enabled) on denying/approving the user's continued access, leave their access unchanged, or remove their access. This decision won't impact users who've been reviewed by the reviewers manually. If the final reviewer’s decision is Deny, then the user’s access will be removed.
3.  To enable the option to take recommendations should reviewers not respond, expand **Advanced settings** and enable **Show recommendations**.
4.  Finally, click **Start**.

Based on your selections in Upon completion settings, auto-apply will be executed after the review's end date or when you manually stop the review. The status of the review will change from Completed through intermediate states such as Applying and finally to state Applied. You should expect to see denied users, if any, being removed from the group membership or app assignment in a few minutes.

### Manage the access review

By default, Azure AD sends an email to reviewers shortly after the review starts. If you choose not to have Azure AD send the email, be sure to inform the reviewers that an access review is waiting for them to complete. You can show them the instructions for how to [review access](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review?azure-portal=true). When your review is for guests to review their own access, show them the instructions for how to [review your own access](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review?azure-portal=true).

If some of the reviewers are guests, guests are notified via email only if they've already accepted their invitation.

To manage a series of access reviews, navigate to the access review from Controls. For the upcoming occurrences in Scheduled reviews, edit the end date or add/remove reviewers as needed.

You can track the progress as the reviewers complete their reviews in the Azure AD dashboard in the Access Reviews section. No access rights are changed in the directory until [the review is completed](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-complete-access-review?azure-portal=true).
