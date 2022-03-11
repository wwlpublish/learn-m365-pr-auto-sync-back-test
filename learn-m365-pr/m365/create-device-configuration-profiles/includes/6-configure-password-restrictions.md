As mentioned previously, device configuration profiles are groups of settings that enable or disable different device capabilities or restrictions. You determine the specific capabilities or restrictions and apply the settings across the devices connected to your organization. You also determine the groups of users and devices that require these capabilities and settings. 

> [!NOTE]
> This modules explains how to create device configuration profiles before enrolling devices into Microsoft Intune.

Use the following steps to create a new iOS/iPadOS device configuration profile:

## Step 1: Create a new iOS/iPadOS profile
1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
   The **Create a profile** pane is displayed.
3. Select **iOS/iPadOS** from the dropdown box under **Platform**.
4. Select **Templates** from the dropdown box under **Profile type**.
5. Select **Device restrictions** within the **Template name** list.
6. Click **Create**.

### Add basic profile values
1. Add a **Name** and **Description** for your new profile.
2. Click **Next**.

## Step 2: Add configuration settings
1. Click **Password** from the list to display password related settings.
2. Select **Yes** next to **Require password**.
3. Select **Yes** next to **Block simple passwords**.
4. Click **Next**.

## Step 3: Assign profile to group
For this device configuration profile, you will skip assigning any groups, users, or devices to use this profile at this time.

## Step 4: Review + create
1. Review the values and settings for this configuration profile.
2. Click **Create**. 

