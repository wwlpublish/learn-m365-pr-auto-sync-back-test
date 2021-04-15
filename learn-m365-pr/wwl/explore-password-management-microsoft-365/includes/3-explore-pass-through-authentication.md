Users typically prefer to maintain one set of login credentials for both cloud and on-premises resources. The common sentiment is the fewer usernames and passwords to remember, the better. This user preference can be achieved by using Azure AD Connect with password hash synchronization.

Some organizations prefer to have all authentication done on-premises. In doing so, an organization must deploy an AD FS service and configure your Azure AD tenant in federated mode. Each authentication request for resources on-premises or in a cloud will then be directed to the AD FS server that's deployed locally.

Until recently, deployment and management of the locally deployed AD FS infrastructure was often too demanding and too complex for some organizations. However, a recent update to Azure AD Connect provided a new option to address this scenario. This new feature is called Azure AD pass-through authentication (PTA).

Azure AD pass-through authentication helps ensure that password validation for services that rely on Azure AD is always performed against an on-premises Active Directory. If PTA fails, automatic failover to password hash synchronization is performed if it’s enabled. Unlike the AD FS solution, PTA is easy to implement and maintain.

Azure AD pass-through authentication is configured by using Azure AD Connect, and it works by using an on-premises agent that listens for external password validation requests. You can deploy this agent to one or more servers to provide high availability. There's no need to deploy this server to the perimeter network, as all communication is outbound only. A server that runs the agent for pass-through authentication should be joined to the Active Directory domain where users are located.

**Additional reading.** For more information, see the following article on [User sign-in with Azure Active Directory Pass-through Authentication](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-how-it-works?azure-portal=true).

:::image type="content" source="../media/data-flow-using-pta-786afe2d.jpg" alt-text="graphic showing data flow with passthrough authentication":::


When a user accesses a cloud service that relies on Azure AD, the user is presented with an Azure AD login page. After a user enters their credentials into the Azure AD login page, the Azure AD service checks if the connector for pass-through authentication is configured for the user’s domain. If it is, credentials are placed on the connector queue for validation. A connector agent deployed on-premises then retrieves the user's credentials and authenticates them against the locally deployed Active Directory. The Active Directory's response is returned to the connector, which in turn provides this response to Azure AD.

To enable Azure AD pass-through authentication, you must:

 *  run the **Azure AD Connect Setup Wizard.**
 *  select the **Pass-through authentication** option on the **User Sign-in** page.

The first connector for pass-through authentication is deployed on the same server where Azure AD Connect runs. It's recommended that you deploy an extra connector on at least one more server to achieve load balancing between the set of available connectors for both high availability and redundancy. The Azure AD Application Proxy Connector can be downloaded as a separate installation for other servers.

All ports required by Azure AD pass-through authentication must be available. These ports are listed in the following table.

:::row:::
  :::column:::
    <p><b>Port</b></p>
  :::column-end:::
  :::column:::
    <p><b>Description</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>80</p>
  :::column-end:::
  :::column:::
    <p>Enables outbound HTTP traffic for security validation such as SSL certificate revocation lists.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>443</p>
  :::column-end:::
  :::column:::
    <p>Enables user authentication against Azure AD.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>8080/443</p>
  :::column-end:::
  :::column:::
    <p>Enables the Connector bootstrap sequence and Connector automatic update.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>9090</p>
  :::column-end:::
  :::column:::
    <p>Enables Connector registration (required only for the Connector registration process).</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>9091</p>
  :::column-end:::
  :::column:::
    <p>Enables Connector trust certificate automatic renewal.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>9352, 5671</p>
  :::column-end:::
  :::column:::
    <p>Enables communication between the Connector and the Azure AD service for incoming requests.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>9350</p>
  :::column-end:::
  :::column:::
    <p>[Optional] Enables better performance for incoming requests.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>10100–10120</p>
  :::column-end:::
  :::column:::
    <p>Enables responses from the connector back to Azure AD.</p>
  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see [User sign-in with Azure AD Pass-through Authentication](https://aka.ms/lusqtt?azure-portal=true).
