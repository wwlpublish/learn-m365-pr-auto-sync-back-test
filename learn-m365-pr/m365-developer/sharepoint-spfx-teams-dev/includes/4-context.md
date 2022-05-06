In this unit, you'll learn how to conditionally display information depending on whether the SharePoint Framework client-side web part is running in a SharePoint or Microsoft Teams environment.

## SharePoint Framework and Microsoft Teams context

All SharePoint components, including client-side web parts, have access to the current context. The context, available from the `this.context` object, gives your components access to details about the page the component is running on.

Your component can use the page's context, accessible from the `this.context.pageContext` object, to get information about the current site collection, site, page, and user.

Microsoft introduced a new context in the SharePoint Framework v1.8 release when they added support for deploying client-side web parts as Microsoft Teams tabs. The `this.context.sdks.microsoftTeams` object is a reference of the `microsoftTeams` object available in the **\@microsoft/teams-js** package.

A client-side web part can detect if it's running in SharePoint or Microsoft Teams by checking if the `microsoftTeams` object is set to a value or is undefined. If it's `undefined`, then the component isn't running in Microsoft Teams.

## Work with the Microsoft Teams context

Let's look at how your component can work with the Microsoft Teams context.

The code sample below contains a method that constructs a message indicating whether the web part is running in SharePoint or Teams, it also uses the appropriate context object to include the name of the team or SharePoint site where the web part is currently running.

```typescript
private _getEnvironmentMessage(): string {
  let message: string = "";

  if (!!this.context.sdks.microsoftTeams) { // running in Teams
    message = this.context.isServedFromLocalhost ?
      strings.AppLocalEnvironmentTeams :
      strings.AppTeamsTabEnvironment;

    message += ". Team name: " + this.context.sdks.microsoftTeams.context.teamName;
  } else {
    message = this.context.isServedFromLocalhost ?
      strings.AppLocalEnvironmentSharePoint :
      strings.AppSharePointEnvironment;

    message += ". Site name: " + this.context.pageContext.web.title;
  }

  return message;
}
```

## Summary

In this unit, you learned how to conditionally display information depending on whether the SharePoint Framework client-side web part is running in a SharePoint or Microsoft Teams environment.
