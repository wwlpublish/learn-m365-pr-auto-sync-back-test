You’re helping Contoso determine if they should deploy their applications using MSIX app attach technology. Before delving into MSIX app attach, you first explore the purpose and benefits of MSIX, MSIX packaging, and the MSIX Packaging tool.

## Purpose and benefits of MSIX

MSIX is a Windows app package format that provides a modern packaging experience to all Windows apps.

You can prepare your application in MSIX package format, which uses container technology to improve application install and uninstall fidelity. All MSIX apps write to their own registry and application data folder, and through the operating system, can read the global registry.

The benefits of MSIX include:

- Predictable and secure deployment. MSIX apps use container technology that isolates the app from the rest of the operating system for security.
- Clean removal. When you remove MSIX apps, you remove all application data. There is no remaining data in the registry or in the file system of the operating system.
- Single instance storage. MSIX app attach uses one instance of the MSIX application to deliver to all hosts without consuming extra space.
- Tampering. After an MSIX package has been expanded into an MSIX image, the latter is read-only and locked down for modification by the operating system.

> [!TIP]

> With MSIX, you can package and distribute Win32 applications using Microsoft Store.

## What’s inside an MSIX package?

Applications packaged in MSIX format are installed in the **c:\Program Files\WindowsApps** folder. Each package folder contains several standardized files that are described in the following table.

| File              | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
|App payload|Contains the app code files and assets.|
|AppxBlockMap.xml|Contains a verified  and secure list of all the files within the package.|
| AppxManifest.xml|Drives the installation by configuring association with files, and contains the identity of the package and their dependencies. |
| AppxSignature.p7x|Contains the signature of the package that must be trusted by the operating system before the app is installed.|

>[!TIP]

>To extract the contents of the MSIX package, change the **.msix** file extension to **.zip**, then extract the files using File Explorer.

## MSIX Containers

Apps prepared in MSIX format run in a lightweight container. An MSIX app writes to its own virtual registry and application data folder, and all MSIX app processes run inside that container.

## Creating an MSIX package

You can create an MSIX package using one of two methods:

- Repackaging existing Win32 installers
- Generating MSIX from source code

## MSIX Packaging tool

You can use the MSIX Packaging tool to create an MSIX application package from any of the following installers:

- MSI
- EXE
- ClickOnce
- App-V
- Script
- Manual installation

You can get access to the MSIX packaging tool from either the Microsoft Store or Hyper-V quick start.

You can use either an interactive UI or a command line to convert an existing package to MSIX package format. It’s important that prior to running the MSIX Packaging tool, you:

- Use a supported  Windows 10 version, minimum 1809.
- Work from a clean computer, without additional services and applications running on the computer.
- Prepare the environment for conversion ensuring it’s similar to the one that will host the newly created MSIX package.
- Ensure that the architecture on the computer used for conversion is the same as the computer that will deploy the application.
- Use a virtual machine with checkpoints, so you can easily test and revert the changes for every modification of the package.
- Understand the dependencies of the applications to properly prepare the MSIX package.

>[!NOTE]

> Starting with Windows 10 Fall Creators Update (Windows 10 version 1709), Microsoft provides a [**Hyper-V Quick Create**](https://docs.microsoft.com/windows/msix/packaging-tool/quick-create-vm) virtual environment on Hyper-V that you can use for MSIX packaging projects.

When you run the MSIX Packaging tool on the clean computer, you’ll be prompted to choose one of the following three options:

- Application package. Use this option to create an MSIX package either from existing installers or through manual installation of the application payload.
- Modification package. Use this option to modify existing MSIX packages. This option might require you to go through the initial packaging steps.
- Package editor. Use this option to make changes to the existing package without running the installers again. For example, you can edit the manifest of the package.

:::image type="content" source="../media/02-Screenshot-MSIX-packaging-tool.PNG" alt-text="Screenshot of MSIX packaging tool." border="true":::

> [!NOTE]

> MSIX app attach does not support modification package.

In the MSIX packaging tool (MPT), use the following steps to repackage an application to MSIX.

1. MPT prepares the computer. In this step, the MSIX package driver is installed and Windows Update is disabled.

2. Choose the installer you want to package. This step varies based on the installers that you choose to convert. The last part of this step is to sign the package using one of the following options:

 - Sign with Device Guard signing
 - Sign with a certificate (.pfx)
 - Specify a .cer file. This does not sign the package but matches the subject of the certificate that will be used for signing.

4. Detail the package information. The MSIX package tool will attempt to autofill information about the app based on the installer that is used. You can customize the input with your own values as needed.

5. Run installation. The tool starts to monitor the installation phase and capture all installation options. If the installer requires restart, you can restart the computer and continue the process of conversion.

6. Manage first launch tasks. This page captures the first run experience launch by selecting **run**.

7. Review the services report. This step is used for installers that register service on the computers. If there are services that are supported, they will be listed in the **Included** table, and services that are not supported will appear in **Excluded** table.

8. Create package. This is the final phase of the process, where you provide a location to save the MSIX package.

You can automate the process of repacking the applications with the command-line interface. The following examples define how to use the MSIX Packaging tool from the command line:

```
 MsixPackagingTool.exe create-package --template c:\users\documents\ConversionTemplate.xml -v
 MSIXPackagingTool.exe create-package --template c:\users\documents\ConversionTemplate.xml --virtualMachinePassword pswd112893
```

>[!NOTE]

> You can find sample PowerShell and Bash scripts that demonstrate how to automate the process of packaging, signing, managing, and distributing MSIX packages in the [scripts](https://github.com/microsoft/MSIX-Toolkit/tree/master/Scripts) folder of the MSIX Toolkit.

>[!NOTE]

> The following versions of Windows support MSIX:

> - Windows 10, version 1709 and later

> - Windows Server 2019 LTSC and later
