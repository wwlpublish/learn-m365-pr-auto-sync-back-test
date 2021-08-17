Now that you’ve learned how to register an application in Azure Active Directory, let’s look at the flip-side and see how to remove an application's registration from your Azure AD tenant.

Applications that an organization has registered appear under the **My apps** filter on its tenant's main **App registrations** page. These applications are ones the organization registered manually through the Azure portal, or programmatically through PowerShell or the Graph API. More specifically, they're represented by both an Application and Service Principal object in the organization's Azure AD tenant.

**Additional reading.** For more information, see [Application Objects and Service Principal Objects](/azure/active-directory/develop/active-directory-application-objects).

Let’s take a moment now and see how to remove both single-tenant and multi-tenant applications.

### To remove a single-tenant application from your directory

Complete the following steps to remove a single-tenant application:

1.  Sign in to the [Azure portal](https://portal.azure.com/?azure-portal=true).
2.  If your account gives you access to more than one Azure AD tenant, select your account in the top-right corner and set your portal session to the required Azure AD tenant.
3.  In the left-hand navigation pane, select the **Azure Active Directory service**, select **App registrations**, then select the application you want to configure. On the application's main registration page, the **Settings** page for the application opens.
4.  From the application's main registration page, select **Delete**.
5.  Select **Yes** in the confirmation message.

### To remove a multi-tenant application from its home directory

Complete the following steps to remove a multi-tenant application:

1.  Sign in to the Azure portal.
2.  If your account gives you access to more than one Azure AD tenant, select your account in the top-right corner and set your portal session to the required Azure AD tenant.
3.  In the left-hand navigation pane, select the **Azure Active Directory service**, select **App registrations**, then select the application you want to configure. On the application's main registration page, the **Settings** page for the application opens.
4.  From the **Settings** page, choose **Properties** and change the **Multi-tenanted** switch to **No** (to first change your application to single-tenant), and then select **Save**. The application's service principal objects remain in the tenants of all organizations that have already consented to it.
5.  Select the **Delete** button from the application's main registration page.
6.  Select **Yes** in the confirmation message.

### Removing a multi-tenant application authorized by another organization

A subset of the applications that appear under the **All apps** filter (excluding the **My apps registrations**) on the tenant's main **App registrations** page are multi-tenant applications.

In technical terms, these multi-tenant applications are from another tenant, and were registered into the organization's tenant during the consent process. More specifically, they're represented by only a service principal object in the organization's tenant, with no corresponding application object.

To remove a multi-tenant application’s access to your directory (after having granted consent), the company administrator must remove its service principal. The administrator must have global admin access and can remove it through the Azure portal or use the [Azure AD PowerShell Cmdlets](https://go.microsoft.com/fwlink/?LinkId=294151?azure-portal=true).

**Additional reading.** For more information on the differences between application and service principal objects, see [Application and service principal objects in Azure AD](/azure/active-directory/develop/active-directory-application-objects).
