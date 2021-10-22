External access is a way for Teams users from an entire external domain to find, call, chat, and set up meetings with you in Teams. You can also use external access to communicate with people from other organizations who are still using Skype for Business and Skype.

Configuring external access for organizations includes:

- **Allow all external domains**: This is the default setting in Teams, and it lets people in your organization find, call, chat, and set up meetings with people external to your organization in any domain.

    In this scenario, your users can communicate with all external domains that are running Teams or Skype for Business or are allowing all external domains or have added your domain to their allow list.

- **Allow only specific external domains**: By adding domains to an **Allow** list, you limit external access to only the allowed domains. Once you set up a list of allowed domains, all other domains will be blocked. 

- **Block specific domains** - By adding domains to a **Block** list, you can communicate with all external domains *except* the ones you've blocked. 

- **Block all external domains** - Prevents people in your organization from finding, calling, chatting, and setting up meetings with people external to your organization in any domain.

## Configure external access

1. In the left navigation pane, go to **Users** > **External access**.

2. Under **Choose which domains your users have access to** section, configure the setting based on business need. 

    **To allow specific domains**:
    
    1. Select **Allow only specific external domains**.
    2. Select **Allow domains**.
    3. In the **Domain** box, type the domain that you want to allow and then select **Done**.
    4. If you want to allow another domain, select **Add a domain**.

    **To block specific domains**:
    
    1. Select **Block only specific external domains**.
    2. Select **Block domains**.
    3. In the **Domain** box, type the domain that you want to allow and then select **Done**.
    4. If you want to block another domain, select **Add a domain**.

3. Turn on the **Allow users in my organization to communicate with Skype users** setting if you want to allow Teams users in your organization chat with and call Skype users. .

4. Select **Save**.

Make sure the admin in the other Teams organization completes these same steps. For example, in their **allowed domains** list, their admin needs to enter the domain for your business if they limit the organizations that can communicate with their users.

After the configuration, you can chat with external users using their email address and adding them as a contact. You can verify if federation is working by sending a chat message to an external user via Teams chat and getting a response.

:::image type="content" source="../media/enable-external-access.png" alt-text="Screenshot of external access switch turned On" :::
