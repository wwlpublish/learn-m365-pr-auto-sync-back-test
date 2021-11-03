When troubleshooting Microsoft Defender for Cloud Apps, it's essential to consider the troubleshooting areas identified in the following table.

:::row:::
  :::column:::
    

**Troubleshooting area**


  :::column-end:::
  :::column:::
    

**What to do**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Service status


  :::column-end:::
  :::column:::
    

You can check the current Microsoft Defender for Cloud Apps service status by going to the [Microsoft Defender for Cloud Apps site](https://status.cloudappsecurity.com/?azure-portal=true) or directly from within your Defender for Cloud Apps portal by selecting **Help > System status**.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Cloud Discovery


  :::column-end:::
  :::column:::
    

Investigate error codes in the following areas:

 -  Log parsing errors
 -  Log collector errors
 -  Discovery dashboard errors

A detailed list of error codes and how to resolve them is available in the following article on [Troubleshooting Cloud Discovery](/cloud-app-security/troubleshooting-cloud-discovery?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

API Connectors using error messages


  :::column-end:::
  :::column:::
    

App connector errors can be seen in the app connector dialog after attempting to connect a cloud app using the API App connector.


A detailed list of error codes and how to resolve them is available in the following article on [Troubleshooting API Connectors using Error Messages](/cloud-app-security/troubleshooting-api-connectors-using-error-messages?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Content inspection


  :::column-end:::
  :::column:::
    

Troubleshooting content inspection, you need to consider the Content inspection status and take appropriate action.


A detailed list of content inspection status codes and how to resolve them is available in the following article on [Troubleshooting Content Inspection](/cloud-app-security/troubleshooting-content-inspection?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Security Information Event and Management (SIEM) integration


  :::column-end:::
  :::column:::
    

You can integrate Microsoft Defender for Cloud Apps with your generic SIEM server to enable centralized monitoring of alerts and activities from connected apps. The Microsoft Defender for Cloud Apps SIEM agent runs on your server and pulls alerts and activities from Microsoft Defender for Cloud Apps and streams them into the SIEM server.

Verify the status of the SIEM agent in the Microsoft Defender for Cloud Apps portal isn't **Connection error** or **Disconnected.** Also ensure there are no agent notifications. The status will display **Connection error** if the connection is down for more than two hours. It will display as **Disconnected** if the connection is down for over 12 hours.


For more information, see [Troubleshooting the SIEM Agent](/cloud-app-security/troubleshooting-siem?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Policies


  :::column-end:::
  :::column:::
    

To troubleshoot Microsoft Defender for Cloud Apps policies, you must consider the error code and find an appropriate resolution. All relevant error codes and resolutions are available in the following article on [Troubleshooting Microsoft Defender for Cloud Apps policies](/cloud-app-security/troubleshoot-policies?azure-portal=true).


  :::column-end:::
:::row-end:::
