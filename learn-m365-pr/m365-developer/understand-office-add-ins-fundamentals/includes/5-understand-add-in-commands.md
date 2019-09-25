The Office Add-ins platform provides add-in commands so users can activate an add-in that opens a task pane or runs code behind the scenes (UI-less command). You can configure your add-in so the Office application renders a custom ribbon or menu command button&mdash;or even a group of buttons&mdash;depending on the tasks your add-in is making available to users.

![Add-in commands in Excel](../media/add-in-commands.png)

*Add-in commands in Excel on Windows*

## Excel, Word, PowerPoint, and OneNote

You can configure a custom ribbon or menu command for your add-in by including the following key areas in the manifest.

```xml
<OfficeApp
  ...
  xsi:type="TaskPaneApp">
   ...
  <VersionOverrides xmlns="http://schemas.microsoft.com/office/taskpaneappversionoverrides" xsi:type="VersionOverridesV1_0">
  ...
    <Hosts>
      <Host xsi:type="Workbook">
        <DesktopFormFactor>
          <!-- FunctionFile needed for UI-less command -->
          <FunctionFile resid="residDesktopFuncUrl" />
            <ExtensionPoint xsi:type="PrimaryCommandSurface">
              <CustomTab id="Contoso Tab">
              <!-- If you want to use a default tab that comes with Office, remove the above CustomTab element, and then uncomment the following OfficeTab element -->
              <!-- <OfficeTab id="TabData"> -->
                ...
                <Group id="Group1Id12">
                  ...
                  <Control xsi:type="Button" id="Button1Id1">
                    <!-- information about the control -->
                    ...
                    <Action xsi:type="ShowTaskpane">
                      ...
                    </Action>
                    <Action xsi:type="ExecuteFunction">
                      <FunctionName>getData</FunctionName>
                    </Action>
                  </Control>
                  <!-- other controls, as needed -->
                </Group>
              </CustomTab>
            </ExtensionPoint>
            <ExtensionPoint xsi:type="ContextMenu">
              <OfficeMenu id="ContextMenuCell">
                <Control xsi:type="Menu" id="ContextMenu2">
                  <!-- information about the control -->
                </Control>
                <!-- other controls, as needed -->
              </OfficeMenu>
            </ExtensionPoint>
          </DesktopFormFactor>
      </Host>
      <!-- Other hosts that support add-in commands: "Document", "Presentation", "Notebook" -->
    </Hosts>
  ...
  </VersionOverrides>
...
</OfficeApp>
```

## Outlook

You can configure a custom ribbon or menu command for your add-in by including the following key settings in the manifest.

```xml
<OfficeApp
  ...
  xsi:type="MailApp">
   ...
</OfficeApp>
```

## Where can you use add-in commands?

Add-in commands are available in Excel, Outlook, OneNote, PowerPoint, and Word as follows.

|Platform|Major Office version|Subscription or one-time purchase?|Notes|
|---|---|---|---|
|Windows|*Not applicable*|connected to Office 365 subscription|*Excluding OneNote*|
||2019|one-time purchase|*Excluding OneNote*|
||2016|one-time purchase|*Outlook only on Exchange 2016 (requires post-release update) or later.*|
||2013|one-time purchase|*Outlook only on Exchange 2016 or later. Requires post-release updates for Outlook and Exchange 2016.*|
|Mac|*Not applicable*|connected to Office 365 subscription|*Excluding OneNote*|
||2019|one-time purchase|*Excluding OneNote*|
||2016|one-time purchase|*Excluding OneNote*|
|iOS|*Not applicable*|connected to Office 365 subscription|*Outlook only*|
|Android|*Not applicable*|connected to Office 365 subscription|*Outlook only*|
|web browser|*Not applicable*|*Not applicable*||
