Microsoft Intune includes different email settings you can deploy to devices in your organization. Most platforms have a native or built-in email app on the device. Using Intune, configure the built-in email app to connect to Microsoft Exchange. End users then connect, authenticate, and synchronize their organizational email accounts on their mobile devices. By creating and deploying an email profile, you can confirm settings are standard across many devices. By configuring standard settings, you can help reduce support calls from end users who don't know the correct email settings.

You can use email profiles to configure the built-in email settings for the following devices:
- Android device administrator on Samsung Knox Standard 5.0 and newer
- Android Enterprise personally-owned devices with a work profile
- iOS 11.0 and newer
- iPadOS 13.0 and newer
- Windows 11
- Windows 10

Use the following steps to create a new Windows 11 email configuration profile:

## Step 1: Create a new Windows 11 email profile
1. Sign in to [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
   The **Create a profile** pane is displayed.
3. Select **Windows 10 and later** from the dropdown box under **Platform**.
4. Select **Templates** from the dropdown box under **Profile type**.
5. Select **Email** within the **Template name** list.
6. Click **Create**.

### Add basic profile values
1. Next to **Name**, add "Windows email settings".
1. [Option] Add a **Description** for your new profile.
1. Click **Next**.

## Step 2: Add configuration settings
1. Add the following email account settings:
   - **Email server**: Enter the host name of your Exchange server. For example, enter `outlook.office365.com`.
   - **Account name**: Enter the display name for the email account. This name is shown to users on their devices.
   - **Username attribute from AAD**: This name is the attribute Intune gets from Azure Active Directory (AAD). Intune dynamically generates the username that's used by this profile. Your options:
   - **User Principal Name**: Gets the name, such as `user1` or `user1@contoso.com`.
   - **Primary SMTP address**: Gets the name in email address format, such as `user1@contoso.com`.
   - **sAM Account Name**: Requires the domain, such as `domain\user1`. Also enter:  
      - **User domain name source**: Select **AAD** (Azure Active Directory) or **Custom**.

         When getting the attributes from **AAD**, also enter:
         - **User domain name attribute from AAD**: Choose to get the **Full domain name** or the **NetBIOS name** attribute of the user.

         When using **Custom** attributes, also enter:
         - **Custom domain name to use**: Enter a value that Intune uses for the domain name, such as `contoso.com` or `contoso`.

   - **Email address attribute from AAD**: Intune gets this attribute from Azure Active Directory (AAD). Choose how the email address for the user is generated. Make sure your users have email addresses that match the attribute you select. Your options:
   - **User principal name**: Uses the full principal name as the email address, such as `user1@contoso.com` or `user1`.
   - **Primary SMTP address**: Uses the primary SMTP address to sign in to Exchange, such as `user1@contoso.com`.

2. Select **Enable** next to *SSL** to use Secure Sockets Layer (SSL) communication when sending emails, receiving emails, and communicating with the Exchange server. **Disable** doesn't require SSL.
3. Select the following email synchronizastion settings:
   - **Amount of email to synchronize**: Select the number of days of email that you want to synchronize. When set to **Not configured** (default), Intune doesn't change or update this setting. Select **Unlimited** to synchronize all available email.
   - **Sync schedule**: Select the schedule for devices to synchronize data from the Exchange server. You can also select **As Messages arrive**, which synchronizes data as soon as it arrives. Or, select **Manual** so the device user starts the synchronization.

   When set to **Not configured** (default), Intune doesn't change or update this setting.


4. Select the content types that you want to synchronize to devices. Your options:
  - **Contacts**: **On** syncs the contacts. **Off** doesn't automatically sync the contacts. Users manually sync.
  - **Calendar**: **On** syncs the calendar. **Off** doesn't automatically sync the contacts. Users manually sync.
  - **Tasks**: **On** syncs the tasks. **Off** doesn't automatically sync the tasks. Users manually sync.

5. Click **Next**.

## Step 3: Assignments
For this device configuration profile, you can skip assigning this profile to any groups, users, or devices until you have created users and enrolled devices.

## Step 3: Applicability Rules
For this device configuration profile, you can skip assigning this profile to any groups, users, or devices until you have created users and enrolled devices.

## Step 4: Review + create
1. Review the values and settings for this configuration profile.
2. Click **Create**.
