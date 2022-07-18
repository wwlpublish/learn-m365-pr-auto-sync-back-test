[Audience targeting](/viva/connections/use-audience-targeting-in-viva-connections)
can be applied to components of the Viva Connections experience.
Audience targeting filters content by Azure Active Directory (Azure AD)
groups set up by your administrators. Often Azure AD groups are set up for
distinct roles and regions, and it's likely an individual will belong
to several Azure AD groups.

**Example of an audience targeting**
**field:**

:::image type="content" source="../media/audience-targeting-field.png" alt-text="Screenshot of the audience targeting field." :::

Audience targeting settings are applied in the flow of creating
the Dashboard, preparing content for the Feed, and setting up Resources
in SharePoint global navigation. Settings can be applied and edited at
any time. Audience targeting settings will apply to both the desktop and
mobile experiences.

**Summary of where audience targeting can be applied for each
component:**

|Dashboard cards|SharePoint news posts|Links in Resources|
|---------------|---------------------|------------------|
|:::image type="content" source="../media/viva-connections-mobile-dashboard.png" alt-text="Screenshot of the dashboard mobile view.":::|:::image type="content" source="../media/viva-connections-mobile-feed.png" alt-text="Screenshot of the Feed mobile view.":::|:::image type="content" source="../media/viva-connections-mobile-resources.png" alt-text="Screenshot of the Resources mobile view.":::|
|Each card on the Dashboard can be targeted to a specific audience by selecting Edit and then adding one or more audiences to the Audience targeting field.|SharePoint news posts can be targeted to specific audiences to filter news posts that are displayed in the Feed. Learn more about targeting news posts. To influence the hierarchy of SharePoint news posts in the Feed, use the News Boost feature.|Navigational links that get set up in SharePoint global navigation that display as Resources in the Viva Connections experience can be targeted. <br> From the home site, select Settings, and then Global navigation. Turn on Audience targeting and then Edit labels and links. Add one or more audiences in the Audience targeting field and select Save.|

:::image type="icon" source="../media/story-telling-logo-white-bg.png"  :::

### Learn how Lamna Healthcare applies audience targeting

At Lamna Healthcare, it's common to see employees belong to multiple
[Azure Active Directory (Azure AD) groups](/azure/active-directory/fundamentals/active-directory-manage-groups).
Let’s see how each Azure AD group affects what Lamna employee affect see in
each component Viva Connections.

#### Lamna Healthcare - audience targeting for Dashboard cards

Cards on the Dashboard are filtered to specific Azure AD groups using
audience targeting. As a result, certain groups will see different
content. Let’s see how Lamna Healthcare employees’ Azure AD group settings
impact what cards they see in
Dashboard.

| **Azure AD group**      | Work-life balance and wellbeing | Shuttle schedule | Café menu | Shifts | Submit time off | Benefits Self-service| Approval for purchase |
|---------|------|-------|-----|----------|-----------------|-----------|---------|
| All Employees |&check; |&check; |&check; | | | | |
| Hourly |   | | | &check;| | | |
| Full time |  | | | | &check;| | |
| Benefits eligible |   | | | | |&check; | |
| People Manager |   | | | | | |&check; |
| Finance professional |   | | | | | |&check; |

:::image type="content" source="../media/-nicoletta.png" alt-text="Diagram of Nicoletta's profile head shot and job title." :::

Nicoletta, a member of Lamna’s janitorial staff working at Region D, is
an hourly paid employee. Nicoletta works over 30 hours a week and is eligible
for healthcare and vacation benefits. Nicoletta belongs to the Azure AD
groups of: *Hourly paid*, *Region D*, and *Benefits eligible*. In the
Viva Connections Dashboard, Nicoletta sees the Shifts card, the Benefits
self-service card and other cards that are available for all Lamna
employees.

:::image type="content" source="../media/-kendall.png" alt-text="Diagram of Kendall's profile head shot and job title." :::

Kendal is a part time nurse working 20 hours a week at Region C of
Lamna Healthcare. Kendal is paid hourly, but not eligible for benefits since
they work less than 20 hours a week. Kendall belongs to the Azure 
AD groups of:
*Medical professional*, *Hourly paid*, and *Region C*. In the Viva
Connections Dashboard, Kendal sees the Shifts card, and other cards that
are available for all Lamna
employees.

:::image type="content" source="../media/-amber.png" alt-text="Diagram of Amber's profile head shot and job title." :::

Amber is a full-time people manager working at Lamna Healthcare Region
A. So, Amber belongs to the Azure AD groups of: *FTE* (Full Time Employee),
*Benefits eligible*, *People manager*, and *Region A*. In the Viva
Connections Dashboard, Amber sees the Submit time off card, the Approval
for purchase card, the Benefits self-service card, and other cards that
are available for all Lamna
employees.

#### Lamna Healthcare - audience targeting for Feed

Content in the Feed automatically gets aggregated into one central
location based on the SharePoint sites and Yammer communities that they
follow. Content in the Feed will be unique for each viewer. Some content
in the Feed can be targeted by ensuring certain Azure AD groups have visitor
permissions to [organizational news
sites](/sharepoint/organization-news-site)
and [Yammer
communities](https://techcommunity.microsoft.com/t5/yammer-blog/10-yammer-communities-considered-the-backbone-of-many-yammer/ba-p/681007)
at Lamna Healthcare. Let’s see how Lamna Healthcare employees’ Azure AD
settings for organizational news and announcements impact what they see
in their Feed:

| **Azure AD group**      | General news | Region A news | Region B news | Region C news | Region D news | News for people managers| News for finance professionals |News for medical professionals|
|---------|------|-------|-----|----------|-----------------|-----------|---------|----|
| All Employees |&check; | | | | | | | |
| People Manager |   | | || |&check; | | |
| Finance professional |  | | | | | |&check; | |
| Medical Professional |   | | | |  | | |&check; |
| Region A |   | &check;| | | | | | |
| Region B |   | | &check;| | | | | |
| Region C |   | | | &check;|  | | | |
| Region D |   | | | | &check; | | | |

Since Nicoletta works at Region D, in the Feed, Nicoletta gets news for
all Lamna Healthcare units, and local news for the Region D
hospital.

Kendall works at Region C. Therefore, in the Feed, Kendall gets news for
all Lamna Healthcare units, and local news for the Region C hospital.
As a part time nurse, Kendall also gets news specifically for
medical professionals, which are for both nurses and
physicians.

Amber works in Region A, so in the Feed, Amber gets news for all Lamna
Healthcare units, and local news for Region A. In addition, Amber gets
news specifically for people
managers.

#### Lamna Healthcare audience targeting for Resources

Navigational links that get set up in SharePoint global navigation will
display as Resources in the Viva Connections experience. These
navigational links can be filtered to specific audiences using Azure AD
groups for audience targeting. Finally, let’s see how Lamna Healthcare
employees’ Azure AD settings affect what they see in their
Resources:

| **Azure AD group**  | General resources |Benefits forms | Forms and resources for people managers |Finance forms | Resources for medical professionals |
|---------|------|-------|-----|----------|-----------------|
| All Employees |&check; | | | | |
| Hourly |   | | | | |
| Full time |   | | | | |
| Benefits eligible |   | &check;| | | |
| People Manager |   |  |&check; |&check; | |
| Finance professional |  | | |&check; | |
| Medical Professional |   | | | |&check; |

As full time employees, both Nicoletta and Amber are eligible for
benefits, so they both has access to the links to Lamna Healthcare
Benefits related pages and forms from their Viva Connections Resources
tab.

As a part time employee, Kendall doesn't belong to the Benefits Eligible Azure AD group. Therefore, Kendall doesn't see the links to Lamna Healthcare
Benefits related pages and forms from the Viva Connections Resources. As a nurse,
Kendall can see links to resources for medical
professionals.

In addition to links to benefits related resources, as a people
manager, Amber can access resources and forms for people managers and
some finance forms.
