Organization relationships must be used to enable federated sharing with another Exchange Server organization or Exchange Online. Each organization relationship is for a single external organization, which Azure AD identifies by its domain name and application identity.

As a result, not only does your organization need to create a federated trust relationship with Azure AD authentication, but so too does the external Exchange Server organization that you want to collaborate with. Both organizations must have bi-directional connectivity in place so that the Exchange Server in each organization can reach the other organization’s respective Exchange Web Services and Autodiscover URLs.

> [!NOTE]
> By default, Exchange Online has a trust in place with the Azure AD authentication system.

When you create an organization relationship in the Exchange Admin Center, you configure the following options:

 -  **Relationship name**. This value is the name that you choose. You can, for example, use the domains to share.
 -  **Domains to share with**. Type the fully qualified domain name (FQDN) of the domain or domains with which you want to establish federation. This value would be the domain name the other organization uses for its federation trust.
 -  **Enable calendar free/busy information sharing**. This setting turns on information sharing. If you enable this option, choose one of the following options:
    
     -  Calendar free/busy information with time only
     -  Calendar free/busy information with time, subject, and location
     -  Share calendar free/busy information for:
        
         -  Everyone in your organization
         -  A specified security group

When you configure the organization relationship, the Azure AD authentication system checks your DNS zone and searches for the appropriate TXT resource record that has the content that validates the domain. Create this record before you create the organization relationship.

> [!NOTE]
> Even if an organization relationship specifies that all user calendars are shared, users can override this setting. Users can configure the default permissions for their own calendars to prevent sharing. However, changing the default permission also affects sharing with internal users.

To identify the external organization with which you want to create an organization relationship, you typically use the domain name of the external organization to automatically populate the necessary information into the organization relationship. If you specify the domain name, the wizard for establishing federation obtains all the necessary configuration information from the Azure AD authentication system.

If you use the Exchange Management Shell (EMS) to create the organization relationship, use the **Get-FederationInformation** cmdlet to obtain the federation information for the external organization. You can pipe this information to the **New-OrganizationRelationship** cmdlet when you create the organization relationship.

The following command provides an example of creating an organization relationship to share Free/Busy information with the **adatum.com** domain:

```powershell
Get-FederationInformation -DomainName adatum.com | New-OrganizationRelationship
-Name "Adatum" -DomainNames adatum.com -FreeBusyAccessEnabled $true
-FreeBusyAccessLevel LimitedDetails
```

You can use Autodiscover to obtain the uniform resource locator (URL) for the external organization’s Availability Web Service. If the external organization doesn't have Autodiscover configured for access from the Internet, you can enter the URL manually.

For example, let’s assume you want to configure the organization relationship for the following settings:

 -  The Exchange Web Services application URL is **mail.adatum.com.**
 -  The Autodiscover URL is **https://mail.adatum.com/autodiscover/autodiscover.svc/wssecurity.**

To configure the relationship for this example, you should run the following command:

```powershell
Set-OrganizationRelationship -Identity "Adatum" -TargetAutodiscoverEpr "https://mail.adatum.com/autodiscover/autodiscover.svc/wssecurity" -TargetApplicationUri "mail.adatum.com"
```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.