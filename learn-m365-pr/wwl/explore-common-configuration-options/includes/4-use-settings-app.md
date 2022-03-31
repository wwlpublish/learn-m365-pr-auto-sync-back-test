Windows continues to use many of the same computer controls that previous Windows versions have included, such as the Control Panel. However, in Windows, many of the Control Panel functions are available in the Settings app. The Settings app contains several settings that you can use to configure your device. While the UI in Windows 10 and 11 are different, you will find many settings in the same or similar locations.

:::row:::
  :::column:::
    **Windows 10 Settings App**
  :::column-end:::
  :::column:::
    **Windows 11 Settings App**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    :::image type="content" source="../media/windows-10-settings-app-b4388dfa.png" alt-text="Screenshot of the Windows 10 settings app showing the main settings categories." lightbox="../media/windows-10-settings-app-b4388dfa.png":::

  :::column-end:::
  :::column:::
    :::image type="content" source="../media/windows-11-settings-app-9bcdddb2.png" alt-text="Screenshot of the Windows 11 settings app showing the main categories, with the System category selected by default." lightbox="../media/windows-11-settings-app-9bcdddb2.png":::

  :::column-end:::
:::row-end:::


You can access the Settings app in any of the following ways:

 -  Open the **Action Center**, and in the lower portion, select the **All Settings** tile (Windows 10) or icon (Windows 11).
 -  Select the **Start** menu icon, and then select **Settings** on the menu.
 -  Type **Settings** in the search box located on the taskbar, and then press **Enter**.

The Settings app page has separate icons that represent the main categories that you can configure. When you select any of these icons, you will access a page with subcategories that appear in a console tree on the left of the page. Depending on the subcategory that you select, more items and configurable settings appear in the details pane.

Desktop Administrators may wish to restrict users from accessing certain settings within the settings app. This can be controlled by group policy as either a user or computer policy in the **Administrative Templates** &gt; **Control Panel** &gt; **Settings Page Visibility** path. Policies can either specify settings pages that are only shown, or alternatively, specify a list of settings pages that are hidden.

> [!NOTE]
> Group Policy is covered in more depth in the next lesson.
