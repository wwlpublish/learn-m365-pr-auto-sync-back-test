Internet Explorer 11 is the previous Microsoft web browser. Microsoft Edge has replaced Internet Explorer as a more modern web browser. While IE does not come with Windows anymore, some computers may still have it installed. It was previously recommended that IE 11 be used for legacy web applications that were developed around specific features that require Internet Explorer. This was not an ideal experience, as it often required the end user to switch between browsers. Microsoft introduced IE Mode in the Microsoft Edge browser, which allowed Edge to seemlessly render web applications designed for IE 11, negating the need to continue using Internet Explorer.

> [!NOTE]
> Internet Explorer 11 will no longer be supported after June 15, 2022.

### Internet Explorer Mode in Microsoft Edge

Internet Explorer (IE) mode was designed for organizations that still need Internet Explorer 11 for backward compatibility with legacy websites but also need a modern browser. This feature makes it easier for organizations to use one browser and not have to switch between browsers depending on which website is being used.

IE Mode uses the integrated Chromium engine for modern sites, and it uses the Trident MSHTML engine from Internet Explorer 11 (IE11) for legacy sites. When a site loads in IE mode, the IE logo indicator displays on the left side of navigation bar. You can select the IE logo indicator to display additional information.

:::image type="content" source="../media/edge-ie-mode-logo-932e1581.png" alt-text="Microsoft Edge URL bar showing the IE logo indicating Edge is in IE mode.":::


When browsing websites that use legacy IE capabilities, Microsoft Edge will not necessarily switch to IE Mode automatically. Users can manually switch to IE Mode when browsing a site that contains legacy code. Alternatively, you can configure known sites (via policy) to use IE mode. When a user navigates to a known site, the browser will automatically switch to IE Mode, while all other sites will be rendered as modern web sites.

#### Creating an Enterprise Mode Site list

In most situations, IE Mode is needed for known legacy web applications. Instead of relying on the user to switch to IE Mode, it's recommended you configure and deploy a policy to use an Enterprise Mode Site List. When used, Microsoft Edge will switch automatically to IE Mode whenever a user navigates to a site on the list.

The Enterprise Site list is an XML file containing a list of sites. There are two versions of list, a schema v.1 and a scheme v.2. You should use the v.2 version if creating a new list, and It's strongly recommended you migrate to the v.2 schema if working with an existing list using the v.1 schema.

The easiest way to create a site list is to use the built-in manager in the Microsoft Edge browser. You can access the in-browser Enterprise Site List Manager at *edge://compat/SiteListManager*. There is a stand-alone tool called the Enterprise Site List Manager (v.2), which is available for download at [https://www.microsoft.com/en-us/download/details.aspx?id=49974](https://www.microsoft.com/en-us/download/details.aspx?id=49974). Only the in-browser manager will receive future updates.

:::image type="content" source="../media/edge-site-list-manager-6a3925a9.png" alt-text="Screenshot of the Enterprise List Manager in Microsoft Edge.":::


An example of an exported XML file:

```xml
<site-list version="x">
  <site url="https://testdrive-archive.azurewebsites.net/">
    <compat-mode>Default</compat-mode>
    <open-in>IE11</open-in>
  </site>
</site-list>

```

### Enabling Microsoft Edge to use the Enterprise Mode Site list

Once the list is created, it must be deployed using a policy. When using IE Mode and an Enterprise Site list, Internet Explorer integration must be enabled and the location of the site list must be configured. To enable using Group Policy, perform the following steps:

1.  Download and use the latest Microsoft Edge Policy Template.
2.  Open Group Policy Editor.
3.  Select User Configuration/Computer Configuration &gt; Administrative Templates &gt; Microsoft Edge.
4.  Double-click **Configure Internet Explorer integration.**
5.  Select **Enabled**.
6.  Under Options, set the dropdown value to:

 -  **Internet Explorer mode** if you want sites to open in IE mode on Microsoft Edge
 -  **None** if you want to stop users from configuring Internet Explorer mode via edge://flags or through the command line

7.  In the content pane, double-click Configure the Enterprise Mode Site List.
8.  Select **Enabled**, in the Configure the Enterprise Mode Site List text box, type the url to the Enterprise Site list XML file.

> [!NOTE]
> The Internet Explorer 11 option in the dropdown values is if you want sites to open in a standalone Internet Explorer 11 window. This option will not be supported after June 15, 2022, and organizations should move away from using this option.

#### Manually enabling IE Mode in the browser

While an Enterprise Site list is recommended for ensuring known websites open in IE Mode, it's not required. Users can open settings and navigate to **edge://settings/defaultBrowser** and set the **Allow sites to be reloaded in Internet Explorer mode** to Allow. They can add sites using the **Add** option. Alternatively, if they are on a website that leverages Internet Explorer capabilities, they can select the ellipsis and select **Reload in Internet Explorer Mode**.
