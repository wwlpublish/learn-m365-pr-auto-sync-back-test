With Azure Active Directory (Azure AD), you can easily ensure that users have appropriate access. You can ask the users themselves or a decision maker to participate in an access review and recertify (or attest) to users' access. The reviewers can give their input on each user's need for continued access based on suggestions from Azure AD. When an access review is finished, you can then make changes and remove access from users who no longer need it.

## Begin an access review

To begin an access review, select the Azure AD group or application you want to manage access to. Decide whether you want individual users to review their own access, or one or more users review access for everyone. Then:

1. Navigate to the **Identity Governance** page.

   ![Step 1 The Identity Governance page](../media/01-identity-governance-page.png)

2. If this is your first time using access reviews, select **Onboard** and **Onboard Now**.

   ![Step 2 Select Onboard and Onboard Now](../media/02-onboard.png)

3. Select **Create an access review** from the Getting started page

   ![Step 3 Create an access review](../media/03-create-access-review.png)

4. On the Access Review screen, provide a **name**, **Start date**, **frequency/duration**, and **end date**. These settings will apply to either members of a group or users assigned to an application. Select the group or application along with the reviewers:

   ![Step 4 Enter needed data](../media/04-enter-needed-data.png)

5. Once the review is created, the access review will initialize and then start on the assigned date. 

   ![Step 5 Initialize and start](../media/05-initialize-start.png)

6. Reviewers assigned to the access review will receive an email from Microsoft, prompting them to review access:

   ![Step 6 Email to review access](../media/06-email-review-access.png)

7. On the Access review page, they can select either the groups and apps that require access reviews, or the access packages:

   ![Step 7 Review access packages](../media/07-access-reviews-webpage.png)

8. Once the reviewer has opened the access review, they are able to approve or deny the access. Here three users are selected and denied for access to the Intune Administrators group:

   ![Step 8 Approve or deny access](../media/08-intune-admin-confirm-deny.png)

9. The Identity Governance access review pane then updates with the results of the access review, and users denied access are removed from the group.

   ![Step 9 Access review pane update](../media/09-access-review-pane.png)
