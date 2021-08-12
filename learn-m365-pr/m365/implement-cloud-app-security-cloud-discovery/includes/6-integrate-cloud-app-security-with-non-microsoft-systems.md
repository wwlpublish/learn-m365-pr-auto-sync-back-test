It's important to be able to integrate Cloud App Security with third-party proxies and firewalls. This helps to ensure that you can properly implement Cloud Discovery throughout your organization.

## Integrate with Zscaler

Zscaler is a standalone cloud proxy device, which you can use to monitor your organization's network traffic. However, integration with Cloud App Security brings extra benefits, including:

- Use Zscaler to proxy traffic. This avoids the need to set up log collectors on network endpoints.
- Use Zscaler's app block capabilities. These capabilities are automatically applied on apps you mark as unsanctioned in Cloud App Security.
- Implement Cloud App Security risk scoring in Zscaler portal. You can review Cloud App Security's risk assessments for 200 popular cloud apps directly in the Zscaler portal.

### Deploy Zscaler integration

Before you deploy integration, ensure that you have:

- A valid Microsoft Cloud App Security license, or a valid Azure AD Premium P1 or P2 license
- A valid Zscaler Cloud 5.6 license
- An active Zscaler NSS subscription

Then use the following procedure to complete integration:

1. Complete the steps provided at the Zscaler website for integration with Cloud App Security: [Configuring a Microsoft Cloud App Security Integration](https://help.zscaler.com/zia/configuring-mcas-integration?azure-portal=true)
2. Open Cloud App Security and select **Settings**.
3. In the **Cloud Discovery** section, choose **Automatic log upload**.
4. On the Settings page, on the **Data sources** tab, select **Add data source**.
5. Enter the following information in the **Add data source** dialog box:

   - Name = NSS
   - Source = Zscaler QRadar LEEF
   - Receiver type = Syslog - UDP

6. Select **Add**.

## Integrate with iboss

iboss is a standalone secure cloud gateway that monitors your organization's traffic. You use iboss to set policies that block transactions. By integrating Cloud App Security with iboss, you can use iboss to proxy your traffic and send it to Cloud App Security. This approach eliminates the need for log collectors.

### Deploy iboss integration

Before you deploy integration, ensure that you have:

- A valid Microsoft Cloud App Security license
- A valid license for iboss cloud gateway (version 9.1.100.0 or newer)

The process is broadly the same as for Zscaler integration. First, create a new data source for Cloud App Security, and define the following properties:

- Name = iboss
- Source = iboss Secure Cloud Gateway
- Receiver type = Syslog - UDP

You'll also need to contact iboss support to learn how to configure iboss to send logs to Cloud App Security.

## Integrate with Corrata

Corrata is a local Mobile gateway and monitors network traffic from your users' mobile devices. By integrating Cloud App Security and Corrata, you can collect mobile device traffic without needing a log collector. You can then forward that data directly to Cloud App Security.

### Deploy Corrata integration

Before you deploy integration, ensure that you have:

- A valid license for Microsoft Cloud App Security
- A valid license for Corrata Cloud

Then use the following procedure:

1. In the Corrata portal, complete the steps provided at the Corrata website for integration with Cloud App Security: [Integrating Corrata with Microsoft Cloud App Security](https://corrata.com/microsoft-mcas-onboarding?azure-portal=true).
2. Open Cloud App Security and select **Settings**.
3. In the **Cloud Discovery** section, choose **Automatic log upload**.
4. On the Settings page, on the **Data sources** tab, select **Add data source**.
5. Enter the following information in the **Add data source** dialog box:

   - Name = Corrata
   - Source = Corrata
   - Receiver type = FTP

6. Select **Add**.

## Integrate with Menlo

Menlo Security is a standalone Secure Web Gateway. It can monitor your organization's traffic enabling you to set policies for blocking transactions. By integrating with Cloud App Security, you can avoid the need to create a log collector. Instead, collected data can be sent direct from Menlo to Cloud App Security. In addition, any apps you mark as unsanctioned in Cloud App Security are automatically blocked by Menlo Security.

### Deploy Menlo integration

Before you deploy integration, ensure that you have:

- A valid Microsoft Cloud App Security license, or a valid Azure AD Premium P1 or P2 license
- A valid license for Menlo Security

Then sign in to the Menlo admin portal and complete the steps documented at the Menlo Security website: [Admin portal](https://admin.menlosecurity.com/docs/guides/web_admin_settings_casb.html?highlight=microsoft).
