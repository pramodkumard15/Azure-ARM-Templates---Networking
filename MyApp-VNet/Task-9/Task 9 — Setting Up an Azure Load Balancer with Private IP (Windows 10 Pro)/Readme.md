Task 9 — Setting Up an Azure Load Balancer with Private IP (Windows 10 Pro)

Objective:
Set up an Azure Load Balancer to distribute traffic across two Windows 10 Pro VMs using a private IP. This will allow you to test load balancing functionality without public exposure.

Step 1: Create the Resource Group and Virtual Network
Create a Resource Group:

Go to Azure Portal.
In the left-hand menu, select Resource groups.
Click + Create.
Enter the following:
Name: RG-LoadBalancer
Region: Choose your preferred region (e.g., East US).
Click Review + Create and then Create.
Create a Virtual Network (VNet):

In the Azure Portal, go to Virtual Networks.
Click + Create.
Fill in the details:
Name: VNet-Task9
Region: Same region as the Resource Group.
Address Space: 10.0.0.0/16 (This will define the IP range for your network).
Under Subnets, add two subnets:
Subnet 1: LoadBalancer-Subnet with IP range 10.0.1.0/24.
Subnet 2: VM-Subnet with IP range 10.0.2.0/24.
Click Review + Create and then Create.
Step 2: Create Two Windows 10 Pro VMs

Create VM1:

Go to Virtual Machines in the Azure Portal.
Click + Create and choose Windows 10 Pro (since you’re using it for cost reduction).
Fill in the details:
Name: VM1
Region: Same region as VNet.
Image: Windows 10 Pro.
Size: Choose a smaller VM (e.g., B1s or B2s to keep costs low).
Authentication Type: Choose Password or SSH Public Key (Password is easier for now).
Username: azureuser
Password: Create a strong password.
Network: Select VNet-Task9 and choose the VM-Subnet.
Public IP: Set to None (you will use private IPs).
Inbound Ports: Allow RDP (3389) for remote access.
Click Review + Create and then Create.

Create VM2:

Repeat the same steps as for VM1, but name it VM2 and place it in the same VM-Subnet.
Use Windows 10 Pro as the OS image.
Step 3: Install IIS Web Server on Both VMs
Connect to VM1 via RDP:

From the Azure Portal, select VM1.
Under Connect, select RDP, then click Download RDP File.
Open the RDP file and log in using the credentials you set earlier.

Install IIS:
Once connected to VM1, open PowerShell as Administrator.
Run the following command to install the IIS web server:
powershell
Copy code
Enable-WindowsOptionalFeature -Online -FeatureName IIS-WebServerRole -All
Create a custom HTML page:
powershell
Copy code
echo "VM1 - Load Balancer Test" > "C:\inetpub\wwwroot\index.html"
Connect to VM2 via RDP:

Repeat the same RDP connection steps for VM2.

Install IIS on VM2:
Run the following command on VM2's PowerShell as Administrator:
powershell
Copy code
Install-WindowsFeature -name Web-Server -IncludeManagementTools
Create a custom HTML page:
powershell
Copy code
echo "VM2 - Load Balancer Test" > "C:\inetpub\wwwroot\index.html"
Step 4: Create the Load Balancer
Create Load Balancer:

In the Azure Portal, go to Load Balancers and click + Create.
Fill in the details:
Name: LB-Task9
Region: Same region as the Resource Group and VNet.
SKU: Select Standard (recommended for production).
Tier: Choose Regional.
Configure Frontend IP:

Under Frontend IP configuration, click + Add.
Name: FrontendIPConfig
IP Address: Set to Private and assign an IP in the 10.0.1.0/24 range (e.g., 10.0.1.10).
Select the VNet-Task9 and LoadBalancer-Subnet.
Click Add.
Configure Backend Pool:

Under Backend Pools, click + Add.
Name: MyBackendPool
Add VM1 and VM2 by their private IP addresses (e.g., 10.0.2.4 for VM1 and 10.0.2.5 for VM2).
Click Add.
Configure Health Probes:

Under Health Probes, click + Add.
Name: HTTPProbe
Protocol: HTTP
Port: 80
Path: /index.html
Interval: 5 seconds
Unhealthy threshold: 3
Click Add.
Configure Load Balancing Rules:

Under Load balancing rules, click + Add.
Name: HTTP-Rule
Frontend IP: Select FrontendIPConfig.
Backend Pool: Select MyBackendPool.
Probe: Select HTTPProbe.
Frontend Port: 80
Backend Port: 80
Session Persistence: Set to None.
Click Add.
Step 5: Test the Load Balancer
Retrieve Load Balancer IP:

Go to Load Balancers in the Azure Portal.
Select LB-Task9 and note the Frontend IP (e.g., 10.0.1.10).
Test the Load Balancer:

From VM1 or VM2, open PowerShell and run:
powershell
Copy code
Invoke-WebRequest -Uri "http://10.0.1.10"
The response should alternate between "VM1 - Load Balancer Test" and "VM2 - Load Balancer Test" based on the load balancing rules.
Conclusion:
You have successfully set up a load balancer with a private IP in Azure, distributing traffic between two Windows 10 Pro VMs. You can now test the load balancing functionality and expand the setup as needed.

Let me know if you'd like to proceed to another task or need further clarifications.
