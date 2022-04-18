The process of running a Power App varies depending on the app type. This unit examines how to run canvas and mobile apps.

### Running canvas apps

App creators and users who have the app shared with them can run a canvas app on Windows, iOS, and Android devices, or in a web browser, provided the app is running on a [supported device platform and browser](/powerapps/maker/canvas-apps/limits-and-config?azure-portal=true).

To run a canvas app on a mobile device:

1.  Download and install Power Apps from the App Store or Google Play onto an iPhone, iPad, or Android device running a [supported operating system](/powerapps/maker/canvas-apps/limits-and-config?azure-portal=true).
2.  Once the user is signed-in, PowerApps makes it easy to find an app:
    
     -  Select the down arrow key to use any of the available filters.
     -  Users can search by app name by selecting the search icon at the top right of the screen and entering the app name in the search box. Selecting search on a filtered list searches only the filtered list.
3.  To run the app, the user selects the app tile. If an app was shared in an email, the user can run the app by tapping the link in the email. If an app requires a connection to a data source or permission to use the device's capabilities (such as the camera or location services), the user must provide consent before using the app.
4.  Users can pin an app to the home screen of their device for quick access. Select the ellipsis (...) icon on the app tile, select **Pin to Home**, and then follow the instructions that appear.
5.  To close an app, users swipe from the left edge of the app to the right. On Android devices, users can also press the **Back** button and then confirm their intent to close the app.

Users can also run a canvas app on SharePoint Online pages or a Microsoft Teams channel:

 -  **SharePoint.** Add a Power Apps canvas app to a SharePoint Online page using the Power Apps web part. For more information, see [Office: Use the Power Apps web part](https://support.office.com/article/use-the-powerapps-web-part-6285f05e-e441-408a-99d7-aa688195cd1c?azure-portal=true).
 -  **Microsoft Teams.** In Microsoft Teams, select a team and then a channel under that team. Select the plus sign (**+**) icon to add a tab. In the **Add a tab** dialog box, select **PowerApps**. Select the desired app and select **save**. The app can now be run by selecting the tab that was added.

App creators that are part of Microsoft Partner Network can also share a canvas app with customers. By doing so, they can generate leads for their business by using [AppSource.com](https://appsource.microsoft.com/?azure-portal=true) and Power Apps Test Drive solutions. A Test Drive solution enables business customers to try out a real app without signing up for a Power Apps plan or installing any applications. Customers just sign into AppSource.com using their Azure Active Directory account and run the app in a web browser.

The process of building an app for a Test Drive solution is similar to building an app in Power Apps, with one exception - the app-maker must use embedded data (imported Excel data in table format) rather than external data connections. App makers must complete the [application form](https://powerapps.microsoft.com/partners/get-listed/?azure-portal=true) to start the process for publication on [AppSource.com](https://appsource.microsoft.com/?azure-portal=true).

### Running model-driven apps

Model-driven apps run on a mobile device using the Dynamics 365 mobile app (the Power Apps mobile app can't be used to run a model driven app). If a user doesn't have the Dynamics 365 app for phones and tablets installed, the app can be run on a web browser on a tablet if the device has a sufficiently high screen resolution. For full functionality and optimized experience, it's recommended that you use the Dynamics 365 for phones and tablets mobile app.

**Additional reading.** For more information regarding the functionality that is supported on model-driven apps, see [What's supported](/dynamics365/mobile-app/support-phones-tablets?azure-portal=true).
