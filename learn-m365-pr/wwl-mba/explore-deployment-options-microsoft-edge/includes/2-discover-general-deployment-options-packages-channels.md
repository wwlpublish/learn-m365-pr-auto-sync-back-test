Microsoft offers many options to deploy Microsoft Edge, to users. Download options include executables that users can download, as a self-service option, and MSI-based packages that can be downloaded and used by software distribution tools for large-scale deployments. Microsoft also provides several options to control how often Microsoft Edge is updated with new features.

 

Watch this video to learn more.

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xNsg]

To recap, here are the key points discussed in the video.

 

**Deployment channels**

One of the benefits of Microsoft Edge (version 77 or later) is that Microsoft can provide new features on a regular basis. However, as the admin who deploys Microsoft Edge, you may want to have more control over how often users get new features. Microsoft provides you four options, called channels, to control how often Microsoft Edge is updated with new features. Here is an overview of the four options.

| **Channel**| **Primary purpose**| **How often updated with new features**| **Supported?** |
| --- |---|---|---|
| [Stable](/deployedge/microsoft-edge-channels)| Broad Deployment| ~6 weeks| Yes |
| [Beta](/deployedge/microsoft-edge-channels)| Representative validation in the organization| ~6 weeks| Yes |
| [Dev](/deployedge/microsoft-edge-channels)| Planning and developing| Weekly| No |
| [Canary](/deployedge/microsoft-edge-channels)| Leading-edge content| Daily| No |

Which update channel you decide to deploy to your users will depend on your business needs. To help you make this decision, review the following information about the four update channels that are available for Microsoft Edge.

 

- **Stable Channel -** The Stable Channel is intended for broad deployment in your organization and is the channel that most users should be on. It is the most stable of the channels and is the result of the stabilization of the feature set available in the prior Beta Channel release. New features ship about every six weeks. Security and quality updates ship as needed. A release from the Stable Channel is considered supported until the next release from the channel is available.

- **Beta Channel -** The Beta Channel is intended for production deployment in your organization, to a representative sample set of users. It is a supported release, and each release from Beta is supported until the next release from this channel is available. This is a great opportunity to validate that things work as expected in your environment. New features ship about every six weeks. Security and quality updates ship as needed.

- **Dev Channel -** The Dev Channel is intended to help you plan and develop with the latest capabilities of Microsoft Edge, but with higher quality than the Canary Channel. This channel is your opportunity to get an early look at what is coming next and prepare for the next Beta release.

- **Canary Channel -** The Canary Channel ships daily and is the most leading-edge of all the channels. If you want access to the newest investments, then they will appear here first. Because of the nature of this cadence, problems will arise overtime, so you may want another channel installed side by side if you are using the Canary releases.

 

**General deployment options**

 

Download package options for general deployment options include:

- [MicrosoftEdgeSetup.exe](https://www.microsoft.com/edge) - This package is what most people will see if they do a search for Microsoft Edge download. This package is best suited for end users to self-install, either as local administrators or standard users, and determines the best architecture and language configuration automatically.  This is not the package to use for business level control.

 

- [Windows installer MSI-based packages](https://www.microsoft.com/edge/business/download) – These packages are suited for large-scale deployments using non-Microsoft software distribution tools, Active Directory (AD) group policy, or automated OS deployment tools such as Microsoft Deployment Toolkit (MDT).  

 

Microsoft further simplifies the deployment options through Microsoft Endpoint Configuration Manager or Intune, as described in the subsequent modules.

 

 
