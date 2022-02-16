To use Azure Migrate, you'll need an Azure subscription. There are many promotional offers available to get started at little to no cost.

Once in your Azure tenant, make sure that you've set the right permissions so that your virtual machine logs can be sent to Azure. Then replicate virtual machines into Azure storage, create and access virtual networks, create virtual machines prior to test, and perform production migration.

## VMware starting environment

Before starting, we recommend that you pilot the process with a single app and small set of virtual machines for your first end-to-end migration. Then you can apply your learnings and resource dependency mapping to scale to larger migrations. We cover discovery and assessment in depth in the next module in this Learning Path.

:::image type="content" source="../media/vmware-starting-environment.png" alt-text="VMWare starting environment." border="false":::

As an example, we will use an app with virtual machines spread across three tiers: a web front end, an app tier, and a backend database tier. We will assess and migrate these virtual machines in subsequent steps.

## Finding Azure Migrate

You configure Azure Migrate in the Azure portal. You can find Azure Migration Tools at the bottom of the Azure portal home screen, or search for "migrate" in the search box.

:::image type="content" source="../media/migrate-azure-tools.png" alt-text="Azure migration tools." border="false":::

Azure Migrate is a service for datacenter migration with integrated assessment and migration tools from both Microsoft and Microsoft's migration partners. Azure Migrate monitors migration progress across all running projects and tools.

:::image type="content" source="../media/start-screen.png" alt-text="Start screen." border="false":::
