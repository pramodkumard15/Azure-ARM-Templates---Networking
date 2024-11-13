Task 4: Setting Up a Network Peering Between Two Virtual Networks
Objective: Connect two Virtual Networks (VNets) in Azure using network peering to enable resource communication across VNets without using the public internet.

Why Perform This Task?
Network peering allows for a low-latency, high-bandwidth private connection between VNets in the same or different regions. This is useful for setting up multi-tier applications or integrating services across networks.

Steps to Complete Task 4 in the Azure Portal
Create Two Virtual Networks (if not already created):

Go to Virtual networks and create two VNets (e.g., VNet1 and VNet2) in the same or different regions.
Assign unique IP address spaces to avoid overlap (e.g., 10.0.0.0/16 for VNet1 and 10.1.0.0/16 for VNet2).
Set Up Network Peering Between VNet1 and VNet2:

Go to VNet1 in the Azure Portal.
Select Peerings under the Settings section.
Click + Add to create a new peering.
Fill in the following details:
Name: Enter a name for the peering (e.g., VNet1-to-VNet2).
Peer virtual network: Select VNet2.
Allow virtual network access: Set to Enabled.
Allow forwarded traffic, Allow gateway transit, and Use remote gateways: Leave these as default for now.
Set Up Peering on the Other Side (VNet2):

Go to VNet2 in the Azure Portal.
Select Peerings and add a new peering.
Fill in the details:
Name: Enter a name for the peering (e.g., VNet2-to-VNet1).
Peer virtual network: Select VNet1.
Allow virtual network access: Set to Enabled.
Click OK to complete the peering setup.
Verify Connectivity (Optional):

Deploy virtual machines in each VNet’s subnet to test connectivity between them.
You can use Ping or Remote Desktop Protocol (RDP) if configured, to ensure they can communicate.
Outcome:
After completing these steps, VNet1 and VNet2 will be peered, allowing resources in each VNet to communicate over Azure’s private backbone network.

Let me know when you're ready to move on or if you'd like more clarification on any step!
