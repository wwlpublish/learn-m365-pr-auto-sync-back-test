You can configure session controls in Microsoft Cloud App Security to work with any web app. You can also configure these controls to work with third-party identity providers, so long as they support SAML 2.0 or OpenID Connect. 

Firstly, verify that you have a relevant PingOne license, and also a Microsoft Cloud App Security license. You’ll also need to check that you have an existing PingOne SSO configuration for the app you want to control.

> [!IMPORTANT]
> This SSO must be based on the SAML 2.0 authentication protocol. 

## Overview

After you verify you meet the prerequisites, you’ll need to complete the following steps: 

1. Obtain the app's SSO settings
2. Configure Cloud App Security with the app’s SSO settings
3. Create a custom app in PingOne
4. Configure Cloud App Security with the PingOne app's information
5. Complete the custom app configuration in PingOne
6. Get the app changes in Cloud App Security
7. Complete the app changes
8. Complete the configuration in Cloud App Security

Let’s look more closely at this procedure using Salesforce as an example app. 

### Obtain the app's SSO settings

This process might vary depending on the specific app being configured. But for Salesforce, select **Setup**, select **Settings**, select **Identity**, and then select **Single Sign-On Settings**. In the **SAML 2.0** section, record the **Login URL**. If a certificate is defined, download a copy of the certificate. 

### Configure Cloud App Security with the app’s SSO settings

The next step is to enter the SSO details from your app into Cloud App Security. Use the following procedure: 

1. In Cloud App Security, in the navigation pane, select **Investigate**, then select **Connected apps**. 
2. On the **Connected apps** page, select the **Conditional Access App Control apps** tab.
3. To add the details for the new app, select the plus symbol. 
4. In the **Add a SAML application with your identity provider** dialog box, in the search box, enter the app name and then select the app. In this example, enter and select **Salesforce**.
5. Select **Start wizard**.
6. In the **APP INFORMATION** section, select **Fill in data manually**. 
7. In the **Assertion consumer service URL**, enter the login URL you recorded earlier and then select **Next**. Pause at this point. 

   > [!NOTE]
   > If your app provides a SAML certificate, select **Use <app_name> SAML certificate** and upload the certificate file you downloaded earlier. 

### Create a custom app in PingOne

You’ll now need to create a custom app in PingOne. 

> [!IMPORTANT]
> You create a custom app so that you can test settings with the existing app without access or session controls and without changing the app’s behavior for your users.

First, you must gather some information:

1. In PingOne, open the app you want to work with. In our example, open Salesforce. 
2. On the **SSO Attribute Mapping** page, make a note of the **SAML_SUBJECT** attribute and value, and then download the **Signing Certificate** and **SAML Metadata** files.
3. Open the downloaded SAML metadata file and locate the **SingleSignOnService Location** value. Record this value. 
4. On the **Group Access** page, record the list of assigned groups.
5. Then use the instructions from the **Add a SAML application with your identity provider** page to configure a custom app in your identity provider’s portal.

To create the custom app: 

1. Create a **New SAML Application**. 
2. When prompted, on the **Application Details** page, enter the required information and then select **Continue to Next Step**.
3. On the **Application Configuration** page, complete the following:

   1.   In the **Single sign-on service URL** field, enter the **Salesforce Login URL** you noted earlier.
   2.   In the **Entity ID** field, enter a unique ID starting with `https://`. This must not be the same as the exiting Salesforce PingOne app's configuration.
   3.    Record the **Entity ID** for use later. 

4. Select **Continue to Next Step**.
5. On the **SSO Attribute Mapping** page, enter the existing Salesforce app's **SAML_SUBJECT** attribute and value you recorded earlier, and then select **Continue to Next Step**.
6. On the **Group Access** page, add the existing Salesforce app's groups you recorded earlier, and complete the configuration.

### Configure Cloud App Security with the PingOne app's information

Switch back to the Cloud App Security portal. 

1. On the Cloud App Security **IDENTITY PROVIDER** page, select **Next**.
2. On the next page, select **Fill in data manually**, and then:

   1.   For the Assertion consumer service URL, enter the **Salesforce Login URL** you recorded earlier.
   2.   In the **Upload identity provider's SAML certificate** section, select **Browse** and upload the certificate file you downloaded earlier.

3. Select **Next**.
4. On the next page, record the following information for later, and then select **Next**:

   - Cloud App Security single sign-on URL

   - Cloud App Security attributes and values

### Complete the custom app configuration in PingOne

Switch back to your identity provider’s portal. In this case, switch to PingOne. Locate the custom app you created earlier. In this case, select the custom Salesforce app, and then complete the following procedure: 

1. Open the custom app for editing.
2. In the **Assertion Consumer Service (ACS)** field, replace the URL with the Cloud App Security single sign-on URL you recorded earlier, and then select **Next**.
3. Add the Cloud App Security attributes and values to the app's properties. You recorded these details earlier. 
4. Save your settings. 

### Get the app changes in Cloud App Security

Switch back to the Cloud App Security portal. In the **Add Salesforce with your identity provider** wizard, on the **APP CHANGES** page: 

1. Copy the Cloud App Security **SAML Single sign-on URL**.
2. Select the **Cloud App Security SAML certificate** link to download the certificate for the app.


   > [!CAUTION]
   > Don’t select **Finish** yet.

### Complete the app changes

Switch to the app. In this case, switch to Salesforce. Select **Setup**, select **Settings**, select **Identity**, and then select **Single Sign-On Settings**. Then complete the following procedure: 

1. It’s recommended that you create a backup of your current settings.
2. Then, replace the **Identity Provider Login URL** field value with the **Cloud App Security SAML single sign-on URL** you recorded earlier.
3. Upload the **Cloud App Security SAML** certificate you previously downloaded.


   > [!IMPORTANT]
   > The Cloud App Security SAML certificate is valid for one year, after which you must renew it.


4. Replace the **Entity ID** field value with the PingOne custom app Entity ID you noted earlier.
5. Select **Save**.

### Complete the configuration in Cloud App Security

Finally, switch to the Cloud App Security portal. In the **Add Salesforce with your identity provider** wizard, on the **APP CHANGES** page, select **Finish**. 

> [!NOTE]
> After completing the wizard, all associated login requests to the app are routed through Conditional Access App Control. 