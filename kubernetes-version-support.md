##TERMINOLOGY 

Release – Format x.y (Major.Minor) Example 1.6, 1.7,1.8
Version – Format x.y.z (Major.Minor.Patch) Example 1.6.8, 1.7.2, 1.8.0

##ACS RP V1

Kubernetes new release/version support in ACS RP v1 needs to be manually updated and rolled out to all regions. Typically, we have waited for the kubernetes release to be stable (enabled in acs-engine for a month) before rolling the release out in the RP. Since ACS RP V1 will be phased phased out soonout end of September , we will leave it out of discussion going forward.supporting newer versions on RP v1 is purely dependent upon business needs.
	
##ACS ENGINE 

ACS-Engine has moved from supporting versions to supporting releases. For example, ACS-Engine customers could choose 1.5.3 or 1.6.2 version of Kubernetes in the ACS template before. ACS engine today, allows the user to specify only a release. For example, 1.6 or 1.7. Upon deploying a template with a specific release, acs-engine automatically selects a default stable patch that it deploys. As of this writing, 1.6.8 is the version support as default.  
Current supported releases are:
•	1.5
•	1.6 (default)
•	1.7
Agreements:
ACS- engine  will support all beta releases on Day 0  soon after the release. The delay is primarily to allow us to run through all our tests and ensure there are no bugs.For example, when 1.8.0 releases in beta we will support it on day 0 in acs-engine.
Open question:
Is there value in supporting more than 3 releases? Once the community releases a stable 1.8, should we keep 1.5? Or should we announce during the 1.8 beta release that once a stable 1.8 release is available, 1.5 will be phased out and not supported? If upgrade support is available by end of September, we might be able to go through with this approach as there will be a path forward for customers deployed on 1.5 release. 
Publish Version text for the open question section.
The goal is to support the last two kubernetes version in acs-engine. 

##ACS RP V2  
        ACS RP v2 will automatically choose the default release in ACS engine. Apart from that, the following options will be allowed through the specific deployment methods.

Portal – Will support only one release (which is the default in ACS Engine) (available today in regions where ACS RPv2 is deployed)
CLI – Will support all releases supported in ACS Engine through a --–version or –release  flag (NOT available today)
Template/ReST API – will support all releases supported in ACS Engine as an input parameter (available today in regions where ACS RPv2 is deployed)
