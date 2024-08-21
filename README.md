# ShopEasy Multi-Tier Application on Azure.
## Objective.

This project aims to design and implement a secure, scalable multi-tier application for ShopEasy, a retail company expanding its online presence. The infrastructure is built using Azure services, focusing on the following key aspects:

* **Security**: Proper segmentation of the network into separate subnets and implementation of Network Security Groups (NSGs) to control traffic flow.
* **Scalability**: Deployment of Virtual Machine Scale Set (VMSS) to handle varying levels of web traffic.
* **Resiliency**: Use Azure Load Balancer to distribute incoming traffic and ensure high availability.
* **Management**: Implementation of Azure Bastion Host to securely manage Virtual Machines (VMs) within the network.

## Project Tasks
1. # Create a Resource Group.
   * I created a Resource Group named Cloudlearner to manage and maintain all the resources for this project.
  
2. # Create a Virtual Network.
   I created an Azure Virtual Network named "Shopeasy-VNET" with IP 10.0.0.0/16.
   Three subnets were created as well:
     *  Web-subnet 10.0.1.0/24
     *  App-subnet 10.0.2.0/24
     *   DB-subnet  10.0.3.0/24
  ![subnets](https://github.com/user-attachments/assets/4f58070c-10d3-4cfc-a816-0f175633317a)

3. # Deploy Virtual Machines.
   I deployed 3 Virtual Machines and Virtual Machine Scale Sets.
     * **Web Subnet**: A Windows VM (Web-VM) is deployed to host the front end and a Virtual Machine Scale Set (VMSS) to automatically scale the web tier.
     * **Application Subnet**: A Linux VM (App-VM) is deployed to host the backend logic.
     * **Database Subnet**: A SQL Server VM (DB-VM) is deployed to store customer data.

4. # Implement Network Security


   * I created Network Security Groups (NSGs) and configured them to control traffic between subnets:
     * **Web-VM-NSG**: HTTP/HTTPS traffic is allowed to the Web VM and VMSS.
     * **App-VM-NSG**: Traffic is allowed only from the Web-Subnet to the DB-subnet.
     * **DB-VM-NSG**: Traffic is allowed only from the App-Subnet.
   * I deployed Azure Bastion Host set up for secure access to all VMs within the VNet.
    
  
   
   ![NSG](https://github.com/user-attachments/assets/f8df7576-cb51-46d0-9281-4523be268689)
       
  
