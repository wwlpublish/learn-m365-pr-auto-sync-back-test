To implement Microsoft Defender for Identity, an organization must create a Defender for Identity instance (previously called a workspace). An administrator must create the instance in the Defender for identity portal. To create the Defender for Identity instance, the administrator must first satisfy the following prerequisites:<br>

 -  The Administrator will need a Microsoft Defender for Identity license. This can either be an individual license or part of a licensing plan, such as an Office 365 E5 license. For more information, see [Defender for Identity licensing guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#azure-advanced-threat-protection?azure-portal=true).
 -  The Administrator must be assigned to either a global administrator role or a security administrator role on the tenant to access the Defender for identity portal.
 -  The domain controller (s) you intend to install Defender for Identity sensors on must have internet connectivity to the Defender for Identity Cloud Service. The Defender for Identity sensor supports the use of a proxy. For more information on proxy configuration, see [Configuring a proxy for Defender for Identity](/defender-for-identity/configure-proxy?azure-portal=true).
 -  One of the following directory services accounts must have read access to all objects in the monitored domains:
    
     -  **A standard AD user account and password.** Required for sensors running Windows Server 2008 R2 SP1.
     -  **A group Managed Service Account (gMSA).** Requires Windows Server 2012 or above. All sensors must have permissions to retrieve the gMSA account's password.

> [!NOTE]
> If you attempt to install the Defender for Identity sensor on a machine configured with a NIC Teaming adapter, you'll receive an installation error. If you want to install the Defender for Identity sensor on a machine configured with NIC teaming, see [Defender for Identity sensor NIC teaming issue](https://docs.microsoft.com/defender-for-identity/troubleshooting-known-issues#nic-teaming?azure-portal=true).

**Additional reading.** For more information, see the [Defender for Identity pre-requisites](/defender-for-identity/prerequisites?azure-portal=true).

### Creating an instance

To create a Microsoft Defender for Identity instance in the Defender for identity portal, the administrator must complete the following steps:

1.  Go to [the Defender for Identity portal](https://portal.atp.azure.com/?azure-portal=true).
2.  Sign in with your Microsoft 365 administrator user account.
3.  On the **Welcome** page, select **Create**.<br><br>:::image type="content" source="../media/defender-for-identity-wizard-create-step-b2f70fc6.png" alt-text="screenshot of Welcome page with the Create button in the defender for identity wizard":::
    
4.  The Defender for Identity instance that's created is automatically named after the Azure AD initial domain name. The Defender for Identity instance is created in the data center located closest to Azure AD.<br>
5.  Select the **Configuration** (gear) icon in the left-hand navigation pane, and then select **Manage role groups**. Use the [Azure AD Admin Center](/azure/active-directory/active-directory-assign-admin-roles-azure-portal?azure-portal=true) link to manage the role groups.<br><br>:::image type="content" source="../media/defender-for-identity-wizard-manage-role-group-step-90063700.png" alt-text="screenshot of the Manage Role Group step in the defender for identity wizard":::
    

    > [!NOTE]
    > Previously deleted Defender for Identity instances don't appear in the Defender for Identity portal. For more information on Defender for Identity data retention, see [Defender for Identity data security and privacy](/defender-for-identity/privacy-compliance?azure-portal=true).

6.  Add your gMSA credentials to connect the Active Directory forest to the Microsoft Defender for identity portal. :::image type="content" source="../media/defender-for-identity-wizard-gmsa-credentials-step-358fa9bc.png" alt-text="screenshot of GMSA credentials step in the defender for identity wizard":::
    

    > [!NOTE]
    > It's recommended to create a new gMSA account and security group containing all domain controllers with sensors with permissions to retrieve the gMSA account's password.

7.  In the left-hand column, select **Sensors**, and then select the **Download** button and save the package locally.<br>:::image type="content" source="../media/defender-for-identity-wizard-select-sensor-step-d1b33789.png" alt-text="screenshot of the Select Sensor step in the defender for identity wizard":::
    
8.  On the **Sensors** page (see prior screenshot image), select the **copy file** icon that appears to the right of the **Access** **key** field. The access key is required for the Defender for Identity sensor to connect to your Defender for Identity instance. The access key is a one-time-password for sensor deployment, after which all communication is performed using certificates for authentication and TLS encryption.

    > [!NOTE]
    > Select the **Regenerate** button if you ever need to regenerate a new access key. Regenerating a new key won't affect any previously deployed sensors, because it's only used for initial registration of the sensor.

9.  Copy the package to the dedicated server or domain controller onto which you're installing the Defender for Identity sensor. Alternatively, you can open the Defender for Identity portal from the dedicated server or domain controller and skip this step.
10. Verify the machine has connectivity to the relevant [Defender for Identity cloud service](https://docs.microsoft.com/defender-for-identity/configure-proxy#enable-access-to-azure-atp-service-urls-in-the-proxy-server?azure-portal=true) endpoint(s).
11. Extract the installation files from the zip file. Installing directly from the zip file will fail.
12. Run **Azure ATP sensor setup.exe** with elevated privileges (**Run as administrator**) and follow the setup wizard.
13. On the **Welcome** page, select your language and select **Next**.
14. The installation wizard automatically checks if the server is a domain controller or a dedicated server to determine which sensor to install:
    
     -  If it's a domain controller, the Defender for Identity sensor is installed.
     -  If it's a dedicated server, the Defender for Identity standalone sensor is installed.
     -  Select **Next.**
15. Under **Configure the sensor**, enter the installation path and the access key that you copied from the previous step, based on your environment:
    
     -  **Installation path.** The location where the Defender for Identity sensor is installed. By default, the path is %programfiles%\\Azure Advanced Threat Protection sensor. Leave the default value.
     -  **Access key.** Retrieved from the Defender for Identity portal in the previous step. :::image type="content" source="../media/defender-for-identity-wizard-configure-sensor-step-b328232f.png" alt-text="screenshot of the Configure Sensor step in the Defender for Identity wizard":::
        
16. Select **Install**.