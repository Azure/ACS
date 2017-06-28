# Azure Container Service - Storage Account

ACS API version `2017-07-01` includes support for the `StorageAccount` Azure resource. The provided sample templates will exemplify how to opt your cluster into this storage paradigm. Supported orchestrators:

- Kubernetes
- DC/OS
- Docker CE

## How to engage StorageAccount features

DC/OS, Docker CE, and Kubernetes have managed disks for *masters* enabled by default; and DC/OS and Docker CE have managed disks for *agents* enabled by default. Below demonstrates how to override these defaults and enable `.vhd` blobs in Azure Storage accounts.

In your cluster schema, include in your master and agent pool definitions the `storageProfile` property, giving it a value of `StorageAccount`. E.g.:

```
"masterProfile": {
  <other masterProfile key/vals>,
  "storageProfile": "StorageAccount",
  <other masterProfile key/vals>
},
"agentPoolProfiles": [
  {
    <other agentPoolProfile key/vals>,
    "storageProfile": "StorageAccount",
    <other agentPoolProfile key/vals>
  }
]
```

The above has been applied in the sample deployment templates `azuredeploy.json` (prepared for example Kubernetes and Docker CE deployments) and `azuredeploy.dcos.json` (prepared for an example DC/OS deployment).

## Deployment via [Azure Portal](https://portal.azure.com)

### For Kubernetes and Docker CE

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FStorageAccount%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a>

### For DC/OS

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FStorageAccount%2Fazuredeploy.dcos.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a>

## Deployment with [Azure CLI](https://github.com/Azure/azure-cli)

(This assumes you are using Azure CLI from a bash environment. If not, you will
need to copy-paste these instructions as appropriate into cmd.exe)

```
export CLUSTER_NAME="choose_a_name"
export LOCATION="uksouth"

```

### For Kubernetes:

Replace all instances of the value `GEN-UNIQUE` in the provided sample parameters file `azuredeploy.params.kubernetes.json` with appropriate values for your environment. Then:

```az group create --name ${CLUSTER_NAME} --location ${LOCATION}
az group deployment create \
  --resource-group "${CLUSTER_NAME}-deployment-${RANDOM}" \
  --template-file "./azuredeploy.json" \
  --parameters "./azuredeploy.params.kubernetes.json"
```

### For DC/OS:

Replace all instances of the value `GEN-UNIQUE` in the provided sample parameters file `azuredeploy.params.dcos.json` with appropriate values for your environment. Then:

```az group create --name ${CLUSTER_NAME} --location ${LOCATION}
az group deployment create \
  --resource-group "${CLUSTER_NAME}-deployment-${RANDOM}" \
  --template-file "./azuredeploy.dcos.json" \
  --parameters "./azuredeploy.params.dcos.json"
```

### For Docker CE:

Replace all instances of the value `GEN-UNIQUE` in the provided sample parameters file `azuredeploy.params.dockerce.json` with appropriate values for your environment. Then:

```az group create --name ${CLUSTER_NAME} --location ${LOCATION}
az group deployment create \
  --resource-group "${CLUSTER_NAME}-deployment-${RANDOM}" \
  --template-file "./azuredeploy.json" \
  --parameters "./azuredeploy.params.dockerce.json"
```