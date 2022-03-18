Desktop Analytics collects and analyzes device, application, and driver data in your organization. Based on this analysis and your input, you can use the service to create deployment plans for Windows. Deployment plans have the following features:

 -  Automatically recommend which devices to include in pilots
 -  Identify compatibility issues and suggest mitigations
 -  Assess the health of the deployment before, during, and after updates
 -  Track the progress of your deployment

As part of your deployment plan, you do the following actions:

 -  Define what versions of Windows you want to deploy
 -  Choose what groups of devices to which you want to deploy
 -  Create readiness rules for the deployment
 -  Define the importance of your apps
 -  Choose pilot devices based on automatic recommendations
 -  Decide how to fix issues with apps based on recommendations from Desktop Analytics

### Readiness rules

The following readiness rules are available in deployment plans:

 -  Whether your devices automatically receive drivers from Windows Update. If devices receive the driver updates from Windows Update, then any driver issues identified as part of readiness assessment are automatically marked as **Ready**.
 -  Low install count threshold for your Windows apps. If an app is installed more than 2%, the deployment plan marks the app as **Noteworthy**.

### Plan assets

While the Assets area also shows devices and apps, the **Plan assets** area under a specific deployment plan includes additional information.

 -  **Devices.** See the **Windows upgrade decision** for each device in the deployment plan. The Windows upgrade decision to **Replace device. This** can be because of reasons such as minimum hard requirements not met, a specific make/model cannot upgrade, a plug-and-play component that blocks upgrade, a risk that after an upgrade it will lose connectivity (such as a driver issue).
 -  **Apps.** Set the **Upgrade decision** and the **Importance** for this app in this deployment plan. In the details of the app, you can also see the following information: Recommendations, Compatibility risk factors, and Microsoft known issues. Use this information to help set the **Upgrade decision**. The apps that Desktop Analytics shows as **noteworthy** are based on the low install count threshold for the readiness rules of the deployment plan.
 -  **Drivers.** See the list of drivers included with this deployment plan. Set the **Upgrade decision**, review Microsoft's recommendation, and see compatibility risk factors.

### Importance

As part of the deployment plan, set the **importance** of the apps. Desktop Analytics detects these apps as installed on the target devices. This setting helps Desktop Analytics determine which devices it includes in the pilot phase of the deployment.

If an app is installed on less than 2% of the targeted devices, it's marked **Low install count**. Two percent is the default value. You can adjust the threshold in the readiness settings from 0% to 10%. Desktop Analytics automatically marks these apps as **Ready to upgrade**.

For apps, choose an importance of **Critical**, **Important**, or **Not important**. If you mark one as critical or important, Desktop Analytics includes in the pilot deployment some devices with that app. The service includes in the pilot more instances of a critical app. If you mark an app as not important, Desktop Analytics automatically sets it to **Ready to upgrade**.

To reduce management efforts, System apps and components published by Microsoft and Apps managed and updated from the Microsoft Store are automatically marked as *Not important* and *Ready*, as they should continue to work.

Asset importance and owner can also be modified in the Assets option in the Desktop Deployment portal.

### Pilot devices

Desktop Analytics combines your importance information with the global pilot settings. It then creates a recommendation for which devices should be part of the pilot deployment. The recommended pilot deployment includes devices with different hardware configurations and one or more instances of all the critical and important apps. If an app is marked critical, the service recommends more devices with that app in the pilot.

### Deployment plans in Configuration Manager

After creating a deployment plan, use Configuration Manager to deploy the products. Once the deployment starts, Desktop Analytics monitors the deployment based on the settings in the plan.
