Microsoft Intune includes different email settings you can deploy to devices in your organization. Most platforms have a native or built-in email app on the device. Using Intune, you can configure the built-in email app to connect to Microsoft Exchange. End users then connect, authenticate, and synchronize their organizational email accounts on their mobile devices. By creating and deploying an email configuration profile, you can confirm settings are standard across many devices in your organization. By configuring standard settings, you can help reduce support calls from end users who don't know the correct email settings.

You can use email profiles to configure the built-in email settings for the following devices:
- Android device administrator on Samsung Knox Standard 5.0 and newer
- Android Enterprise personally-owned devices with a work profile
- iOS 11.0 and newer
- iPadOS 13.0 and newer
- Windows 11
- Windows 10

Use the following steps to create a new Windows 11 email configuration profile.

## Step 1: Create a new Windows 11 email profile
1. Sign in to [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
   The **Create a profile** pane is displayed.
3. Select **Windows 10 and later** from the dropdown box under **Platform**.
4. Select **Templates** from the dropdown box under **Profile type**.
5. Select **Email** within the **Template name** list.
6. Click **Create**.

## Step 2: Add basic profile values
1. Next to **Name**, add "Windows 11 email settings".
2. *[Optional]* Add a **Description** for your new profile.
3. Click **Next**.

## Step 3: Add configuration settings
1. Add the following email account settings:
   - **Email server**: Enter the Exchange location (URL) of your email Exchange server. For example, enter `outlook.office365.com`.
   - **Account name**: Enter the display name for the email account. This name is shown to users on their devices.
2. For **Username attribute from AAD**, select **Primary SMTP address**. 
   The **Username attribute from AAD** is an attribute Intune gets from Azure Active Directory (AAD). Intune dynamically generates the username that's used by this profile. The **Primary SMTP address** is the name in email address format, such as `user1@contoso.com`.
3. For **Email address attribute from AAD**, select **Primary SMTP address**. Intune gets the email address attribute from Azure Active Directory (AAD). Uses the primary SMTP address to sign in to Exchange, such as `user1@contoso.com`. Make sure your users have email addresses that match the attribute you select. Your options:

    :::image type="content" source="../media/create-device-configuration-profiles-02.png" alt-text="Device configuration profile email settings":::

4. Select **Enable** next to **SSL** to use Secure Sockets Layer (SSL) communication to securely send emails, receive emails, and communicate with the Exchange server.
5. In the synchronization section, select **One Week** next to **Amount of email to synchronize**. 
   This email synchronization setting controls how much email to store on the device and how often to connect to the server.
6. Select **15 Minutes** next to  **Sync schedule**. 
   This setting allows you to select the schedule for devices to synchronize data from the Exchange server. You can also select **As Messages arrive**, which synchronizes data as soon as it arrives. Or, select **Manual** so the device user starts the synchronization.
7. In the **Content type to sync** section, select **On** next to **Contacts**, **Calendar**, and **Tasks**. 
   In addition to email, you can use these settings to configure other items you want to synchronize like contacts, calendar, and tasks. Email is still synchronized, regardless of these settings.
8. Click **Next**.

## Step 4: Assign profile to group
For this device configuration profile, you can skip assigning this profile to any groups, users, or devices until you have created users and enrolled devices.
1. Click **Next**.

## Step 5: Set applicability Rules
For this device configuration profile, you can skip specifying how to apply this profile within an assigned group.
1. Click **Next**.

## Step 6: Review + create
1. Review the values and settings for this configuration profile.
2. Click **Create**.

You have now created a new device configuration profile named "Windows 11 email settings". You can see the new configuration profile in the list by selecting **Devices** > **Configuration profiles**. For more information about email configuration settings in Intune, see [Email profile settings for devices running Windows 10/11 in Microsoft Intune](/mem/intune/configuration/email-settings-windows-10).