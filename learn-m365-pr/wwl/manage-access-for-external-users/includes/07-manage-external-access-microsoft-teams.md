External access is a way for Teams users from an entire external domain to find, call, chat, and set up meetings with you in Teams. You can also use external access to communicate with people from other organizations who are still using Skype for Business and Skype.

Configuring external access for organizations includes three scenarios for setting it up:

- **Open federation**: This setting is the default setting in Teams. The setting lets people in your organization find, call, chat, and set up meetings with people external to your organization in any domain.

    Users can communicate with all external domains that are running Teams or Skype for Business AND are using open federation OR have added your domain to their allowlist.

- **Allow specific domains**: By adding domains to an **Allow** list, you limit external access to only the allowed domains. Once you set up a list of allowed domains, all other domains will be blocked. To allow specific domains, select **Add a domain**, add the domain name, select **Action to take on this domain**, and then select **Allowed**.

- **Block specific domains**: By adding domains to a **Block** list, you can communicate with all external domains *except* the ones you've blocked. To block specific domains, select **Add a domain**, add the domain name, select **Action to take on this domain**, and then select **Blocked**. Once you set up a list of blocked domains, all other domains will be allowed.

## Configure external access

1. In the left navigation pane, go to **Org-wide settings** > **External access**.

2. Turn on the **Users can communicate with other Skype for Business and Teams users** setting.

3. If you want to allow all Teams organizations to communicate with users in your organization, skip to step 5.

4. If you want to limit the organizations that can communicate with users in your organization, you can either allow all except some domains, or you can allow only specific domains.

    - To allow all except some domains, add the domains you want to block by selecting **Add domain**. In the **Add a domain** pane, type the domain name, select **Blocked**, and then select **Done**.

    - To limit communications to specific organizations, add those domains to the list with a status of **Allowed**. Once you have added any domain to the allowlist, communications with other organizations will be limited to only those organizations whose domains are in the allowlist.

5. Select **Save**.

6. Make sure the admin in the other Teams organization completes these same steps. For example, in their **allowed domains** list, their admin needs to enter the domain for your business if they limit the organizations that can communicate with their users.

After the configuration, you can chat with external users using their email address and adding them as a contact. You can verify if federation is working by sending a chat message to an external user via Teams chat and getting a response.

:::image type="content" source="../media/enable-external-access.png" alt-text="Screenshot of external access switch turned On" lightbox="../media/enable-external-access.png":::
