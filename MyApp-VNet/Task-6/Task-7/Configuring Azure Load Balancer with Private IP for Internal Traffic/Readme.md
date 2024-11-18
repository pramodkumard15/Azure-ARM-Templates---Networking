Task 7: Configuring Azure Load Balancer with Private IP for Internal Traffic
Goal
Create and configure a Load Balancer in Azure that uses a private IP address to distribute traffic to multiple virtual machines (VMs) within the same virtual network (VNet).
This allows for internal traffic balancing and ensures high availability and scalability of applications hosted on the VMs.
Step-by-Step Overview:
Step 1: Create the Load Balancer
Navigate to the Azure Portal: Go to the Azure Portal and search for "Load Balancers."
Create a Load Balancer:
Name: Enter a descriptive name (e.g., "MyInternalLoadBalancer").
Region: Ensure it’s in the same region as your VMs.
Type: Select "Internal" to specify that the load balancer will use a private IP for communication within the VNet.
Frontend IP Configuration:
Create a Frontend IP Configuration using a private IP (e.g., 10.0.1.10).
Choose the VM Subnet (VM-Subnet-Task5) in the VNet.
Set the IP allocation to Static to ensure that the IP doesn’t change.
Step 2: Configure Backend Pool
Backend Pool:
A backend pool contains the VMs that will receive traffic from the Load Balancer.
In the Load Balancer settings, go to Backend Pools.
Add your two VMs (e.g., Task5-VM1 and Task5-VM2) to the backend pool.
These VMs will now receive traffic that the Load Balancer directs to them.
Step 3: Create Health Probes
Health Probes:
Health probes determine the health of your VMs and help the Load Balancer decide which VM to direct traffic to.
Create a TCP health probe with port 80 (or another application port as needed).
The Load Balancer will use the probe to ensure the VMs are healthy before sending traffic.
Step 4: Set Up Load Balancer Rules
Load Balancing Rule:
A load balancing rule defines how incoming traffic is distributed to VMs.
In the Load Balancer settings, go to Load balancing rules and click + Add.
Specify the frontend IP (e.g., 10.0.1.10).
Set the backend port and frontend port to the port your application is listening on (e.g., port 80 for HTTP traffic).
Choose the backend pool (e.g., MyBackendPool) for routing traffic.
Step 5: Verify Connectivity
Test the Load Balancer Setup:

Once the Load Balancer is set up and traffic is being distributed, you should verify the setup by pinging the backend VMs.
Test if you can connect to the Load Balancer IP (private IP, e.g., 10.0.1.10) from other VMs or within the same VNet.
Ping Test:

VM-to-VM Communication: You successfully verified that pinging between VMs in the backend pool (Task5-VM1 and Task5-VM2) was successful.
Test Connectivity from Client VM to Load Balancer: Ensure that clients (other VMs or services in the same VNet) can send requests to the Load Balancer’s private IP.
Testing Health Probes:

Health Check: The Load Balancer checks the health of your VMs through health probes. Ensure that your VMs are marked as healthy.
Failover Behavior: If one VM is down or unhealthy, the Load Balancer will route traffic only to the healthy VM.
Step 6: Troubleshooting (Optional)
If you’re unable to ping or the connection isn’t working as expected:
Ensure the Network Security Group (NSG) attached to the VMs and subnet allows the relevant traffic (e.g., ICMP for ping or TCP port 80).
Ensure the VMs’ firewall settings allow inbound traffic from the Load Balancer.
Review the Health Probe configuration to ensure that it is set up correctly and that the VMs are healthy.
Key Concepts
Frontend IP Configuration: This is the public or private IP address used to send traffic to the Load Balancer. In this case, we used a private IP since it's an internal load balancer.
Backend Pool: The pool of VMs (or other resources) that will receive the traffic routed by the Load Balancer.
Health Probes: Probes that monitor the health of the backend resources to ensure that the Load Balancer routes traffic only to healthy resources.
Load Balancer Rules: Define how traffic should be distributed across the backend pool based on the frontend IP and ports.
Outcome
You successfully set up an Azure Load Balancer with a private IP for internal traffic.
The traffic is distributed between two VMs in the backend pool (Task5-VM1 and Task5-VM2).
Health probes monitor the VMs' status, ensuring only healthy VMs receive traffic.
You verified the setup by pinging the VMs and testing the Load Balancer.
Commit to GitHub
Create a Task 7 folder in your GitHub repository and add any relevant configuration files, scripts, and templates you used for this task.
Commit the changes with a message like "Task 7: Configured Azure Load Balancer with Private IP for Internal Traffic."
