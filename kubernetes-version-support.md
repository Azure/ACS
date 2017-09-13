## TERMINOLOGY 

Release – Format x.y (Major.Minor) Example 1.6, 1.7,1.8

Version – Format x.y.z (Major.Minor.Patch) Example 1.6.8, 1.7.2, 1.8.0

## ACS RP V1

Because ACS RP v1 will be phased out soon, adding newer kubernetes releases/versions to RP v1 will be done only with a compelling business need.

The current Release and Version in RPv1 today is v1.6.6
	
## ACS ENGINE 

ACS-Engine has moved from supporting versions to supporting releases. For example, previously ACS-Engine customers could choose the 1.5.3 or the 1.6.2 version of Kubernetes in the ACS template. Today, ACS engine allows the user to specify only a release (for example, Release 1.6 or Release 1.7), and then ACS applies a patch that updates that release's version to the most recent stable version.

The current **default** Release and Version is 1.6.6.  

Current supported releases are:
1. 1.5
2. 1.6 (default)
3. 1.7


## ACS RP V2  

ACS RP v2 automatically chooses the default release in ACS engine. Apart from that, the following deployment methods have slightly varying options and features:

- Portal. Support only one release (which is the default in ACS Engine) (available today in regions where ACS RPv2 is deployed)
- CLI. Support all releases supported in ACS Engine through a --–version or –release  flag (NOT available today)
- Template/REST API. Support all releases supported in ACS Engine as an input parameter (available today in regions where ACS RPv2 is deployed)
