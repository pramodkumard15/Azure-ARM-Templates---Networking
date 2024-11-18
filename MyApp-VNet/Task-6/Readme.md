Task 6: Secure Communication Between Virtual Machines Using an NSG.

Step 1: Create a Network Security Group (NSG)
Go to Azure Portal:

Navigate to Network Security Groups from the search bar.
Click + Create.
Provide NSG Details:

Subscription: Select your subscription.
Resource Group: Use an existing one or create a new resource group.
Name: Enter MySubnetNSG.
Region: Choose the same region as your virtual network.
Click Review + create, then Create.
Step 2: Add Security Rules to the NSG
Navigate to Inbound Security Rules within the created NSG.

Add Rules:

Allow RDP:
Source: Any
Source Port Ranges: *
Destination: Any
Destination Port Ranges: 3389
Protocol: TCP
Action: Allow
Priority: 100
Name: AllowRDP
Allow Ping:
Source: Any
Source Port Ranges: *
Destination: Any
Destination Port Ranges: 0-65535
Protocol: ICMP
Action: Allow
Priority: 110
Name: AllowPing
Save the rules.

Step 3: Associate the NSG with the Subnet
Navigate to your Virtual Network and select the subnet where your VMs are deployed.
Under Settings, click on Subnets.
Edit Subnet:
Under Network Security Group, select the NSG (MySubnetNSG) you created.
Click Save.
Step 4: Test the Configuration
Log in to one of the VMs using RDP (this validates the RDP rule).
Open Command Prompt and attempt to ping the other VM's private IP:
If successful, the ping rule is working correctly.
Try accessing the other VM using any port not allowed in the NSG:
The connection should be blocked.
Optional Step: Clean Up
After testing:
Delete the VMs and disks to minimize costs.
Keep the NSG and VNet for reference if needed.
