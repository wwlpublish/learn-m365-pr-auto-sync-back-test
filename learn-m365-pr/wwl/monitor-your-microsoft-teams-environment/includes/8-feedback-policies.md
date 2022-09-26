Users in your organization can send feedback about Microsoft Teams directly from within the Teams desktop, web clients, and mobile. Microsoft uses this feedback to improve the Teams experience and make Teams better.

Data sent through **Give feedback** and **Send feedback** is considered as "Support Data" under your Microsoft 365 or Office 365 agreement, including information that would otherwise be considered "Customer Data" or "Personal Data".

As an admin, you can control whether users in your organization can send feedback about Teams to Microsoft and whether they receive the survey.

## Feedback features in Microsoft Teams

### Give feedback feature

Users can send comments and suggestions about Teams to Microsoft from Teams clients.

  - **Teams desktop** **and** **web** **client.** Go to **Help** \> **Give feedback** in Teams desktop and web.

    :::image type="content" source="../media/teams-feedback.png" alt-text="Give feedback option in Teams":::

  - **Teams mobile client.** Access feedback on mobile using **Settings** \> **Help & feedback** \> **Send feedback**.

    :::image type="content" source="../media/teams-feedback-mobile.png" alt-text="Give feedback option in Teams mobile client":::



### Surveys feature

Users can also rate their experience with Teams and send Microsoft details about the rating they give. This pop-up survey is displayed to users from time-to-time in Teams. When a user selects **Provide feedback** in the notification, the survey is displayed for them to complete.

:::image type="content" source="../media/teams-survey.png" alt-text="Give feedback using Surveys in Teams":::

## Manage feedback policies

By default, all users in your organization are automatically assigned the global (Org-wide default) policy, and the feedback feature and survey are enabled in the policy. You can edit the global policy or create and assign a custom policy. After you edit the global policy or assign a custom policy, it can take a few hours for changes to take effect. 

You manage feedback policies by using PowerShell:

  - Use the ```New-CsTeamsFeedbackPolicy``` PowerShell cmdlet to create a custom policy.

  - Use the ```Grant-CsTeamsFeedbackPolicy``` PowerShell cmdlet to assign it to one or more users or groups of users, such as a security group or distribution group.

  - Use the ```Set-CsTeamsFeedbackPolicy``` PowerShell cmdlet to set specific flags.

To turn off and turn on the features, set the following parameters:

  - **Give feedback**: Set the **userInitiatedMode** parameter to **enabled** to allow users who are assigned the policy to give feedback. Setting the parameter to **disabled** turns off the feature and users who are assigned the policy don't have the option to give feedback.

  - **Surveys**: Set the **receiveSurveysMode** parameter to **enabled** to allow users who are assigned the policy to receive the survey. To have users receive the survey and allow them to opt out, set the parameter to **enabledUserOverride**. In Teams, users can then go to **Settings > Privacy** and choose whether they want to participate in surveys. Setting the parameter to **disabled** turns off the feature and users who are assigned the policy won't receive the survey.

  - **Email**: Use the **AllowEmailCollection** flag to add an email field.

  - **Log collection**: Use the **AllowLogCollection** flag to add log collection opt-in for users. Log collection is currently enabled only on mobile.

The following example creates a feedback policy called New Hire Feedback Policy and we turn off the ability to give feedback through **Give feedback** and the survey.

```PowerShell
New-CsTeamsFeedbackPolicy -identity "New Hire Feedback Policy" -userInitiatedMode disabled -receiveSurveysMode disabled
```

Then, assign a custom policy named New Hire Feedback Policy to a user named user1.

```PowerShell
Grant-CsTeamsFeedbackPolicy -Identity user1@contoso.com -PolicyName "New Hire Feedback Policy"
```
## Review product feedback from users

Organizations own all user feedback data and this functionality will assist administrators to provide direct transparency into their users’ experiences with Microsoft 365 products and enable user feedback data to be provided as part of any Data Subject Request. 

Global admins and compliance data administrators now have the ability to view, export and delete user feedback. All other administrators, as well as readers, are able to view and export feedback data but can't perform compliance related tasks or see information about who posted the feedback (such as user name, email, or device name). 

Administrators can view, delete, and export the feedback data from the **Microsoft 365 admin center** > **Health** > **Product feedback**.
