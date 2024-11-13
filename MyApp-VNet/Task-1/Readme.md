Task 1: Setting Up a Virtual Network (VNet)
Scenario
Imagine you’re setting up a new environment for a web application that requires isolated network access for its front-end and back-end components. Your first step is to create a VNet with subnets to separate these components.

Step-by-Step Instructions
Log in to the Azure Portal: Go to portal.azure.com and sign in to your Azure account.

Navigate to Virtual Networks:

In the search bar at the top, type Virtual Networks and select it from the list.
Create a New VNet:

Click on + Create or + Add to start creating a new VNet.
Configure VNet Basics:

Subscription: Choose your subscription.
Resource Group: Either create a new resource group or select an existing one.
Name: Give your VNet a meaningful name, like MyApp-VNet.
Region: Choose the Azure region closest to your users or where most of your resources will be hosted.
IP Addresses and Subnet Configuration:

IP Address Space: Define the address space using CIDR notation. For instance, 10.0.0.0/16 provides 65,536 IP addresses, which is usually enough for most applications.
Subnets: Click on Add Subnet to create subnets within the VNet.
Frontend Subnet: Name it Frontend, and assign an IP range within the VNet, like 10.0.1.0/24.
Backend Subnet: Name it Backend, with an IP range of 10.0.2.0/24.
This setup isolates front-end and back-end traffic, keeping things organized and secure.
Additional Settings (optional for now):

DDoS Protection and Firewall options can be left at default for this beginner task.
Review and Create:

Click Review + Create to validate the configurations. Azure will check if the address ranges are valid.
Once validation passes, click Create to deploy the VNet.
Why You’re Doing This
Setting up a VNet with subnets is essential because it:

Isolates Resources: Separate networks for front-end and back-end components enhance security.
Provides Control over Traffic: With subnets, you can apply specific rules for traffic management and access control between different app layers.
Enables Scalability: By allocating different IP ranges, you can scale up each subnet independently as your application grows.
Take your time with this task. Let me know when you’re ready to move on, or if you’d like additional guidance on any step!
