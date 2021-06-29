Messaging is managed through the creation and assignment of messaging policies. If your users experience problems with messaging, the first place to start is by reviewing these messaging policies. You can create, configure, and assign these policies using the Microsoft Teams admin center or by using PowerShell. 

## Review messaging policies

In the Microsoft Teams admin center, select the Messaging policies node, and then open the appropriate policy. 

> [!TIP]
> You can use only the built-in Global (Org-wide default) policy if you want. 

The default settings for the Global (Org-wide default) policy are displayed in the following screenshot. 

:::image type="content" source="../media/message-policy.png" alt-text="A screenshot that displays the Global (Org-wide default) messaging policy.":::


You can review and modify the following settings: 

- **Owners can delete sent messages**. When you turn on this setting, channel owners can remove all sent messages in a channel. 
- **Delete sent messages**. When you turn on this setting, users can delete their own messages. 
- **Edit sent messages**. When you turn on this setting, users can edit their own messages. 
- **Read receipts**. Choose which users can use read receipts. Choose between:

   - User controlled (default value)
   - Turned off for everyone
   - Turned on for everyone

- **Chat. Enables or disables chat.**
- **Use Giphys in conversations**. When you turn on this setting, users can use animated pictures within the conversations. 
- **Giphy content rating**. When you turn on the setting for sharing animated images, you can use this setting to apply content rating to restrict the type of animated images that can display in conversations. Available content rating options are: 

   - **No restriction**
   - **Moderate (default value)**
   - **Strict**

- **Use Memes in conversations**. When you turn on this setting, users can use internet memes. 
- **Use stickers in conversations**. When you turn on this setting, users can post images with editable text to get channel members’ attention. 
- **Allow URL previews**. Enables a preview of a pasted URL to be visible in a message.
- **Translate messages**. Translates the message.
- **Allow immersive reader for viewing messages**. Enables users to hear posts, chat messages, and assignments read aloud. Immersive Reader also includes grammar tools such as Parts of Speech and Picture Dictionary.
- **Send urgent message using priority notifications**. When enabled, users can send messages marked as urgent.
- **Create voice messages**. Enables users to use voice messages. You can choose between: 

   - **Allowed in chats and channels (default value)**
   - **Allowed in chats only**
   - **Disabled**

- **On mobile devices, display favorite channels above recent chats**. Choose between Disabled and Enabled.
- **Remove users from group chats**. Enables users to remove other users from group chats.
- **Suggested replies**. Provides quick and simple replies to inbound messages. 
- **Chat permission role**. If role-based chat permissions are enabled, you can choose the permission role. Choose between: 

   - Restricted permissions (default value)
   - Limited permissions
   - Full permissions

> [!TIP]
> If you’ve reviewed policies, and you’re still having messaging issues, consider collecting the chat ID. You can do this by accessing Teams through a web browser, and collecting the link that shows up as part of the URL when accessing the chat. 