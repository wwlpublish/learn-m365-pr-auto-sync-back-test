Slack provides Contoso's users with ways to collaborate, and work together on projects. As with both Workplace from Facebook and Box, you can use Conditional Access App Control policies in Defender for Cloud Apps to help secure Contoso's content in this app.

Like Workplace, you start by adding the Slack app to Azure Active Directory, and then configure the required SSO settings before you're able to create a Conditional Access policy, and finally the required Conditional Access App Control policies.

## Add the Slack app and assign users

First, you'll need to add the Slack app to Azure AD, and then provision users for the app.

1. Open the **Azure Active Directory admin center** and sign in as a global admin.
1. In the navigation pane, select the **Enterprise applications** tab.
1. On the **All applications** page, select **New application**.
1. Search for **Slack**, and then select **Slack**.
1. In the **Slack** page, select **Create**.
1. On the **Overview** page, select **Assign users and groups**. Use the procedure we used for both Workplace and Box assign the required users.

## Setup SSO

1. Back on the **Overview** tab, select the **Get started** link in the **2. Set up single sign on** section.
1. On the **Single sign-on** tab, select the **Change single sign-on modes** link.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up Single Sign-On with SAML** page, in the **Basic SAML configuration** section, select **Edit**.
1. You'll need to obtain the necessary links from Slack settings. Enter the required information and select **Save**.
1. On the **Set up Single Sign-On with SAML** page, in Step 3, select the **Download** link next to **Certificate (Base64)**.

    > [!IMPORTANT]
    > If necessary, install the My Apps Secure Sign-in browser extension. This process is described in the preceding unit.

1. In step 4, expand the **Configuration URLs** section, and copy the URLs for later use.
1. Select the **Set up Slack** button, and then prompted, sign in to Slack using at administrative account.
1. Complete the process to configure the required SAML settings in Slack:

    1. In Slack, navigate to **Microsoft Azure AD** then select **Team Settings**.
    1. In the **Team Settings** section, select the **Authentication** tab, and then select **Change** **Settings**.
    1. In the **SAML Authentication Settings** dialog box, complete the following steps:

        - In the **SAML 2.0 Endpoint (HTTP)** textbox, paste the value of **Login URL**, which you copied from Azure portal.
        - In the **Identity Provider Issuer** textbox, paste the value of **Azure AD Identifier**, which you copied from Azure portal.
        - Open your downloaded Azure AD Signing Certificate (Base64) file in notepad, copy the content of it into your clipboard, and then paste it to the **Public Certificate** textbox.
        - Configure the Settings value as desired, and then select **Save Configuration**.

    > [!TIP]
    > For additional details, review the following document: [Tutorial: Azure Active Directory single sign-on (SSO) integration with Slack](/azure/active-directory/saas-apps/slack-tutorial?azure-portal-true).

1. Switch back to the **Azure Active Directory admin center**, and on the **SAML-based Sign-on** page, select **Test**. You should be able to successfully sign in to Slack, assuming the currently signed in user is one of the users you assigned earlier.

## Create a Conditional Access policy for Slack

The next step is to create a Conditional Access policy in Azure AD.

1. In the **Azure Active Directory admin center**, select Enterprise apps in the navigation pane, and then select **Slack**.
1. In the **Slack** page, in the navigation pane, select **Conditional Access**.
1. On the **Conditional Access** page, select **New Policy**.
1. On the **New** page, in the **Name** text box, enter the policy name.
1. Select **Users and groups** and then choose the users or groups to which the policy is assigned.
1. Select **Cloud apps or actions**. Notice that one app is already included – Slack.
1. In the **Access Controls** section, select **Session**, and then on the **Session** page, select the **Use Conditional Access App Control** check box.
1. In the drop-down list, select **Use custom policy**.
1. Select the **Select** button.
1. In the **Enable policy** section, select **On**, and then select **Save**.

## Configure an access or session policy

The final stage is to create the Access control or Session control policies. You complete these steps in the **Defender for Cloud Apps** portal. As they do not differ greatly from the preceding apps, we won't repeat them here.

## Block chats with sensitive data using Microsoft Defender for Cloud Apps

The following video demonstrates how to use Conditional Access App Control policies to control message content in Slack:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyyLQ]
