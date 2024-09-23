# ShopEasy Multi-Tier Application on Azure.
## Objective.

This project aims to design and implement a secure, scalable multi-tier application for ShopEasy, a retail company expanding its online presence. The infrastructure is built using Azure services, focusing on the following key aspects:

* **Security**: Proper segmentation of the network into separate subnets and implementation of Network Security Groups (NSGs) to control traffic flow.
* **Scalability**: Deployment of Virtual Machine Scale Set (VMSS) to handle varying levels of web traffic.
* **Resiliency**: Use Azure Load Balancer to distribute incoming traffic and ensure high availability.
* **Management**: Implementation of Azure Bastion Host to securely manage Virtual Machines (VMs) within the network.

# Architecture Overview
The architecture comprises a Virtual Network (ShopEasy-VNet) segmented into three subnets: Web, Application, and Database. The Web Subnet contains a single VM and a VM Scale Set to handle web traffic. The Application and Database Subnets contain a single VM for backend processing and data storage. A Load Balancer distributes traffic to the web tier, and a Bastion Host provides secure access to the VMs. Network Security Groups (NSGs) enforce security policies across the subnets.


## Project Tasks
1. # Create a Resource Group.
   * I created a Resource Group named Cloudlearner to manage and maintain all the resources for this project.
  
2. # Create a Virtual Network.
   I created an Azure Virtual Network named "Shopeasy-VNET" with IP 10.0.0.0/16.
   Three subnets were created as well:
     *  Web-subnet 10.0.1.0/24
     *  App-subnet 10.0.2.0/24
     *   DB-subnet  10.0.3.0/24
     *   AzureBastionSubnet 10.0.0.192/24


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
    
  
   
  

5. # Enable Load Balancer and Auto-Scale.
     * I enabled Azure Load Balancer to distribute incoming web traffic across multiple instances of Web-VM and VMSS.
     * I implemented Auto-calling for VMSS based on CPU utilization to handle varying loads.
  
6. # Enable Application Insight.
     * I enabled Application Insights to collect performance data from your application components running within the VNets, such as response times, dependency calls, and failure rates.
     * Application insight tracks the application's overall health, identifying bottlenecks or underperforming areas within the infrastructure.
     * it helped me in detecting and diagnosing issues by logging exceptions, failed requests, and dependency failures, offering insights into the root cause of problems.
     * It provides detailed insights into user interactions with the infrastructure helping to improve user experience.
     * it will give real-time alerts for any critical issues or performance degradation, ensuring I am aware of the problem.
   
       
  
