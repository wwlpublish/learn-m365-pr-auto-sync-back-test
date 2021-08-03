---
metadata:
  unitType: designdoc
  title: Design Doc
  description: Understand the process of setting up tenant attach.
  ms.date: 8/03/2021
  author: Erikre
  ms.author: erikre
  ms.topic: interactive-tutorial
  ms.prod: learning-endpoint-manager
---

# Title

Setup cloud-attach using Microsoft Endpoint Configuration Manager

## Role(s)

- Administrator

## Level

- Beginner

## Product(s)

- Microsoft Endpoint Manager
- Microsoft 365
- Microsoft Intune

## Prerequisites

- Basic knowledge of endpoint management
- Basic knowledge of Microsoft Endpoint Manager, Microsoft Intune

## Summary

Microsoft Endpoint Configuration Manager, which is a part of Microsoft Endpoint Manager, helps you protect the on-premises devices, apps, and data that the people at your organization use to be productive. After completing this module, you will understand and enable tenant attach, which is the first step to cloud attach your on-premises devices.

In this module, you'll step through the process of setting up tenant attach. When you're complete, you'll have connected your Configuration Manager implementation to your cloud tenant. All of these steps will prepare you to add and manage devices and apps from Microsoft Endpoint Manager, whether your endpoints are on-premises or cloud-based.

## Learning objectives

In this module, you will:

- Understand tenant attach
- Confirm tenant attach prerequisites
- Enable internet endpoints
- Enable device upload
- Display the connector status
- Perform device actions
- View on-premises device details

## Chunk your content into subtasks

Identify the subtasks of *Setup cloud-attach using Microsoft Endpoint Configuration Manager*

| Subtask | What part of the introduction scenario does this subtask satisfy? | How will you assess it: **Exercise or Knowledge check**? | Which learning objective(s) does this help meet? | Does the subtask have enough learning content to justify an entire unit? If not, which other subtask will you combine it with? |
| ---- | ---- | ---- | ---- | ---- |
| Understand tenant attach | Understand the primary end user needs that should be addressed. | Knowledge check | 1 | Yes |
| Confirm tenant attach prerequisites | Step through the process of signing up for Microsoft Intune. | Knowledge check | 2 | Yes |
| Enable internet endpoints | Configure the Intune tenant domain name | Knowledge check | 3 | Yes |
| Enable device upload | Configure the Intune tenant domain name | Knowledge check | 4 | Yes |
| Display the connector status | Display the connector status | Knowledge check | 4,5 | Yes |
| Perform device actions | Perform device actions | Knowledge check | 4,5 | Yes |
| View on-premises device details | View on-premises device details | Knowledge check | 4,5 | Yes |

## Outline the units

1. **Introduction**

Suppose that you're the administrator or business decision maker of a company with several thousand employees. You need to keep your corporate data safe by protecting data, apps, and devices that your employees use, as well as keep your employees productive and maximize the return on your endpoint management investment. You and your company have determined that you need to manage aspects of both your on-premises endpoints, as well as your cloud-based endpoints. Microsoft Endpoint Manager provides this capability by using cloud attach. The first part of cloud attach is called tenant attach. The second part of cloud attach is called co-management. Each can be completed independently and neither requires the other.
    
2. **Understand tenant attach**

    List the content that will enable the learner to understand this module:
    - Enabling objective
        - Understand tenant attach

3. **Confirm tenant attach prerequisites**
   List the content that will enable the learner to understand this module:
    - Enabling objective
        - Confirm tenant attach prerequisites:
            - An account that is a Global Administrator 
            - An Azure public cloud environment
            - The user accounts triggering device actions
            -  CAS has a remote provider scenario

4. **Enable internet endpoints**
   List the content that will enable the learner to understand this module:
    - Enabling objective
        - Admin must enable internet endpoints:
            - Configuration Manager uses Microsoft URL forwarding services
            - If environment has proxy rules to allow only specific certificate revocation lists (CRLs) or online certificate status protocol (OCSP) verification locations
  


- View on-premises device details

5. **Enable device upload**
   List the content that will enable the learner to understand this module:
   - Enabling objective
       - Upload devices
 
6. **Display the connector status**
   List the content that will enable the learner to understand this module:
   - Enabling objective
        - Confirm connector status

7. **Perform device actions**
   List the content that will enable the learner to understand this module:
   - Enabling objective
       - Perform device actions

8. **View on-premises device details**
   List the content that will enable the learner to understand this module:
   - Enabling objective
       - View on-premises device details

9. **Knowledge check**

quiz:
  questions:
  - content: "Which best describes tenant attach?"
    choices:
    - content: "Tenant attach is the process of attaching your Intune tenant to the cloud. The process incorporates co-management so that all your endpoints are successfully managed."
      isCorrect: false
      explanation: "Tenant attach allows you to recognize your Configuration Manager devices and infrastructure."
    - content: "Tenant attach allows you to recognize your Configuration Manager devices and infrastructure by the Intune cloud service and take actions from Microsoft Endpoint Manager."
      isCorrect: true
      explanation: "Tenant attach enables all your on-premises endpoints using Microsoft Endpoint Manager."
    - content: "Tenant attach sets up synchronization between your Azure Active Directory instance and M365. When you use tenant attach, you no longer need to use Microsoft Endpoint Manager."
      isCorrect: false
      explanation: "Tenant attach allows you to recognize your Configuration Manager devices and infrastructure."
  - content: "When implementing tenant attach, why is enabling internet endpoints important?"
    choices:
    - content: "Enabling specific internet endpoints will provide needed connectivity that will allow Configuration Manager features to fully function."
      isCorrect: true
      explanation: "If your organization restricts network communication with the internet using a firewall or proxy device, enabling endpoints will allow needed connectivity."
    - content: "Enabling internet endpoints must be prevented when implementing tenant attach."
      isCorrect: false
      explanation: "Enabling internet endpoints will allow needed Configuration Manager connectivity."
    - content: "Internet endpoints must be secure. For this reason, they must be managed by Microsoft Endpoint Manager."
      isCorrect: false
      explanation: "Enabling internet endpoints will allow needed Configuration Manager connectivity."
  - content: "Which statement best describes the actions you can take after implementing tenant attach?"
    choices:
    - content: "Tenant attach allows you to recognize your Microsoft Endpoint Manager devices and take actions from Configuration Manager."
      isCorrect: false
      explanation: "Tenant attach allows you to recognize your Configuration Manager devices and take actions from Microsoft Endpoint Manager."
    - content: "Tenant attach allows you to recognize your Configuration Manager devices and take actions from Microsoft Endpoint Manager, such as viewing client device details, viewing client device data, managing client apps, and running scripts on client devices."
      isCorrect: true
      explanation: "Tenant attach allows you to view client and device details, install apps, and run PowerShell scripts from Microsoft Endpoint Manager admin center. Additionally, you can view a timeline of device events that are synced each day, as well as perform other actions."
    - content: "Tenant attach allows you to recognize your Configuration Manager devices without taking action from Microsoft Endpoint Manager. By implementing tenant attach you can view cloud-based tenant details, cloud-based device data, and cloud-based apps."
      isCorrect: false
      explanation: "Tenant attach allows you to recognize your Configuration Manager devices and take actions from Microsoft Endpoint Manager."
  

10. **Summary**

Microsoft Endpoint Manager helps you by providing a single, modern, integrated management platform for managing, protecting, and monitoring all of your organization's endpoints. These endpoints may also include the on-premises computers and devices used by your organization.

The first part of attaching your on-premises devices to the cloud is call tenant attach. Tenant attach allows you to recognize your Configuration Manager devices and infrastructure in the Microsoft Intune cloud service and take actions from Microsoft Endpoint Manager.

In this module, you've learned how to attach your on-premises Configuration Manager devices to your cloud-based tenant using tenant attach. The goals of this module included the following:

Understand tenant attach
Confirm tenant attach prerequisites
Enable internet endpoints
Enable device upload
Display the connector status
Perform device actions
View on-premises device details
    
Next steps
    
Now that you have completed attaching to your tenant, consider adding co-management. For more information, see the following resources:

What is co-management?
How to enable co-management in Configuration Manager