External sharing in Microsoft 365 (OneDrive, SharePoint Online, Unified Groups, and so on) and Azure AD B2B collaboration are technically the same thing. All external sharing (except OneDrive/SharePoint Online), including guests in Microsoft 365 Groups, already uses the Azure AD B2B collaboration invitation APIs for sharing.

### How does Azure AD B2B differ from external sharing in SharePoint Online?

OneDrive/SharePoint Online has a separate invitation manager. Support for external sharing in OneDrive/SharePoint Online started before Azure AD developed its support. Over time, OneDrive/SharePoint Online external sharing has accrued several features and many millions of users who use the product's built-in sharing pattern. However, there are some subtle differences between how OneDrive/SharePoint Online external sharing and Azure AD B2B collaboration work, including:

 -  OneDrive/SharePoint Online adds users to the directory after users have redeemed their invitations. So, before redemption, the user isn't visible in the Azure AD portal. If another site invites a user in the meantime, a new invitation is generated. However, when Azure AD B2B collaboration is used, users are added immediately on invitation so that they show up everywhere.
 -  The redemption experience in OneDrive/SharePoint Online looks different from the experience in Azure AD B2B collaboration. After a user redeems an invitation, the experiences look alike.
 -  Azure AD B2B collaboration invited users can be picked from OneDrive/SharePoint Online sharing dialog boxes. OneDrive/SharePoint Online invited users also show up in Azure AD after they redeem their invitations.
 -  The licensing requirements differ. For each paid Azure AD license, up to five guest users can access an organization's paid Azure AD features.

### Managing external sharing in SharePoint Online with Azure AD B2B collaboration

To manage external sharing in OneDrive/SharePoint Online with Azure AD B2B collaboration, set the OneDrive/SharePoint Online external sharing setting to **Allow sharing only with the external users that already exist in your organization's directory**. Users can go to externally shared sites and pick from external collaborators that the admin has added. The admin can add the external collaborators through the B2B collaboration invitation APIs.

After enabling external sharing, the ability to search for existing guest users in the SharePoint Online (SPO) people picker is turned OFF by default to match legacy behavior.

This feature can be enabled by using Windows PowerShell to set the **ShowPeoplePickerSuggestionsForGuestUsers** property at the tenant and site collection level. The feature can be set using the **Set-SPOTenant** and **Set-SPOSite** cmdlets, which allow members to search all existing guest users in the directory. Changes in the tenant scope don't affect already provisioned SPO sites.

**Additional reading.** For more information about external sharing in SharePoint Online, see [External sharing overview](/sharepoint/external-sharing-overview).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”