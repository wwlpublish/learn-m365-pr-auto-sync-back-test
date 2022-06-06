> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OIvN]

Link unfurling is the process of taking a hyperlink pasted into a message and doing some action based on the result of processing the link. This process allows developers to do a search, or display a card.

In this unit, you’ll learn how to add link unfurling to your Microsoft Teams app and how to implement this type of messaging extension.

## Link unfurling

With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area. The `invoke` will contain the full URL that was pasted into the compose message area, and you can respond with a card the user can unfurl, providing additional information or actions. This works similarly to a search command, with the URL serving as the search term.

![Screenshot of link unfurling.](../media/07-test-01.png)

## Developing link unfurling

Adding a link unfurling messaging extension follows a similar process as action commands and search commands. You'll first register domain(s) supported by your messaging extension and then implement the handler in your web service.

### Registering link unfurling messaging extensions

The first step is to register your link unfurling messaging extension in your Microsoft Teams app manifest file. Do this by adding an entry to the `messageHandlers` property on the `composeExtensions` property:

```json
"composeExtensions": [
  {
    "botId": "<REPLACE_WITH_MICROSOFT_APP_ID>",
    "canUpdateConfiguration": false,
    "commands": [...],
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "*.wikipedia.org"
          ]
        }
      }
    ]
  }
],
"validDomains": [
  "{{HOSTNAME}}",
  "*.wikipedia.org"
]
```

The `type` property must be set to `link`.

The `value` property must contain a `domains` collection of domains that the link message handler watches for. If a link is added to a message that matches a domain listed in this collection, the message handler is invoked.

In addition to the `messageHandlers` property, all domains must also be listed in the `validDomains` property of the Microsoft Teams app's manifest.

### Respond to the message handler invocation

When a valid domain is detected by the Microsoft Teams client, the Bot Framework will send an `Activity` object to your web service of type `composeExtension/queryLink` with the URL from the message.

Your web service will respond with a similar response as the search command. However, if you return multiple attachments, only the first one in the collection will be used by the Microsoft Teams client

```typescript
export class PlanetBot extends TeamsActivityHandler {
  protected handleTeamsAppBasedLinkQuery(context: TurnContext, query: AppBasedLinkQuery): Promise<MessagingExtensionResponse> {
    // load planets
    const planets: any = require("./planets.json");
    // get the selected planet
    const selectedPlanet: any = planets.filter((planet) => planet.wikiLink === query.url)[0];
    const adaptiveCard = this.getPlanetDetailCard(selectedPlanet);

    // generate the response
    return Promise.resolve(<MessagingExtensionActionResponse>{
      composeExtension: {
        type: "result",
        attachmentLayout: "list",
        attachments: [adaptiveCard]
      }
    });
  }
}
```

## Summary

In this unit, you learned how to add link unfurling to your Microsoft Teams app and how to implement this type of Messaging extension.
