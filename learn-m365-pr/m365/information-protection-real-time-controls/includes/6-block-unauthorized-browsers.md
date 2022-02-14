To ensure security and functionality for your web apps you should test them with all commonly used browsers in your organization. You could then block other browsers from accessing your web apps. These browsers could include the Tor browser, which routes traffic through the Tor network, but also include unusual browsers and old versions of commonly used browsers, which have not had the latest security patches applied.

## Create a policy to block unauthorized browsers from accessing corporate web apps

To create a policy to block unauthorized browsers from accessing corporate web apps, perform the following steps:

1. Navigate to <https://portal.cloudappsecurity.com>.
2. Select **Control** and select **Policies**.

    :::image type="content" source="../media/4-microsoft-cloud-app-security-policies.png" alt-text="Policies.":::

3. Follow the steps from a previous unit in this module to create a policy with a **Category** of **Access control**.
4. In **ACTIVITIES MATCHING ALL OF THE FOLLOWING** add the following filters:
    a.  Add an **App** filter and select all of the web apps that you want to apply the policy to.
    b.  Add a **Client app** filter and select **Browser**.
    c.  Add a **User agent string** filter and select **does not contain** and then the user agent string of the approved browser.

    :::image type="content" source="../media/6-edit-access-policy.png" alt-text="User agent string.":::

5. Select **Block** and add a message for users that are blocked.

> [!NOTE]
> You can search for websites in **Bing** that will display your current user agent string.

> [!NOTE]
> It is possible to change a user agent string and, therefore, this should not be the only method of security.

The following video gives you an overview of how to block unauthorized browsers from accessing corporate web apps with Microsoft Defender for Cloud Apps:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyaKG]
