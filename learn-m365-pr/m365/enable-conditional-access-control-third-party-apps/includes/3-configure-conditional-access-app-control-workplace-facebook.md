Workplace from Facebook is a collaborative app that enables the users at Contoso to work together. You can use Conditional Access App Control policies in Microsoft Defender for Cloud Apps to help secure content in this app, and to manage things such as file uploads and downloads.

## Locate the Audience and ACS URLs

To configure Conditional Access App Control policies for Workplace from Facebook, start with the Workplace settings. You'll need to locate several URLs needed for subsequent configuration.  

1. Sign in to Workplace using an administrative account.
1. In the portal, select **Admin Panel**.
1. In the navigation pane, select **Security**, and on the **Security** page, select the **Authentication** tab.
1. In the SSO providers section, select **Add New SSO Provider**.
1. In the **Single sign-on (SSO) setup** dialog box, scroll down and locate the **SAML configurations** section.
1. Copy the **Audience URL** and **ACS (Assertion Consumer Service) URL** strings. You'll need these URLs later.

    :::image type="content" source="../media/saml-configuration.png" alt-text="A screenshot showing the SAML configuration settings in a trial Workplace from Facebook tenant.":::

## Configure the identity provider

Next, you'll need to configure the identity provider. In this case, we'll add the Workplace from Facebook app to Azure AD, and then provision users for the app.

1. Open the **Azure Active Directory admin center** and sign in as a global admin.
1. In the navigation pane, select the **Enterprise applications** tab.
1. On the **All applications** page, select **New application**.
1. Search for **Facebook**, and then select **Workplace from Facebook**.
1. In the **Workplace from Facebook** page, select **Create**.
1. In the navigation pane, select **Users and groups**.
1. On the **Users and groups** page, select **Add user/group**.
1. On the **Add Assignment** page, select **None Selected**, and then, in the **Users and Groups** page, select the desired users or groups, and then select the **Select** button.
1. On the **Add Assignment** page, select **Assign**.

    :::image type="content" source="../media/users-groups.png" alt-text="A screenshot displaying the Users and groups page in the Azure AD portal. The administrator is adding users to the Workplace from Facebook app.":::

## Create a Conditional Access policy for the app

The next step is to create a Conditional Access policy in Azure AD.

1. In the **Workplace from Facebook** page, in the navigation pane, select **Conditional Access**.
1. On the **Conditional Access** page, select **New Policy**.
1. On the **New** page, in the **Name** text box, enter the policy name.
1. Select **Users and groups** and then choose the users or groups to which the policy is assigned.
1. Select **Cloud apps or actions**. Notice that one app is already included – Workspace from Facebook.

    :::image type="content" source="../media/cloud-app.png" alt-text="A screenshot displaying the Cloud apps or actions page. Workplace from Facebook is displayed.":::

1. In the **Access Controls** section, select **Session**, and then on the **Session** page, select the **Use Conditional Access App Control** check box.
1. In the drop-down list, select **Use custom policy**.
1. Select the **Select** button.
1. In the **Enable policy** section, select **On**, and then select **Save**.

    > [!NOTE]
    > You can configure additional conditions, such as device state.

    :::image type="content" source="../media/session.png" alt-text="A screenshot displaying the Session page of a new Conditional Access policy in the Azure Active Directory admin center.":::

## Configure Workplace from Facebook SSO settings

In the Azure Active Directory Admin Center, you must now complete the app configuration process.

1. In the **Workplace from Facebook** page, in the navigation pane, select **Single sign-on**.
1. In the **Single sign-on** page, select **SAML**.
1. On the **SAML-based Sign-on** page, in the **Basic SAML Configuration** section, select **Edit**.
1. In the **Identifier (Entity ID)** text box, paste the **Audience URL** string you recorded earlier.
1. In both the **Reply URL (Assertion Consumer Service URL)** and the **Sign on URL** text boxes, paste the **ACS (Assertion Consumer Service) URL** string you recorded earlier.
1. Select **Save**.
1. In Step 3, select the **Download** link next to **Certificate (Base64)**.
1. In step 4, select the **Install the extension** button. Follow the on-screen instructions to install the extension.
1. Switch back to the browser tab that displays the SAML-based Sign-on page. Move to step 5.
1. Select the link to expand the Configuration URLs. Record the Login URL and Azure ID Identifier. You'll need these values shortly.
1. Select the **Set up Workplace from Facebook** button.
1. A new tab opens. It displays the **Authentication** tab on the **Security** page in Workplace settings. Select the **Single sign-on (SSO)** check box.
1. Select the **Add New SSO Provider** button.
1. In the **Name for the SSO provider** box, enter **AzureADsso**.
1. In the **SAML URL** box, paste the **Login URL** you recorded.
1. In the **SAML issuer URL** box, paste the **Azure AD Identifier** you recorded.
1. Browse and locate the certificate file you previously downloaded. Open in a text editor. Copy the entire contents of the file and then, in the Workplace Admin panel, in the SAML certificate box, paste the file contents.
1. Select the **Test SSO** button.
1. In the **Single sign-on (SSO) setup** dialog box, select **Save Changes**.

## Configure a Defender for Cloud Apps Conditional Access App Control app

The next stage is to create the Conditional Access App Control policy. In a new browser tab, open the Microsoft Defender for Cloud Apps portal, and then complete the following steps:

1. In the navigation pane, expand **Investigate** and then select **Connected apps**.
1. In the **Connected apps** page, select the **Conditional Access App Control apps** tab.
1. Select the plus symbol.
1. In the **Add a SAML application with your identity provider** dialog box, in the **Search for an app** text box, enter **Workplace** and then select **Workplace by Facebook**.
1. Select **Start wizard**.
1. In the **Add a SAML application with your identity provider** wizard, on the **APP INFORMATION** page, select **Fill in data manually**.
1. In the **Assertion consumer service URL** text box, paste the **Assertion consumer service URL** you recorded earlier.
1. Select the **Use Workplace by Facebook SAML certificate** check box, and browse and select the certificate you downloaded earlier.
1. Select **Next** twice.
1. On the Identity provider page, select **Fill in data manually**.
1. In the **Single sign-on service URL** text box, paste the **Login URL** you recorded in the Azure portal earlier.
1. Select **Next**, **Finish**, and then select **Close**.

    :::image type="content" source="../media/connected-app.png" alt-text="A screenshot of the Conditional Access App Control apps tab. The Workplace by Facebook app is displayed. Available controls are Access control and Session control.":::

## Configure a session policy

The final stage is to create the Access control or Session control policies. In this example, we'll create a session policy. In the Microsoft Defender for Cloud Apps portal, complete the following steps:

1. In the navigation pane, select **Control** and then select **Policies**.
1. In the **Policies** page, select the **Conditional Access** tab.
1. Select the **Create policy** button, and then select **Session policy**.
1. In the Policy template list, select the type of activity. For example, select **Block sending of messages based on real-time content inspection**.
1. Select **Apply template**. The various fields are updated with suitable values based on the template. If you want to modify any fields, you can do so.
1. When you're finished, select **Create**.

    :::image type="content" source="../media/add-session-policy.png" alt-text="A screenshot of a session policy with the Block sending of messages based on real-time content inspection template selected.":::

## Block or apply DLP to file downloads in Workplace from Facebook using Microsoft Defender for Cloud Apps

The following video demonstrates how to use DLP for file downloads in Workplace from Facebook using Defender for Cloud Apps:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyDG3]
