The Office Deployment Tool (ODT) can be downloaded from the Microsoft 365 admin center, or directly from the Microsoft Download Center. The ODT is used to run the following tasks:

 -  Download Office source files.
 -  Install or remove Click-to-Run or customize installations.
 -  Apply software update policies.

The Office Deployment Tool supports the following command-line switches:

 -  **/download \[path to configuration.xml\]** to specify the download.
 -  **/configure \[path to configuration.xml\]** to specify the Office source file location.
 -  **/packager** to prepare Office source files so that you can use Click-to-Run in an App-V infrastructure.

### Using the Office Deployment Tool

The Office Deployment Tool is used in the following steps to configure Microsoft 365 Apps for enterprise:

1.  Edit the Configuration.xml file to specify the Microsoft 365 software to download, such as Microsoft 365 Apps for enterprise or Visio, and the shared location to use.
2.  Use the Office Deployment Tool with the download option to place source files in a software distribution infrastructure; for example, setup.exe /download \\LON-CL1\\Office16\\Configuration.xml.
3.  Use the Office Deployment Tool with the configure option to deploy the Office Deployment Tool and the configuration file to clients; for example, setup.exe /configure \\LON-CL1\\Office16\\Configuration.xml.
4.  When a client computer executes the Office Deployment Tool, it reads the configuration file and then streams Click-to-Run from the specified location; for example, where the source files downloaded internally.

### Customizing the configuration.xml file using the Office Customization Tool

To customize an organization's Microsoft 365 Apps for enterprise deployment, the configuration.xml file should be modified to specify various settings that are applicable to the organization. The Office Customization Tool creates the configuration files that are used to deploy Office in large organizations. These configuration files provide organizations with greater control over an Office installation. They can define:

 -  which applications and languages are installed.
 -  how those applications should be updated.
 -  application preferences.

After creating the configuration files, you can use them with the Office Deployment Tool to deploy a customized version of Office.

To customize the configuration.xml file, go to the Office Customization Tool and choose the products, languages, and application preferences required by the organization. For example, the configuration file can be modified to download the 64-bit English version of Microsoft 365 Apps for enterprise. Or, the configuration file can be modified to install the 64-bit English and German version of Office without Microsoft Access and Publisher and with the EULA automatically accepted. Once the configuration file has been updated, it can be exported and then used with the Office Deployment Tool to deploy Office in the organization.<br>

The following graphic shows how the Office Customization Tool can run in any browser to create a custom installation package, which can then be deployed to workstations.

:::image type="content" source="../media/m365-deployment-using-odt-dc68e320.jpg" alt-text="graphic shows that the Office Customization Tool can run in any browser to create a custom installation package":::


The following example displays a sample of the Microsoft 365 client configuration file.

:::image type="content" source="../media/sample-m365-config-file-bb10683c.png" alt-text="Screenshot of a sample Microsoft 365 configuration file":::


The following example displays this same configuration file that has been customized. The channel has been changed to Broad, which is a semiannual update. Japanese and English have been added as the available product languages, and Visio has been added as part of the deployment.

```
&lt;Add SourcePath="\\Server\Share"

    OfficeClientEdition="32"

    Channel="Broad"

    Version="16.0.8201.2193"

    ForceUpgrade="FALSE"&gt;

    &lt;Product ID="O365ProPlusRetail"&gt;

    &lt;Language ID="en-us" /&gt;

    &lt;Language ID="ja-jp" /&gt;

    &lt;/Product&gt;

    &lt;Product ID="VisioProRetail"&gt;

    &lt;Language ID="en-us" /&gt;

    &lt;Language ID="ja-jp" /&gt;

    &lt;/Product&gt;

    &lt;/Add&gt;
```

By specifying different settings in the configuration.xml file, users can be pointed to an internal file share location for downloading updates for Microsoft 365 Apps for enterprise. The configuration.xml file can also be used to exclude certain Office applications. For example, if an organization doesn't want its users to create Microsoft Access databases, the configuration.xml file can indicate that Microsoft Access should be removed from the deployment.

**Additional reading.** For a complete reference to the settings that are available in the configuration.xml file, see [Configuration options for the Office Deployment Tool](https://docs.microsoft.com/deployoffice/office-deployment-tool-configuration-options#:~:text=Example%20of%20a%20standard%20configuration%20file%20%20,365%20App%20...%20%204%20more%20rows%20?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”