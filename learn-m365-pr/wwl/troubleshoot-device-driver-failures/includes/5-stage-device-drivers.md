Installing a device driver in Windows is a two-step process. During staging, you add the driver package into the driver store. You can do this regardless of whether the device is attached to the computer. You must use administrator credentials to add the device driver package into the driver store. The second step is the driver’s installation from the driver store. The driver is installed when Windows detects an attached device that would need the driver for the first time. A standard user can perform the second step, because it does not require administrative permissions.

Depending on the packaging of the device driver, you can install it in different ways. If the device driver has its own installation program (for example, setup.exe), you run the installation program, which performs the staging when you add the driver package to the driver store. If you attach a device to Windows computer, and its device driver is not in the driver store, Windows searches for a matching driver package in several locations. You can customize these locations, and you can include folders specified by the DevicePath registry entry and the Windows Update site. If Windows finds the driver package, it adds the driver package into the driver store, and then installs it from the driver store to the system. You also can stage the driver package manually, when you use the pnputil.exe command.

During device driver staging, Windows verifies the driver files, copies them to the driver store, and then indexes them for quick retrieval. However, it does not install them. During the staging process, Windows verifies that the driver packages contain all required files, that they do not display any user prompts, and that they do not require LocalSystem security context during installation. This allows a user, who does not have administrator privileges on a computer, to install them.

> [!NOTE]
> If there are multiple driver packages available for the same device, Windows ranks the driver packages by evaluating criteria such as:

 -  Is the driver signed?
 -  Is the driver specific to the attached device or for a compatible set of devices?
 -  What is the driver version?

### Benefits of staging driver packages

Device drivers run as part of the operating system, so it is critical that you allow only known and authorized device drivers to run. Staging device-driver packages on Windows provides several benefits, including:

 -  Improved security. You can allow standard users to install approved device drivers without compromising computer security or requiring help-desk assistance.
 -  Reduced support costs. Users can install only devices that your organization has tested and is prepared to support. Therefore, you can maintain computer security while you reduce help-desk demands.
 -  Better user experience. A staged driver package, in the driver store, works automatically when the user plugs in the device. Alternatively, Windows will discover driver packages that you place on a shared network folder whenever the operating system detects a new hardware device. In both cases, the user receives no prompts prior to installation.

### Stage device drivers manually

You can use the following steps to use the Pnputil.exe command-line tool to add a device driver to the Windows driver store manually:

1.  Obtain a digitally signed driver package.
2.  Sign in as **Administrator**, and then open a command prompt.
3.  At the command prompt, type **pnputil.exe /add-driver package\_name**, and then press Enter.
4.  The command runs, and Windows verifies the driver’s integrity and digital signature, and then copies the driver into the driver store.

> [!NOTE]
> The Pnputil.exe tool only runs at a command prompt with elevated user rights. The tool cannot invoke the User Account Control dialog box.

### Manage the driver store

You also can use the Pnputil.exe command-line tool to manage the driver store, including adding and removing driver packages from the driver store, and listing non-Microsoft driver packages that already are in the store.

You can use the Pnputil.exe command-line tool to perform the following tasks:

 -  Add a driver package to the driver store.
 -  Add a driver package to the driver store, and then install it in the same operation.
 -  Delete a driver package from the driver store.
 -  List all driver packages in the driver store.

The following table lists the Pnputil.exe command-line syntax.

:::row:::
  :::column:::
    **Command line**
  :::column-end:::
  :::column:::
    **Details**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    pnputil.exe /add-driver d:\\usbcam\\USBCAM.inf
  :::column-end:::
  :::column:::
    Adds a package that USBCAM.inf specifies.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    pnputil.exe /add-driver c:\\drivers\*.inf
  :::column-end:::
  :::column:::
    Adds all packages in C:\\drivers.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    pnputil.exe /add-driver a:\\usbcam\\USBCAM.inf /install
  :::column-end:::
  :::column:::
    Adds and installs a driver package.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    pnputil.exe /enum-drivers
  :::column-end:::
  :::column:::
    Lists all non-Microsoft packages.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    pnputil.exe /delete-driver oem0.inf
  :::column-end:::
  :::column:::
    Deletes package oem0.inf.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    pnputil.exe /delete-driver oem0.inf /force
  :::column-end:::
  :::column:::
    Forces deletion of package oem0.inf.
  :::column-end:::
:::row-end:::


> [!NOTE]
> You also can distribute drivers by adding them to the operating system images that your organization uses. To do this, use the DISM.exe tool to mount the image, inject the driver package, and effect the changes.
