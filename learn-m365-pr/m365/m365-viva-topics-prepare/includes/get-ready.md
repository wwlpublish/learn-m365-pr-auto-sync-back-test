To make the most of Viva Topics, you want to have as much content as possible for topic discovery. This ensures a rich set of topics for your users. The more content is in scope, the better the insights the AI can discover.

There are five activities to complete before a successful deployment to ensure you are including the appropriate content, and have the right people and resources:

1. Migrate content to SharePoint.
2. Connect information to Microsoft Graph.
3. Modernize SharePoint pages.
4. Secure content appropriately.
5. Identify Knowledge managers & topics.

## Step 1: Migrate content to SharePoint

There are several tools and services to help with content migration. You can migrate your content to Microsoft 365 with these migration tools:

- Migration Manager
- SharePoint Migration Tool (SPMT)
- Microsoft 365 FastTrack
- Partner migration tools and services

Make the most of your migration with the following tasks:

- **Migrate to a modern site** – including Microsoft Teams. While indexing can happen on any SharePoint site (classic or modern), displaying topics to users through highlights and cards only happens on modern pages.
- **Maintain usernames** – most migration tools allow you to map user identities across the migration, so properties like Created By or Modified By are maintained after the migration. This is important for topics because the authorship of files is used to identify the experts are added to a topic page or card. 
- **Make service account names descriptive** – In some cases, maintaining usernames isn't possible. For example, if you're migrating content created by someone who is no longer an employee of the organization. In this instance, most migration tools will move a file as if it was created by an admin account or a service account. If this happens frequently, the service account could be listed on topics as an expert. This is where the naming of that account becomes important. If you make it descriptive, the presence of these non-human accounts will be understandable for users consuming topics.

## Step 2: Connect information to Microsoft Graph

Microsoft Search indexes all your Microsoft 365 data to make it searchable for users. With Microsoft Graph content connectors*, your organization can index third-party data, so it appears in Microsoft Search results. If you can't migrate some content, then connect it with Microsoft Graph content connectors.

View the list of resources at the end of this module for information on how to configure Graph content connectors.  

## Step 3: Modernize SharePoint pages

Although both classic and modern SharePoint page content drive resource for Viva Topics, Topic cards and highlights can only appear on modern pages. You can update any pages you want to include in Viva Topics from classic to modern SharePoint pages. Use the SharePoint Modernization scanner to prepare your classic sites for modernization. If you have a lot of classic sites, prioritize high profile pages to convert to modern.

## Step 4: Secure content appropriately

Users see different resources when they interact with a topic card or a topic page. Different users have access to different files associated with the topic; resources are security trimmed to only show users the resources they have permissions to see.

Encourage site owners to review sharing and permissions. SharePoint site owners can review a Sharing report for their site with full details of all permissions and sharing links configured on the site. These reports list internal and external (guest) users. Site owners can also see who has permissions for the site by going to the Site Permissions and Advanced Permissions Settings pages:

- On your site, choose **Settings > Site permissions**. Check to see who is listed under **Site Owners**, **Site Members**, and **Site Visitors**. Check for any *Guest* users.
- On the **Permissions** page, choose **Advanced Permissions Settings**. You can check for unique permissions and see who has limited access to any items in the site.
- Audit Microsoft 365 Groups and Teams to make sure they are appropriately set as public or private groups or teams. New Teams and Microsoft 365 Groups are set to private by default; but when they were first released, these groups were *public* by default. If you were an early adopter of these technologies, you might want to review. Also, the function of a team often evolves over its lifecycle, and the setting might need to be updated to reflect the current use of the team.

Review use of "everyone", "everyone except external users," and broad security groups. Content may be incorrectly shared with these values. To review the use of these groups, you can:

1. Create an account that has no group memberships.
1. Use search with this account to discover content that is broadly shared.

If inappropriate content is visible to this account through search, then work with the site owners to correct the permission configuration.

Administrators can configure indexing in the Microsoft 365 admin center. With Knowledge Management, you can:

- Allow discovery across all SharePoint sites or specify sites to include or exclude as topic sources.
- Where you have sensitive terms, you can also exclude topics by name. For example, if you have the name of a sensitive project, where you don't want a highlight or card to appear, irrespective of the user's permissions, you can exclude that project name.
- At the content level, you can control what is discoverable. Any configuration you've done to exclude content from search will also be used by content discovery. For example, if you have excluded a specific document library from appearing in search results, this document library will not be used for topic discovery.

## Step 5: Identify Knowledge managers & topics

Managing topics involves the following key roles:

- **Knowledge administrator** – a technical role, typically in IT. This role allows the setup of the Viva Topics in the Microsoft 365 admin center, and the configuration of topic discovery and visibility.
- **Knowledge manager** – works with the topics themselves and oversees quality and completeness.
- **Topic contributors** – are based on permissions in the Microsoft 365 admin center. They are subject matter experts able to curate the content on topics, add resources and people.

Choose which group of users to allow to see topics:

- **Everyone in my organization**. "Everyone" does not include guests. It is all internal users in your directory.
- **Only selected people or security groups**. This option is good while rolling out Viva Topics, so you can test a pilot with a subset of users. If you want guests to view Topics, you will need to use the "selected people or security groups" option and grant them a license. All users, even guest users, will need to have a license to view the topic experience.  
- **No one**.

Which Topics are visible? You can choose to:

- Show all candidate topics.
- Show only confirmed topics.

Seeding topics is where the Knowledge manager and subject matter experts can help. Combining human knowledge with the AI is the best route for quality topics. So, if there are topics you anticipate, manually create these in the topic center. This will give the AI a strong signal of the topic relevance and to identify resources and people associated.

Use existing category of topics to help your topic planning, either from SharePoint or elsewhere. Existing categories often include organizational terms, products, subject areas, and so on. Sources for topics can also come from lists of projects, existing search bookmarks and so on.
