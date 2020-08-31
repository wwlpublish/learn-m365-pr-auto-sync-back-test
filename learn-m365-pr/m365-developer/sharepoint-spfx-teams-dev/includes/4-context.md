In this unit, you'll learn how to conditionally display information depending on whether the SharePoint Framework client-side web part is running in a SharePoint or Microsoft Teams environment.

## SharePoint Framework and Microsoft Teams context

All SharePoint components, including client-side web parts, have access to the current context. The context, available from the `this.context` object, gives your components access to details about the page the component is running on.

Your component can use the page's context, accessible from the `this.context.pageContext` object, to get information about the current site collection, site, page, and user.

Microsoft introduced a new context in the SharePoint Framework v1.8 release when they added support for deploying client-side web parts as Microsoft Teams tabs. The `this.context.microsoftTeams` object is a reference ot the `microsoftTeams` object available in the **\@microsoft/teams-js** package.

A client-side web part can detect if its running in SharePoint or Microsoft Teams by checking if the `microsoftTeams` object is set to a value or is undefined. If its `undefined`, then the component is not running in Microsoft Teams.

## Work with the Microsoft Teams context

Let's look at how your component can work with the Microsoft Teams context.

First, you need to import a reference for the **\@microsoft/teams-js** package.

Next, check to see if the component is running within Microsoft Teams and if so, get a reference to the Microsoft Teams context. This is best done in the component's `onInit()` method when its added to the page. In this code, notice how the `onInit()` method checks if the `this.context.microsoftTeams` object is defined. If its, it calls the `getContext()` method to request the Microsoft Teams context. This method passes the populated Microsoft Teams context into a callback that we can make a copy of.

Finally, using the context, your code can check if the web part is running in SharePoint or Microsoft Teams and display the current site or team name depending on the scenario.

```typescript
import * as microsoftTeams from '@microsoft/teams-js';

...

private teamsContext: microsoftTeams.Context;

...

protected onInit(): Promise<void> {
  return new Promise<void>((resolve, reject) => {
    if (this.context.microsoftTeams) {
      this.context.microsoftTeams.getContext(context => {
        this.teamsContext = context;
        resolve();
      });
    } else {
      resolve();
    }
  });
}

...

let title: string = (this.teamsContext)
  ? 'Teams'
  : 'SharePoint';

let currentLocation: string = (this.teamsContext)
  ? `Team: ${ this.teamsContext.teamName }`
  : `Site collection: ${ this.context.pageContext.web.title }`;
```

## Summary

In this unit, you learned how to conditionally display information depending on whether the SharePoint Framework client-side web part is running in a SharePoint or Microsoft Teams environment.
