In this exercise, you'll create a new SharePoint Framework project with a single client-side web part that uses React and Microsoft Graph to display users in the currently logged in user's directory. You'll use the Azure AD HTTP client API included in the SharePoint Framework to authenticate and call the Microsoft Graph REST API.

## Create the SharePoint Framework solution

> [!IMPORTANT]
> The instructions below assume you are using v1.13.1 of the SharePoint Framework Yeoman generator.

Open a command prompt and change to the folder where you want to create the project. Run the SharePoint Yeoman generator by executing the following command

```console
yo @microsoft/sharepoint
```

Use the following to complete the prompt that is displayed (*if additional options are presented, accept the default answer)*:

- **What is your solution name?**: SPFxAadHttpClient
- **Only SharePoint Online (latest) is supported. For earlier versions of SharePoint (2016 and 2019) please use the 1.4.1 version of the generator.**: SharePoint Online only (latest)
- **Do you want to allow the tenant admin the choice of being able to deploy the solution to all sites immediately without running any feature deployment or adding apps in sites?**: No
- **Will the components in the solution require permissions to access web APIs that are unique and not shared with other components in the tenant?**: No
- **Which type of client-side component to create?**: WebPart
- **What is your Web part name?**: SPFxAadHttpClient
- **What is your Web part description?**: SPFxAadHttpClient description
- **Which framework would you like to use?**: React

After provisioning the folders required for the project, the generator will install all the dependency packages by running `npm install` automatically. When NPM completes downloading all dependencies, open the project in **Visual Studio Code**.

## Create an interface that reflects the results of the query

Locate the **./src** folder in the project.

Create a new folder **models** in the existing **./src** folder.

Add a new file, **IUserItem.ts**, to the **models** folder with the following code:

```typescript
export interface IUserItem {
  id: string;
  mail?: string;
  displayName?: string;
}
```

## Implement the user interface for the web part

Update the public interface of the React component to accept a collection of users.

Locate and open the file **./src/webparts/spFxAadHttpClient/components/ISpFxAadHttpClientProps.ts**.

Update the contents of the file to match the following code:

```typescript
import { IUserItem } from '../../../models/IUserItem';

export interface ISpFxAadHttpClientProps {
  userItems: IUserItem[];
}
```

Locate and open the file **./src/webparts/spFxAadHttpClient/components/SpFxAadHttpClient.module.scss**.

Add the following classes to the bottom of the file, immediately before the closing `}`:

```scss
.list {
  color: $ms-color-themeDark;
  background-color: $ms-color-themeLight;
  font-family: 'Segoe UI Regular WestEuropean', 'Segoe UI', Tahoma, Arial, sans-serif;
  font-size: 14px;
  font-weight: normal;
  box-sizing: border-box;
  margin: 0 0;
  padding: 10px 0 100px 0;
  line-height: 50px;
  list-style-type: none;
}

.item {
  color: $ms-color-themeDark;
  background-color: $ms-color-themeLighterAlt;
  vertical-align: center;
  font-family: 'Segoe UI Regular WestEuropean', 'Segoe UI', Tahoma, Arial, sans-serif;
  font-size: 14px;
  font-weight: normal;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  box-shadow: none;
  *zoom: 1;
  padding: 0 15px;
  position: relative;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
}
```

Locate and open the file **./src/webparts/spFxAadHttpClient/components/SpFxAadHttpClient.tsx**.

Update the markup returned by the `render()` method to the following code. This will create a list using the CSS classes with each item displaying the properties of a user returned from the call to Microsoft Graph:

```tsx
<div className={ styles.spFxAadHttpClient }>
  <div className={ styles.container }>
    <div className={ styles.row }>
      <div className={ styles.column }>
        <span className={ styles.title }>AadHttpClient Demo</span>
      </div>
    </div>

    <div className={ styles.row }>
      <div><strong>Mail:</strong></div>
      <ul className={ styles.list }>
        { this.props.userItems &&
          this.props.userItems.map((user) =>
            <li key={ user.id } className={ styles.item }>
              <strong>ID:</strong> { user.id }<br />
              <strong>Email:</strong> { user.mail }<br />
              <strong>DisplayName:</strong> { user.displayName }
            </li>
          )
        }
      </ul>
    </div>

  </div>
</div>
```

## Call Microsoft Graph

Locate and open the file **./src/webparts/spFxAadHttpClient/SpFxAadHttpClientWebPart.ts**.

Add the following `import` statements immediately following the existing `import` statements:

```typescript
import { IUserItem } from '../../models/IUserItem';
import {
  AadHttpClient,
  HttpClientResponse
} from '@microsoft/sp-http';
```

Add the following method to the `SpFxAadHttpClientWebPart` class.

This method will first obtain an instance of the Azure AD HTTP client that has been configured with the necessary details, including the authentication HTTP header, to call Microsoft Graph.

It will then use that `aadClient` object to issue an HTTP GET request to Microsoft Graph endpoint, requesting the first 10 users for the current logged in user.

Once a response is received, the body is processed as JSON and the collection of users is resolved in the JavaScript promise:

```typescript
private _getUsers(): Promise<IUserItem[]> {
  return new Promise<IUserItem[]>((resolve, reject) => {
    this.context.aadHttpClientFactory
      .getClient('https://graph.microsoft.com')
      .then((aadClient: AadHttpClient) => {
        const endpoint: string = 'https://graph.microsoft.com/v1.0/users?$top=10&$select=id,displayName,mail';
        aadClient.get(endpoint, AadHttpClient.configurations.v1)
          .then((rawResponse: HttpClientResponse) => {
            return rawResponse.json();
          })
          .then((jsonResponse: any) => {
            resolve(jsonResponse.value);
          });
      });
    });
}
```

Update the contents of the `render()` method to the following code:

```typescript
public render(): void {
  if (!this.renderedOnce) {
    this._getUsers()
      .then((results: IUserItem[]) => {
        const element: React.ReactElement<ISpFxAadHttpClientProps > = React.createElement(
          SpFxAadHttpClient,
          {
            userItems: results
          }
      );

      ReactDom.render(element, this.domElement);
    });
  }
}
```

In this code, we've added a check to see if the web part has already been rendered on the page. If not, it calls the `_getUsers()` method previously added.

## Update the package permission requests

The last step before testing is to notify SharePoint that upon deployment to production, this app requires permission to Microsoft Graph API.

Open the **./config/package-solution.json** file.

Locate the `solution` section. Add the following permission request element just after the property `isDomainIsolated`:

```json
"webApiPermissionRequests": [
  {
    "resource": "Microsoft Graph",
    "scope": "User.ReadBasic.All"
  }
],
```

## Create the SharePoint package for deployment

Build the solution by executing the following command on the command line:

```console
gulp build
```

Bundle the solution by executing the following command on the command line:

```console
gulp bundle --ship
```

Package the solution by executing the following command on the command line:

```console
gulp package-solution --ship
```

## Deploy and trust the SharePoint package

In the browser, navigate to your SharePoint Online Tenant App Catalog.

> [!TIP]
> Creation of the Tenant App Catalog site is one of the steps in the **[Getting Started > Set up Office 365 Tenant](/sharepoint/dev/spfx/set-up-your-developer-tenant)** setup documentation.

Select the **Apps for SharePoint** link in the navigation:

![Screenshot of the navigation in the SharePoint Online Tenant App Catalog](../media/tenant-app-catalog-01.png)

Drag the generated SharePoint package from **/sharepoint/solution/sp-fx-aad-http-client.sppkg** into the **Apps for SharePoint** library.

In the **Do you trust sp-fx-aad-http-client-side-solution?** dialog, select **Deploy**.

![Screenshot of trusting a SharePoint package](../media/05-azure-ad-add-package-01.png)

## Approve the API permission request

Navigate to the SharePoint Admin Portal located at **https://{{REPLACE_WITH_YOUR_TENANTID}}-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx**, replacing the domain with your SharePoint Online's administration tenant URL.

In the navigation, select **Advanced > API access**:

![Screenshot of the API management page](../media/sharepoint-admin-portal-01.png)

Select the **Pending approval** for the **Microsoft Graph** permission **User.ReadBasic.All**.

![Screenshot of the permission requests pending approval](../media/sharepoint-admin-portal-02.png)

Select the **Approve** button, then select the **Approve** button in the **Approve access** dialog.

## Test the web part

> [!NOTE]
> The SharePoint Framework includes a SharePoint-hosted workbench for testing custom solutions. However, the workbench will not work the first time when testing solutions that utilize Microsoft Graph due to nuances with how the workbench operates and authentication requirements. Therefore, the first time you test a Microsoft Graph enabled SPFx solution, you will need to test it in a real modern page.
>
> Once this has been done and your browser has been cookied by the Azure AD authentication process, you can leverage local webserver and SharePoint-hosted workbench for testing the solution.

### Add the web part to your site collection

In a browser, navigate to a SharePoint Online site.

In the Office 365 gear, select **Add an app**.

In site navigation, select **From my organization**.

Select the **Add** button in the **sp-fx-aad-http-client-side-solution** tile to add your web part.

![Screenshot of the Apps you can add dialog](../media/05-add-app.png)

### Test the web part on a SharePoint Online modern page

In the site navigation, select the **Pages** library.

Select an existing page or create a new page in the library to test the web part on.

![Screenshot of the SharePoint Online Pages library](../media/add-page-01.png)

In the browser, select the Web part icon button to open the list of available web parts:

![Screenshot of adding the web part to the modern SharePoint page](../media/add-web-part-01.png)

Search for the **SPFxAadHttpClient** web part and select it

![Screenshot of adding the web part to the modern SharePoint page - Web part gallery](../media/05-add-web-part-02.png)

When the page loads, notice after a brief delay, it will display a list of users:

![Screenshot of the web part running in a modern SharePoint page - web part on the page](../media/05-test-01.png)

## Summary

In this exercise, you created a new SharePoint Framework project with a single client-side web part that used React and Microsoft Graph to display users in the currently logged in user's directory. You used the Azure AD HTTP client API included in the SharePoint Framework to authenticate and call the Microsoft Graph REST API.
