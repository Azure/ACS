Recently we discovered a few ACS kubernetes clusters that were not responding after system reboots of the Master VM's. 
All ACS RPv1 clusters deployed will see this issue and ACS RPv2 clusters deployed after Fri Oct 20 06:49:20 PDT 2017 will see this issue.

Upon investigation, we found out that that this was due to etcd not restarting.

As a fix, we set etcd2 restart to 'always' after rebooting master VM's. This issue has been fixed and has being rolled out to RPv2 resions. 

To fix this issue manually, please run the following commands on all the master nodes in your cluster

`
+- sudo /bin/sed -i s/Restart=on-abnormal/Restart=always/g /lib/systemd/system/etcd.service
`

`
+- systemctl daemon-reload
`

List of all ACS RPv1 regions:

1) australiasoutheast

2) northeurope       

3) brazilsouth       

4) australiaeast     

5) japaneast         

6) northcentralus    

7) westus            

8) eastasia          

9) eastus2           

10) southcentralus    

11) southeastasia     

12) eastus            

13) westeurope        

14) Centralus

List of RPv2 regions:

1) UK West

2) UK South

3) West Central US

4) West US 2

5) Canada East

6) Canada Central

7) West India

8) South India

9) Central India

10) japanwest 
