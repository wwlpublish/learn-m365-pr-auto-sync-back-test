It's important to be able to integrate Defender for Cloud Apps with third-party proxies and firewalls. This helps to ensure that you can properly implement Cloud Discovery throughout your organization.

## Integrate with Zscaler

Zscaler is a standalone cloud proxy device, which you can use to monitor your organization's network traffic. However, integration with Defender for Cloud Apps brings extra benefits, including:

- Use Zscaler to proxy traffic. This avoids the need to set up log collectors on network endpoints.
- Use Zscaler's app block capabilities. These capabilities are automatically applied on apps you mark as unsanctioned in Defender for Cloud Apps.
- Implement Defender for Cloud Apps risk scoring in Zscaler portal. You can review the Defender for Cloud Apps risk assessments for 200 popular cloud apps directly in the Zscaler portal.

### Deploy Zscaler integration

Before you deploy integration, ensure that you have:

- A valid Microsoft Defender for Cloud Apps license, or a valid Azure AD Premium P1 or P2 license
- A valid Zscaler Cloud 5.6 license
- An active Zscaler NSS subscription

Then use the following procedure to complete integration:

1. Complete the steps provided at the Zscaler website for integration with Defender for Cloud Apps: [Configuring a Microsoft Defender for Cloud Apps Integration](https://help.zscaler.com/zia/configuring-mcas-integration?azure-portal=true)
2. Open Defender for Cloud Apps and select **Settings**.
3. In the **Cloud Discovery** section, choose **Automatic log upload**.
4. On the Settings page, on the **Data sources** tab, select **Add data source**.
5. Enter the following information in the **Add data source** dialog box:

   - Name = NSS
   - Source = Zscaler QRadar LEEF
   - Receiver type = Syslog - UDP

6. Select **Add**.

## Integrate with iboss

iboss is a standalone secure cloud gateway that monitors your organization's traffic. You use iboss to set policies that block transactions. By integrating Defender for Cloud Apps with iboss, you can use iboss to proxy your traffic and send it to Defender for Cloud Apps. This approach eliminates the need for log collectors.

### Deploy iboss integration

Before you deploy integration, ensure that you have:

- A valid Microsoft Defender for Cloud Apps license
- A valid license for iboss cloud gateway (version 9.1.100.0 or newer)

The process is broadly the same as for Zscaler integration. First, create a new data source for Defender for Cloud Apps, and define the following properties:

- Name = iboss
- Source = iboss Secure Cloud Gateway
- Receiver type = Syslog - UDP

You'll also need to contact iboss support to learn how to configure iboss to send logs to Defender for Cloud Apps.

## Integrate with Corrata

Corrata is a local Mobile gateway and monitors network traffic from your users' mobile devices. By integrating Defender for Cloud Apps and Corrata, you can collect mobile device traffic without needing a log collector. You can then forward that data directly to Defender for Cloud Apps.

### Deploy Corrata integration

Before you deploy integration, ensure that you have:

- A valid license for Microsoft Defender for Cloud Apps
- A valid license for Corrata Cloud

Then use the following procedure:

1. In the Corrata portal, complete the steps provided at the Corrata website for integration with Defender for Cloud Apps: [Integrating Corrata with Microsoft Defender for Cloud Apps](https://corrata.com/microsoft-mcas-onboarding?azure-portal=true).
2. Open Defender for Cloud Apps and select **Settings**.
3. In the **Cloud Discovery** section, choose **Automatic log upload**.
4. On the Settings page, on the **Data sources** tab, select **Add data source**.
5. Enter the following information in the **Add data source** dialog box:

   - Name = Corrata
   - Source = Corrata
   - Receiver type = FTP

6. Select **Add**.

## Integrate with Menlo

Menlo Security is a standalone Secure Web Gateway. It can monitor your organization's traffic enabling you to set policies for blocking transactions. By integrating with Defender for Cloud Apps, you can avoid the need to create a log collector. Instead, collected data can be sent direct from Menlo to Defender for Cloud Apps. In addition, any apps you mark as unsanctioned in Defender for Cloud Apps are automatically blocked by Menlo Security.

### Deploy Menlo integration

Before you deploy integration, ensure that you have:

- A valid Microsoft Defender for Cloud Apps license, or a valid Azure AD Premium P1 or P2 license
- A valid license for Menlo Security

Then sign in to the Menlo admin portal and complete the steps documented at the Menlo Security website: [Admin portal](https://admin.menlosecurity.com/docs/guides/web_admin_settings_casb.html?highlight=microsoft).
