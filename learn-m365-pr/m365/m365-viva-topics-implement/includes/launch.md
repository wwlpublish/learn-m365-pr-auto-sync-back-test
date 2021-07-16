Once you have decided on the rollout strategy for either a crowd-sourced or authoritative model, it's time to implement Viva Topics in your organization's Microsoft 365. The five steps to launch Viva Topics are:

1. Review admin console elements.
2. Select sources to discover.
3. Choose who can add/edit/manage topics.
4. Monitor, administer, and use reporting.
5. Follow a process for change management and adoption.

## Step 1: Review admin console elements

Knowledge admins manage the Viva Topics settings after setting up has been completed. They are also Microsoft 365 global or SharePoint admin in the Microsoft 365 admin center for Viva Topics and SharePoint Syntex.

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LhZP]

## Step 2: Select sources to discover

Viva Topics uses Microsoft Graph and AI to identify topics in your organization. A topic is a phrase or term with a specific meaning to the organization, and has resources related to help people understand what it is and find more information about it.  

SharePoint topic sources are in the Admin setup for **Connect people to knowledge** in the Microsoft 365 admin center. It is not accessible in the topic center.  

The topic discovery settings specify which SharePoint sites are used as sources for topics. You can choose to include all SharePoint sites, a specific list of sites, or no sites. We recommend you choose all sites so topic experiences can discover many good topics for your users.

When you set up Topics, you can choose from the following options:

- **All sites**: All SharePoint sites in your organization. This includes current and future sites.
- **All, except selected sites**: All sites except for the ones you specify. Sites created in the future will be included as sources for topic discovery.
- **Only selected sites**: Only the sites you specify. Sites created in the future will not be included as sources for topic discovery.
- **No sites**: Do not include any SharePoint sites.

If you choose either All, except selected sites or Only selected sites, you can upload a .csv file with a list of sites (in Site name, URL format). These options are useful for a pilot and you want to include a limited number of sites to start.

You can change the SharePoint sites in your organization to be crawled for topics.

If you add sites using the site picker, they are added to the existing list of sites to include or exclude. If you upload a .csv file, it overwrites any existing list. If you have previously included or excluded specific sites, you can download the list as a .csv file, make changes, and upload the new list.

### Choose sites for topic discovery

1. On the **Topic discovery** tab, under **Select SharePoint topic sources**, select **Edit**.
2. Select the SharePoint sites to be crawled as sources for your topics during discovery. This includes:
   - **All sites**
   - **All, except selected sites**
   - **Only selected sites**
   - **No sites**

### Exclude topics by name

You can exclude topics from discovery by uploading a list using a .csv file. If you've previously excluded topics, you can download the .csv, make changes, and upload it again.

1. On the **Topic discovery** tab, under **Exclude topics**, select **Edit**.
2. Select **Exclude topics by name**.

   If you need to create a list, download the .csv template described in [Manage topic discovering in Microsoft Viva Topics](/microsoft-365/knowledge/topic-experiences-discovery) and add the topics you want to exclude.
3. Select **Save**.

### Create a .csv list of sites

If you need to include or exclude multiple sites, you can use a comma-separated value (.csv) list. Use this format:

```c
Name (required),Expansion,MatchType- Exact/Partial (required)
```

In the CSV template, enter the following information about the topics you want to exclude:

- **Name**: Type the name of the topic you want to exclude. There are two ways to do this:

  - **Expansion**: If you want to exclude an acronym, type the words the acronym stands for.
  - **MatchType-Exact/Partial**: Type whether the name you entered was an exact or partial match type.

    - Partial match: You can exclude all topics with a specific word in it. For example, arc will exclude all topics with the word arc in it, such as Arc circle, Plasma arc welding, or Training arc. Note it will not exclude topics in which the text is included as part of a word, such as Architecture.
    - Exact match: You can include the exact name or acronym (for example, Contoso or ATL).

## Step 3: Choose who can add/edit/manage topics

Microsoft 365 security settings (permissions to sites, files, and folders) and Viva Topics admin settings determine what a user can view, add, edit, or manage in topics.

Setting up Topics does not modify any existing access controls on content in your organization. Users will only see what they already have access to.

### Manage topic visibility

You can manage the set of users who can see topic highlights, topic cards, and the topic center in the Microsoft 365 admin center. You must be a global administrator, SharePoint administrator, or Knowledge administrator to perform these tasks.

Learn more about [Knowledge management of Viva Topics](/learn/modules/m365-viva-topics-knowledge/).

### Manage topic permissions

Manage topic permissions settings and topic discovery settings in the Microsoft 365 admin center as a global administrator, SharePoint administrator, or Knowledge administrator.

## Step 4: Monitor, administer, and use reporting  

- Configure indexing in the Microsoft 365 admin center under **Knowledge Management**.
- Look at abandoned queries in Search where the user did not find a good result. As Admin, continue to review the Search metrics to determine potential useful Topics for your people. Are people finding appropriate Topics with Search? If not, then create a Topic for it to enable search results for this.
- Complete the pilot & testing for Viva Topics.  
- Add site usage analytics.

## Step 5: Change management/adoption

Decide on high-quality Topics to be shown to your users and they have the right permissions to consume and contribute knowledge. Plan your approach and target scenarios, engage your organization, train your organization, and build a champion network.  
