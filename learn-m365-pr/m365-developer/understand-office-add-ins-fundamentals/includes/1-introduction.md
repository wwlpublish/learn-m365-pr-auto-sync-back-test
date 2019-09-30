The Office Add-ins platform enables you to extend the functionality of Office applications. Thanks to a "write once, run everywhere" strategy, your add-in should run wherever Office is supported.

## What is an Office Add-in?

An Office Add-in can enrich the user's experience within an Office application. Add-ins allow you to provide:

- Additional functionality in Office: You can incorporate external data, expose non-native functionality, and more.
- Embedded rich, interactive objects: Your add-in can insert maps, charts, and interactive visualizations into Excel spreadsheets and PowerPoint presentations.

An add-in has two main components as follows.

- A web application that defines the functionality and user interface (UI), if any, of the add-in.
- A manifest file (in XML format) that defines the add-in's settings and capabilities.

Like any other web application, the add-in must be hosted on a web server. After a user installs the add-in, the Office application reads the manifest to wire up any custom buttons in the UI and determine the location of the add-in's default page. When the add-in is activated, the web application's code is loaded and runs in a sandboxed context.

## Why Office Add-ins?

Key benefits of Office Add-ins include:

- Cross-platform support: Add-ins can run in Office on Windows, Mac, and iPad/iOS, and in a web browser.
- Centralized deployment and distribution: Office 365 administrators can deploy add-ins across their organization.
- Public availability via AppSource: By publishing your add-in to AppSource, you can make it available to the general public.
- Built using standard web technology: You can develop your add-in using your favorite framework.

## Where are Office Add-ins supported?

Office Add-ins run in various Office applications on certain clients. Add-ins also have defined types or extension points that determine how the add-in interacts with the Office application. The following table lists supported applications, clients, and add-in types. You'll learn about most of these add-in types as you progress through the remaining units in this module.

|Office application|Supported clients|Available add-in types|
|---|---|---|
|Excel|Windows, Mac, iPad, web browser|task pane, content, custom functions (excluding iPad)|
|OneNote|web browser|task pane|
|Outlook|Windows, Mac, iOS, Android, web browser|task pane, contextual, UI-less functions, module (Windows only)|
|PowerPoint|Windows, Mac, iPad, web browser|task pane, content|
|Project|Windows|task pane|
|Word|Windows, Mac, iPad, web browser|task pane|
