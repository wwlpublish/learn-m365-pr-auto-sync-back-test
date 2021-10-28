Box provides Contoso's users with cloud-based storage and collaborative tools and apps. However, you want to be sure that users are not downloading, or indeed uploading, files that might contain malicious content. You can use Cloud App Security to help manage these requirements by creating Conditional Access App Control session or access policies.

The process for configuring Conditional Access App Control with Cloud App Security for Box is broadly similar to the process we reviewed in the last unit for Workplace from Facebook.

## Configure Box in Azure AD

To configure Box with Conditional Access App Control, you start the process in the **Azure Active Directory admin center**.

1. In the navigation pane, select **Enterprise applications**.
1. On the **All applications** page, select **Box**.
1. On the **Overview** page, there are links for assigning users and groups, set up for SSO, provisioning user accounts, Conditional Access, and self-service.

## Add users and groups

1. Start by selecting the **Assign users and groups** link.
1. On the **Users and groups** page, select **Add user/group**.
1. On the **Add Assignment** page, select **None Selected**, and then, in the **Users and Groups** page, select the desired users or groups, and then select the **Select** button.
1. On the **Add Assignment** page, select **Assign**.

## Setup SSO

1. Select the **Overview** tab, and then select the **Get started** link in the **2. Set up single sign-on** section.
1. On the **Single sign-on** tab, select the **Change single sign-on modes** link.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up Single Sign-On with SAML** page, in the **Basic SAML configuration** section, select **Edit**.
1. In the **Sign on URL** text box, enter the sign-on URL for Box, then select **Save**.
1. On the **Set up Single Sign-On with SAML** page, in Step 3, select the **Download** link next to **Certificate (Base64)**.
1. Also select the **Download** link for **Federation Metadata XML**.

    > [!IMPORTANT]
    > If necessary, install the My Apps Secure Sign-in browser extension. This process is described in the preceding unit.

1. Select the **Set up Box** button, and then prompted, sign in to Box using at administrative account.
1. Complete the process to configure the required SAML settings in Box.

    > [!TIP]
    > These will be broadly similar to the approach we took with Workplace from Facebook. For additional details, review the following document: [Tutorial: Azure Active Directory single sign-on (SSO) integration with Box](/azure/active-directory/saas-apps/box-tutorial?azure-portal=true).

1.  Switch back to the **Azure Active Directory admin center**, and on the **SAML-based Sign-on** page, select **Test**. You should be able to successfully sign in to Box, assuming the currently signed in user is one of the users you assigned earlier.

> [!NOTE]
> If you are unable to configure the SSO settings for your Box account, then send the downloaded Federation Metadata XML to Box support team. They can then configure the required SAML SSO connection.

## Create a Conditional Access policy for Box

The next step is to create a Conditional Access policy in Azure AD.

1. In the **Azure Active Directory admin center**, select Enterprise apps in the navigation pane, and then select **Box**.
1. In the **Box** page, in the navigation pane, select **Conditional Access**.
1. On the **Conditional Access** page, select **New Policy**.
1. On the **New** page, in the **Name** text box, enter the policy name.
1. Select **Users and groups** and then choose the users or groups to which the policy is assigned.
1. Select **Cloud apps or actions**. Notice that one app is already included – Box.
1. In the **Access Controls** section, select **Session**, and then on the **Session** page, select the **Use Conditional Access App Control** check box.
1. In the drop-down list, select **Use custom policy**.
1. Select the **Select** button.
1. In the **Enable policy** section, select **On**, and then select **Save**.

## Configure an access policy

The final stage is to create the Access control or Session control policies. In this example, we'll create an access policy. In the **Cloud App Security** portal, complete the following steps:

1. In the navigation pane, select **Control** and then select **Policies**.
1. In the **Policies** page, select the **Conditional Access** tab.
1. Select the **Create policy** button, and then select **Access policy**.
1. Enter a policy name in the **Policy name** text box.
1. In the query section, select the **Select apps** list, and then select **Box**.
1. Scroll down to **Actions**. Select **Block** if you want to enforce the access policy immediately. Otherwise, leave the value on **Test**.
1. Select **Apply template**.
1. Review any extra settings, and then select Create.
1. When you're finished, select **Create**.
