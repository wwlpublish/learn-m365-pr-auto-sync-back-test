An Office Add-in's XML manifest file defines the settings and capabilities of the add-in. You can configure it to control how your add-in is rendered and behaves in the targeted Office applications.

## What the manifest defines

In the manifest, you define key information about the add-in, including:

- Add-in metadata (for example, ID, version, description, display name, default locale)
- Information about how the add-in integrates with Office (for example, target applications, custom functionality, add-in commands)
- Location of images the add-in should use for branding and command iconography
- Permissions that the add-in requires
- Dimensions of the add-in (for example, default dimensions for content add-ins, requested height for Outlook add-ins)
- Rules that specify when the add-in should activate in a message or appointment (Outlook only)

## How the manifest is used

An add-in manifest is used in the following ways:

- The Office applications where your add-in runs use information from the manifest to render add-in UI and wire up custom buttons or menu entries.
- If you publish your add-in to AppSource:
  - Information from the manifest (name, description, author, logo, etc.) is used to create the app entry that's displayed to potential customers in AppSource.
  - The AppSource validation process reads information from the manifest and validates that your add-in runs on expected platforms.
