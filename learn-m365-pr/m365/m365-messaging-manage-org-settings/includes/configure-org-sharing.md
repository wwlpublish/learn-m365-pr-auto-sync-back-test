You can share calendar information with an external business partner by setting up an organization relationship. As a Microsoft 365 admin, you can set up an organization relationship with another Microsoft 365 organization or with an Exchange on-premises organization.

You can create an organization relationship by using either the Exchange admin center or PowerShell cmdlets.

## Create an organization relationship in the Exchange admin center

1. On the Microsoft 365 admin center dashboard, go to **Admin > Exchange**.
1. Go to **organization > sharing**, and then click **New +**.
1. Type a friendly name for the organization relationship in **Relationship name**.
1. Type the domain for the external Microsoft 365 or Exchange on-premises organization you want to let see your calendars in **Domains to share with**. If you need to enter more than one domain, use a comma to separate the domain names. For example, contoso.com, service.contoso.com.
1. Select **Enable calendar free/busy information sharing** to turn on calendar sharing with the domains you listed. Set the sharing level for calendar free/busy information, and set which users can share calendar free/busy information.

     To set the free/busy access level, select one of the following options:
      - **Calendar free/busy information with time only**
      - **Calendar free/busy with time, subject, and location**

     To set which users will share calendar free/busy information, select one of the following options:
      - **Everyone in your organization**
      - **A specified security group**

    Click **browse** to pick the security group from a list, then click **ok**.

1. Click **save** to create the organization relationship.

>[!NOTE]
>Cross-tenant configurations don't support personal contacts for free/busy lookup. Contacts must be included in the global address list for free/busy lookup to work.

## Create an organization relationship by using the Exchange Online PowerShell cmdlets

This example creates an organization relationship with Contoso, Ltd, with the following conditions:

- An organization relationship is set up with contoso.com, northamerica.contoso.com, and europe.contoso.com.
- Free/busy access is enabled.
- Contoso.com and the subdomains get free/busy time, subject, and location information from your organization.

```PowerShell
New-OrganizationRelationship -Name "Contoso" -DomainNames "contoso.com","northamerica.contoso.com","europe.contoso.com" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel LimitedDetails
```

If you're not sure which domains Contoso has set up for cloud-based authentication, you can run this command to automatically find the configuration information. In the following example, the **Get-FederationInformation** cmdlet is used to find the right information, which is then passed to the **New-OrganizationRelationship** cmdlet.

```PowerShell
Get-FederationInformation -DomainName Contoso.com | New-OrganizationRelationship -Name "Contoso" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel LimitedDetails
```

If you're setting up an organization relationship with an on-premises Exchange organization, you may want to provide the connection settings. This example creates an organization relationship with Fourth Coffee and specifies the connection settings to use. The following conditions apply:

- The organization relationship is established with the domain fourthcoffee.com.
- The Exchange Web Services application URL is mail.fourthcoffee.com.
- The Autodiscover URL is <https://mail.fourthcoffee.com/autodiscover/autodiscover.svc/wssecurity>.
- Free/busy access is enabled.
- Fourth Coffee sees free/busy information with the time.

```PowerShell
New-OrganizationRelationship -Name "Fourth Coffee" -DomainNames "fourthcoffee.com" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel AvailabilityOnly -TargetAutodiscoverEpr "https://mail.fourthcoffee.com/autodiscover/autodiscover.svc/wssecurity" -TargetApplicationUri "mail.fourthcoffee.com"
```

## Modify an organization relationship in Exchange Online

You can change the settings of an organization relationship, such as changing the name, temporarily disabling calendar sharing, changing the access level, or changing which security groups will share calendars.

### Add a domain to an organization relationship

1. In the Microsoft 365 admin center, go to **Admin > Exchange**.
1. Go to **organization > sharing**.
1. In list view, under **Organization Sharing**, select the organization relationship Contoso, and then click **Edit**.
1. In **organization relationship > general**, don't change the **Name** for the organization relationship.
1. Enter the domain *service.contoso.com* in **Domains to share with**, then click **Add +**.
1. Click **save** to update the organization relationship.

### Disable free/busy sharing for the organization relationship

1. In the Microsoft 365 admin center, go to **Admin > Exchange**.
1. Go to **organization > sharing**.
1. In list view, under **Organization Sharing**, select the organization relationship Contoso, and then click **Edit**.
1. Click **sharing** in **organization relationship**.
1. Clear the **Enable calendar free/busy information sharing** option to disable free/busy sharing. The free/busy access level and security group buttons will also be disabled.
1. Click **save** to update the organization relationship.

### Change the free/busy access level for the organization relationship

1. In the Microsoft 365 admin center, go to **Admin > Exchange**.
1. Go to **organization > sharing**.
1. In list view, under **Organization Sharing**, select the organization relationship Contoso, and then click **Edit**.
1. Click **sharing** in **organization relationship**.
1. Select **Calendar free/busy information with time only**.
1. Click **save** to update the organization relationship.

## Remove an organization relationship in Exchange Online

You can remove an organization relationship to disable calendar sharing with the other organization.

1. In the Microsoft 365 admin center, go to **Admin > Exchange**.
1. Go to **organization > sharing**.
1. Under **Organization Sharing**, select an organization relationship, and then click **Delete**.
1. In the warning that appears, click **yes**.

## Learn more

[PowerShell command reference library](/powershell/windows/get-started?azure-portal=true)
