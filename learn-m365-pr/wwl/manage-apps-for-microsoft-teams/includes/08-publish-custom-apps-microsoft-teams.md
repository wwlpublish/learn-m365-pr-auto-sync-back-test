Microsoft Team enables you to provide and distribute team apps to your users. There are three options to distribute custom apps, depending on who your target audience is.
 
| Custom apps distribution methods | Who can use the app?        |
|---------------|---------------|
| Teams app store                           | **Everyone**.<br/> This is Microsoft’s global app store that you can use to provide your apps to all Microsoft Teams users globally, and to users located in other Microsoft 365 tenants. |
| Tenant apps catalog                 | **Users in your organization**.<br> This app catalog provides your apps to all your Microsoft 365 tenant users only. Users in other Microsoft 365 tenants cannot see or add your apps.                                |
| Sideloading                         | **A few individuals in your organization**.<br/> Sideloading makes the apps available only to specific users.  <br/> For examples:<br/> - You want to test and debug an app locally yourself or with other developers. <br/> - You built an app just for yourself. For example, to automate a workflow. <br/>  - You built an app for a small set of users, such as, your work group. |


In this topic, we focus on the custom apps in **Tenant apps catalog**. 

A Teams app package is created by using [Teams App Studio](/microsoftteams/platform/get-started/get-started-app-studio?azure-portal=true). When you have the app package, you can add it to your app catalog. While all users in your organization can view the app catalog, only global admins and Teams admins can publish and manage it. 

## Publish custom apps to organization's app store

To make the custom app available to users in your organization's app store (Built for your org), you need to make sure the status of the custom app shows **Allowed** on the **Manage apps** page of the Microsoft Teams admin center.

You can upload the custom app or approve the apps submitted by users(developers).

### Upload an app package as a Teams admin

1. Go to **Teams admin center**.
2. On the **Manage apps** page, select **+ Upload** to upload your app package in .zip format. 

    ‎:::image type="content" source="../media/upload-custom-app.png" alt-text="Screenshot of uploading a custom app":::  

### Approve custom apps submitted by users

When the app is ready for production use, the developer can submit the app using the **Teams App Submission API** or **Submit to app catalog** option in Teams client. 

You can see the newly submitted app automatically shows a **Publishing status** of **Submitted** and **Status** of **Blocked** on the **Manage apps** page of the Microsoft Teams admin center. 

‎:::image type="content" source="../media/custom-app-lifecycle-validate-app.png" alt-text="Publishing status " lightbox="../media/custom-app-lifecycle-validate-app.png":::  

When you're ready to make the app available to users, publish the app.

1. Select the app name to go to the app details page. 
2. On the **About** tab, you can view details about the app, including description, status, submitter, and app ID.
3. Once you validate the app, select **Publish** in the **Publishing status** box.

After you publish the app, the **Publishing status** changes to **Published** and the **Status** automatically changes to **Allowed**.

:::image type="content" source="../media/custom-app-lifecycle-app-details.png" alt-text="App details page for a submitted app" lightbox="../media/custom-app-lifecycle-app-details.png":::


## Update custom apps

As a Teams admin, you can update the app on the Manage apps page in the Microsoft Teams admin center. 

1. Go to **Teams admin center**.
2. On the **Manage apps** page, select the app name, and then select **Update**.

Doing this replaces the existing app in your app catalog and all app permission policies and app setup policies remain enforced for the updated app. 

‎:::image type="content" source="../media/update-app.png" alt-text="Update a custom app from Teams admin center" lightbox="../media/update-app.png":::  

