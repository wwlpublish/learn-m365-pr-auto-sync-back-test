Several tools can help you explore Office Add-ins functionality and set up your own add-in. In this unit, you'll learn about a few of them:

- Yeoman generator for Office Add-ins
- Script Lab
- Manifest validator
- Visual Studio

## Yeoman generator for Office Add-ins

To scaffold an Office Add-ins project using Node.js quickly and easily, use Yeoman generator for Office Add-ins. This tool creates the files for Office Add-ins that use Excel, OneNote, Outlook, PowerPoint, Project, Word, and Excel custom functions. Choose from a variety of options for the automatically generated scaffolded files, including a plain HTML, CSS, and JavaScript template. You can also choose other frameworks and languages, such as Angular, React, or TypeScript.

To use this tool:

1. Install Yeoman and `generator-office` globally using NPM. In the command line, use the following command.

    ```command&nbsp;line
    npm install -g yo generator-office
    ```

1. Run the following command to set up a project.

    ```command&nbsp;line
    yo office
    ```

## Script Lab

The Script Lab add-in, which is available free from AppSource, enables you to explore the Office JavaScript API while you're working in an Office program such as Excel or Word. Script Lab is a convenient tool to add to your development toolkit as you prototype and verify functionality you want in your add-in. Through Script Lab, you can access a library of samples to quickly try out features or you can use a sample as the starting point for your own code. You can even use Script Lab to try preview APIs.

The following video shows Script Lab in action.

[![Preview video showing Script Lab running in Excel, Word, and PowerPoint.](../media/screenshot-wide-youtube.png 'Script Lab preview video')](https://aka.ms/scriptlabvideo)

## Manifest Validator

The Office Add-ins manifest validator tool examines your project's manifest file for errors and ensures it's correct and complete. If you created a project using the Yeoman generator for Office Add-ins version 1.1.17 or later, the validator requires running the following command in the root directory of your project.

```command&nbsp;line
npm run validate
```

If you didn't use the Yeoman generator for your project, you can still validate your project's manifest.

1. Install Node.js.
2. Run the following command in the root directory of your project. Replace `MANIFEST_FILE` with the name of the manifest file.

```command&nbsp;line
npx office-addin-manifest validate MANIFEST_FILE
```

## Visual Studio

Visual Studio can be used to create Office Add-ins for Excel, Word, PowerPoint, or Outlook. Visual Studio offers a few built-in features, including the automatic hosting of your web application on your local IIS server and the ability to use IntelliSense, a code-completion aid.

In Visual Studio, choose a new project and create a scaffolded Visual C# or Visual Basic Office add-in project. It creates a manifest file, along with the basic script, CSS, and HTML files for the web application component of your add-in.

> [!NOTE]
> If you prefer to use Typescript or Angular 2+ for your project in Visual Studio, it's possible with some modifications to the automatically generated scaffolded files.
