The manifest enables you to configure your Office add-in, including how the add-in behaves and shows up in the targeted Office applications.

## What the manifest defines and declares

In the manifest, you declare key information about the add-in, including:

- Information about the add-in
  - Examples: ID, version, description, display name, default locale
- Office integration
  - Examples: target applications, custom functionality, custom ribbon buttons
- Brand images and command iconography
- Required permissions
- Add-in dimensions
  - Default dimensions for content add-ins
  - Requested height for Outlook add-ins
- (Outlook only) Rules for when add-ins should activate in a message or appointment

## What reads the manifest and why

|Reads the manifest|Why?|
|---|---|
|AppSource|Displays add-in info to potential customers and validates add-in runs on expected platforms.|
|Office application|Displays any add-in UI and custom buttons or menus.|
