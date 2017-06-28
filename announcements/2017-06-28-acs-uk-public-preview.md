# Microsoft Azure Container Service

## ACS UK Public Preview Release
**Announced: June 28, 2017**

On June 28, 2017, the Azure Container Service team released a new version of the
service as public preview in the UK region. This is available in the `ukwest`
and `uksouth` regions. The new service is based on the open-source heart of
ACS: [ACS-Engine](https://github.com/Azure/acs-engine). As part of this new
release, a new preview header version `2017-07-01` is now available.

The new header version `2017-07-01` exposes the following new preview features:

  1. [Simple Clusters](../docs/Simple/README.md) - Deploy a standard cluster
  2. [Large Clusters](../docs/LargeCluster/README.md) - Supports multiple worker pools
  3. [Storage via Managed Disks](../docs/ManagedDisks/README.md) - Support for storing OS disks in Azure's new Managed Disk feature (see #3)
  4. [Storage via Storage Accounts](../docs/StorageAccount/README.md) - Support for storing OS disks in Azure's classic Storage Accounts
  5. [Configurable Master Size](../docs/MasterSize/README.md) - User control over Master VM SKU/size
  6. [Configurable OS Disk Size](../docs/OSDiskSize/README.md) - User control over Master VM OS Disk size
  7. [Configurable Network Ports](../docs/Ports/README.md) - User control over additional network ports
  8. [Bring your own VNET](../docs/VNET/README.md) - User control of the network the cluster is deployed into
  9. [Windows](../docs/Windows/README.md) - Support for deploying Windows clusters

You may wish to start with [the documentation index page](../docs/README.md) which contains
instructions for deploying via [Azure CLI](https://github.com/Azure/azure-cli). Additionally, each extended feature
page should contain a link to deploy via the Portal.

And don't forget, these new features only work in `ukwest` and `uksouth`,
for now.