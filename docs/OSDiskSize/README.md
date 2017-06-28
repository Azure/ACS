# Azure Container Service - OSDiskSizeGB
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fazure%2Facs%2F924bf5294fd94cbd1d276afe8cba5cef4d8c6688%2Fdocs%2FOSDiskSize%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

You may change the disk size of both the master VM and agent VMs using the `OSDiskSizeGB` parameter. Providing more disk space to these VMs may allow you to have a longer retention period for your logs or cache things to disk from your containers. Valid disk sizes are between `1GB` and `1023GB`

## Deployment
Please make sure that you have created a resource group in one of the following regions: `ukwest` or `uksouth`.

You will also need to change the following values in the `azuredeploy.params.kubernetes.json` file:
* `masterDnsNamePrefix`
* `agentDnsNamePrefix`
* `windowsAgentAdminPassword`
* `sshaRSAPublicKey`
* `servicePrincipalClientId`
* `servicePrincipalClientSecret`

You can deploy an ACS cluster with the following command:

`az group deployment create -g <your resource group> --template-file azuredeploy.dcos.json --parameters azuredeploy.params.dcos.json`
