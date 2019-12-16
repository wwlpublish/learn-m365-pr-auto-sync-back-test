You can use Office Add-ins developer tools to create an Office Add-in, explore Office JavaScript APIs, and validate an Office Add-in manifest file. In this unit, you'll learn about the following tools:

- Yeoman generator for Office Add-ins
- Visual Studio
- Script Lab
- Manifest validator

## Creating an Office Add-in

You can create an Office Add-in by using the Yeoman generator for Office Add-ins or Visual Studio.

### Yeoman generator for Office Add-ins

The Yeoman generator for Office Add-ins can be used to create a Node.js Office Add-in project that can be managed with Visual Studio Code or any other editor. The generator can create Office Add-ins for:

- Excel
- OneNote
- Outlook
- PowerPoint
- Project
- Word
- Excel custom functions

You can choose to create the project using HTML, CSS, and JavaScript, or using Angular or React. TypeScript is also an option.

To create an Office Add-in project with the Yeoman generator, complete the following steps.

1. To globally install Yeoman and the Yeoman generator for Office Add-ins using npm, the Node package manager, run the following command.

    ```command&nbsp;line
    npm install -g yo generator-office
    ```

1. To create an add-in project using the Yeoman generator, run the following command.

    ```command&nbsp;line
    yo office
    ```

### Visual Studio

Visual Studio can be used to create Office Add-ins for Excel, Word, PowerPoint, or Outlook. An Office Add-in project gets created as part of a Visual Studio solution, which means you can use Visual Studio features like selecting **Start** or choosing **F5** to automatically run your add-in locally on IIS. Office Add-in projects that you create with Visual Studio use HTML, CSS, and JavaScript.

To create an Office Add-in with Visual Studio, create a new C# or Visual Basic project and choose one of the following project types:

- Excel Web Add-in
- Outlook Web Add-in
- PowerPoint Web Add-in
- Word Web Add-in

## Explore the APIs using Script Lab

Script Lab is an add-in that enables you to run Office JavaScript snippets while you're working in an Office program such as Excel or Word. It's available for free via AppSource and is a useful tool to include in your development toolkit as you prototype and verify the functionality you want in your add-in. In Script Lab, you can access a library of built-in samples to quickly try out APIs or even use a sample as the starting point for your own code.

The following video shows Script Lab in action.

[![Preview video showing Script Lab running in Excel, Word, and PowerPoint.](../media/screenshot-wide-youtube.png 'Script Lab preview video')](https://aka.ms/scriptlabvideo)

## Validating an Office Add-in's manifest file

The Office Add-ins manifest validator examines your add-in's manifest file to determine if it's correct and complete. If you created your add-in project using the Yeoman generator for Office Add-ins (version 1.1.17 or later), you can validate the manifest by running the following command in the root directory of the project.

```command&nbsp;line
npm run validate
```

If you didn't use the Yeoman generator to create your add-in project, you can validate your add-in's manifest by completing the following steps.

1. Install Node.js.
2. Run the following command in the root directory of your project. Replace `MANIFEST_FILE` with the name of your manifest file.

```command&nbsp;line
npx office-addin-manifest validate MANIFEST_FILE
```
