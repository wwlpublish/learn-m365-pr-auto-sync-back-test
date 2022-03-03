Performance is one of the key characteristics of great apps. It’s acceptable for an app to take a moment to load its data initially. But to be perceived as fast, the app must minimize the amount of data that it needs to retrieve initially. Further, after the app retrieves its data, it should cache it as long as reasonable for the data to stay fresh.

For example, assume that you want to display information about a person in your app:

:::image type="content" source="../media/2-mgt-person.png" alt-text="Screenshot of the Microsoft Graph Toolkit Person component, showing information about a person.":::

To show this information you would need to call Microsoft Graph three times. First, you’d retrieve the information about the person, then their picture, and finally their presence.

Now, let’s say you want to show this information not for one person but for five people. Your app will need to run 15 requests. If you need to show information about users in multiple places in your app (for example for showing messages, file authors, or meeting attendees), you might issue calls for data that has already been retrieved.

To avoid loading data that you already have, you might consider building a custom caching mechanism. But before you do, consider using Microsoft Graph Toolkit instead.

## Configure cache for Microsoft Graph Toolkit components

Microsoft Graph Toolkit components automatically cache the data they retrieve. If you need a particular piece of information in your app, it's downloaded only once, and stored in the cache until it expires. By default, Microsoft Graph Toolkit caches data for 1 hour. Information about user’s presence is cached for only 5 minutes, because presence tends to change often.

You can control cache globally but also override configuration for a specific workload if necessary. Cache settings are exposed through the **CacheService** class.

To change the cache duration for all components, change the value of the `defaultInvalidationPeriod` property:

```typescript
import { CacheService } from '@microsoft/mgt';

// set cache expiration for all components to 30 minutes
CacheService.config.defaultInvalidationPeriod = 1800000;
```

> [!NOTE]
> If you load Microsoft Graph Toolkit from a content delivery network, you can access the `CacheService` configuration through the global `mgt` variable, as follows:
>
> ```html
> <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
> <script>
>   mgt.CacheService.config.defaultInvalidationPeriod = 1800000;
> </script>
> ```

To disable the cache for all components, set the `isEnabled` property to `false`:

```typescript
import { CacheService } from '@microsoft/mgt';

// disable cache for all Microsoft Graph Toolkit components
CacheService.config.isEnabled = false;
```

> [!IMPORTANT]
> If you disable the cache for all components in Microsoft Graph Toolkit, your app might download the same data multiple times from Microsoft Graph. This will have a negative impact on your application’s performance.

To disable components from caching people data, set the `isEnabled` property of the people cache to `false`:

```typescript
import { CacheService } from '@microsoft/mgt';

// disable people cache for all Microsoft Graph Toolkit components
CacheService.config.people.isEnabled = false;
```

## Configure cache for the mgt-get component

Microsoft Graph Toolkit components cache their data per workload, such as people, photos, or groups. Such organization of the cache allows one component to load the data and other components to retrieve it from cache, without running duplicate requests. The only component that works differently is **mgt-get**.

With the **mgt-get** component, you can load and show any data from Microsoft Graph in your app. Because **mgt-get** can show arbitrary data, it has its own cache named **response**. As with any other cache object, you can configure if the **response** cache is enabled, and how long it should keep data. The **response** cache isn't used by any other component in Microsoft Graph Toolkit.

## Next steps

Let’s put what you’ve learned into practice, and change configuration settings for Microsoft Graph Toolkit components.
