You can add both free and paid-for iOS applicaitons to Intune for Education. Paid iOS applications require a Volume Purchase Plan (VPP) token.

Here, you will learn how to deploy free and paid-for iOS applications to Intune for Education.

## Add free iOS apps to Intune for Education

Search for and add free apps from the iOS App Store to your app inventory. Instructions apply only to apps that are listed as Free in the App Store.

### Recommendation: Set up VPP token

You do not need a VPP token to install free apps, but we recommended it. A VPP token permits you to purchase all apps--free and paid--through the VPP store. Intune silently installs VPP-purchased apps on devices, and does not require an Apple ID to authenticate.

If you choose not to use a VPP token to purchase your app, you will only be able to manage free apps in the Intune for Education. The device user will also need to sign in with an Apple ID to install assigned apps.

### Add new iOS app

Complete the following steps to add an iOS app to Intune for Education.

1. Sign in to the Intune for Education portal.
1. Click **Apps**.
1. In the left pane, under **iOS Apps**, click **New app**.
1. In the search box, type the full or partial name of an app.
1. Select the app and click **Save** to add the app to your Intune inventory.

### View app details in Intune for Education

Added apps appear in the app list, under iOS store. Click the app to view its:

- **Overview**: Lists app name, publisher, and date you added it to Intune. Click the app name to see the app in iTunes.
- **Groups**: Lists all groups that are assigned the app. Change group assignments here or go to the details page for a specific group.
- **Install status**: Shows details about the app's installation, such as the device it was assigned to. The status also lists last check-in time - and if the installation was a success, failure, or still-in-progress.

## Add VPP-purchased iOS apps to Intune for Education

Add Volume Purchase Program (VPP) iOS apps from the Intune for Education portal. This section describes how to manage VPP-purchased apps that have been synced to Microsoft Intune.

### What is the Volume Purchase Program

The Apple Volume Purchase Program lets organizations buy app licenses in bulk and manage them through their mobile device manager (MDM). With an MDM, such as Intune for Education, licenses can be managed and then silently deployed over-the-air to student devices. A VPP/MDM partnership is ideal in classrooms and organizations where the same app is needed on many devices.

### Before you begin

To view and manage licenses from the Intune for Education portal, you must first:

- Configure a VPP token.
- Purchase apps through an Apple VPP vendor or through the Apple School Manager > Apps and Books store.
- Transfer existing purchased licenses to the appropriate Intune VPP token. See the Apple education support site to learn how to transfer licenses.

### Search and add apps

Complete the following steps to search and add paid-for iOS apps from the Intune for Education portal.

Free apps are made available for purchase directly from the portal. However, these apps are made available so that users without a VPP account can easily get them. If you plan to deploy free apps silently and in volume to your school's devices, you should purchase them through the Apple VPP or Apple School Manager websites.

1. Sign in to the Intune for Education portal.
1. Click **Apps**, click **New app**, and then click **New iOS app**.
1. From the app list, under **iOS Apps**, click **New app**.
1. Select the country/region from where you're purchasing the app.
1. Type in the app's full or partial name. Intune returns a list of relevant results from the App Store.
1. Select the app.
1. A message appears that prompts you to complete your purchase through Apple School Manager. Click the link to go to Apple School Manager.
1. Follow the steps in Apple School Manager to complete your purchase. You'll be prompted to assign your licenses to the appropriate location.
1. Return to **Intune for Education** > **Apps**. Your app will appear in the **iOS App**s list. If you don't see it right away, wait a few minutes and refresh your page.

### View app details

Apps appear in the app list, under **iOS Apps**. Click the app to view its:

- **Overview**: Lists app name, publisher, and date you added it to Intune. Also lists the number of licenses available to assign.
- **Groups**: Lists all groups that are assigned the app. Change group assignments here or go to the details page for a specific group.
- **Install status**: Shows details about the app's installation, such as the device it was assigned to. The status also lists last check-in time and if the installation was a success, failure, or still-in-progress.

### Reassign VPP-purchased licenses

VPP-purchased apps can't be deleted from Intune for Education. However, you can remove a user from an assigned group, or remove the entire group from assignment.
