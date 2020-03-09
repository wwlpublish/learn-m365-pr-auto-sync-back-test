In this unit, you'll learn how to use mocks to simulate SharePoint data when developing and testing SharePoint Framework components in the local workbench.

## Local workbench vs. the SharePoint hosted workbench

The local workbench is a great option for testing your SharePoint Framework components, but it has a significant limitation when compared to the SharePoint hosted workbench. The SharePoint hosted workbench runs in a real SharePoint environment, which means that components can use SharePoint APIs including the SharePoint REST API.

The local workbench doesn't have a real SharePoint context, which means that it has no security context and can't authenticate to call SharePoint APIs, including the SharePoint REST API. If your component calls the SharePoint REST API, it will fail when you run it in the local workbench.

While this doesn't make for a good debugging experience, there's a technique you can implement so your web part will work in both the local and SharePoint hosted workbenches. Your web part can detect the current environment and conditionally use fake data when it's running in the local workbench. This fake data is commonly referred to as *mock* data.

## Work with mock data in the SharePoint Framework

Developers can use parts of the SharePoint Framework API to detect the current runtime environment the component is currently executing within. The `Environment` object in the **\@microsoft/sp-core-library** package contains a `type` property that returns the current SharePoint environment your component is running in. You can also use the `EnvironmentType` enumeration from the same NPM package to detect the current SharePoint environment:

```typescript
private get _isSharePoint(): boolean {
  return (
    Environment.type === EnvironmentType.SharePoint
    || Environment.type === EnvironmentType.ClassicSharePoint
  );
}
```

This TypeScript method returns true if the component is running in a real SharePoint environment, either a modern SharePoint page (`EnvironmentType.SharePoint`) or the SharePoint classic experience (`EnvironmentType.ClassicSharePoint`).

The local workbench can also be detected with the `EnvironmentType.Local` option.

> [!TIP]
> The fourth option on the `EnvironmentType` enumeration is `Test`. The `Test` value indicates the component is running within a test harness which also doesn't have access to a real SharePoint Framework context.

## Conditionally calling the SharePoint REST API

Now that you have a way to detect the current SharePoint environment, you can use this method to conditionally call the SharePoint REST API when running in a real SharePoint environment. The following method uses the `_isSharePoint()` previously defined to populate an array with sample data or use the SharePoint REST API to populate the array.

```typescript
private _onGetListItems = (): void => {
  if (!this._isSharePoint) {
    /* populate the _countries array with sample data */
    this._countries = [
      { Id: '1', Title: 'Country 1' },
      { Id: '2', Title: 'Country 2' },
      { Id: '3', Title: 'Country 3' },
      { Id: '4', Title: 'Country 4' }
    ];
    this.render();
  } else {
    /* get data using the SharePoint REST API */
    this._getListItems()
      .then(response => {
        this._countries = response;
        this.render();
      });
  }
}
```

## Summary

In this unit, you'll learn how to use mocks to simulate SharePoint data when developing and testing SharePoint Framework components in the local workbench.
