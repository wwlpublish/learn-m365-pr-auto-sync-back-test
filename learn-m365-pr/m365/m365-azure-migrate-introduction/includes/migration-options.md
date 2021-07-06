
In this module, we'll focus on migrating from your own VMware infrastructure to Azure. If you're using Windows Server Hyper-V, the process is similar. Each virtualization platform has a specialized virtual machine appliance installed on your virtualization hosts to discover, assess, and replicate the virtual machines you target for migration.

If you currently use VMware and are migrating to Azure, there are two primary options for migration: Azure VMware Solution and Azure Migrate.

**Azure VMware Solution** allows you to provision a native VMware environment running in Azure. You get dedicated, isolated Azure bare metal infrastructure to create native VMware private cloud environments. Setting up this option is similar to setting up a separate VMware site. Azure VMware Solution is great for bulk migration in a short period of time – for example when retiring a data center – while using the same VMware toolset and expertise you already have.

We do not cover the Azure VMware Solution in detail in this or the subsequent modules of this Learning Path. See the Learn more links below for additional information on this topic.

Azure Migrate is the other option and the focus of this module. Azure Migrate is great for driving more compute efficiency, providing the flexibility to right-size your infrastructure on demand, and helps dramatically save costs in the long term by running your VMs in native Azure IaaS.

**Azure Migrate** has been updated to include the migration-specific tools previously available only in Azure Site Recovery, fully integrated and optimized for Azure Migrate. It also offers both Microsoft and partner tools for assessment and migration. Azure Migrate allows you to centrally track your projects from one place via a set of simplified end-to-end workflows.

>[!NOTE]
>**Cloud Adoption Framework**
>
>If you're considering moving your workloads to the cloud, the free Cloud Adoption Framework provides a set of tools and guidance for developing your migration strategy, including organizational readiness
>

## Learn more

- [How to run VMware in Azure - Demo Tutorial](https://www.microsoft.com/videoplayer/embed/RE4sOiW?azure-portal=true)
- [Real life migrations to Azure and how they did it](https://www.microsoft.com/videoplayer/embed/RE4sOiN?azure-portal=true)
(Includes a demonstration of vMotion from an on-premises VMware environment using HCX into an Azure VMware instance)
