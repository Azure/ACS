
### The ACS New RP V2 enables a bunch of new features including:
1) Exisiting VNET Support
2) Choice of  master size
3) Multiple agent pools
4) Choice of managed disks vs storage account and their respective sizes for Masters and Agents

The below use cases will be documented on ACOM when the RP V2 is Generally Available in a month or so. 
Please try them out and provide feedback on the issues section of this repo.

Preview features only available in the following regions:
UK West
UK South
West Central US
West US 2
Canada East
Canada Central
West India
South India
Central India

### Install Azure CLI v 2.0.14
### https://github.com/Azure/azure-cli

#### Login
` az login `

#### Create a resource group
` az group create -n <resource-group-name> -l ukwest `

#### Multiple agent pools with default node size (Standard_D2_V2)*
*Default – 1 agent pool and 3 nodes*
` az acs create -n <container-service-name> -g <resource-group-name> -t Kubernetes `

*2 agent pools each with default number of nodes (3)*

` az acs create -n <container-service-name> -g <resource-group-name> -t kubernetes -a "[{'name':'agentpool1'},{'name':'agentpool2'}]" `

*Multiple agent pools with custom node size*

` az acs create -n <container-service-name> -g <resource-group-name> -t kubernetes -a "[{'name':'agentpool1'},{'name':'agentpool2','vmSize':'Standard_D2','count':5}]" `

agentpool1 with default node size Standard D2V2 and default no of nodes 3
agentpool2 with VM size Standard_A0 and node count 5

#### Custom VNET and Ports

*Create a custom VNET*

` az network vnet create -g vnetrg -n vnet007 `

*Use the VNET id (see above) to create a cluster*

` az acs create -n vnetcs -g vnetrg -t kubernetes --agent-vnet-subnet-id "/subscriptions/<subscription-id>/resourceGroups/vnetrg/providers/Microsoft.Network/virtualNetworks/vnet007" `

*Use the VNET id and specifiy a custom port*

` az acs create -n portvnetcs -g vnetrg -t kubernetes --agent-vnet-subnet-id "/subscriptions/<subscription-id>/resourceGroups/vnetrg/providers/Microsoft.Network/virtualNetworks/vnet007" --agent-ports 4005 `

#### Storage accounts and Managed Disks
By default, the ACS RP v2 creates storage accounts for masters and storage accounts for agents, both of which can be changed to use managed disks.

*Use managed disks for masters and agents* 

` az acs create -n storagecs -g storagerg -t kubernetes --master-storage-profile ManagedDisks --agent-storage-profile ManagedDisks `

Default master os disk size and agent os disk size are 30GB each
Master etcd disk size is 128GB

*Use managed disks for masters and agents and specifiy each size*

` az acs create -n storagecs -g storagerg -t kubernetes --master-storage-profile ManagedDisks --master-osdisk-size 30 --agent-storage-profile ManagedDisks --agent-osdisk-size 120 `

#### Delete a cluster
Deleting an ACS cluster deletes the resources it created in a separate resource group it created but leaves the user created resource group untouched*

` az acs delete -n <container-service-name> -g <resource-group-name> `




