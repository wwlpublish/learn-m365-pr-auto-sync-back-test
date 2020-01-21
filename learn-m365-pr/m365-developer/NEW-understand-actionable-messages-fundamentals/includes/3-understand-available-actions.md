Actionable Messages in Outlook are built on the Adaptive Card format. Outlook extends the standard Adaptive Card schema to define additional actions to support Actionable Message scenarios.

In this unit, we take a look at the following Outlook-specific actions.

- `Action.Http`
- `Action.InvokeAddInCommand`
- `Action.DisplayMessageForm`
- `Action.DisplayAppointmentForm`
- `Action.ToggleVisibility`

## Action.Http

The `Action.Http` action is the core action used to make an Actionable Message interact with your service. This action sends an HTTP POST to your service, and can include user input.

An `Action.Http` action can also be set to automatically execute when the user opens the message. This allows your card to be up-to-date when the user reads it. For example, if an expense report tool sends an approval request to multiple approvers, the card could auto-invoke an action to query the service to see if someone has already approved the report. In that case, it could replace the card asking the recipient to approve with a card informing them who approved it and when.

Your service can provide a completely new card in response to this action, referred to as a refresh card. The refresh card will permanently replace the card on that email message. Refresh cards are typically used to report back status of the action. For example, when a recipient responds to a survey Actionable Message, your service could send back a card with a thank you message, confirming their response has been recorded.

```json
{
  "type": "Action.Http",
  "title": "Send Feedback",
  "method": "POST",
  "url": "https://...",
  "body": "{{feedbackText.value}}"
}
```

## Action.InvokeAddInCommand

The `Action.InvokeAddInCommand` action invokes a task pane Outlook add-in. It supports one-click installation of the add-in, so it is not required that the recipient have the add-in already installed.

This action can be used to:

- Enable scenarios that require more complex user interactions that aren't well-suited to the Actionable Message schema, but still keep the user in Outlook by invoking an add-in.
- Help drive adoption of your Outlook add-in by giving recipients the option to one-click install your add-in to respond to a request for action.

```json
{
  "type": "Action.InvokeAddInCommand",
  "title": "Create Support Ticket with Contoso Support",
  "addInId": "527104a1-f1a5-475a-9199-7a968161c870",
  "desktopCommandId": "openTicketPane",
  "initializationContext": {
    "referenceNumber": "REF039420",
    "bucketId": 2,
    "priority": "normal"
  }
}
```

## Action.DisplayMessageForm and Action.DisplayAppointmentForm

The `Action.DisplayMessageForm` and `Action.DisplayAppointmentForm` actions are used to open an existing email message or appointment in the recipient's mailbox.

```json
{
  "type": "Action.DisplayMessageForm",
  "title": "Show me the message",
  "itemId": "AAMkAGUy...g3BZAAA="
}
```

## Action.ToggleVisibility

The `Action.ToggleVisibility` action makes it possible to show and/or hide specific elements of a card as a result of a user clicking on a button or other actionable element. This allows your Actionable Message card to be responsive, changing it's UI based on user input.

```json
{
  "type": "Action.ToggleVisibility",
  "title": "Show only unassigned issues",
  "targetElements": [
    "assignedIssues"
  ]
}
```
