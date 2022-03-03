The Microsoft Store provides a convenient, single location where users can browse, install, and update applications. Many Universal Windows apps from the Microsoft Store are free, while others are available for purchase, or for free trial period. Users can access the Microsoft Store from both the desktop taskbar and the Start menu.

:::image type="content" source="../media/microsoft-store-home-04d4e5cd.png" alt-text="Screenshot of Microsoft Store Home screen, showing a banner for Microsoft 365, and a list of trending apps.":::


> [!NOTE]
> To access the Microsoft Store, users must sign in by using a Microsoft account. Users can create this account during the Windows installation, or after installation. You also can access the Microsoft Store by connecting your Microsoft account to your AD DS user account. The built-in administrator account cannot access the Microsoft Store or run any Universal Windows apps by default.

### Universal Windows apps

The Microsoft Store design enables users to access and install Universal Windows apps. Universal Windows apps are not like desktop apps, such as Office 2019 apps that run only on PC editions of Windows. Universal Windows apps are capable of running on multiple Windows devices, such as desktops, tablets, Xbox, HoloLens and IoT devices.

Universal Windows apps can communicate with one another and with the Windows operating system, making it simpler to search for and share information such as photographs. When you install a Universal Windows app, you can pin tiles to the Start menu, some of which update continuously with live app information or status.

Microsoft developed a procedure that provides the ability to convert desktop apps to Universal Windows apps targeting Windows Enterprise and Professional editions. The conversion functionality relies on two components. The first component is the Desktop App Converter, which is a tool that repackages an existing binary into the Universal Windows Platform (UWP) format. The resulting package contains the same base code that runs the desktop app. The second component is a runtime that allows UWP packages to operate with the full trust level, rather than in an app container. It also assigns a package identity to a converted app.

The conversion provides numerous benefits. It gives you the ability to apply a consistent app deployment methodology that uses sideloading and offers a straightforward and clean uninstallation process. It allows developers to enhance desktop apps with UWP features, including, for example, visual enhancements or support for background tasks. It also provides integration with the Microsoft Store licensing and update functionality.

> [!NOTE]
> The Microsoft Store now supports installation of Win32 apps as well as UWP apps.

#### Locating Universal Windows apps

When users connect to the Microsoft Store, the initial page they see is known as the landing page. This page makes it easier to locate and receive information on applications. The Microsoft Store divides applications into categories such as Games, Entertainment, and Music &amp; Videos.

Users also can search the Microsoft Store for specific Universal Windows apps. For example, if a user needs an application that provides video editing capabilities, the user can type the search text string in the search text box of the Microsoft Store app. The Microsoft Store lists the applications from which the user can choose.

> [!NOTE]
> Not all applications are available in all geographic locations or in every language.

#### Installing Universal Windows apps

Installing Universal Windows apps is a single-step process for users. A single select on the appropriate application in the Microsoft Store will install the application. The application installs in the background, so the user can continue browsing the Microsoft Store. After the application installs, a shortcut to the application displays in the user’s Start menu under All apps. The user then can select to pin the application to the Start menu, to the taskbar, or both.

#### Updating Universal Windows apps

Windows checks the Microsoft Store daily for updates to installed Universal Windows apps. When updates for installed applications are available, the user can open the Microsoft Store app and select to update one, several, or all of their installed applications.

> [!NOTE]
> By default, Windows will update installed applications automatically. However, users can change this setting if they want only to update specific applications.

#### Installing Universal Windows apps on multiple devices

Many users have multiple devices—for example, a desktop and a laptop computer. The Microsoft Store allows 10 installations of a single application so that users can run the same application on each of their devices. If users attempt to install an application on an 11th device, they receive a prompt that they must first remove the application from another device.

### Microsoft Store for Business

Microsoft Store for Business is a store that enterprises can customize. Microsoft Store for Business consists of two parts. The first part is a web portal hosted in Microsoft Azure, known as the Business Store portal, where information technology (IT) administrators can purchase, approve, and distribute applications for the entire enterprise. The second part is the Microsoft Store app, with an enterprise-managed private section that only employees of that enterprise can access. Any Universal Windows app that you want to be available in the Microsoft Store for Business must be uploaded to the Microsoft Store. However, it will only appear in the Microsoft Store app for users in that enterprise, and not in the retail version of the Microsoft Store.

#### Microsoft Store vs. Microsoft Store for Business

The Microsoft Store is primarily for end-users’ use when not necessarily working for an enterprise, whereas the Microsoft Store for Business gives enterprise employees a way to install work-related Universal Windows apps. The following table highlights some of the differences between the Microsoft Store and the Microsoft Store for Business.

:::row:::
  :::column:::
    **Microsoft Store**
  :::column-end:::
  :::column:::
    **Microsoft Store for Business**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Purchasing requires a Microsoft account.
  :::column-end:::
  :::column:::
    Purchasing requires an Azure AD account.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Each user purchases their own license for an application.
  :::column-end:::
  :::column:::
    An administrator can purchase multiple application licenses.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    You can deploy applications only through the Microsoft Store.
  :::column-end:::
  :::column:::
    You can deploy applications through the Microsoft Store and by using deployment tools.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Applications acquired will work on Windows 8.1 and later operating systems.
  :::column-end:::
  :::column:::
    Applications acquired in the Microsoft Store for Business will work on Windows client only.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    The store contains Universal Windows apps only.
  :::column-end:::
  :::column:::
    The store contains Universal Windows apps, desktop apps, and Android apps.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Available in all Windows 10 and later editions.
  :::column-end:::
  :::column:::
    The store is available only in Windows 10 Pro, Enterprise, and Education editions.
  :::column-end:::
:::row-end:::


> [!IMPORTANT]
> Microsoft announced that the Microsoft Store for Business will be retired in 2023. Microsoft Store for Business is not supported for managing delpoyment of apps to Windows 11. However, organizations can still use management solutions such as Endpoint Manager to deliver apps to Windows 11 devices, until the store is retired. Microsoft introduced a new tool called Windows Package Manager, which allows customers to install and manage private organization apps, as well as set up their own private repository. Customers can also use Endpoint Manager to manage their private catalogs. These functionalities are either in Preview or not yet released, and therefore outside the scope of this training.
