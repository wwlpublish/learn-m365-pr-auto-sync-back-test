In this unit, you'll learn about the different App Catalogs in SharePoint and how you can programmatically deploy SharePoint apps with the Application Lifecycle Management APIs.

## Tenant-scoped App Catalog

The tenant-scoped App Catalog was initially introduced to SharePoint in the SharePoint Server 2013 release. It's available in all later on-premises SharePoint Server releases and SharePoint Online.

The tenant App Catalog is managed by the SharePoint tenant administrators. All SharePoint packages deployed to the tenant's App Catalog are available to all site collections throughout the entire tenant.

Starting in SharePoint Server 2019 and in SharePoint Online, when deploying a SharePoint package to the tenant App Catalog, you can optionally have web parts installed to all site collections in the tenant. For this option to be available when deploying the package, the developer must enable it in the **./config/package-solution.json** file. This option can save administrators and site collection owners time from having to go to each site collection and install the app in each site collection after deploying it. Also, it will automatically install the app in all new site collections created after deploying the package.

## Site collection-scoped App Catalog

The site collection App Catalog is only available in SharePoint Online. The site collection App Catalog works just like the tenant-scoped App Catalog, except SharePoint packages deployed to it are only available to that specific site collection.

The site collection App Catalog is a good option when you have a component that intended for a subset of site collections and not your entire tenant.

Site collection App Catalogs aren't provisioned in site collections automatically, nor can they be created using the SharePoint Admin Center. They must be provisioned by a tenant administrator using the SharePoint REST API, PowerShell, or the CLI for Microsoft 365.

### Create site collection App Catalogs

The reason site collection App Catalogs aren't created automatically is that Microsoft has taken a secure by default approach.

When someone can add a SharePoint package to a site and install items from that package, administrators are effectively giving the ability to add JavaScript files to your SharePoint site. This delegates the responsibility of who's allowed to add JavaScript files to a site to the site collection owners.

Once those script files are running on a SharePoint page, they run in the context of the current user that's logged into the site and interacting with the page.  If that user has privileged access permissions, such as access to a document library that contains files related to mergers and acquisitions for the organization, the script file can use the SharePoint REST API, accessed by the user's context, and send files from that library to another location... all without the user knowing this was happening. The person who installed the app may not realize that can happen or have done a thorough code review of the custom components before deploying the package. With a site collection App Catalog, tenant administrators are effectively delegating this responsibility to site collection owners. Because of this, Microsoft has taken the approach that each customer needs to decide if they want to trust this delegation to their site collection owners and so, requires tenant administrators to "opt-in" to site collection App Catalogs on a site collection by site collection basis.

The only way to create site collection App Catalogs is ultimately through the SharePoint REST API. You can do this through code, or using one of the administrative command-line tools available to tenant administrators.

The site collection App Catalog is a special document library in the site collection accessible from the **Site Contents** page.

#### Create site collection App Catalogs with SharePoint Online PowerShell

The [SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) contains cmdlets that you can use to create and remove App Catalogs to and from site collections. First, connect to your SharePoint Online tenant by signing into your Tenant Admin Center and then use the `Add-SPOSiteCollectionAppCatalog` cmdlet to add a site collection App Catalog to the specified site collection.

```powershell
PS> Connect-SPOService -Url https://contoso-admin.sharepoint.com
PS> Add-SPOSiteCollectionAppCatalog -Site https://contoso.sharepoint.com/sites/test-site
```

#### Create site collection App Catalogs with the CLI for Microsoft 365

The [CLI for Microsoft 365](https://pnp.github.io/cli-microsoft365) contains commands that you can use to create and remove App Catalogs to and from site collections. First, connect to your SharePoint Online tenant by signing into your Tenant Admin Center and then use the `site appcatalog` command to add a site collection App Catalog to the specified site collection:

```console
$ m365 login
$ m365 spo site appcatalog add --url https://contoso.sharepoint/sites/test-site
```

### Remove site collection App Catalogs

Removing a site collection App Catalog doesn't actually delete the library, it just disables the deployment of SharePoint packages to the site collection. After removing a site collection App Catalog, any packages uploaded to the library in the future are treated just like files in a document library.

Use the following commands to remove a site collection App Catalog using SharePoint Online PowerShell:

```powershell
PS> Connect-SPOService -Url https://contoso-admin.sharepoint.com
PS> Remove-SPOSiteCollectionAppCatalog -Site https://contoso.sharepoint.com/sites/test-site
```

Use the following commands to remove a site collection App Catalog using the CLI for Microsoft 365:

```console
$ m365 login
$ m365 spo site appcatalog remove --url https://contoso.sharepoint/sites/test-site
```

## Application lifecycle management (ALM) REST API

The SharePoint REST API includes endpoints and methods for managing the complete application lifecycle of SharePoint packages and apps. This is referred to as *application lifecycle management*, or ALM. These ALM APIs are only available in SharePoint Online.

The SharePoint ALM APIs enable developers programmatic control of all parts of the package lifecycle. They allow for complex automation in continuous integration and continuous deployment scenarios (CI/CD) including control over large numbers of deployments.

The ALM APIs enable the following scenarios:

- add/remove SharePoint Framework solutions and SharePoint add-ins to/from App Catalogs
- enable/disable SharePoint Framework solutions and SharePoint add-ins for installation in site collections
- install/uninstall SharePoint Framework solutions and SharePoint add-ins to site collections
- upgrade SharePoint Framework solutions and SharePoint add-ins in site collections
- list/get one SharePoint Framework solution and SharePoint add-in within App Catalogs

These ALM APIs are available as both REST API endpoints and various tools including the PnP PowerShell and the CLI for Microsoft 365 projects and the SharePoint Client Side Object Model (CSOM).

## Summary

In this unit, you learned about the different App Catalogs in SharePoint and how you can programmatically deploy SharePoint apps with the Application Lifecycle Management APIs.
