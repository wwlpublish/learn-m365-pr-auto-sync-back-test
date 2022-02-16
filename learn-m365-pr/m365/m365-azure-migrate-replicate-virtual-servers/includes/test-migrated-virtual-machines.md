Once your targeted virtual machines are replicated and into Azure, before you migrate them into production, you can test them to ensure everything works.

1. Start by clicking Replicating Servers in the Azure Migrate: Server Migration tile.

:::image type="content" source="../media/replicating-servers.png" alt-text="Replicating servers." border="false":::

2. In the list of servers, find the one you want to test and select Test Migration from the ellipses for the group just migrated.

:::image type="content" source="../media/test-migration.png" alt-text="Test migration." border="false":::

3. In Test Migration, select the Azure Virtual Network to use for the test. We recommend you use a non-production VNET.

:::image type="content" source="../media/select-virtual-network.png" alt-text="Select virtual network." border="false":::

The process runs a prerequisite check, prepares for the test, creates a new test virtual machine, and starts it. This takes a few minutes.
