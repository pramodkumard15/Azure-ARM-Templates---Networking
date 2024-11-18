Task 5: Deploying and Connecting Two Virtual Machines in a Single Subnet
In this task, you successfully deployed two Windows Server virtual machines (VMs) within the same subnet of a virtual network (VNet) in Azure, configured them for communication, and tested connectivity using ping.

Summary of What You Did
Created a Resource Group:
You created a resource group to logically group all the resources used in this task.

Deployed a Virtual Network (VNet):

Configured a VNet with a defined address space (e.g., 10.0.0.0/16).
Created a single subnet (e.g., 10.0.1.0/24) within the VNet to host the VMs.
Deployed Two Windows Server Virtual Machines:

Launched two VMs, ensuring they were placed in the same subnet.
Selected cost-effective VM sizes to minimize expenses during the learning phase.
Verified Default Network Settings:

Confirmed that no Network Security Group (NSG), NAT Gateway, or Route Table was applied to the subnet, ensuring default Azure network behavior.
Tested Communication Between VMs:

Logged into the VMs via Remote Desktop Protocol (RDP).
Enabled ICMP (ping) requests by turning off the Public Network firewall profile on both VMs.
Achieved Successful Ping Results:
Verified that the VMs could communicate with each other by pinging their private IPs within the subnet.

Why This Task Was Important
Understand Subnet Behavior: Learned how resources communicate within the same subnet in a default configuration.
Firewall Configuration: Recognized the impact of local firewall profiles on network connectivity.
Hands-On Debugging: Practiced troubleshooting connectivity issues and resolved them step-by-step.
GitHub Update
You can save this task in your GitHub repository as follows:

Folder Structure:
Create a folder named Task-5-VMs-Same-Subnet.

Files to Include:

README.md: Add the steps, configurations, and summary of what you learned.
Any relevant screenshots (optional, e.g., successful ping results).
Commit Message:
Use a descriptive commit message, such as:
Added Task 5: Deployed and connected VMs in the same subnet.
