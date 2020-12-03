# Module: Secure a Windows Virtual Desktop deployment

## Learner roles

- Administrator
- Security engineer
- Solution architect
- Technology manager

## Learner level

Beginner 

## Product(s) taught

Windows Virtual Desktop (WVD) security

## Prerequisites

To get the best learning experience from this module, you should have:

- Intermediate knowledge of Azure services such as: Core Azure compute, storage, networking, and virtualization technologies.
- Intermediate knowledge of Azure operational concepts, such as monitoring, logging, and alerting.

- Familiarity of WVD.
- Knowledge of security concepts at a fundamental level.

You’ll also need an Azure subscription to enable a WVD deployment using setup scripts. (Placeholder text: whatever additional dialogue that Marjan uses from working with the deployment scripts from Stefan Georgiev. Will be removed) 

## Module summary description

Introduction to Microsoft security capabilities that can keep your applications and data secure in your WVD deployment.

## Subtasks in this module

- Access the new WVD from the Azure Portal.
- Configure the WVD services that are delivered in a shared responsibility model.

## Lab exercise

With the successful completion of the WVD setup scripts, the student will follow the exercise steps detailed in Units 2 and 5. The exercise will increase the security of identity access and virtual host environments.

A video demo of a secure WVD environment will provide supplemental information. For the video from the Azure webinar series, refer to [Security Fundamentals for Windows Virtual Desktop Environments](https://info.microsoft.com/ww-ondemand-azure-webinar-series-security-fundamentals-for-windows-virtual-desktop-environments.html?lcid=en-us).

## Module learning objectives

After completing this module, you’ll be able to:

- Secure the user’s identity used to access their WVD environment.
- Use AppLocker to secure the downloaded desktop.

## Estimate module duration

60 minutes

## Module outline of units

### Summary of units

1. Introduction

2. Set up exercise environment

3. Enable security services of a WVD deployment

4. Exercise: Secure users identity used to access their WVD environment 

5. Secure Session Hosts and Applications

6. Enable Data Security

7. Secure Network access

8. Exercise: Secure the downloaded desktop using AppLocker 

9. Knowledge Check

10. Summary

### Unit descriptions

#### Unit 1: Introduction

**Type of unit:** Introduction unit

**Estimate unit duration:** 4 minutes

**Module scenario**

Imagine that you work for a growing financial services company in London with a branch office in New York. The company uses Microsoft 365 and a Windows Server Active Directory (AD) that’s in sync with Microsoft Azure AD and configured using Azure AD Connect. 

The IT director has asked you, their lead system engineer and Azure administrator, to evaluate the risks and benefits to using Windows Virtual Desktop to support their remote workers. The key aspects of the evaluation will be functionality, scalability, security, and cost of WVD.

After completing this module, you’ll be able to explain the responsibilities of a WVD deployment and assess its security.



#### Unit 2: Set up exercise environment

This unit will instruct the learner how to run the provided script to automatically set up their BYOS environment. 



#### Unit 3: Enable security services of a WVD deployment

**Type of unit:** Learning content unit

**Estimate unit duration:** 9 minutes

**Key content per learning objective**

After you complete this unit, you’ll understand the WVD architecture and areas of responsibility for securing the deployment.

Topics include:

- Overview of Windows Virtual Desktop architecture
- Azure security services for WVD
- Shared responsibilities of securing WVD

 

#### Unit 4: Exercise: Secure user identity used to access their WVD environment 

**Type of unit:** Exercise unit

**Estimate unit duration:** 10 minutes

**Key content per learning objective**

After you complete this unit, you’ll be able to increase the security of WVD deployment with Identity controls

- Learn how to require MFA
- Understand the value of conditional access policy for WVD

**Video**: We suggest embedding an existing Microsoft video as a supplement to the exercise for learners unable to do the exercise.



#### Unit 5: Secure session hosts and applications

**Type of unit:** Learning content unit

**Estimate unit duration:** 8 minutes

**Key content per learning objective**

After you complete this unit, you’ll understand how to protect and monitor the session hosts including RemoteApp groups and host pools.

- Configure your deployment for using the deployment options for an entire desktop or selected application.
- Understand how the security controls of Azure Defender can detect and respond to active threats on WVD hosts.
- Understand Microsoft Endpoint Manager and how it’s integrated with Intune.
- Learn how to control which applications and drivers users can run with Microsoft Defender Application Control.



#### Unit 6: Enable data security

**Type of unit:** Learning content unit

**Estimate unit duration:** 6 minutes

**Key content per learning objective**

After you complete this unit, you’ll understand how to use Azure files as persistent, stateful containers.

- Learn how to store user profiles using FSLogix containers as VHDX files.
- Understand how you can use a private link to enable a more secure data access when using Azure Files.
- Securing your data with Azure Disk Encryption
- Introduce VHDX encryption using Azure Disk Encryption.

 

#### Unit 7: Secure network access

**Type of unit:** Learning content unit

**Estimate unit duration:** 6 minutes

**Key content per learning objective**

After you complete this unit, you’ll understand how to use WVD and Azure services to help secure internet access.

- Learn how reverse connect allows you to disable all inbound ports.
- Understand how to limit WVD traffic with network security group firewall service tags.
- Learn how to use Azure Firewall for application-level protection. 

 

#### Unit 8: Exercise: Secure the downloaded desktop using AppLocker 

**Type of unit:** Exercise unit

**Estimate unit duration:** 10 minutes

**Key content per learning objective**

After you complete this unit, you’ll understand how to increase the security of WVD host. 

- Enable AppLocker
- Secure data 

 

#### Unit 9: Knowledge check

**Type of unit:** Knowledge check unit

**Estimate unit duration:** 5 minutes

Q&A of module content

 

#### Unit 10: Summary

**Type of unit:** Summary unit

**Estimate unit duration:** 3 minutes

**Resolution of module problem**

This company wanted to deploy a solution that supported their employees working remotely. This solution needed to be up-to-date, secure, and highly scalable. You found that Microsoft Windows Virtual Desktop provided its users access to every system a physical desktop would provide.

This module addressed how to add strict identity and device verification regardless of the location of the user accessing company resources. This is the basis of the Zero Trust security model. This model protects corporate data and resources while ensuring that organizations can build a modern workplace using technologies like WVD, that empower employees to be productive anytime, anywhere.

In this module, we reviewed many of the security features that create an extra layer of security that doesn’t rely only on the device itself. These features included:

- Security aspects of WVD architecture, including a shared responsibility model
- How to utilize Azure AD identity management services
- Securing session hosts and applications
- Storage security
- Network security
- Threat protection and analytics

Windows Virtual Desktop offers significant benefits to businesses including the flexibility to scale up or down, increase security, create an infrastructure, and reduce labor costs.

**Further learning links**

- [Windows Virtual Desktop documentation](https://docs.microsoft.com/azure/virtual-desktop/) 
- [What is Windows Virtual Desktop?](https://docs.microsoft.com/azure/virtual-desktop/overview)
- [Windows Virtual Desktop for the enterprise](https://docs.microsoft.com/azure/architecture/example-scenario/wvd/windows-virtual-desktop)
- [Security Fundamentals for Windows Virtual Desktop Environments](https://info.microsoft.com/ww-ondemand-azure-webinar-series-security-fundamentals-for-windows-virtual-desktop-environments.html?lcid=en-us)

 

 