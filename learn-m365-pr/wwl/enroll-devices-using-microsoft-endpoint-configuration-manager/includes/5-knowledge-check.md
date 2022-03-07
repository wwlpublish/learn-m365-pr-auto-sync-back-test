Choose the best response for each of the questions below. Then select **Check your answers**.

### quiz title: Check your knowledge

## Multiple Choice
Which Configuration Manager console feature gives you the ability to see if a device is connected to its assigned management point?
(x) Client Online Status {{Correct. With Client Online Status, the site considers the device is online if it's connected to its assigned management point.}}
( ) Client Activity {{Incorrect. The site considers the client active when there's communication with Configuration Manager within seven days. With client activity, the site evaluates if the client has completed one of the key actions within seven days. These activities include requesting policy updates, sending a heartbeat message, or sending a hardware inventory message. Try again.}}
( ) Client Check {{Incorrect. With Client Check, the site runs a periodic evaluation with the Configuration Manager client on the device. The evaluation checks the device and remediate the problems it finds. Try again.}}

## Multiple Choice
To manage a Windows computer using Configuration Manager, there are multiple ways to deploy the client. What are the four most common methods of deployment?
( ) Client push, Manual deployment, Configuration Manager application package, Microsoft Intune {{Incorrect. While the client can be delieverd as a package, the client must already be installed and running on the device before it can recieve packages. This method isn't practical for the common scenarios. Try again.}}
( ) Windows update, Manual deployment, OS deployment, Microsoft Intune {{Incorrect. The Client is not deployed through Windows update. Try again.}}
(x) Client push, Manual deployment, OS Deployment, Microsoft Intune {{Correct. With Client push, the client deploys from the Configuration Manager console. By using manual deployment, the ccmsetup.exe file is delivered and executed on the device. With the OS Deployment method, the client is installed as part of a task sequence. With devices that are managed with Microsoft Intune, the client can be delivered as an application.}}

