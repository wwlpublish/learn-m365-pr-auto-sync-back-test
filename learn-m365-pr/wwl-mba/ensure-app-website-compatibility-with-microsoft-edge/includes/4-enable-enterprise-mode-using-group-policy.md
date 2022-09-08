
Check out the video below to see how to enable Enterprise Mode through group policy, as well as some pro-tips to make things easier.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Fm7C]

As you just saw in the video, you can use group policy to configure IE mode through either the IE node or the Microsoft Edge node, and then effectively apply those policies to end users.

### Enable Internet Explorer integration using group policy

1. Download and use the latest [Microsoft Edge Policy Template](https://www.microsoft.com/edge/business/download).
1. Open Group Policy Editor (*Start &rarr; Run &rarr; GPEdit.msc*).
1. Select **Computer Configuration &rarr; Administrative Templates &rarr; Microsoft Edge**.
1. Choose **Configure Internet Explorer integration**.
1. Select **Enabled**.
1. Under **Options**, set the dropdown value to
    1. **Internet Explorer mode** if you want sites to open in IE mode on Microsoft Edge
    1. **Internet Explorer 11** if you want sites to open in a standalone Internet Explorer 11 window
    1. **None** if you want to stop users from configuring Internet Explorer mode via edge://flags or through the command line
1. Select **OK** or **Apply** to save this policy setting.

### Configure sites on the Enterprise Site list

Once you’ve configured IE integration, you can use the following group policies to configure specific sites to open in IE mode:

- [Use the Enterprise Mode IE website list](/deployedge/edge-ie-mode-policies#configure-using-the-use-the-enterprise-mode-ie-website-list-policy) (Internet Explorer node)
- [Configure the Enterprise Mode Site List](/deployedge/edge-ie-mode-policies#configure-using-the-configure-the-enterprise-mode-site-list-policy) (Microsoft Edge node, version 78 or later)

### Enterprise Site Discovery

Enterprise Site Discovery can help you configure your Enterprise Mode Site List by looking at network traffic to determine which sites actually need to be rendered in IE mode. Enterprise Site Discovery will help you:

- Discover which sites are using legacy document modes. Unless these sites are detecting modern browsers and providing different HTML, they probably need to use IE mode.
- Discover which sites are using ActiveX controls. Microsoft Edge doesn't support ActiveX controls. Unless these sites are detecting modern browsers and providing different HTML, they probably need to use IE mode.

For more information, see [Enterprise Site Discovery Step-by-Step Guide](/deployedge/edge-ie-mode-site-discovery).
