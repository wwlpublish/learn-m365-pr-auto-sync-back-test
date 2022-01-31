In this exercise, you'll improve on the existing Microsoft Teams meetings app by implementing the post-meeting experience.

The tab in the meeting will display the presentations delivered during the meeting and include the resources for each of the presentations that were submitted by the presenter in the pre-meeting experience.

> [!IMPORTANT]
> This exercise assumes you've created the Azure AD app and Microsoft Teams meetings app from the previous exercises in this module.

## Implement an in-meeting app stage experience

Meeting apps for Microsoft Teams can share an experience with all attendees in the meeting, just like they can share their video, screen, or share PowerPoint slides. This presentation area is referred to as the *meeting stage*.

You can use this area to provide an experience during the meeting for all meeting attendees.

### Create the stage user experience

Add the following code just after the existing `getSidepanelUX` function:

```typescript
const getMeetingStageUX = () => {
  const presenters = Object.values(
    standupTopics.filter((topic) => { return topic.approved; })
      .reduce(
        (result, standupTopic) => {
          // create presenter if !exist
          if (!result[standupTopic.presenter.name]) {
            result[standupTopic.presenter.name] = {
              presenter: standupTopic.presenter.name,
              topics: []
            };
          }

          // add topic to presenter
          result[standupTopic.presenter.name].topics.push({
            title: standupTopic.title,
            approved: standupTopic.approved,
            presented: standupTopic.presented
          });

          return result;
        }, {}
      )
  );

  // TODO: add meeting-stage code here
}
```

This code takes all stand-up topics submitted and excludes all topics that weren't approved using the `filter` function. It then uses the `reduce` function to create a new array of topics, grouped by the presenter.

Now implement the user experience. Replace the existing `// TODO: add meeting-stage code here` comment with the following code:

```tsx
return (
  <Grid columns="3" styles={{ margin: "20px", gap: "20px" }}>
    {
      sortBy(presenters, [(p: any) => p.presenter]).map(presenter => (
        <div>
          <Text content={presenter.presenter} weight="semibold" size="larger" />
          <Flex column styles={{ gap: "10px" }}>
            {
              orderBy(presenter.topics,
                ["presented", "title"],
                ["desc", "asc"]
              )
                .map(
                  (topic: any) => (
                    <Card>
                      <Text content={topic.title} size="large" />
                      {topic.presented &&
                        <Pill styles={{ background: "#E7F2DA" }}>Presented</Pill>
                      }
                    </Card>
                  )
                )
            }
          </Flex>
        </div>
      ))
    }
  </Grid>
);
```

This code creates columns of attendees and lists all the topics they were approved to present. Each topic's **presented** status is also indicated.

The last step is to tell the app to use this new function when the app is running in the side-panel of the meeting. This can be determined by the `frameContext` of the meeting.

Locate the `switch` statement for our tab that creates the user experience. It should look like the following code:

```typescript
let mainContentElement: JSX.Element | JSX.Element[] | null = null;
switch (frameContext) {
  case microsoftTeams.FrameContexts.content:
    mainContentElement = getPreMeetingUX();
    break;
  case microsoftTeams.FrameContexts.sidePanel:
    mainContentElement = getSidepanelUX();
    break;
  default:
    mainContentElement = null;
```

Add the following `case` statement to the `switch` to create our new side-panel experience when appropriate:

```typescript
let mainContentElement: JSX.Element | JSX.Element[] | null = null;
switch (frameContext) {
  case microsoftTeams.FrameContexts.content:
    mainContentElement = getPreMeetingUX();
    break;
  case microsoftTeams.FrameContexts.sidePanel:
    mainContentElement = getSidepanelUX();
    break;
  case microsoftTeams.FrameContexts.meetingStage:
    mainContentElement = getMeetingStageUX();
    break;
  default:
    mainContentElement = null;
```

## Implement the post-meeting experience

Meeting apps for Microsoft Teams can also support a post-meeting experience. This would be used to display a summary of the meeting.

For our app, the meeting stage experience is what we want to display after the meeting. However, we want to change the meeting so it will conditionally only show it after the meeting starts. Otherwise we want to show the pre-meeting experience.

Locate the `switch` statement for our tab that creates the user experience. Update the `case microsoftTeams.FrameContexts.content` statement so it conditionally shows the pre-meeting experience only if the meeting hasn't started. Otherwise, it should show the post-meeting experience:

```typescript
switch (frameContext) {
  case microsoftTeams.FrameContexts.content:
    if (onlineMeeting.startDateTime) {
      mainContentElement = ((new Date(onlineMeeting.startDateTime as string)).getTime() < Date.now())
        ? getPreMeetingUX()
        : getMeetingStageUX();
    }
    break;
  case microsoftTeams.FrameContexts.sidePanel:
    mainContentElement = getSidepanelUX();
    break;
  case microsoftTeams.FrameContexts.meetingStage:
    mainContentElement = getMeetingStageUX();
    break;
  default:
    mainContentElement = null;
}
```

## Build and test the application

Let's now test the changes made to the in-meeting stage & post-meeting experience.

If the app isn't still running from our previous test, from the command line, navigate to the root folder for the project and execute the following command:

```console
gulp ngrok-serve
```

The app manifest didn't change so we don't have to upload or update the app on our existing meetings.

Using the Microsoft Teams client, sign in with the credentials of a Work and School account of the meeting organizer.

Go back to the first meeting you previously created, the one for a date before today.

Notice when you select the meeting app, you no longer see the list of editable stand-up topics. Instead, you see the post-meeting experience:

![Screenshot of the post-meeting experience.](../media/07-post-meeting-experience.png)

Now, join the meeting and launch the meeting app.

When the side-panel loads, select the presentation icon to launch the stage. Microsoft Teams will display your stage user experience in the main window:

![Screenshot of the in-meeting stage experience.](../media/07-in-meeting-stage-experience.png)
