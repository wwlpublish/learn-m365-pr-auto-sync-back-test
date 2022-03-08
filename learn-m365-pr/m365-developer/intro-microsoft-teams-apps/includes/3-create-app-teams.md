Creating and distributing an app built on the Microsoft Teams Platform involves deciding what to build, building your web services, creating an app package, and distributing that package to your target end users. It will be up to an organization's administrators to decide who can access and install your app, and it will be up to your users to install your app in any particular context. Let's look at each of those steps in a bit more detail.

## Design your app

The most important step in creating a successful app for Microsoft Teams is choosing the right combination extensibility points and UI elements to take advantage of. You should spend a good deal of time understanding the problem you're trying to solve with your app and mapping your solution across the various ways users can interact with your app in the Microsoft Teams client. Don't underestimate the importance of context and scope! A conversational bot that works well in a one-to-one chat may not work at all as part of a group chat or channel conversation.

Here's a recap of what's available for you, and some scenarios they're best suited for. You can accomplish many tasks in more than one way; choosing the right tool for the job will make for a much better user experience.

- **Messaging Extensions - search commands** are useful for allowing your users to search an external system and then share the results of that search within Teams. With cards and card actions, you can richly format the results of that search, and allow users to do actions on the result without leaving the Microsoft Teams client.
- **Messaging Extensions - action commands** are great for collecting information from your user in a single place, then sending that information to your web services. They excel in scenarios where you need to create a record of some kind, or collect more than a few pieces of information as part of a single transaction.
- **Tabs - in groups and channels** provide a shared canvas for multiple people to collaborate. You should add this to your app if you've got information or services that are applicable to a group of people. Keep in mind that everyone is working from the same canvas, your page should be stateless and operate as a single-page app.
- **Tabs - in personal apps** allow for a personal web-like experience. They're typically best for "hub" scenarios - "items assigned to me", or "things I've created". They can also be useful for static content like help or about pages.
- **Conversational bots - in groups and channels** help add additional information to a conversation that is useful for everyone (or at least most) involved. They can be used to proactively add relevant information to the conversation, or respond to user requests ("hey bot, create a poll for where we should go to lunch"). Typically they shouldn't be used for multi-turn conversations - use a task module to collect the information or move the conversation to a one-to-one chat instead, then insert the results back into the original conversation.
- **Conversational bots - in personal apps** can enable incredibly diverse workloads. Q&A bots, bots that start workflows in other systems, bots that tell jokes and bots that take notes are just a few examples. Just remember to consider if a conversation-based interface is the best way to present your functionality.
- **Webhooks & Connectors** are useful to allow users to subscribe a channel to notification messages from an external system.
- **Meeting apps** enable collaboration, partnership, informed communication, and shared feedback. The meeting app can deliver a user experience for each stage of the meeting lifecycle. Meeting lifecycle includes pre-meeting, in-meeting, and post-meeting app experience, depending on the attendee's status. In this module, you'll learn how to create custom apps to be used in Microsoft Teams meetings.

The best apps will typically take advantage of more than one extension point. For example, let's say your organization wants to allow people to submit suggestions for improvements. You could create an app with a messaging extension search command to find and share existing suggestions, add an action command to allow users to create and update suggestions, a channel tab so a team can see all suggestions assigned to them, and a personal tab so a user can see all the suggestions they've submitted in the past. Add a conversational bot powered by natural language processing and machine learning allowing users to do complex queries across the suggestions and you've got a fully featured, fully integrated Teams app!

## Prepare your development environment

At a minimum, you'll need access to an Microsoft 365 organization with custom app uploading enabled. If you don't have one, you can obtain a development organization by signing up for the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program). You'll also need a way to deploy and host your web services. For local development you can use a tunneling service like [ngrok](https://ngrok.com), but for production you'll want to deploy your services, probably to a cloud service provider like Azure. You can use on-premises infrastructure to host your web services, but they must be publicly accessible (not behind a firewall).

## Select your development environment

Developers have multiple options when building Microsoft Teams apps.

The community-based **Yeoman Generator for Microsoft Teams** (*also known as: "yo teams"*) scaffolds a project once the developer has answered a few questions for the type of Microsoft Teams app they're building. You can learn more about the Yeoman Generator for Microsoft Teams here: [Create your First Microsoft Teams App](/microsoftteams/platform/tutorials/get-started-yeoman).

The **Microsoft Teams Toolkit** enables you to create custom Teams apps directly within the **Visual Studio Code** environment. The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app. You can learn more about the Microsoft Teams Toolkit for Visual Studio Code here: [Build apps with the Microsoft Teams Toolkit and Visual Studio Code](/microsoftteams/platform/toolkit/visual-studio-code-overview).

The **Microsoft Teams Toolkit** enables you to create custom Teams apps directly within the **Visual Studio** integrated development environment (IDE). The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app. You can learn more about the Microsoft Teams Toolkit for Visual Studio Code here: [Build apps with the Microsoft Teams Toolkit and Visual Studio](/microsoftteams/platform/toolkit/visual-studio-overview)

## Build your web services

Once you've decided how users are going to interact with your app, its time to build the web services to power it. Depending on what you're creating, Teams provides various SDKs, templates, code samples, and generators to help you get started, including:

- Bot Framework SDK for messaging extensions and conversational bots
- Teams JavaScript client SDK for tabs and other content pages
- A Yeoman generator for building apps in Node.js
- A set of open-source controls for your web content pages, Fluent UI
- Ready-for-production App Templates

For the complete list of tools and samples available to help you get started, see [the complete documentation](/microsoftteams/platform/).

Remember, you'll need to host your web services in a way that makes them publicly accessible over the internet (typically in a cloud service provider like Azure), and serve up your content over HTTPS.

## Create your app package

Web services up and running, you'll need to create an app package that can be distributed and installed in Microsoft Teams. The app package contains two icons and a JSON manifest file describing the metadata for your app, the extension points your app is using, and pointers to the services powering those extension points.

When creating your app package you can choose to create it manually, or use App Studio, which is an app inside Teams that helps you make Teams apps (we know, meta). App Studio will guide you through creating your app manifest, and can help you register your bot with the Bot Framework. It also contains a card designer to help you visually create cards and card actions, and send examples to yourself in Teams.

## Distribute your app

You have three options for distributing your custom Microsoft Teams app, depending on your target audience.

- **Share your app package directly.** You can choose to share your app package directly with users. This is useful if your app is directed towards a limited audience (just a couple of teams or individuals), and during development and testing of your app.
- **Publish your app to your organizational app catalog.** If your app applies to a specific organization (or if you've customized your app to meet an organization's specific needs), a tenant administrator can upload your app to the organization's app catalog. This makes your app available for anyone in the organization to install (but doesn't automatically install it).
- **Publish your app to the public App Store.** If your app is intended for all Teams users everywhere, you can submit your app for publication in the public app store. You'll need to go through a rigorous review process, so make sure you've dotted your i's and crossed your t's.

When distributing your app you need to take into consideration not just your wanted audience, but the IT policies in place in the organization you want to share your app with. Each organization has complete control over determining which apps will be uploaded to their organizational app catalog, and which apps are available to install from the app store.

## Installing apps

Installing apps in Microsoft Teams is *context-specific*. Installing the personal app portion of your app (things that are scoped for an individual user), doesn't install your app in any particular team, and vice-versa. Installing your app in a particular team doesn't install your app in any other teams. This means you shouldn't ever assume your app is installed in all possible contexts - it probably isn't. An organization's IT administrators have complete control over who can install which apps in which context, so you also shouldn't assume the user your app is currently interacting with has the permission to install your app in a different context. For better or worse, installing an app directly from an app package tends to be heavily restricted, so if you choose to distribute your app by sharing your app package directly you'll want to make sure your users can install it.
