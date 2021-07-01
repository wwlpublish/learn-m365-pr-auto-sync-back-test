You're helping Contoso determine if it should deploy its applications by using MSIX app attach technology. Before delving into MSIX app attach, you first explore the purpose and benefits of MSIX, MSIX packaging, and the MSIX Packaging Tool.

## Purpose and benefits of MSIX

MSIX is a Windows app package format that provides a modern packaging experience to all Windows apps.

You can prepare your application in MSIX package format, which uses container technology to improve the fidelity of application installation and uninstallation. All MSIX apps write to their own registry and application data folder, and they can read the global registry through the operating system.

The benefits of MSIX include:

- Predictable and secure deployment. MSIX apps use container technology that isolates the app from the rest of the operating system for security.
- Clean removal. When you remove MSIX apps, you remove all application data. There is no remaining data in the registry or in the file system of the operating system.
- Single-instance storage. MSIX app attach uses one instance of the MSIX application to deliver to all hosts without consuming extra space.
- Resistance to tampering. After an MSIX package has been expanded into an MSIX image, the latter is read-only and locked down for modification by the operating system.

> [!TIP]
> With MSIX, you can package and distribute Win32 applications by using the Microsoft Store.

## What's inside an MSIX package?

Applications packaged in MSIX format are installed in the **c:\Program Files\WindowsApps** folder. Each package folder contains these standardized files:

| File              | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
|App payload|Contains the app code files and assets.|
|AppxBlockMap.xml|Contains a verified  and secure list of all the files within the package.|
| AppxManifest.xml|Drives the installation by configuring association with files, and contains the identity of the package and their dependencies. |
| AppxSignature.p7x|Contains the signature of the package that the operating system must trust before the app is installed.|

>[!TIP]
>To extract the contents of the MSIX package, change the **.msix** file extension to **.zip**, and then extract the files by using File Explorer.

## MSIX containers

Apps prepared in MSIX format run in a lightweight container. An MSIX app writes to its own virtual registry and application data folder. All MSIX app processes run inside that container.

## Creating an MSIX package

You can create an MSIX package by using one of two methods:

- Repackaging existing Win32 installers
- Generating MSIX from source code

## MSIX Packaging Tool

You can use the MSIX Packaging Tool to create an MSIX application package from any of the following installers:

- MSI
- EXE
- ClickOnce
- App-V
- Script
- Manual installation

You can get access to the MSIX Packaging Tool from either the Microsoft Store or the Hyper-V quickstart.

You can use either an interactive UI or a command line to convert an existing package to MSIX package format. It's important that prior to running the MSIX Packaging Tool, you:

- Use a supported Windows 10 version, minimum 1809.
- Work from a clean computer, without additional services and applications running on it.
- Prepare the environment for conversion, ensuring that it's similar to the one that will host the newly created MSIX package.
- Ensure that the architecture on the computer used for conversion is the same as the computer that will deploy the application.
- Use a virtual machine with checkpoints, so you can easily test and revert the changes for every modification of the package.
- Understand the dependencies of the applications to properly prepare the MSIX package.

>[!NOTE]
> Starting with Windows 10 Fall Creators Update (Windows 10 version 1709), Microsoft provides a [Hyper-V Quick Create](/windows/msix/packaging-tool/quick-create-vm) virtual environment that you can use for MSIX packaging projects.

When you run the MSIX Packaging Tool on the clean computer, you'll be prompted to choose one of the following three options:

- **Application package**. Use this option to create an MSIX package either from existing installers or through manual installation of the application payload.
- **Modification package**. Use this option to modify existing MSIX packages. This option might require you to go through the initial packaging steps.
- **Package editor**. Use this option to make changes to the existing package without running the installers again. For example, you can edit the manifest of the package.

:::image type="content" source="../media/02-screenshot-msix-packaging-tool.png" alt-text="Screenshot of the M S I X Packaging Tool." border="true":::

> [!NOTE]
> MSIX app attach does not support a modification package.

In the MSIX Packaging Tool, use the following steps to repackage an application to MSIX:

1. The MSIX Packaging Tool prepares the computer. In this step, the MSIX package driver is installed and Windows Update is disabled.

1. Choose the installer that you want to package. This step varies based on the installers that you choose to convert. The last part of this step is to sign the package by using one of the following options:

    - Sign with Device Guard signing.
    - Sign with a certificate (.pfx).
    - Specify a .cer file. This option doesn't sign the package but matches the subject of the certificate that will be used for signing.

1. Detail the package information. The MSIX Packaging Tool tries to autofill information about the app based on the installer that's used. You can customize the input with your own values as needed.

1. Run the installation. The tool starts to monitor the installation phase and capture all installation options. If the installer requires a restart, you can restart the computer and continue the process of conversion.

1. Manage the tasks that determine the user experience the first time you run the tool.

1. Review the services report. This step is used for installers that register services on the computers. Supported services are listed in the **Included** table. Services that aren't supported appear in the **Excluded** table.

1. Create a package. This is the final phase of the process, where you provide a location to save the MSIX package.

You can automate the process of repacking the applications by using the command-line interface. The following examples define how to use the MSIX Packaging Tool from the command line:

```PowerShell
 MsixPackagingTool.exe create-package --template c:\users\documents\ConversionTemplate.xml -v
 MSIXPackagingTool.exe create-package --template c:\users\documents\ConversionTemplate.xml --virtualMachinePassword pswd112893
```

>[!NOTE]
> You can find sample PowerShell and Bash scripts that demonstrate how to automate the process of packaging, signing, managing, and distributing MSIX packages in the [scripts](https://github.com/microsoft/MSIX-Toolkit/tree/master/Scripts) folder of the MSIX Toolkit.
