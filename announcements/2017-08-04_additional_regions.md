The new Azure Container Service is now available in the following regions :

1. UK West
2. UK South
3. West Central US
4. West US 2
5. Canada East
6. Canada Central
7. West India
8. South India
9. Central India

The following regions are available under a feature flag and needs subscription access:

1. Korea South
2. Korea Central

See the previous [announcement](announcements/2017-06-28-acs-uk-public-preview.md) for new features.

New functionality in the regions uksouth and ukwest can be deployed using the Azure CLI 2.0  version 2.0.12 which can be 
downloaded [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)

For the other new regions you can download the nightly build [here](https://github.com/Azure/azure-cli#nightly-builds) 

#### Please ensure that if you choose to create your own Service Principal, you need to have scope set to contributor and scope to the subscription under which you are deploying the ACS cluster
