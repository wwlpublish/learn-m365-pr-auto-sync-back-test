There are several deployment options for installing Windows 10, depending on the current device state.

 -  **The device is running one of the previous supported Windows client operating systems.** Reserve existing settings, either by doing an in-place upgrade or migration.
 -  **The device isn't running Windows or can't be upgraded to Windows 10.** Complete a clean installation by using either a default or custom Windows 10 image, which can be followed by migration.
 -  **The device already has Windows 10 preinstalled and you want to customize it to adhere to company policy without reinstallation.** Use provisioning or Windows Autopilot. Windows Autopilot is considered the modern way of deploying Windows 10, while computer reimaging is considered the traditional deployment methodology.

Windows 10 can be deployed by using several deployment scenarios. Deployment scenarios are organized into the following three deployment methods:

 -  **Modern deployment.** These methods are recommended for Windows 10 deployments unless you have a specific need. For example, you must deploy a custom Windows 10 image or deploy Windows 10 to a device without a previous operating system. Modern deployment methods include in-place upgrade and Windows Autopilot.
 -  **Dynamic deployment.** These methods enable you to customize an existing Windows 10 device and configure it to meet your needs. The goal of dynamic deployment is to avoid reinstallation and transform an existing Windows 10 device into a productive company device, with minimal time and effort. Dynamic deployment methods include provisioning packages, subscription activation, and deployment by using Azure AD and Mobile Device Management (MDM) integration.
 -  **Traditional deployment**. These methods are image-based and can always be used, regardless of the current device state. Traditional deployment methods include bare metal deployment and refresh and replace. They're typically completed by using tools such as the Microsoft Deployment Toolkit (MDT) and Configuration Manager.

The rest of this module examines each of these deployment models in greater detail.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”