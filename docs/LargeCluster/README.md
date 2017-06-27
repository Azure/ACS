# Microsoft Azure ContainerService
## Multi agent pool clusters
Starting in api-version "2017-07-01" ACS is adding support for multiple agent pools for DCOS and DockerCE(SwarmMode) clusters. Kubernetes is not ready yet but defintiely on our TODO list. Each agent pool can have different counts of vms and different vm sizes. They also can each have their own [dns prefix/port configuration](../ports/README.md). The dns prefix for each agent pool must be unique/we do not support directly load balancing from a single loadbalancer to multiple agent pools. The common solution to this type of issue is to have a single public agent pool with an ingress controller and have the ingress controller load balance between the nodes.
## Sample Template
  <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Facs%2Fmaster%2Fdocs%2FLargeCluster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Targeting agent pools with workloads
How to get your work loads to land on a specific agent pool varies depending on the orchestrator
### DCOS
TODO
### DockerCE
TODO