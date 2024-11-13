Task 2: Create a Virtual Network (VNet) in Azure
Creating a Virtual Network (VNet) is a foundational step in Azure networking. VNets allow you to securely connect resources to each other and to the internet.

Goal of This Task
You will:

Create a Virtual Network in Azure.
Define an address space for the VNet.
Create one or more subnets within the VNet.
Why This Task Is Important
A VNet provides the foundation for isolating and managing your resources in a secure way. Each VNet acts as a private network for your Azure environment, enabling you to control IP address allocation, subnets, and even connectivity between different VNets or on-premises networks.

Step-by-Step Instructions
Step 1: Define Your VNet Parameters
Before creating the VNet, decide on the following:

Address Space: This is the range of IP addresses that will be available within your VNet (e.g., 10.0.0.0/16).
Subnets: Each VNet can be divided into subnets. For instance, you could have a "web" subnet for frontend services and a "data" subnet for databases. Each subnet requires its own IP address range (e.g., 10.0.1.0/24).
Step 2: Create the ARM Template
Here’s a sample ARM template (vnet-template.json) to create a VNet with two subnets:

json
Copy code
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Network/virtualNetworks",
      "apiVersion": "2021-02-01",
      "name": "MyVNet",
      "location": "[resourceGroup().location]",
      "properties": {
        "addressSpace": {
          "addressPrefixes": [
            "10.0.0.0/16"
          ]
        },
        "subnets": [
          {
            "name": "web-subnet",
            "properties": {
              "addressPrefix": "10.0.1.0/24"
            }
          },
          {
            "name": "data-subnet",
            "properties": {
              "addressPrefix": "10.0.2.0/24"
            }
          }
        ]
      }
    }
  ]
}
Save this as vnet-template.json.

Step 3: Deploy the ARM Template in Azure Portal
Go to the Azure Portal.
Navigate to Resource Groups and select the resource group where you want to deploy the VNet.
Click Deploy a custom template.
Select Build your own template in the editor and paste the contents of vnet-template.json.
Click Save, then click Review + create.
Click Create to deploy the VNet.
Step 4: Verify the VNet Creation
Once the deployment completes:

Go to Virtual Networks in the Azure Portal.
Verify that your VNet (MyVNet) and its subnets (web-subnet and data-subnet) have been created.
Commit Your Work to GitHub
Once you're comfortable with the template:

Create a Task 2 folder in your GitHub repository.
Add vnet-template.json to this folder.
Commit the changes with a message like "Added Task 2: VNet creation template".
