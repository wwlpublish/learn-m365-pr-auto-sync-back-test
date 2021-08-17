![download icon](../media/download-icon.png)

All current versions of Office use the same Click-to-Run packaging and are installed and configured using the same tools and processes, including Office 2019 volume licensing editions: Office 2019 Professional Plus, and Office 2019 Standard.

## Office Deployment Tool for Click-to-Run

At the foundation, Click-to-Run packages use XML files to configure install-time settings and a setup.exe command line bootstrapper to run the installation. These are the core components of the **Office Deployment Tool**.

The setup.exe in the Office Deployment Tool allows you to:

- **Download** Office installation files for Microsoft 365 and Office 2019 desktop apps for Windows. The configuration XML details what tool to use to download the files and where to save those files. Here's the syntax:

    `setup.exe /download [Path]\download.xml`

- **Configure** and install Office on Windows devices using settings specified in the configuration XML, such as products, update channel, and languages. Here's the syntax:

    `setup.exe /configure [Path]\configuration.xml`

- **Customize** an existing Office installation on a Windows device. This mode applies only the application settings you specify in the configuration XML without changing any other deployment settings. Here's the syntax:

    `setup.exe /customize [Path]\settings.xml`

The configuration XML lets you configure dozens of settings when downloading and configuring Office. For example, you can define which products and languages to install, how to update those products, and whether or not to display the installation experience to your users. You can get a complete list of configuration options under the **Learn more** link below.

## Office Customization Tool

You can use the **Office Customization Tool** to create and modify configuration XML files using a web-based interface found within the Office 365 Client Configuration Service. Use the Office Customization Tool with the setup.exe from the Office Deployment Tool to deploy Office packages to a small number of systems. You can also use it instead of Configuration Manager if your organization doesn't use Configuration Manager.

Since release 1806, Configuration Manager includes an integrated experience with the Office Customization tool that uses the same web experience as part of the **Office 365 Installer** application package creation process.

As part of the Office 365 Installer in Configuration Manager, the wizard downloads the up-to-date setup.exe as needed from the Office Deployment Tool, creates the configuration XML file, and downloads Office installation files to your defined package folder location.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Office 365 Client Configuration Service](https://config.office.com)
- [Overview of the Office Deployment Tool and configuration options](https://aka.ms/odt)
