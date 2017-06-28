# Azure Container Service - Ports
`ports` is now supported in ACS since version 2017-07-01. It will be one of the optional attribute in the `agentPoolProfile` definition. Ports need to conform the following rules
- All ports must be unique
- they must be specified with a agentDnsNamePrefix
- range is 1 <= x <= 65535

In sample templates we specify the public agent pool's ports like this
![nsg image](resources/ports_publicagent_definition.png)

## Before using sample template and parameters
- Replace GEN-UNIQUE and GEN-UNIQUE-2 with different unique strings
- Replace GEN-SSH-PUB-KEY with valid SSH public key

## Deploy using sample template and parameters
With the provided sample ARM templates and parameters, 
- Using [az cli](https://github.com/Azure/azure-cli) to deploy
    ```
    az group deployment create -g <your resource group> --template-file azuredeploy.dcos.json --parameters azuredeploy.params.dcos.json
    ``` 
    Note, `<your resource group>` need to be in either `ukwest` or `uksouth` regions. Other regions don't support the new version yet.

- Or simply click <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FPorts%2Fazuredeploy.dcos.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## After deployment
You should be able to check the public agent pool's nsg rules, in [azure portal](https://portal.azure.com/)
![nsg image](resources/ports_publicagent_nsg.png)