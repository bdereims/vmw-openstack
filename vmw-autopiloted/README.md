# Ubuntu Openstack with vCenter/NSX-V plugins 

Assuming that you have Up & Running vCenter and [Landscape/Autopilot](http://www.ubuntu.com/cloud/openstack/autopilot).  
I have create a [slave node template](scripts/autopilot-cloudnode.ova) for my lab.

## How to setup correctly slave node in Landscape
There are tricky tips in order to allow Landscape to manage powerstate of VM through vCenter. 
   
1. After deploying a slave node, you have to retrieve the vc.uuid from the vmx file on ESX or from the datastore 
![](docs/datastore-vmx-vc-uuid.png)

2. Reformat the uuid like this 
  * from "16S-16S" to "8S-4S-4S-4S-12S"
  * Example: "50 25 db a3 83 f0 cc db-0b ea bd 5a 1e 98 db 64" to "5025dba3-83f0-ccdb-0bea-bd5a1e98db64"

3. Modify the node slave in Landscape like the example below, now Lamdscape is able to deploy the env
![](docs/autopilot-node-management.png)

