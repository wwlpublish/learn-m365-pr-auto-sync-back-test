You can download the Office Deployment Tool (ODT) from the Microsoft 365 admin center, or directly from the Microsoft Download Center. The ODT is used to run the following tasks:

 *  Download Office source files
 *  Install or remove Click-to-Run or customize installations
 *  Apply software update policies

The Office Deployment Tool supports the following command-line switches:

 *  **/download \[path to configuration.xml\]** to specify the download
 *  **/configure \[path to configuration.xml\]** to specify the Office source file location
 *  **/packager** to prepare Office source files so that you can use Click-to-Run in an App-V infrastructure

### Using the Office Deployment Tool

The Office Deployment Tool is used in the following steps to configure Microsoft 365 Apps for enterprise:

1.  Edit the Configuration.xml file to specify the Microsoft 365 software to download, such as Microsoft 365 Apps for enterprise or Visio, and the shared location to use.
2.  Use the Office Deployment Tool with the download option to place source files in a software distribution infrastructure; for example, setup.exe /download \\LON-CL1\\Office16\\Configuration.xml.
3.  Use the Office Deployment Tool with the configure option to deploy the Office Deployment Tool and the configuration file to clients; for example, setup.exe /configure \\LON-CL1\\Office16\\Configuration.xml.
4.  When a client computer executes the Office Deployment Tool, it reads the configuration file and then streams Click-to-Run from the specified location; for example, where the source files downloaded internally.

### Customizing the configuration.xml file using the Office Customization Tool

To customize the Microsoft 365 Apps for enterprise deployment in your organization, you can modify the configuration.xml file to specify various settings that are applicable to your organization. The Office Customization Tool creates the configuration files that are used to deploy Office in large organizations. These configuration files give you more control over an Office installation. You can define which applications and languages are installed, how those applications should be updated, and application preferences. After creating the configuration files, you can use them with the Office Deployment Tool to deploy a customized version of Office.

To customize the configuration.xml file, go to the Office Customization Tool and choose the products, languages, and application preferences you want to configure. For example, the configuration file can be modified to download the 64-bit English version of Microsoft 365 Apps for enterprise. Or, the configuration file can be modified to install the 64-bit English and German version of Office without Access and Publisher and with the EULA automatically accepted. When you're done, the configuration file can be exported and then used with the Office Deployment Tool to deploy Office in your organization.<br>

The following graphic shows how the Office Customization Tool can run in any browser to create a custom installation package, which can then be deployed to workstations.

:::image type="content" source="../media/m365-deployment-using-odt-dc68e320.jpg" alt-text="graphic shows that the Office Customization Tool can run in any browser to create a custom installation package":::


The following example displays a sample of the Microsoft 365 client configuration file.

:::image type="content" source="../media/sample-m365-config-file-bb10683c.png" alt-text="Screen shot of a sample Microsoft 365 configuration file":::


The following example displays this same configuration file that has been customized. The channel has been changed to Broad, which is a semiannual update. Japanese and English have been added as the available product languages, and Visio has been added as part of the deployment.

```
<Add SourcePath="\\Server\Share"

    OfficeClientEdition="32"

    Channel="Broad"

    Version="16.0.8201.2193"

    ForceUpgrade="FALSE">

    <Product ID="O365ProPlusRetail">

    <Language ID="en-us" />

    <Language ID="ja-jp" />

    </Product&gt;

    <Product ID="VisioProRetail">;

    <Language ID="en-us" />

    <Language ID="ja-jp" />

    </Product>

    </Add>
```

By specifying different settings in the configuration.xml file, users can be pointed to an internal file share location for downloading updates for Microsoft 365 Apps for enterprise. You can also exclude some of the Office applications. For example, if you don’t want your users to create Microsoft Access databases, Microsoft Access can be removed from the deployment in your organization.

**Additional reading.** For a complete reference to the settings that are available in the configuration.xml file, see [Configuration options for the Office Deployment Tool](https://go.microsoft.com/fwlink/?linkid=831357?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”