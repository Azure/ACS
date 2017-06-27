# Simple Azure Container Service demo
In this demo, we will be creating three popular orchestrators `DCOS, DockerCE, and Kubernetes` on Azure Container Service using template with `2017-07-01` api version header which is available in `UK South` and `UK West`.

## Prerequsites
This demo will use [Azure cli](https://github.com/Azure/azure-cli).
1. `az login`
2. `az account set --subscription ${SUBSCRIPTION_ID}`

## Steps to create DCOS cluster
1. `az group create -l ukwest -n acs-demo-dcos`
2. edit `azuredeploy.params.dcos.json` with 
   - `sshRSAPublicKey` (a valid SSH key)
   - Replace GEN-UNIQUE with proper unique dns prefix
3. `az group deployment create -g acs-demo-dcos --template-file azuredeploy.dcos.json --parameters azuredeploy.params.dcos.json`

## Steps to create DockerCE cluster
1. `az group create -l ukwest -n acs-demo-dockerce`
2. edit `azuredeploy.params.dockerce.json` with 
   - `sshRSAPublicKey` (a valid SSH key)
   - Replace GEN-UNIQUE with proper unique dns prefix
3. `az group deployment create -g acs-demo-dockerce --template-file azuredeploy.json --parameters azuredeploy.params.dockerce.json`

## Steps to create Kubernetes cluster
1. `az group create -l ukwest -n acs-demo-k8s`
2. To create Kubernetes cluster, we need a valid service principal
3. `az ad sp create-for-rbac --scopes /subscriptions/${SUBSCRIPTION_ID}`
4. edit `azuredeploy.params.kubernetes.json` with 
   - `sshRSAPublicKey` (a valid SSH key)
   - `servicePrincipalClientId` (taken from the appId generated in step 2)
   - `servicePrincipalClientSecret` (taken from the password generated in step 2)
   - Replace GEN-UNIQUE with proper unique dns prefix
5. `az group deployment create -g acs-demo-k8s --template-file azuredeploy.json --parameters azuredeploy.params.kubernetes.json`

## Quick Deploy
### DCOS
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FSimple%2Fazuredeploy.dcos.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

### DockerCE & Kubernetes
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FSimple%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
