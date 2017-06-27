# Azure Container Service - Storage Account

ACS API version `2017-07-01` includes support for the `StorageAccount` Azure resource. This provided sample template will exemplify how to opt your cluster into this storage paradigm. Supported orchestrators:

- Kubernetes
- DCOS
- Docker Swarm //TODO is this true?

### How to engage StorageAccount features

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

### Deployment via [Azure Portal](https://portal.azure.com)

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FStorageAccount%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a>

### Deployment with [Azure CLI](https://github.com/Azure/azure-cli)

(This assumes you are using Azure CLI from a bash environment. If not, you will
need to copy-paste these instructions as appropriate into cmd.exe)

```
export CLUSTER_NAME="choose_a_name"
export LOCATION="uksouth"

# edit ./azuredeploy.params.kubernetes.json as you need to

az group create --name ${CLUSTER_NAME} --location ${LOCATION}
az group deployment create \
  --resource-group "${CLUSTER_NAME}-deployment-${RANDOM}" \
  --template-file "./azuredeploy.json" \
  --parameters "./azuredpeloy.params.json"