:::image type="content" source="../media/step-7-wheel.png" alt-text="Step 7 highlighted on deployment wheel." border="false":::

:::image type="icon" source="../media/step-7-icon.png" :::

Windows servicing updates fall into two main categories: **feature updates** and **quality and security updates**, which contain cumulative security, reliability, and bug fixes.

Both Windows 10 and Microsoft 365 Apps deliver:

- A semi-annual feature update that delivers new features twice per year.
- A monthly quality and security update.

Additionally, for Office applications, Microsoft offers a fully supported **monthly channel** option where updates, available every month, contain both new features and quality updates.

## Semi-annual feature updates

In order to manage larger and semi-annual updates, you can use policy settings with Windows Update for Business, software update management via Microsoft Endpoint Configuration Manager, Windows Server Update Services (WSUS), or policies set by Microsoft Intune. If network bandwidth is a concern, consider one of the options to reduce network traffic - delivery optimization, Express Updates, and other peer-to-peer caching technologies.

The support timeline for updates depends on the specific product you're using. You can review the timelines at <https://support.microsoft.com/lifecycle/> selectindex - search for the product you're using, like "Windows 10, version 1903" (a semi-annual channel release) to see the exact support duration.

## Monthly quality and security updates

Quality and security updates are delivered using a cumulative model – each subsequent update incorporates all preceding updates in it. Delivering quality and security updates as a cumulative update package corrects many past issues, from inconsistent and lengthy sets of test matrices for support to hours or days of deployment time. The monthly servicing model is designed to give you flexibility to limit the roll-out of new features to twice per year, and if needed to even skip a feature update, while still receiving quality and security updates. It's important, though, to keep in mind that the cumulative nature of monthly updates means the update increases in size each month.

With the cumulative model, your PCs are always one update away from being current, so there are fewer monthly updates you have to deploy. Each update builds on updates from previous months and contains all the fixes that are needed to get current. Cumulative updates are especially helpful when a PC has been turned off for several months.

### Explore Windows 10 servicing options

View a [video version](https://www.microsoft.com/videoplayer/embed/RE44DnU) of the interactive guide (captions available in more languages).

[:::image type="content" source="../media/lab-servicing-options.png" alt-text="Discover servicing options for Windows 10." border="false":::](https://mslearn.cloudguides.com/guides/Discover%20servicing%20options%20for%20Windows%2010)

Be sure to click the full-screen option in the video player. When you're done, use the **Back** arrow in your browser to come back to this page.
