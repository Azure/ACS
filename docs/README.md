# Microsoft Azure Container Service

## Extended Features

* [Extended Features and Examples](#extended-features-and-examples)
* [Deployment via Azure CLI](#deployment-via-azure-cli)
* [Useful Information](#useful-information)

### Extended Features and Examples

(Note, these examples currently only work in [the UK Public Preview regions](../announcements/2017-06-28-acs-uk-public-preview).)

  1. [Simple Clusters](../docs/Simple/README.md) - Deploy a standard cluster
  2. [Large Clusters](../docs/LargeCluster/README.md) - Supports multiple worker pools
  3. [Storage via Managed Disks](../docs/ManagedDisks/README.md) - Support for storing OS disks in Azure's new Managed Disk feature (see #3)
  4. [Storage via Storage Accounts](../docs/StorageAccount/README.md) - Support for storing OS disks in Azure's classic Storage Accounts
  5. [Configurable Master Size](../docs/MasterSize/README.md) - User control over Master VM SKU/size
  6. [Configurable OS Disk Size](../docs/OSDiskSize/README.md) - User control over Master VM OS Disk size
  7. [Configurable Network Ports](../docs/Ports/README.md) - User control over additional network ports
  8. [Bring your own VNET](../docs/VNET/README.md) - User control of the network the cluster is deployed into
  9. [Windows](../docs/Windows/README.md) - Support for deploying Windows clusters

### Deployment via [Azure CLI](https://github.com/Azure/azure-cli)

**NOTE**: This assumes you are using Azure CLI from a bash environment. If not, you will
need to minorly modify these instructions as appropriate into `cmd.exe`.

You will want to edit the specified parameters file ahead of time, in order to exercise the functionality of each feature.

```
export CLUSTER_NAME="choose_a_name"
export LOCATION="westuk"

# edit ./azuredeploy.params.kubernetes.json as you need to
# for example, try setting `orchestratorVersion` to `1.5.7` instead of `1.6.6`.

az group create --name "${CLUSTER_NAME}" --location "${LOCATION}"
az group deployment create \
  --name "${CLUSTER_NAME}-deployment-${RANDOM}" \
  --template-file "./azuredeploy.kubernetes.json" \
  --parameters "@./azuredeploy.params.kubernetes.json"
```

### Useful Information

* You can discover the avialable SKUs and sizes by executing `az vm list-sizes`.
