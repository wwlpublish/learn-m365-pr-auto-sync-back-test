You've decided to use Intune for Education for your school, and you want to start managing your devices.

You can use express configuration in Intune for Education to help you to quickly get started. Intune for Education also works together with tools such as School Data Sync (SDS) and Take a Test, to help manage your users and devices.

Here, you'll see how to use express configuration in Intune for Education. You'll also explore how to plan and deploy School Data Sync (SDS) to sync your school data with Intune for Education. And you'll see how to configure a Take a Test profile to ensure online tests are administered securely.

## What is express configuration?

Express configuration in Intune for Education allows you to easily and rapidly deploy and customize apps and settings for your users and devices. Express configuration provides you with recommended configurations for Windows and iOS related settings, and recommended apps to deploy for both Windows and iOS operating devices. You can make changes to these default recommendations to address requirements specific to your environment at any point in time.

### Launch express configuration

You can start express configuration by doing the following:

1. Sign in to the Intune for Education portal (a link to the portal is available in the *Learn more* section) with an account that has Global Administrator permissions or Intune Service Administrator permissions. After successful sign-in, you'll see the Intune for Education dashboard:

    :::image type="content" source="../media/2-intune-education-portal.png" alt-text="Intune for Education portal.":::

1. Select **Launch Express Configuration** in the dashboard.

   > [!NOTE]
   > You won't see configuration options for iOS device management until you set up your tenant to manage iOS devices. To enable iOS management, review the instructions in the *Set up iOS device management* link in the *Learn more* section.

   :::image type="content" source="../media/2-select-get-started.png" alt-text="Select get started.":::

1. Select **Get started**.

### Choose groups to configure

If you're already using Microsoft 365 Education, express configuration will be able to collect information from Azure Active Directory groups, to automatically create, and populate the following groups:

- All devices
- All users

If you have School Data Sync (SDS) deployed for your school, express configuration will pick up on it, and will also automatically create the following groups:

- All teachers
- All students

> [!NOTE]
> Don't worry if you don't have School Data Sync deployed already. You'll see how you can deploy it later on in this unit.

You can also create your own groups, either manually, or with dynamic rules.

Groups are displayed in a list. When you configure a top-level group, all of its subgroups will also inherit its settings.
:::image type="content" source="../media/2-choose-group.png" alt-text="Choose a group.":::

Choose the group you want to configure. For example, you might want to ensure that password requirements are the same for all users, so you'd use the **All users** group to ensure this is the case for all users. After you've selected the group, select **Next**.

### Choose apps to assign

Express configuration will prompt you to choose apps to make available to the group you've chosen. You can add different types of apps to devices for your selected group, including:

- Web apps.
- Windows 10 apps such as:
  - Microsoft Office.
  - Desktop apps.
  - Microsoft Store for Education apps.
- iOS apps such as:
  - Volume purchased program (VVP) apps.
  - Free iOS App Store apps.

:::image type="content" source="../media/2-choose-apps.png" alt-text="Choose apps.":::

You can select any apps you want to assign, and they'll be assigned to your chosen group. After you've selected all the apps you want to assign, you select **Next**.

### Choose settings to apply

After you've selected apps to assign, express configuration will recommend commonly used settings for users and devices in Intune, and categorize them accordingly. You can change these settings at any time to meet your school's particular needs and policies.
:::image type="content" source="../media/2-choose-settings.png" alt-text="Choose settings.":::

After you've looked at the recommended settings, and chosen any particular settings you might need, select **Next**.

### Review all choices

Now you'll get the chance to review all of your choices one final time, and you can select **Done** to indicate that you're done with this group.

:::image type="content" source="../media/2-review-choices.png" alt-text="Review your choices.":::

You can then continue to set up more groups or select **All Done** to finish up:

:::image type="content" source="../media/2-express-config-done.png" alt-text="Express configuration done.":::

### How to apply further customization outside of express configuration

Use the following interactive guide to see how you can configure additional settings outside of express configuration for further customization of devices.

[Link to interactive guide](http://mdm-intune-for-edu.immersivelearning.online/)

## What is School Data Sync?

School Data Sync (SDS) is a free service available in Microsoft 365 Education. SDS lets you automatically import and synchronize your Student Information System (SIS) data or student and teacher data stored in CSV files, with Microsoft 365. SDS can read school data and roster data from your SIS or CSV files and create:

- School groups for Intune for Education.
- Class teams for Microsoft Teams.
- OneNote Class notebooks.
- Microsoft 365 Groups for SharePoint Online, and Exchange Online.

The SDS tool also gives application developers a single cloud API to use for creating applications that integrate with multiple SIS providers, along with single sign-on (SSO) capabilities. App developers can use the API to access section, student, teacher, school, and class roster information to personalize experiences for teachers and students who use their apps.

You can access School Data Sync by going to the SDS product page on your browser and selecting **Sign in** at the top right of the page to access the portal.

:::image type="content" source="../media/2-school-data-sync-page.png" alt-text="The School Data Sync product page.":::

> [!NOTE]
> The link to the product page is in the *Learn more* section. You can also access SDS from your Microsoft 365 Admin Center.

### Plan for SDS

For a smooth deployment, and to get the best out of SDS, you should take the following considerations into account:

#### Checklist

Put together a checklist to ensure you're covering key configuration items and options, including:

|Item  |Description  |
|---------|---------|
|Which source directory will you use?|You might have an SIS that is OneRoster 1.1. capable, or PowerSchool. These will allow you to sync using the API. If you're using other sources, you'll need to upload your data using one of the various CSV formats (including Clever format, and OneRoster 1.0 format).|
|Do you want to create new users, or sync existing users?  |You might already have a Microsoft 365 tenant with users, or you might have a new tenant with no users present yet. SDS will give you one option for each scenario, but if you want to sync existing users and also add new users, you may need multiple sync profiles to complete the setup. A sync profile is a group of settings and options that SDS uses to synchronize the data you want to upload. A sync profile is what you'll create for SDS deployment. You set up sync profiles in the SDS portal.|
|Assign licenses to new users|If you're creating new users, you'll need to assign licenses to each user account created. You can review the licenses that are available in your tenant to assign the appropriate licenses to teachers and students.|
|Use regular automated synchronization|If you're using the API to sync, it can sync continuously. If you're using a CSV file for syncing, the sync will only run whenever a new CSV file is uploaded. For this, you can use Power Automate or the SDS Toolkit to configure a regular automated sync schedule to process all changes. The toolkit can look at a specified location in your environment on a scheduled basis, and automatically process CSV files for synchronization.|

> [!NOTE]
> Use the planning checklist for School Data Sync link in the *Learn more* section for an extensive checklist.

#### Identity matching

During SDS configuration, every teacher and student identity from your source directory will be matched against an appropriate user in your target directory, which is Azure Active Directory. When you're synchronizing existing users, you'll need to choose an attribute that will always have the same exact value across both directories. This helps SDS know how to match a student or teacher, and sync their identity appropriately.

You look at the attributes available to you, and choose one attribute from the source directory, and one attribute from the target directory. For example, you could have the following attributes:

:::image type="content" source="../media/2-identity-matching.png" alt-text="Identity matching.":::

|Source directory attributes |Target directory attributes |
|---------|---------|
|Username|UserPrincipalName|
|Secondary email|Mail (PrimarySMTPAddress)|
|Teacher Number|mailNickname (Alias)|

In this example, you could choose to sync users based on the **Username** for each user in the target directory, and the **UserPrincipalName** in the target directory, because for your school, you know that these would be an exact match:

:::image type="content" source="../media/2-chosen-properties.png" alt-text="Choose a property.":::

To do this, you'd select **Username** as the source directory key, and select **userPrincipalName** as the target directory key during configuration:

:::image type="content" source="../media/2-select-properties.png" alt-text="Select the source and target properties.":::

> [!NOTE]
> The screenshot above shows how SDS lets you specify identity matching for teachers. SDS will ask you to do the same for students.

It might be the case that you have to use attributes that need a domain suffix to be added for an exact match. For example:

:::image type="content" source="../media/2-suffix.png" alt-text="Partial match.":::

The **Username** here is "Jim" and you'd need the domain name to get an exact match with the **UserPrincipalName**.  In this case, you could specify the domain as a suffix by selecting it in the **Domain (optional)** field to ensure a match.

#### Limits for synchronization

There are some limits you should take into account for successful synchronization:

|Limit |Description  |
|---------|---------|
|Maximum simultaneous sync profiles|School Data Sync can process a maximum of three syncs at a time. |
|Maximum number of users or rosters for each sync profile|If you're using CSV files for synchronization, don't go over 250,000 students per sync profile. If you want to go higher than this number, then you can reach out to Microsoft's SDS Onboarding Team.|
|Maximum number of errors for each sync profile|If you experience more than 15,000 errors for a sync profile, synchronization will stop. You'll then have to address those errors, and restart the process.|

#### Integration with Intune for Education

During sync profile configuration, you'll get the chance to enable integration with Intune for Education. You can select a single checkbox that will ensure the following actions are carried out for you:

- Create an **All Teachers** group and an **All Students** group.
- Create a **Teachers of each school** group, and a **Students of each school** group.
- Assign a license to each user within the profile.

> [!NOTE]
> You should only select this checkbox if you are sure that you want all of these steps to be carried out. For example, you might not have enough licenses to cover all of your users, in which case you shouldn't select this checkbox until you have enough licenses.

### Deploy SDS

Now that you have an idea of how to plan ahead for SDS deployment, you're ready to deploy SDS. For successful deployment, make sure you meet the following requirements:

- You have a Microsoft 365 Education tenant
- You have Global Administrator permissions

There are several methods that you can choose from to deploy SDS:

- Using the PowerSchool SIS API
- Using the OneRoster API
- Using Clever format CSV files
- Using SDS format CSV files
- Using OneRoster format CSV files

The method you choose dictates the steps you'll perform for deployment. For example, suppose you've got your data ready in Clever format CSV files, you'll perform the following steps:

#### Sign in

1. Go to the SDS portal using your internet browser, and select **Sign in**.

    :::image type="content" source="../media/2-start-school-data-sync.png" alt-text="Sign in to the SDS portal.":::

1. Make sure to sign in with your Global Administrator credentials for your Microsoft 365 Education tenant.

#### Choose a sync method

1. After successful sign-in, select **+ Add Profile** on the left of the dashboard.

    :::image type="content" source="../media/2-deploy-add-profile.png" alt-text="Select Add profile.":::
1. In the form that appears, give your profile a name, and select **Upload CSV files**, and **CSV files: Clever format**. Then select **Start** at the bottom of the form.

    :::image type="content" source="../media/2-deploy-create-profile.png" alt-text="Create profile.":::

#### Choose sync options

1. The sync options form appears:

    :::image type="content" source="../media/2-deploy-sync-options.png" alt-text="Set sync options.":::

1. You'll provide the following information:

    |Field  |Description  |
    |---------|---------|
    |Existing users/New users|Select whether you want to synchronize existing users or new users.|
    |Upload files|You select this to upload your CSV files. You must upload the following files: schools.csv, students.csv, teachers.csv, enrollments.csv, and sections.csv |
    |School properties|After you've uploaded the CSV Files, the attributes in your School.csv file will be autoselected here. Use this to validate whether the right attributes have been picked up the CSV file.|
    |Section properties|The attributes in your Student.csv file will be autoselected here. Use this to validate whether the right attributes have been picked up from the CSV file.|
    | Team Creation Option | Select this if you want to create a Microsoft 365 group and class team in Microsoft Teams for each class or section. You don't need to select this if you just want a Microsoft 365 group to be created.
    |Replace unsupported special characters|Select this to enable SDS to automatically look for and replace unsupported special characters during synchronization. This will help prevent some errors. These characters will be replaced with an "_". |
    |Sync option for Section Group display name|Select this option to allow teachers to overwrite section names.|
    |Delay student access|You select this option if you want to set a future date where students can view their classes. Alternatively, disable this option if you want them to be able to see their classes immediately after the Team owner has activated the class.|
    |When should we stop syncing this profile?     |You'll usually want to set this for the end of your school year. After synchronization stops, you'll be able to retire any classes associated with this profile.|

1. When you're done with this form, you select **Next** at the bottom of the form.

#### Teachers options

In the teacher options form, you set the identity matching attributes for teachers:

:::image type="content" source="../media/2-deploy-teacher-options.png" alt-text="Set teachers options.":::

1. Select an attribute from your source directory in the **Primary key (Source Directory)** field.
1. Select a matching attribute from the target directory in the **Primary key (Azure Active Directory**) field.
1. Optionally, you can select a **Domain** if a domain needs to be used as a suffix for a successful match.
1. When you're done, you select **Next** at the bottom of the form.

#### Student options

1. Next up, you'll perform the same steps as above to set the identity matching attributes for students:

    :::image type="content" source="../media/2-deploy-student-options.png" alt-text="Set student options.":::

2. When you're done, select **Next**.

#### Review

The review form appears. You're ready to review your selections:

:::image type="content" source="../media/2-deploy-review.png" alt-text="Review selections.":::

If everything looks good, select **Create profile** to start synchronization. If any errors occur concerning your CSV files, synchronization will be paused for you. You'll be able to fix those issues, upload your files again, and resume synchronization.

For automated synchronization after you've finished setting up your sync profile, use the Microsoft School Data Sync Toolkit (a link is available in the *Learn more* section). This way, you can create automated sync schedules for your CSV files. For further information, review the link *Deploy Settings with School Data Sync* in the *Learn more* section

## What is Take a Test?

Your school is one of the many schools that uses online testing for assessments. You need to make sure that testing is done in a secure way that prevents the use of internet resources or other resources and apps during a test. The Take a Test app can help you. When a test is launched, Take a Test can ensure that:

- Test takers can't use other apps or open other websites.
- Screen recording, sharing, or printing are disabled unless allowed by teachers or IT administrators.
- Test takers are unable to change settings.
- Autofill, notifications, and updates are turned off.

> [!NOTE]
> Some users need assistive technologies such as narrators while taking a test. These technologies will not be affected as long as they're configured to run above the lock screen. For more information, use the *Take a Test app technical reference* link in the *Learn more* section.

### Configure a Take a Test profile in Intune for Education

To set up Take a Test, you can configure a Take a Test profile in Intune for Education. Take a Test profiles define how assessments can be accessed, and what capabilities are available during assessments.

1. In the Intune for Education portal, select **Groups**, then select the group for which you want to create a Take a Test profile:

    :::image type="content" source="../media/2-select-groups-devices.png" alt-text="Select groups and then select all devices.":::

1. Select **Windows device settings**, select **Take a Test profiles**, then select **Assign new Take a Test profile**.

    :::image type="content" source="../media/2-select-windows-devices-settings.png" alt-text="Select Windows device settings.":::

1. Fill in the **New Take a Test profile** form that appears on the right:

    :::image type="content" source="../media/2-create-profile.png" alt-text="Create a new Take a Test profile.":::

    |Field  |Description  |
    |---------|---------|
    |Profile name|Provide a descriptive name for your profile.|
    |Account name|Provide the name of a local guest account to be used for tests. This name will be visible in the tile that the users will select to start a test.|
    |Assessment URL|Provide the URL of the assessment.|
    |Description|Optionally, you can provide a meaningful description for the profile. This won't be visible to test takers, it will only be visible in Intune for Education.|
    |Require printer connection|Set this to **Yes** if you want to ensure that test takers can only access the Take a Test app using devices that are connected to a printer.|
    |Allow screen capture|Set this to **Yes** if you want to allow the use of screen recording and screen capture capabilities in the Take a Test app.||
    |Allow text suggestions|Set this to **Yes** if you want to allow text suggestions during testing.||

1. When you're done, select **Create and assign profile**.

A student can now launch **Take a Test** from the Windows Lock screen. The app will navigate to the specified assessment URL, enabling the student to focus on the assessment.
