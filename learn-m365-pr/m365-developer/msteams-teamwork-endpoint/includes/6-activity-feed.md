> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4ODbx]

The Microsoft Teams activity feed enables users to see a list of relevant items specific to them. Users can use the activity feed to address changes, notifications, and other alerts in a productive manner.

In this unit, you'll learn how to use Microsoft Graph to submit notifications to the Microsoft Teams activity feed.

![Screenshot of an activity feed notification.](../media/07-test-03.png)

## Understanding the basics of activity feed notification

Activity feed notifications in Microsoft Teams are composed of multiple bits of information, displayed together, as shown in the following image.

![Screenshot breakdown of an activity feed notification.](../media/06-activity-feed-notification.png)

The notification object contains the following components, as shown in the image above:

- The actor who started the activity
- An icon that represents the activity type
- The reason the actor did the activity
- A text preview
- A time stamp
- The location of the activity

The activity feed notifications are used to inform a user of something. Microsoft Teams apps can be installed for users, teams, and group chats that mean there are three different contexts that your app can send a notification to a user:

- notify a user
- notify a user in a team
- notify a user in chat

## Requirements for sending activity feed notifications

To send a notification to a user from your custom Microsoft Teams app, you must meet the following requirements:

- For a user to receive the notification, the custom Microsoft Teams app must be installed for the recipient of the notification. This can be done by the recipient (such as a Personal app), or in a team or group chat they're associated with.
- The custom Microsoft Teams app must be associated with an Azure Active Directory (Azure AD) application.
- Notification activity types supported by your application must be defined in the application's manifest.

The first requirement is self-explanatory, so let's look at the other two requirements in more depth.

### Requirement #2: Associate the Microsoft Teams app with the Azure AD app

The first requirement is to associate the Microsoft Teams app with the Azure AD app registration created for the app. The Azure AD app is used to define permissions and ensure the app (and user) has gone through the consent process before sending notifications.

This association is defined in the Microsoft Teams app manifest file:

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.8",
  ...
  "webApplicationInfo": {
    "id": "8a2d385d-8504-43f8-a9b2-80caa44bfe22",
    "resource": "api://app.contoso.com/8a2d385d-8504-43f8-a9b2-80caa44bfe22"
  }
}
```

> [!IMPORTANT]
> Activity feed notifications are supported in the Microsoft Teams app manifest schema v1.7 or higher.

The `id` property should be set to the Azure AD app's client ID, while the `resource` should be set to the Azure AD app's URI.

### Requirement #3: Register the supported activity types

The second requirement is to register with Microsoft Teams the types of activities the app can send notifications about.

The activity registration, like the Azure AD app association, is done in the Microsoft Teams app's manifest file:

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.8",
  ...
  "activities": {
    "activityTypes": [
      {
        "type": "userMention",
        "description": "Personal Mention Activity",
        "templateText": "{actor} added the {tabName} tab to the {teamName}'s | {channelName} channel"
      }
    ]
  }
}
```

Each activity has a `type` property that must be unique in the app's manifest. This is how your API will send consistent notifications to your users. The `templateText` property contains the string that's used to display the alert message. You'll notice this is a parameterized string where your app can define the parameters. Parameters are indicated with the `{` and `}` characters.

> [!NOTE]
> A special parameter, `{actor}`, is always inserted by Microsoft Teams. It represents the name of the caller which is either the user or app that sent the activity feed notification.

## Sending activity feed notifications

Activity feed notifications are sent to users with the Microsoft Graph's `/teams/{groupId}/sendActivityNotification`  endpoint using an HTTP POST.

The body of the http request contains the details of the notification. Take the following example HTTP request payload:

```json
{
  "topic": {
    "source": "entityUrl",
    "value": "https://graph.microsoft.com/v1.0/teams/{groupId}"
  },
  "activityType": "userMention",
  "previewText": {
    "content": "New tab created"
  },
  "recipient": {
    "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
    "userId": "{recipient-objectID}"
  },
  "templateParameters": [
    { "name": "tabName", "value": "Word" },
    { "name": "teamName", "value": "Test Team" },
    { "name": "channelName", "value": "General" }
  ]
}
```

The `topic` object represents the subject of the notification - it specifies the resource being talked about in the notification. This can be either `entityUrl` or `text`. Learn more about the `topic` type: [Microsoft Graph: teamworkActivityTopic resource type](/graph/api/resources/teamworkactivitytopic).

The `activity` property must match one of the activities listed in the Microsoft Teams app's manifest file.

The `previewText` contains the text for the notification. Only the first 150 characters are shown in Microsoft Teams.

The `recipient` contains a reference to the intended recipient of the notification message.

The `templateParameters` is an array of name-value pairs that Microsoft Teams will use to replace parameterized values in the activity as defined in the Microsoft Teams app manifest file.
