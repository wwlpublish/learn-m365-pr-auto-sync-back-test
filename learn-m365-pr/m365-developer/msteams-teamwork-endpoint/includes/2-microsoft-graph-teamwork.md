> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OyaF]

Microsoft Graph can be used to integrate your custom applications and processes. Developers can use Microsoft Graph to create new teams and channels, install apps in new teams, and pin apps to a tab in new channels, among other things.

In this unit, you'll learn how to create an application that interacts with Microsoft Teams using Microsoft Graph.

Microsoft Teams is the ultimate hub for teamwork and intelligent communications. Built on the strength and scale of Microsoft 365 with over 120 million users, Microsoft Teams delivers chat-based collaboration, meetings, calling, and enterprise voice features.

## Why integrate with Microsoft Teams?

### Automate team lifecycles

Use Microsoft Graph to create a new virtual team when a new business issue arises, add the right people to the team, and configure the team with channels, tabs, and apps. If you want to get the new team together to discuss the business issue, add a new event to the team calendar.

When the business issue is resolved and you no longer need the team, use the Microsoft Teams API to archive or delete the team. If you know the maximum duration of the team when you create it, set a Microsoft 365 group expiration policy for the team that automatically removes the team according to the policy.

### Get work done even when no one is around

Use application permissions to work with teams, channels, and tabs without human intervention. Create a new channel when your customer files an order. Automatically create teams for classes at the beginning of the school year, and archive them at the end.

### Create teams linked to your app

Let customers create new teams and channels. Install your Teams app in the new teams. Pin your app to a tab in the new channel. Send messages to the channel linking back to your website.

### Create and manage multiple teams and channels

Microsoft Graph makes it easy to create large numbers of teams and populate them with users and channels, by automate creating and managing teams, channels, tabs, and apps. Microsoft Graph also lets you find and archive the teams you're no longer using. This is the same API that the Microsoft Teams Admin Center and Teams PowerShell cmdlets are built on.

### Deploy apps to teams

List the teams in your tenant, and install apps to them. Create tabs in channels to give users easy access to apps.

### Use Microsoft Graph in any kind of app

Microsoft Teams apps give work groups a new tool to make collaboration a more productive and compelling experience. These apps let work group users share assets, interact through chat, and schedule events on the team calendar. These apps can also automate creating teams, channels, and conversations, enhancing the value of Microsoft Teams.

You can create web sites, services, and native platform applications that run outside the Microsoft Teams user experience, and call the Teams API to automate Teams scenarios.

These collaboration tools include Microsoft Graph-enabled tabs or bots running inside Microsoft Teams apps. You can also call Microsoft Graph outside of a Microsoft Teams app, such as from a website or a web service. If you've already enabled your website for Microsoft Graph, you can use that work for Microsoft Teams by using the Microsoft Teams developer platform to create a tab that uses the existing website code.

### Get notified about changes

Microsoft Teams supports subscribing to changes (create, update, and delete) to messages in channels and chats to allow apps to get near-instant updates.

## Microsoft Graph's teamwork endpoint

Let's explore some of the things you can do with Microsoft Graph's teamwork endpoint, the way you interact with Microsoft Teams with an API.

### Create teams

You can use the Microsoft Teams API in Microsoft Graph to create teams in multiple ways.

All teams are backed by Microsoft 365 groups. The quickest way to get your team up and running when you create new teams with Microsoft Graph is to set up a new Microsoft 365 group, all owners and members, and convert that into a team.

When creating a new group that will be converted to a team, you must do the following:

- set `groupTypes` = **Unified**
- set `mailEnabled` = **true**
- set `securityEnabled` = **false**

Create the group using the Microsoft Graph v1 `/groups` endpoint by submitting an HTTP POST with the group's details:

```http
POST https://graph.microsoft.com/v1.0/groups
{
  "displayName":"Flight 157",
  "mailNickname":"flight157",
  "description":"Everything about flight 157",
  "visibility":"Private",
  "groupTypes":["Unified"],
  "mailEnabled":true,
  "securityEnabled":false,
  "members@odata.bind":[
    "https://graph.microsoft.com/v1.0/users/bec05f3d-a818-4b58-8c2e-2b4e74b0246d",
    "https://graph.microsoft.com/v1.0/users/ae67a4f4-2308-4522-9021-9f402ff0fba8",
    "https://graph.microsoft.com/v1.0/users/eab978dd-35d0-4885-8c46-891b7d618783",
    "https://graph.microsoft.com/v1.0/users/6a1272b5-f6fc-45c4-95fe-fe7c5a676133"
  ],
  "owners@odata.bind":[
    "https://graph.microsoft.com/v1.0/users/6a1272b5-f6fc-45c4-95fe-fe7c5a676133",
    "https://graph.microsoft.com/v1.0/users/eab978dd-35d0-4885-8c46-891b7d618783"
  ]
}
```

Once a Microsoft 365 group has been created, you then convert it to a Microsoft Teams team with the `/teams` endpoint. To do this, submit an HTTP POST that includes the ID of the Microsoft 365 group to convert to a team:

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json
{
  "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
  "group@odata.bind": "https://graph.microsoft.com/v1.0/groups('groupId')"
}
```

### List teams

To list all teams in an organization (tenant), you find all groups that have teams, and then get information for each team.

Start by submitting a request for a list of all groups. To get a list of all groups in the organization that have teams, get a list of all groups and then in code find the ones that have a `resourceProvisioningOptions` property that contains **Team**.

Groups are large objects, so you may want to use the `$select` query parameter to only get the properties of the group you care about:

```http
GET https://graph.microsoft.com/v1.0/groups?$select=id,resourceProvisioningOptions
```

To get details on a specific team, use the `/groups` endpoint and specify the group by its ID:

```http
GET https://graph.microsoft.com/v1.0/teams/{group-id}
```

> [!TIP]
> When working with the Microsoft Teams support in Microsoft Graph, keep in mind a team has two types of IDs. The `groupID` for a team is in the format of a GUID while the `teamID` can be in the format of `19:[id]@thread.skype`.

### List all teams the current user has joined

You can also use Microsoft Graph to obtain a list of all teams the current user has joined.

```http
GET https://graph.microsoft.com/v1.0/me/joinedTeams
```

## Protected APIs in Microsoft Teams

Some APIs related to Microsoft Teams exposed by Microsoft Graph access sensitive data. These are considered *protected APIs* and require more validation beyond the typical permissions and consent other APIs require.

In order for your app to use one of the protected APIs, you must submit a request to Microsoft for review. You can learn more about protected APIs, including which APIs are included in this list and the review process from the Microsoft Graph documentation: [Microsoft Graph: Protected APIs in Microsoft Teams](/graph/teams-protected-apis)
