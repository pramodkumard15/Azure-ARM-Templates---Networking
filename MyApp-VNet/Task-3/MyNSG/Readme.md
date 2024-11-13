Step-by-Step Instructions (Azure Portal)


Step 1: Create a Network Security Group
Go to the Azure Portal and navigate to Network Security Groups.
Click + Create to start creating a new NSG.
Fill in the required fields:
Subscription: Choose your Azure subscription.
Resource Group: Select the resource group where you want to place this NSG.
Name: Enter a name for your NSG (e.g., MyNSG).
Region: Select the same region as your virtual network.
Click Review + create, then Create.


Step 2: Add Security Rules to the NSG
Once the NSG is created, navigate to it in the Azure Portal.
In the left-hand menu, select Inbound security rules.
Click + Add to create a new inbound rule:
Source: Set to Any (or specify an IP range if you want more control).
Source port ranges: Set to * (all ports).
Destination: Set to Any (or specify an IP if needed).
Destination port ranges: Enter 22 if you want to allow SSH traffic.
Protocol: Set to TCP.
Action: Set to Allow.
Priority: Set a priority (e.g., 100). Lower numbers indicate higher priority.
Name: Enter a rule name (e.g., AllowSSH).
Click Add to create the rule.
Repeat for other rules as needed (e.g., you might also add outbound rules to restrict certain traffic).


Step 3: Associate the NSG with a Subnet
Go to Virtual Networks in the Azure Portal and select the VNet where you want to associate the NSG.
In the left-hand menu, select Subnets.
Click on the specific subnet (e.g., web-subnet) that you want to secure with the NSG.
Under Network security group, select the NSG you created (MyNSG) from the dropdown list.
Click Save to apply the NSG to the subnet.


Step 4: Verify the NSG Association
Go back to your Network Security Groups and confirm that the rules are set up.
Check your Virtual Networks > Subnets to ensure that the NSG is associated with the correct subnet.


Summary
You’ve successfully:

Created an NSG in the Azure Portal.
Defined inbound and outbound rules.
Associated the NSG with a specific subnet in your VNet.
