Developers creating custom Microsoft Teams meetings apps can implement different experiences for meeting participants depending on the participants role in the meeting and the lifecycle of the meeting.

In this unit, learn how to use the Microsoft Teams SDK to determine the current lifecycle stage of the meeting and the participant’s role to present context aware experiences to each user.

## Determine current meeting lifecycle

Developers can conditionally show different content in custom meeting apps based on the current lifecycle of the meeting. The different lifecycle options include:

- **pre-meeting**: This experience is shown in the meeting details as a tab before the meeting starts or concludes.
- **in-meeting**: This experience is shown in the meeting's side-panel or stage as a tab when a meeting is in process.
- **post-meeting**: This experience is shown in the meeting details as a tab after the meeting starts or concludes.

The **in-meeting** lifecycle is only implemented in the meetings side-panel or meeting stage as those are only available when the meeting is currently in process.

However, the **pre-meeting** and **post-meeting** experiences are determined by checking the time of the meeting.

For example, to display one experience for the **pre-meeting** lifecycle of the meeting, and another for the **post-meeting** lifecycle, and you define the start time of the meeting as the breakpoint between the two, you could do something like the following:

```tsx
const mainContentElement = (
    (new Date(onlineMeeting.startDateTime as string)).getTime() < Date.now()
  ) ? getPreMeetingUX() : getPostMeetingUX();

return (
  <Provider theme={theme}>
    <RTProvider themeName={TeamsTheme[themeString.charAt(0).toUpperCase() + themeString.slice(1)]} lang="en-US">
      {mainContentElement}
    </RTProvider>
  </Provider>
);
```

## Determine current meeting context

Developers can conditionally show different content in custom meeting apps based on the current context where the tab is loaded.

Meeting apps can be rendered in the following locations:

- **content**: This is the main area of a meeting, where the **Details** and **Files** tab is found. This is commonly used for the pre-meeting and post-meeting experience.
- **sidePanel**: The side panel is available when the current user has joined an in-process meeting. It enables developers to implement an experience that's targeted to the currently signed in user. The side panel occupies the same location where the meeting chat and participant list are displayed.
- **stage**: The meeting stage is the main presentation area of the meeting. This is where presentations and screen-sharing are displayed during a meeting. Using the stage, the meeting app developer can create an experience that's presented to all attendees in the meeting.

The current meeting context is available to developers using the Microsoft Teams `context` object that's passed into custom apps. The `context` object contains a property, `frameContext`, that's set to one of the three values for meeting apps.

The Yeoman generator for Microsoft Teams includes the NPM package [msteams-react-base-component](https://www.npmjs.com/package/msteams-react-base-component) that contains a React hook `useTeams()` based on the Microsoft Teams JavaScript SDK.

In your meeting app tab, use this React hook to get the tab's current context:

```typescript
import { useState, useEffect } from "react";
import { useTeams } from "msteams-react-base-component";
import * as microsoftTeams from "@microsoft/teams-js";

const [{ inTeams, context }] = useTeams();
const [meetingId, setMeetingId] = useState<string | undefined>();
const [frameContext, setFrameContext] = useState<microsoftTeams.FrameContexts | null>();
```

Use the React hook `useEffect()` to execute whenever the `context` object is set:

```typescript
useEffect(() => {
  if (context) {
    setMeetingId(context.meetingId);
    setFrameContext(context.frameContext);
  }
}, [context]);
```

Your tab can then use the `frameContext` state object to conditionally create return different user experiences based on where the tab is loaded:

```tsx
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
}

return (
  <Provider theme={theme}>
    <RTProvider themeName={TeamsTheme[themeString.charAt(0).toUpperCase() + themeString.slice(1)]} lang="en-US">
      {mainContentElement}
    </RTProvider>
  </Provider>
);
```

## Determine current meeting attendee role

Developers can conditionally show different content in custom meeting apps based on the role of the current user. Your app could show one experience and provide some capabilities to meeting organizers, while all other meeting attendees received a different experience.

One way to do this is using a React hook as the other previous examples have done:

```typescript
const [onlineMeeting, setOnlineMeeting] = useState<OnlineMeeting>({});
const [currentUserId, setCurrentUserId] = useState<string>("");
const [currentUserIsOrganizer, setCurrentUserIsOrganizer] = useState<boolean>(false);
```

In this example, the `onlineMeeting` state property is set after retrieving the details of the current meeting using Microsoft Graph. The **OnlineMeeting** type is from the Microsoft Graph type package [@microsoft/microsoft-graph-types-beta](https://www.npmjs.com/package/@microsoft/microsoft-graph-types-beta).

Using a React hook, you can set the `currentUserIsOrganizer` state property when the other two state properties change:

```typescript
useEffect(() => {
  if (onlineMeeting && currentUserId && onlineMeeting?.participants?.organizer?.identity?.user?.id === currentUserId) {
    setCurrentUserIsOrganizer(true);
  } else {
    setCurrentUserIsOrganizer(false);
  }
}, [currentUserId, onlineMeeting]);
```

Your meeting app's tab could then use this state property flag to do things like disable controls that for attendees who aren't the meeting organizers:

```tsx
<Checkbox toggle
          label="Presented"
          checked={topic.presented}
          disabled={!setCurrentUserIsOrganizer} />
```
