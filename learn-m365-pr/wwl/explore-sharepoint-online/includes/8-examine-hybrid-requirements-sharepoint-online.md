In a hybrid SharePoint deployment, productivity services in SharePoint Online are integrated with on-premises SharePoint Server. This design provides unified functionality and access to data while allowing a company to get started in the cloud. For enterprises that want to gradually move their existing on-premises SharePoint Server services to the cloud, SharePoint Server hybrid provides a staged migration path. This design enables an organization to take a first step in exploring cloud functionality at its own pace. It also extends high-impact SharePoint Server workloads to SharePoint Online in Microsoft 365.

A SharePoint Server hybrid environment enables trusted communications between SharePoint Online and SharePoint Server. Once this trust framework is established, an organization can configure integrated functionality between services and features such as Search, Follow, and user profiles. When you add Microsoft 365 to an environment where you're already using SharePoint Server, by default there's no integration between the two. With SharePoint hybrid features, you can tie the two environments together in various ways to make a more seamless user experience.

With SharePoint hybrid features, you can:

 -  Consolidate search results between SharePoint Server and Microsoft 365.
 -  Consolidate user profiles in Microsoft 365.
 -  Offload your users' personal storage to the cloud.

The following table compares the features in non-hybrid and hybrid SharePoint and OneDrive deployments.

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    **Non-hybrid**
  :::column-end:::
  :::column:::
    **Hybrid**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    OneDrive

  :::column-end:::
  :::column:::
    OneDrive is available in Microsoft 365 but there's no link to it from SharePoint Server. If you've deployed MySites, users may have a second OneDrive in SharePoint Server.

  :::column-end:::
  :::column:::
    OneDrive links are provided in SharePoint Server. These links direct users to OneDrive.
For more information, see [Plan hybrid OneDrive](/sharepoint/hybrid/plan-hybrid-onedrive-for-business?azure-portal=true).

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Site following

  :::column-end:::
  :::column:::
    The followed sites list in Microsoft 365 tracks followed SharePoint Online sites. If you've deployed MySites, a second followed sites list in SharePoint Server tracks followed SharePoint Server sites.

  :::column-end:::
  :::column:::
    Followed sites from both locations are consolidated in the SharePoint Online followed sites list. SharePoint Server links to the followed sites list redirect users to the SharePoint Online followed sites list.
For more information, see [Hybrid site following](/sharepoint/hybrid/hybrid-site-following?azure-portal=true).

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Document following

  :::column-end:::
  :::column:::
    If you've deployed MySites, the followed documents list in SharePoint Server tracks followed SharePoint Server documents.

  :::column-end:::
  :::column:::
    Hybrid document following isn't available. If you use hybrid OneDrive, the SharePoint Server followed documents list will be hidden from users.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Profiles

  :::column-end:::
  :::column:::
    Users have separate profiles in SharePoint Server and in Microsoft 365.

  :::column-end:::
  :::column:::
    Profiles exist in both locations, but SharePoint Server links to users' profiles redirect profiles in Microsoft 365.
For more information, see [Plan hybrid profiles](/sharepoint/hybrid/plan-hybrid-profiles?azure-portal=true).

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Extensible app launcher

  :::column-end:::
  :::column:::
    Users see a different app launcher in Microsoft 365 and in SharePoint Server.

  :::column-end:::
  :::column:::
    There are still separate app launchers, but the SharePoint Server app launcher includes several tiles from Microsoft 365. For more information, see [The extensible hybrid app launcher](/sharepoint/hybrid/the-extensible-hybrid-app-launcher?azure-portal=true).

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Hybrid self-service site creation

  :::column-end:::
  :::column:::
    Users see separate self-service site creation experiences in SharePoint Server and Microsoft 365, as configured by the administrator.

  :::column-end:::
  :::column:::
    Users going to the default SharePoint Server site creation page are redirected to the SharePoint Online Group Creation page. This design allows them to create sites in SharePoint Online.
For more information, see [Hybrid self-service site creation](/sharepoint/hybrid/hybrid-self-service-site-creation?azure-portal=true).

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Search

  :::column-end:::
  :::column:::
    Separate search indexes and search centers for SharePoint Server and Microsoft 365. Users must search from SharePoint Server to find items stored there and they must search from Microsoft 365 to find items stored there.

  :::column-end:::
  :::column:::
    Search results between the two locations are combined in one of two ways. Cloud hybrid search crawls on-premises content and indexes it in the search index in Microsoft 365. Users can search the Microsoft 365 index from either location. Hybrid federated search combines search results from each search index in a single search center.
For more information, see [Hybrid search in SharePoint in Microsoft 365](/sharepoint/hybrid/hybrid-search-in-sharepoint?azure-portal=true).

  :::column-end:::
:::row-end:::


### What is redirection?

Many of the SharePoint hybrid features make use of a technique called redirection. With redirection, when users attempt to access a service in SharePoint Server using site navigation, they're automatically redirected to the equivalent service in Microsoft 365. For example, in a non-hybrid environment, when a user selects OneDrive on a SharePoint Server site, they're taken to their SharePoint Server OneDrive location. With hybrid OneDrive, when a user selects OneDrive, they're taken to OneDrive.

Hybrid OneDrive, hybrid site following, and hybrid profiles all use redirection to send users from on-premises SharePoint Server to the equivalent service in Microsoft 365. The on-premises SharePoint Server services continue to function in the background and are accessible by users if they've bookmarked the URL.

When redirection is used, existing data in SharePoint Server isn't automatically migrated to the equivalent Microsoft 365 service. Documents in OneDrive and user profile information must be manually migrated for each user. SharePoint Server followed sites will also have to be refollowed.

### SharePoint Server hybrid configuration roadmaps

The following table provides links to hybrid configuration roadmaps for various hybrid scenarios. These roadmaps guide you through the steps you need to follow to set up the hybrid features of your choice. Be sure to follow each step in the roadmap. If you follow more than one roadmap, there's no need to repeat the steps that are the same.

:::row:::
  :::column:::
    **Content**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Configure hybrid OneDrive - roadmap](/sharepoint/hybrid/configure-hybrid-onedrive-for-businessroadmap?azure-portal=true).

  :::column-end:::
  :::column:::
    With hybrid OneDrive, users will be redirected to OneDrive when they select the OneDrive link in SharePoint Server.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Configure hybrid sites features - roadmap](/sharepoint/hybrid/configure-hybrid-sites-featuresroadmap?azure-portal=true).

  :::column-end:::
  :::column:::
    With hybrid sites features, you can integrate parts of your site navigation between SharePoint Server and Microsoft 365 for enterprises.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Configure cloud hybrid search - roadmap](/sharepoint/hybrid/configure-cloud-hybrid-searchroadmap?azure-portal=true).

  :::column-end:::
  :::column:::
    With cloud hybrid search, you have a single search index in Office 365 for enterprises with content from SharePoint Server and SharePoint in Microsoft 365.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Configure hybrid federated search from SharePoint Server to SharePoint in Microsoft 365 - roadmap](/sharepoint/hybrid/configure-hybrid-federated-search-sharepoint-serverroadmap?azure-portal=true).

  :::column-end:::
  :::column:::
    With outbound hybrid search, users will be able to see search results from Microsoft 365 for enterprises when they perform a search in SharePoint Server.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Configure hybrid federated search from SharePoint in Microsoft 365 to SharePoint Server - roadmap](/sharepoint/hybrid/configure-hybrid-federated-search-sharepoint-onlineroadmap?azure-portal=true).

  :::column-end:::
  :::column:::
    With inbound hybrid search, users will be able to see search results from SharePoint Server when they perform a search in Microsoft 365 for enterprises.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Configure hybrid Business Connectivity Services - roadmap](/sharepoint/hybrid/configure-hybrid-business-connectivity-servicesroadmap?azure-portal=true).

  :::column-end:::
  :::column:::
    With hybrid Business Connectivity Services (BCS), you can use your existing BCS solutions to allow connections to your SharePoint Server data sources from SharePoint in Microsoft 365.
  :::column-end:::
:::row-end:::
