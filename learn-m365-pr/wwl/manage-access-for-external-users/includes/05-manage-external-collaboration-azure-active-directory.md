Azure Active Directory is the directory service used by Microsoft 365. The Azure Active Directory Organizational relationships settings directly affect sharing in Teams, Microsoft 365 Groups, SharePoint, and OneDrive.

In Azure AD, the settings for invitations control the guest experience at the directory, tenant, and application levels. 

## External collaboration settings in Azure AD

| Setting | Default | Description |
|:--|:--|:--|
|Guest user access|Guests have limited access to properties and memberships of directory objects|Determines the [permissions that guests have in Azure Active Directory](/azure/active-directory/fundamentals/users-default-permissions).|
|Guest invite settings|Anyone in the organization can invite guests including guests and non-admins|Determines whether guests, members, and admins can invite guests to the organization.<br><br> This setting affects  Microsoft 365 sharing experiences such as Teams and SharePoint.|
|Enable guest self-service sign up via user flows|No|Determines if you can create user flows that allow someone to sign up for an app that you created and create a new guest account.|
|Collaboration restrictions|Allow invitations to be sent to any domain|This setting allows you to specify a list of allowed or blocked domains for sharing. When allowed domains are specified, then sharing invitations can only be sent to those domains. When denied domains are specified, then sharing invitations cannot be sent to those domains.<br><br> This setting affects  Microsoft 365 sharing experiences such as Teams and SharePoint. You can allow or block domains at a more granular level by using domain filtering in SharePoint or Teams.|

## Configure external collaboration in Azure AD admin center


1. Sign in to the Azure portal as a tenant administrator.

2. Select Azure Active Directory.

3. Select **User settings** > **Manage external collaboration settings**.

4. Under **Guest user access restrictions**, choose the level of access you want guest users to have:
  
   - **Guest users have the same access as members (most inclusive)**. This option gives guests the same access to Azure AD resources and directory data as member users.

   - **Guest users have limited access to properties and memberships of directory objects**. (Default) This setting blocks guests from certain directory tasks, like enumerating users, groups, or other directory resources. Guests can see membership of all non-hidden groups.

   - **Guest user access is restricted to properties and memberships of their own directory objects (most restrictive)**. With this setting, guests can access only their own profiles. Guests are not allowed to see other users' profiles, groups, or group memberships.

5. Under **Guest invite settings**, choose the appropriate settings:

   - **Anyone in the organization can invite guest users including guests and non-admins (most inclusive)**. To allow guests in the organization to invite other guests including those guests who are not members of an organization, select this radio button.
   - **Member users and users assigned to specific admin roles can invite guest users including guests with member permissions**. To allow member users and users who have specific administrator roles to invite guests, select this radio button.
   - **Only users assigned to specific admin roles can invite guest users**. To allow only those users with administrator roles to invite guests, select this radio button. The administrator roles include **Global Administrator**, **User Administrator**, and **Guest Inviter**.
   - **No one in the organization can invite guest users including admins (most restrictive)**. To deny everyone in the organization from inviting guests, select this radio button.
   

6. Under **Enable guest self-service sign up via user flows**, select **Yes** if you want to be able to create user flows that let users sign up for apps. 

7. Under **Collaboration restrictions**, you can choose whether to allow or deny invitations to the domains you specify and enter specific domain names in the text boxes. For multiple domains, enter each domain on a new line. 

	:::image type="content" source="../media/external-collaboration-settings.png" alt-text="External collaboration settings in AAD" lightbox="../media/azure-ad-collaboration-settings.png":::



## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”