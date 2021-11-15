You can use the Office Add-ins platform to build solutions that extend Office applications and interact with content in Office documents. With Office Add-ins, you can use familiar web technologies such as HTML, CSS, and JavaScript to extend and interact with Word, Excel, PowerPoint, OneNote, Project, and Outlook.

## Recommended approach for deploying Office add-ins

Consider rolling out add-ins in a phased approach to help ensure your add-in deployment goes smoothly. We recommend the following plan:

1. Roll out the add-in to a small set of business stakeholders and members of the IT department. If the deployment succeeds, move on to step 2.
2. Extend to a larger set of individuals within the business who will be using the add-in. Again, evaluate results and, if all went well, go to the next step of a full deployment.
3. Deploy to target audience of users.

Depending on the size of the target audience, you may want to add or remove steps.

## Deploy an Office add-in using the admin center

1. In the admin center, go to the **Settings > Add-ins** page. If you don't see the **Add-in** Page, go to the **Settings > Integrated apps > Add-ins** page.
2. Select **Deploy Add-in** at the top of the page, and then select **Next**.
3. Select an option and follow the instructions.
4. If you're adding an add-in from the Office Store, make your add-in selection. Notice that you can sort available add-ins by **Suggested for you**, **Rating**, or **Name**. You can only add free add-ins from the Office Store. Paid add-ins aren't currently supported. After you've selected your add-in, review and accept any additional terms and conditions.
    >[!NOTE]
      >You can also deploy add-ins in the admin center through **Integrated Apps**. Integrated Apps is visible to Global and Exchange administrators. If you don't see the above steps, go to the Centralized Deployment section by going to **Settings > Integrated apps**. On the top of the Integrated apps page, choose **Add-ins**.

When you use the Office Store option, updates and enhancements to the add-in are automatically made available to users without your intervention.

5. On the next page, select **Everyone**, **Specific users/groups**, or **Just me** to specify who the add-in is deployed to. You can search for users or groups.

    >[!NOTE]
    >Learn about the other states that apply to an add-in. See **Add-in states** in the **Learn more** section below.

6. Select **Deploy**.
7. A green tick appears when the add-in has been deployed. You can follow the on-page instructions to test that the add-in has deployed successfully.
    >[!NOTE]
    > Users might need to restart Office to see the add-in icon appear on the ribbon of app. Outlook add-ins can take up to 24 hours to appear on app ribbons.
8. When the add-ins are all deployed, select **Next**. If you've deployed to just yourself, select **Change who has access to add-in** to deploy to more users.

If you've deployed the add-in to members of your organization other than yourself, follow the instructions to announce the deployment of the add-in to those members.

You now see your add-in along with other apps in Microsoft 365.

It's a good idea to tell the users and groups who you deployed the add-in to that it's available. Consider sending an email to them that describes when and how to use the add-in and how the add-in can help them.

## Manage add-ins

You can manage the add-ins you've deployed to your organization. You can turn add-ins on and off and control who can access the add-ins.

### Add-in states

You can turn on or off the add-ins you deploy to your organization.

1. In the Microsoft 365 admin center, go to **Settings > Add-ins**.
2. Select the add-in you want to turn on or off.
3. Toggle the status to turn the add-in On or Off.
4. **Save** the changes.

### Edit add-in access

Post deployment, admins can also manage user access to add-ins.

1. In the admin center, go to the **Settings > Integrated apps** page.
2. Select the deployed add-in.
3. Click on **Edit** under **Who has Access**.
4. Save the changes.

### Control add-in downloads by turning off the Office Store across all clients (except Outlook)

One way to manage who can download and install an add-in is by choosing who can download new Office add-ins from the Office Store. When you also use Centralized Deployment, you can ensure that the users can deploy only organization-approved add-ins.

>[!NOTE]
>This doesn't apply to the Outlook add-in because its installation is managed by a different process.

To turn off add-in acquisitions:

1. In the admin center, go to the **Settings > Org settings** page.
2. Select **User owned apps and services**.
3. Clear the option to let users access the Office store.

This will prevent all users from acquiring the following add-ins from the store.

- Add-ins for Word, Excel, and PowerPoint 2016 from:
    - Windows
    - Mac
    - Office
- Acquisitions starting within AppSource
- Add-ins within Microsoft 365

A user who tries to access the store will see the following message: **Sorry, Microsoft 365 has been configured to prevent individual acquisition of Office Store add-ins**. 

### Delete an add-in

You can also delete an add-in that was deployed.

1. In the admin center, go to the **Settings > Integrated apps** page.
2. Select the deployed add-in and then select the **Configuration** tab.
3. In the **Configuration** pane, go to **Advanced Settings > Add-ins**.
4. Select the add-in from the list again.
5. Choose **Remove Add-In**. Remove the Add-in button on the bottom right corner.
6. Validate your selections, and choose **Remove**.

## User experience with add-ins

Now that you've deployed an add-in, your users can start using it in their Office applications. The add-in will appear on all platforms that the add-in supports.

### View your add-ins

If the add-in supports add-in commands, those commands appear on the Office ribbon. In the following example, the command **Search Citation** appears for the Citations add-in.

If the add-in doesn't support add-in commands or if you want to view all deployed add-ins, you can view in **My Add-ins**.

#### In Word 2016, Excel 2016, or PowerPoint 2016

1. Select **Insert > My Add-ins**.
2. Go to the **Admin Managed** tab in the Office Add-ins window.
3. Double-click the add-in you deployed earlier (in this example, Citations).

#### In Outlook

1. Select **Get Add-ins** on the **Home** ribbon.
1. Select **Admin-managed** in the left nav.

## Learn more

- [Determine if Centralized Deployment of add-ins works for your Microsoft 365 organization](/microsoft-365/admin/manage/centralized-deployment-of-add-ins?azure-portal=true)
- [See Add-in states](/microsoft-365/admin/manage/manage-deployment-of-add-ins?add-in-states?azure-portal=true)
- [Specify the administrators and users who can install and manage add-ins for Outlook](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins?redirectedfrom=MSDN?azure-portal=true)
