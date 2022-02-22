In Windows, you can configure UAC to notify you when changes are made to your computer. To do this, go to the Control Panel, select **System and Maintenance**, and then under **Action Center**, select **Change User Account Control settings**. Use the slider to determine how Windows will prompt you. The default is **Notify me only when apps try to make changes to my computer**.

:::image type="content" source="../media/user-account-control-notification-settings-73297947.jpg" alt-text="Screenshot of the UAC notification settings screen.":::


The following table identifies the four settings that enable customization of the elevation-prompt experience.

:::row:::
  :::column:::
    **Prompt**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Never notify me
  :::column-end:::
  :::column:::
    UAC is off.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Notify me only when apps try to make changes to my computer (do not dim my desktop)
  :::column-end:::
  :::column:::
    When a program makes a change, a prompt appears, but the desktop does not dim. Otherwise, the user is not prompted.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Notify me only when apps try to make changes to my computer (default)
  :::column-end:::
  :::column:::
    When a program makes a change, a prompt appears, and the desktop dims to provide a visual cue that an installation is being attempted. Otherwise, the user is not prompted.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Always notify me
  :::column-end:::
  :::column:::
    The user always is prompted when changes are made to the computer.
  :::column-end:::
:::row-end:::


You can configure varying user experiences by using different Group Policy settings. The configuration choices that you make for your environment affect the prompts and dialog boxes that standard users, administrators, or both can view.

For example, you might require administrative permissions to change the UAC setting to **Always notify me** or **Always notify me and wait for my response**. When you configure this type of configuration, a yellow notification appears at the bottom of the **User Account Control Settings** page, indicating the requirement.
