Connectors can be considered as proxy wrappers around the APIs provided by services that interact with Power Automate and Power Apps. It's the connectors that enable Power Automate and Power Apps to easily interact with the service.

Connectors can be either public or custom. There are currently over 200+ public connectors that can be used by all organizations. Examples of public connectors are Microsoft 365, Common Data Service, Twitter, and Dropbox. Custom connectors are defined in the context of an environment and are only available to apps and flows within that environment. Connectors make triggers and actions available that can be used by the apps and flows. Triggers are used by flows to start the execution of the workflow. Actions are used by apps and flows to complete a defined set of actions.

Microsoft Power Platform supports connectors for popular services and on-premises data sources. Microsoft Power Platform also provides the option to build custom connectors, which enable an app or flow to call a publicly available API, or a custom API hosted by a cloud provider. Custom connectors are defined in the context of an environment and are only available within that environment.

With Microsoft Power Platform, applications and workflows aren't limited to a single connection. Multiple data connections are supported, allowing users to bring data together from many platforms into a single automation. In the context of Power Automate, each connector offers a set of operations classified as 'Triggers' and 'Actions'. Triggers determine what starts the flows, while actions determine what happens.

Some of the more commonly used triggers include when an item is:

 -  created
 -  created or modified
 -  deleted

Some of the more commonly used actions include:

 -  Add an attachment.
 -  Copy a file.
 -  Check in a file.
 -  Check out a file.

**Additional reading.** For more information on connectors, see the [connector index](/connectors/index).

### Sharing flows with connectors

Flows can be shared with other users either as co-owners or run-only users. When a user adds another user or group as an owner of a flow, those users have full access to all the connections used in the flow. If they run the flow, it will take the action in the context of the user signed into the connection. Because they're co-owners of the flow, they can also modify the flow using the connections that already exist. They may also change the sign-in on the connection, although they're not required to do so. Co-owners are limited to using the connection with that flow. They can't create a new flow and use the same connection.

### On-premises data sources

Connections to on-premises data sources require the use of an on-premises data gateway. The on-premises data gateway acts as a bridge to provide quick and secure data transfer between on-premises data and Microsoft cloud services, such as Power Apps, Power Automate, Power BI, and more. By using a gateway, organizations can keep databases and other data sources on their on-premises networks, yet securely use that on-premises data in cloud services.

An on-premises data gateway enables multiple users to connect to multiple on-premises data sources. A single installation of an on-premises data gateway can also be used with all supported services.

### Data source authentication

When an app or flow creates a connection to a data source, the connector typically requires some form of authentication. The specific connection’s credentials and associated service entitlements determine permissions when apps use the connector. Depending on the type of authentication used, some connectors are shared automatically when a user shares the app. Others require that when an app is shared with a user, the user must create their own connections.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”