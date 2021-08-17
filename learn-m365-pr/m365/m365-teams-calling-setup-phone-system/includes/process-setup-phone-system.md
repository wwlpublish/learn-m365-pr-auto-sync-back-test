You understand that Phone System can enable your users to make and receive public switched telephone network (PSTN) calls through their Microsoft Teams clients. So, you want to know how you can set up Phone System.

In this unit, you'll go through the process for setting up Phone System across your organization.

## The 10-step process

You can set up Phone System for your organization through the following 10-step process.

### Step 1: Verify that Phone System is available for your region or country

Make sure Phone System is available for your region or country by following these steps:

1. Visit the **Country and region availability for Audio Conference and Calling** page (link in the Learn more section) in the documentation.
1. At the top of the page, choose your region or country from the list.
1. You'll be forwarded to the availability details page relevant to your region or country.  Under the **Phone System** heading, review whether Phone System is available for purchase, and which features are available for it.

You can use the same method to check whether Teams Calling Plans are available in your country or regions. Teams Calling Plans are useful if you want to use Microsoft as your PSTN carrier. Otherwise, you'd need to use Phone System with Direct Routing. For more information on how to configure Direct Routing, use the **Configure and manage Direct Routing with Microsoft Teams** module (link in the Learn more section).

### Step 2: Get and assign licenses

You can assign licenses Phone System licenses on a single user basis, or through bulk assignment. The specific steps you'll do depend on whether you want to use the Microsoft 365 admin center or PowerShell. For example, to assign a Phone System license to users using the admin center, you do the following steps:

1. Sign in to the [Microsoft 355 admin center](https://admin.microsoft.com/).
1. In the navigation pane, select **Billing > Licenses**.
1. In the products list, select **Phone System**.
1. Select **Assign licenses** in the product details page.
1. In the **Assign licenses to users** pane, enter a username, and then select it from the results list.

    > [!NOTE]
    > This will let you add up to 20 users at a time. If you want to assign licenses to a large number of users in the hundreds or thousands, use PowerShell (link in the Learn more section).

1. Select **Turn apps and services on or off** to assign or remove access to specific items.
1. When you're done, select **Assign**, and then select *Close*.

If you want to use Teams Calling Plans, you assign those licenses at this stage as well.

### Step 3: Get user phone numbers

Get phone numbers for your users. You can get new numbers for your users using the Microsoft Teams admin center. You can also use it to transfer or port your users' existing numbers from your phone carrier or current service provider to Microsoft 365 or Office 365.

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/).
1. In the navigation pane on the left, select **Voice > Phone numbers**.

    :::image type="content" source="../media/add-phone-numbers-teams-calling.png" alt-text="Screenshot of adding phone numbers to Calling for Microsoft Teams":::

1. Select **Add** to add new numbers or **Port** to port numbers, and then follow the prompts.

    > [!NOTE]
    > Depending on your region or country, you might not be able to get new numbers using the Teams admin center until you download number request form (link in the Learn more section) and send it back to Microsoft.

### Step 4: Get service phone numbers

Next, add phone numbers (toll or toll-free) for services like auto attendants, audio conferencing, and call queues.  Service phone numbers have higher concurrent calling capacity than user phone numbers. A service phone number can handle hundreds of calls at the same time, while a user phone number is designed to handle only a few calls.  You can get new service numbers by doing the following steps:

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/).
1. In the left navigation pane, select **Voice > Phone numbers > Add**.
1. In the pane that opens, select your country or region in the **Country or region** field.

    :::image type="content" source="../media/select-phone-number-type.png" alt-text="Screenshot of adding service phone numbers":::

1. The **Number type** field appears, use it to select the type of service numbers you want to add. Then follow the prompts to finish adding your numbers.

### Step 5: Set up Teams Calling Plans (optional)

If you've decided to use Microsoft as your PSTN carrier, then you can now set up Teams Calling Plans. At a high level, the steps are as follows:

1. Verify whether Teams Calling Plans are available in your region or country.
1. Get and assign Calling Plan licenses.
1. Get user and service phone numbers.
1. Add emergency address and locations for your organization.
1. Assign an emergency address and phone number to a user.
1. Tell users about their new telephone numbers.

At this stage, you'll have already understood how to do step 2 to 3, since those are identical to what you do for Phone System. Use the Set up Calling Plans link in the **Learn more** section for details on how to carry out the complete list of tasks.

### Steps 6: Set up Audio Conferencing (optional)

There might be cases where people in your organization need to use their phone to call in to a meeting. The Audio Conferencing feature in Microsoft Teams will enable your users to dial in to meetings without having to use the Microsoft Teams app on their mobile or their desktop device. At a high level, you can configure Audio Conferencing for Microsoft Teams by doing the following steps:

1. Verify that Audio Conferencing is available in your region or country.
1. Get and assign Audio Conferencing licenses.
1. Get service numbers for conferencing bridges
1. Assign service numbers to the conferencing bridges
1. Set the languages for a conferencing bridge
1. Set your conferencing bridge settings
1. Set dial-in phone numbers for users who lead meetings
1. Set up meeting invitations (optional)

Use the Set up Audio Conferencing for Microsoft Teams guide (link in the Learn more section) for details on how to carry out those steps.

### Step  7: Set up cloud call queue (optional)

Call queues enable you to organize and route large numbers of incoming calls to make sure they're answered appropriately. Callers are put into a queue, and will be able to hear a greeting message, and music while they're on hold. Here are the high-level steps you can perform to set up call queues:

1. In the Teams admin center, go to the call queues section by selecting Voice > Call queues > Add.
1. Specify a resource account and language. 
1. Upload the greeting and music for the hold in the queue.
1. Add users or groups as agents to route calls to.
1. Specify call routing method.
1. Configure call overflow handling settings (such as maximum calls in the queue, or where to redirect calls)
1. Set call timeout handling (specify how long a call can be on hold before it's redirected or disconnected).

For a detailed breakdown, use the Manage calls in Microsoft Teams by using auto attendants and call queues module (link in the Learn more section).

### Step: 8 Set up cloud auto attendant (optional)

Auto attendant makes it possible for people to call in, and be directed through a menu system that will take them to the right department, person, or call queue. You can use the Microsoft Teams admin center to create an auto attendant. The steps are as follows:

1. In the Teams admin center, go to the auto attendant section by selecting Voice > Auto attendants > Add.
1. Configure general information such as time zone, language, operator.
1. Specify the call flow (including greeting message, and menu options).
1. Specify the call flow for after hours and holidays.
1. Specify which users will be made available, or excluded to callers via dial-by-name or extension.
1. Specify a resource account with an associated service number to use for the auto attendant.

For a detailed breakdown, use the Manage calls in Microsoft Teams by using auto attendants and call queues module (link in the Learn more section).

### Step 9: Assign service phone numbers for audio conferencing, call queues, auto attendants

In step 4, you will have gotten your service numbers. This means you can assign them to the different types of services you want:

- For **Audio Conferencing**: Assign a dedicated number to a conferencing bridge by changing the number for your conferencing bridge in the Teams admin center. Use the **Change the phone numbers on your Audio Conferencing Bridge** guide (link in the **Learn more** section) for detailed steps.

- For **Auto Attendants**: Assign a dedicated number for an auto attendant by going to **Org-wide settings > Resource accounts**, select your auto attendant's **resource account**, then select **Assign/unassign** and follow the prompts in the pane that appears.

    :::image type="content" source="../media/assign-number-auto-attendant.png" alt-text="Screenshot of assigning a number to an auto attendant":::

- For **call queues**: Assign dedicated numbers by setting the caller ID for members of a call queue to the service number of an auto attendant. You specify this in your caller ID policy (more on caller ID later in the module):

    :::image type="content" source="../media/change-caller-id-policy.png" alt-text="Screenshot of changing the caller ID policy for service numbers":::

### Step 10: Set up Communication Credits for your organization (optional)

Communication Credits provide a convenient way to pay for Calling Plan and Audio Conferencing minutes. Microsoft recommends that you configure Communications Credits for Teams Calling Plans and Audio Conferencing users that will need to dial out to different destinations. Communication Credits are also necessary if you want to use toll-free numbers. At a high level, you can configure Communication Credits for your organization by doing the following:

1. Assign Audio Conferencing or Calling Plan licenses users.
1. Set up Communication Credits for your organization.
1. Assign Communication Credits licenses to users

Audio Conferencing licenses are assigned in the same way as Calling Plan licenses. Use the **Set up communications credits for your organization** guide (link in the **Learn more** section) for details on how to complete the full set of steps.

## Learn more

- [Request forms for new numbers](/microsoftteams/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization#request-forms-for-new-phone-numbers)
- [Country and region availability for Audio Conference and Calling](/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)
- [Assign Teams add-on licenses to users using PowerShell](/microsoftteams/teams-add-on-licensing/assign-teams-add-on-licenses#using-powershell)
- [Set up Calling Plans](/microsoftteams/set-up-calling-plans)
- [Set up Audio Conferencing for Microsoft Teams](/microsoftteams/set-up-audio-conferencing-in-teams#step-3-get-service-numbers-for-your-conferencing-bridges)
- [Create a call queue](/microsoftteams/create-a-phone-system-call-queue)
- [Manage calls in Microsoft Teams by using auto attendants and call queues](/learn/modules/m365-teams-manage-calls-using-auto-attendants/)
- [Change the phone numbers on your Audio Conferencing bridge](/MicrosoftTeams/change-the-phone-numbers-on-your-audio-conferencing-bridge#steps-when-you-are-assigning-a-new-service-phone-number-to-your-conference-bridge)
- [Set up Communications Credits for your organization](/microsoftteams/set-up-communications-credits-for-your-organization)
- [Configure and manage Direct Routing with Microsoft Teams](/learn/modules/m365-teams-configure-manage-direct-routing/)
