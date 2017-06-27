# Microsoft Azure Container Service
## Multi agent pool clusters
Starting in api-version "2017-07-01" ACS is adding support for multiple agent pools for DCOS and DockerCE(SwarmMode) clusters. Kubernetes is not ready yet but defintiely on our TODO list. Each agent pool can have different counts of vms and different vm sizes. They also can each have their own [dns prefix/port configuration](../ports/README.md). The dns prefix for each agent pool must be unique/we do not support directly load balancing from a single loadbalancer to multiple agent pools. The common solution to this type of issue is to have a single public agent pool with an ingress controller and have the ingress controller load balance between the nodes.
## Quick Deploy
  <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FLargeCluster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Deploying 'az' cli
### Prerequsites 
This demo will use [Azure cli](https://github.com/Azure/azure-cli). 
1. `az login` 
2. `az account set --subscription ${SUBSCRIPTION_ID}` 
 
### Steps to create DCOS cluster 
1. `az group create -l ukwest -n acs-demo-dcos` 
2. edit `azuredeploy.params.dcos.json`
   - Replace GEN-SSH-PUB-KEY with 
   - Replace GEN-UNIQUE with proper unique dns prefix(s), each needs to be unique 
   - Change any agent pool counts or vm sizes to desired values
3. `az group deployment create -g acs-demo-dcos --template-file azuredeploy.json --parameters azuredeploy.params.dcos.json` 

### Steps to create DockerCE cluster 
1. `az group create -l ukwest -n acs-demo-dockerce` 
2. edit `azuredeploy.params.dockerce.json`
   - Replace GEN-SSH-PUB-KEY with 
   - Replace GEN-UNIQUE with proper unique dns prefix(s), each needs to be unique
   - Change any agent pool counts or vm sizes to desired values
3. `az group deployment create -g acs-demo-dockerce --template-file azuredeploy.json --parameters azuredeploy.params.dockerce.json` 
