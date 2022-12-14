In this exercise, you'll create a new SharePoint Framework project with a single client-side web part that uses React to display the results from a call to an anonymous third-party API: the [NASA Image REST API](https://images.nasa.gov/docs/images.nasa.gov_api_docs.pdf).

## Create the SharePoint Framework solution

> [!IMPORTANT]
> The instructions below assume you're using v1.15.2 of the SharePoint Framework Yeoman generator. For more information on the use of the SharePoint Framework Yeoman generator, see [Yeoman generator for the SharePoint Framework](https://aka.ms/spfx-yeoman-info).

Open a command prompt and change to the folder where you want to create the project. Run the SharePoint Yeoman generator by executing the following command:

```console
yo @microsoft/sharepoint
```

Use the following to complete the prompt that is displayed (*if more options are presented, accept the default answer)*:

- **What is your solution name?**: SPFxHttpClient
- **Which type of client-side component to create?**: WebPart
- **What is your Web part name?**: SPFxHttpClient
- **Which template would you like to use?**: React

After provisioning the folders required for the project, the generator will install all the dependency packages by running `npm install` automatically. When npm completes downloading all dependencies, open the project in **Visual Studio Code**.

## Create interfaces that reflect the results of the query

Locate the **./src** folder in the project.

Create a new folder **models** in the existing **./src** folder.

Add a new file, **INasaImageSearchResponse.ts**, to the **models** folder with the following code:

```typescript
export interface INasaItemData {
  title: string;
  keywords: string[];
  description: string;
}

export interface INasaItemLink {
  href: string;
}

export interface INasaItem {
  data: INasaItemData[];
  links: INasaItemLink[];
}

export interface INasaItemCollection {
  items: INasaItem[];
}

export interface INasaImageSearchResponse {
  collection: INasaItemCollection;
}
```

## Update the public interface for the React component

Locate and open the file **./src/webparts/spFxHttpClient/components/ISpFxHttpClientProps.ts**. This is the interface for the public properties on the React component.

Update the interface to replace the existing `description` property with a property that will hold the object that represents a NASA image. 

```typescript
import { INasaItem } from "../../../models/INasaImageSearchResponse";

export interface ISpFxHttpClientProps {
  apolloMissionImage: INasaItem;
  isDarkTheme: boolean;
  environmentMessage: string;
  hasTeamsContext: boolean;
  userDisplayName: string;
}
```

## Implement the user interface for the web part

Locate and open the file **./src/webparts/spFxHttpClient/components/SpFxHttpClient.tsx**.

Update the contents of the `render()` method to the following code. This will display an image, the title of the image, and a list of keywords associated with the image.

```tsx
public render(): React.ReactElement<ISpFxHttpClientProps> {
  return (
    <section className={`${styles.spFxHttpClient} ${this.props.hasTeamsContext ? styles.teams : ''}`}>
      <div>
        <img src={this.props.apolloMissionImage.links[0].href} />
        <div><strong>Title:</strong> {escape(this.props.apolloMissionImage.data[0].title)}</div>
        <div><strong>Keywords:</strong></div>
        <ul>
          {this.props.apolloMissionImage &&
            this.props.apolloMissionImage.data[0].keywords.map((keyword: string) =>
              <li key={keyword}>
                {escape(keyword)}
              </li>
            )
          }
        </ul>
      </div>
    </section>
  );
}
```

## Implement the web part logic

Locate and open the **./src/webparts/spFxHttpClient/SpFxHttpClientWebPart.ts** file.

Add the following `import` statements to the top of the file after the existing `import` statements:

```typescript
import {
  HttpClient,
  HttpClientResponse
} from '@microsoft/sp-http';

import { INasaImageSearchResponse } from '../../models/INasaImageSearchResponse';
```

Add the following method to the `SpFxHttpClientWebPart` class:

```typescript
private async _getApolloImage(): Promise<INasaImageSearchResponse> {
  const response: HttpClientResponse = await this.context.httpClient.get(
    `https://images-api.nasa.gov/search?q=Apollo%204&media_type=image`,
    HttpClient.configurations.v1
  );

  if (!response.ok) {
    const responseText = await response.text();
    throw new Error(responseText);
  }

  const responseJson = await response.json();
  return responseJson as INasaImageSearchResponse;
}
```

This method uses the `HttpClient` available from the current SharePoint context and issues an HTTP GET request to the NASA Image REST API with the query equal to **Apollo 4**. After processing the response to JSON, it's returned to the caller as an untyped `any` object.

Replace the `render()` method with the following code:

```typescript
protected get isRenderAsync(): boolean {
  return true;
}

public async render(): Promise<void> {
  if (!this.renderedOnce) {
    const response: INasaImageSearchResponse = await this._getApolloImage();

    const element: React.ReactElement<ISpFxHttpClientProps> = React.createElement(
      SpFxHttpClient,
      {
        apolloMissionImage: response.collection.items[0],
        isDarkTheme: this._isDarkTheme,
        environmentMessage: this._environmentMessage,
        hasTeamsContext: !!this.context.sdks.microsoftTeams,
        userDisplayName: this.context.pageContext.user.displayName
      }
    );

    ReactDom.render(element, this.domElement);
  }

  this.renderCompleted();
}

protected renderCompleted(): void {
  super.renderCompleted();
}
```

The `render()` method is replaced by three methods because asynchronous rendering is being used. In this code, we've added a check to see if the web part has already been rendered on the page. If not, it calls the `_getApolloImage()` method previously added. When it receives a response, it attaches the first item in the results returned by the NASA Imagery REST API.

## Test the web part

Locate and open the file **config/serve.json**

In the **serve.json** file, locate the `initialPage` setting. It's currently configured with a placeholder URL.

```json
"initialPage": "https://enter-your-SharePoint-site/_layouts/workbench.aspx",
```

Replace **https://enter-your-SharePoint-site** with the URL of a SharePoint Online site in your tenant. This will form a valid URL that will open the hosted workbench. The following is an example that would work in the **contoso** tenant:

```json
"initialPage": "https://contoso.sharepoint.com/sites/mySite/_layouts/workbench.aspx",
```

Execute the following command to build, start the local web server, and test the web part in the hosted workbench:

```console
gulp serve
```

If you see this warning in the hosted workbench, switch back to the command prompt, wait for the **reload** subtask to finish executing, and then refresh the hosted workbench.

![Screenshot of the gulp serve warning](../media/gulp-serve-warning.png)

Select the web part icon button to open the list of available web parts:

![Screenshot of the add web part control](../media/03-http-client-test-01.png)

Select the web part from the toolbox:

![Screenshot of the web part in the toolbox](../media/03-http-client-test-02.png)

Observe when the web part renders, it shows data from the NASA Imagery REST API:

![Screenshot of the rendered web part](../media/03-http-client-test-03.png)

Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the console/terminal window.

## Summary

In this exercise, you created a new SharePoint Framework project with a single client-side web part that uses React to display the results from a call to an anonymous third-party API: the [NASA Image REST API](https://images.nasa.gov/docs/images.nasa.gov_api_docs.pdf).
