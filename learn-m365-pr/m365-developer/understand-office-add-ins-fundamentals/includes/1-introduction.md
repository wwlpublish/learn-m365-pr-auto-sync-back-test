The Office Add-ins platform enables you to extend the functionality of Office applications to suit your needs. Thanks to a "write once, run everywhere" strategy, your add-in should run wherever Office is supported.

## What is an Office Add-in?

An Office Add-in can enrich the user's experience within an Office application. Add-ins allow you to provide:

- Additional functionality in Office: You can incorporate external data, expose non-Microsoft functionality, and more. 
- Embedded rich, interactive objects: Through your add-in, users can embed maps, charts, and interactive visualizations into their Excel spreadsheets and PowerPoint presentations.

Each add-in has two main components:

- Manifest (XML) for configuration
- Webpage (HTML, JavaScript) for functionality

Like any other web application, the add-in should be hosted on a web server (your own or through a service like Microsoft Azure). After a user installs the add-in, the Office application reads the manifest to hook up any custom buttons in the UI. When the add-in is activated, the web code is loaded and runs in a sandboxed browser context.

## Why Office Add-ins?

Benefits of Office Add-ins include the following.

- Cross-platform support: Add-ins can run in Office on the web, Windows, Mac, and iPad/iOS.
- Centralized deployment and distribution: Administrators can deploy add-ins across their organization.
- Available on AppSource: The general public can download and use your add-in solution.
- Based on standard web technology: You can develop your add-in using your favorite library.

## Where are Office Add-ins supported?

Office Add-ins run in various Office applications on certain clients. Add-ins also have defined types or extension points, which determine how the add-in interacts with the Office application. The following table maps supported applications, clients, and add-in types.

|Office application|Supported clients|Available add-in types|
|---|---|---|
|Excel|Windows, Mac, iPad, web browser|task pane, content, custom functions|
|OneNote|web browser|task pane|
|Outlook|Windows, Mac, iOS, Android, web browser|task pane, contextual, UI-less functions|
|PowerPoint|Windows, Mac, iPad, web browser|task pane, content|
|Project|Windows|task pane|
|Word|Windows, Mac, iPad, web browser|task pane|