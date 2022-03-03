One of the biggest concerns for users and organizations is the issue of security and privacy with respect to the Internet. Microsoft Edge helps users maintain their security and privacy, and offers several options for users to control thier information when accessing websites.

### InPrivate browsing

For enterprises that want their users to able to browse without collecting browsing history, Microsoft Edge has a privacy mode called InPrivate Browsing. This allows users to surf the web without leaving a trail. InPrivate Browsing helps protect data and privacy by preventing the browser from locally storing or retaining browsing history, temporary Internet files, form data, cookies, user names, and passwords. This leaves virtually no evidence of browsing or search history as the browsing session does not store session data.

InPrivate Browsing is a proactive feature that allows users to control what is tracked in a browsing session. InPrivate Browsing is also useful when credentials are cached, and you wish to sign-in with different credentials without clearing the cached credentials.

:::image type="content" source="../media/edge-private-browsing-281b28be.png" alt-text="Screenshot showing Microsoft Edge in InPrivate browsing mode.":::


> [!NOTE]
> Some users may attempt to use InPrivate Browsing to conceal their tracks when browsing prohibited websites, or websites that don't pertain to work. However, you can use Group Policy to configure how your organization uses InPrivate Browsing, thereby providing you with full manageability control on users’ work devices.

### Tracking protection

Most websites today contain content from several different sites. The combination of these sites, known as a mashup, is an integration that users have come to expect, and can include an embedded map from a mapping site, and greater integration of advertisements or multimedia elements. Organizations try to offer more of these experiences because it draws potential customers to their site. This capability makes the web more robust, but it also provides an opportunity for a hacker to create and exploit vulnerabilities.

Every piece of content that a browser requests from a website discloses information to that site, sometimes even if a user blocks all cookies. Often, users are not fully aware that websites are tracking their web browsing activities are tracked by websites other than those they have consciously chosen to visit.

Tracking Protection monitors the frequency of all third-party content as it appears across all websites that a user visits. You can configure what level of tracking you want allowed, such as blocking trackers from sites you haven't visted, but allowing sites you frequent to track. While it might seem like the most strict level is best, keep in mind that this could impact your browsing experience, such as how relevant ads are to the user, or social media capabilities.

> [!NOTE]
> Tracking Protection Lists can help increase your browsing privacy. When you install a Tracking Protection List, you will prevent the websites specified in the list from sending your browsing history to other content providers. Microsoft maintains a website that contains Tracking Protection Lists that you can install.

### Clear browsing data

Microsoft Edge allows uers to clear browsing data. This can be found in option found in Settings -&gt; Privacy, search and services. Users can selectively choose which information they wish to clear, as well as a time range, such as the hour, or the last day of activity. Types of information that can be cleared include the following:

 -  **Browsing history.**  Clears the history of all urls visited within the selected time range. As an alternative to InPrivate Browsing, a user can delete their browsing history manually without losing site functionality. From an enterprise and IT professional perspective, InPrivate Browsing is inherently more secure than clearing browsing history option to maintain privacy.
 -  **Download history.** Clears the list of files downloaded. Note that this does not delete the actual files downloaded.
 -  **Cookies and other site data.** Cookies and cookie protection are one aspect of online privacy. Some organizations write scripts to clean up cookies and browsing history at the end of a browsing session. This type of environment might be necessary for sensitive data, for regulatory or compliance reasons, or for private data, such as in the healthcare industry. Deleting cookies typically signs you out of any sites you are currently authenticated to.
 -  **Cached images and files.** As you browse, the content you view is downloaded and stored. This improves performance when frequenting the same websites, as the content does not re-download if it hasn't changed. Over time, this cache can grow quite large, and clearing the cache can sometimes free up a significant amount of disk space. If users are having trouble viewing a website (that is working fine on other devices), clearing the cache is a good first-step in troubleshooting.
 -  **Passwords and Autofill form data.**  These options clear saved passwords and common form data (such as an address) that may be stored.
