## TERMINOLOGY 

Release – Format x.y (Major.Minor) Example 1.6, 1.7,1.8

Version – Format x.y.z (Major.Minor.Patch) Example 1.6.8, 1.7.2, 1.8.0

## ACS RP V1

Kubernetes new release/version support in ACS RP v1 needs to be manually updated and rolled out to all regions. Typically, we have waited for the kubernetes release to be stable (enabled in acs-engine for a month) before rolling the release out in the RP. Since ACS RP v1 will be phased  out soon , supporting newer kubernetes releases/versions on RP v1 is purely dependent upon business needs. 
Default in RPv1 today is v1.6.6
	
## ACS ENGINE 

ACS-Engine has moved from supporting versions to supporting releases. For example, previously ACS-Engine customers could choose 1.5.3 or 1.6.2 version of Kubernetes in the ACS template. ACS engine today, allows the user to specify only a release. For example, 1.6 or 1.7. Upon deploying a template with a specific release, acs-engine automatically selects a default stable patch that it deploys. As of this writing, 1.6.6 is the version support as default.  

Current supported releases are:
1. 1.5

2. 1.6 (default)

3. 1.7


## ACS RP V2  

ACS RP v2 will automatically choose the default release in ACS engine. Apart from that, the following options will be allowed through the specific deployment methods.

Portal – will support only one release (which is the default in ACS Engine) (available today in regions where ACS RPv2 is deployed)

CLI – will support all releases supported in ACS Engine through a --–version or –release  flag (NOT available today)

Template/ReST API – will support all releases supported in ACS Engine as an input parameter (available today in regions where ACS RPv2 is deployed)
