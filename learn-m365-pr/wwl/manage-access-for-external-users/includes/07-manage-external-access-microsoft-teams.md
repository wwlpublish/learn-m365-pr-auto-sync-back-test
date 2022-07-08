External access is a way for Teams users from an entire external domain to find, call, chat, and set up meetings with you in Teams. You can also use external access to communicate with people from other organizations who are still using Skype for Business and Skype.

Configuring external access for organizations includes:

- **Allow all external domains**: This is the default setting in Teams, and it lets people in your organization find, call, chat, and set up meetings with people external to your organization in any domain.

    In this scenario, your users can communicate with all external domains that are running Teams or Skype for Business or are allowing all external domains or have added your domain to their allow domains list.

- **Allow only specific external domains**: By adding domains to an **Allow domains** list, you limit external access to only the allowed domains. Once you set up a list of allowed domains, all other domains will be blocked. 

- **Block specific domains** - By adding domains to a **Block domains** list, you can communicate with all external domains *except* the ones you've blocked. 

- **Block all external domains** - Prevents people in your organization from finding, calling, chatting, and setting up meetings with people external to your organization in any domain.

## Configure external access

1. Sign-in to Teams admin center.

2. In the left navigation pane, go to **Users** > **External access**.

3. Under **Teams and Skype for Business users in external organizations** section, configure the setting based on business need. 

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

4. Under **Teams accounts not managed by an organization** section, configure the setting based on business need.

    |People in my organization can communicate with Teams users whose accounts aren't managed by an organization|	External users with Teams accounts not managed by an organization can contact users in my organization|	Scenario|
    |--|--|--|
    |Turn off	|Uncheck|	Block Teams users in your organization from communicating with external Teams users whose accounts are not managed by an organization.|
    |Turn on|	Uncheck	|Let Teams users in your organization communicate with external Teams users whose accounts are not managed by an organization if your Teams users have **initiated** the contact.<br/><br/>Unmanaged Teams users will not be able to search the full email address to find organization contacts.|
    |Turn on|	Check	|Let Teams users in your organization **initiate** and **receive requests** to communicate with external Teams users whose accounts are not managed by an organization.|

5. Turn on the **Allow users in my organization to communicate with Skype users** setting if you want to allow Teams users in your organization chat with and call Skype users.

    :::image type="content" source="../media/enable-external-access.png" alt-text="Screenshot of external access for Teams accounts" :::

6. Select **Save**.

Make sure the admin in the other Teams organization completes these same steps. For example, in their **allowed domains** list, their admin needs to enter the domain for your business if they limit the organizations that can communicate with their users.

After the configuration, you can chat with external users using their email address and adding them as a contact. You can verify if federation is working by sending a chat message to an external user via Teams chat and getting a response.

