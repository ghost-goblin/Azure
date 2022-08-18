# [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

## 🚒 Describe core Azure Services

### Describe the core Azure architectural components
1. Describe the benefits and usage of **Regions** and **Region Pairs**
+ An **Azure Region** is a set of Datacenters that are connected through a dedicated low-latency network
+ A region could be made up of one or multiple datacenters
+ A **Region Pair** is a relationship between 2 Azure Regions within the sane geographic region for disaster recovery purposes

2. Describe the benefits and usage of **Availability Zones**
+ **Availability Zones** are physically seperate locations within each Azure region that are [tolerant to local failures](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview)

> Azure provides 4 levels of scope: 
>> Management Groups
>>> Subscriptions
>>>> Resource Groups
>>>>> Resources

3. Describe the benefits and usage of **Resource Groups**
+ A **Resource Group** is a logical container where you are creating your Azure resources
+ A **Resource Group** created in a specific region can contain the resources created in the other regions
+ **Resource Group** _tags_ are not inherited to resources within the group
+ If you go to the `Access Control (IAM)` section of the resource, you will see that the _permissions_ are inherited from the Resource Group
4. Describe the benefits and usage of **Subscriptions**
+ To use Azure's cloud-based services, you must first purchase a subscription
+ Highest level Azure resource
+ Each subscription has a unique ID
+ Subscriptions have quotas
+ A subscription is the parent of the Resource Group

5. Describe the benefits and usage of **Management Groups**
+ A logical construct
+ Organise multiple Azure subscriptions or other Management Groups

6. Describe the benefits and usage of [Azure Resource Manager](https://docs.microsoft.com/en-us/azure/azure-resource-manager/) (ARM)
+ A deployment and management service for Azure and it's central to the management of resources.
The Azure Portal sends instructions to the ARM endpoint, ARM handles authentication using Active Directory (Azure AD) and authorises the request.
ARM then sends the request to the service you are attemting to create or manipulate (App service, VM, etc.).
ARM is used by __ALL__ the tools to manage resources.
  - Azure Portal
  - Azure PowerShell
  - Azure CLI
  - REST interface (an architectural style or design pattern for APIs)

7. Explain Azure resources

### Describe core resources available in Azure
1. Describe the benefits and usage of **Virtual Machines**, **Azure App Services**, **Azure Container Instances** (ACI), **Azure Kubernetes Service** (AKS), and **Azure Virtual Desktop**
+ **IaaS** makes up the Infrastructure that constitutes your Azure Virtual Machines
+ URL to manage Azure Web Apps: [https://portal.azure.com/#create/hub](https://portal.azure.com/#create/hub)
+ **Azure Cognitive Services** has an entire list of features that can be used to build **Artificial Intelligence** based applications

#### Compute services - _executing code on the cloud_
+ Virtual Machines
  - IaaS
  - Take an existing machine from your environment into the cloud - _a copy_
  - Windows or Linux operating systems - sveral of each
  - A "slice" of physical machine shared with other customers
  - Full control over it, as if it was your machine
  - Over 200 Virtual Machine types to choose from
  - Number of CPU cores, CPU speed, RAM size, temporary disk size, IOPS, etc.
+ VM Scale Sets (VMSS)
  - Elasticity
  - 2 or more VMs running the exact same code
  - A **Load Balancer** in front to direct traffic randomly to one of the machines
  - Autoscaling: add more and reduce machines on demand
  - Can handle up to 100 VMs in a single scale set
  - Can be configured to increase that to 1000 VMs in a single scale set
+ App servicea (Web apps)
  - A new paradigm for running code in the cloud
  - Give your code and configuration to Azure, and they will run it
  - Promise of performance with no access to physical hardware
  - PaaS
+ Azure Container Instances (ACI)
  - Containers contain everything the app needs to run in a "container image"
  - Fastest and easiest to deploy
+ Azure Kubernetes Service (AKS)
  - runs on a cluster of servers, enterprise-grade
+ Windows Virtual Desktop

2. Describe the benefits and usage of **Virtual Networks**, **VPN Gateway**, **Virtual Network peering**, and **ExpressRoute**
+ Connectivity
  - A **Virtual Network** emulates a physical network
  - **ExpressRoute** is _(a high speed private connection to Azure)_

> Tutorial: [Create and manage a VPN gateway using the Azure portal](https://docs.microsoft.com/en-us/azure/vpn-gateway/tutorial-create-gateway-portal)

3. Describe the benefits and usage of **Container (Blob) Storage**, **Disk Storage**, **File Storage**, and storage tiers

4. Describe the benefits and usage of **Cosmos DB**, **Azure SQL Database**, **Azure Database** for **MySQL**, **Azure Database** for **PostgreSQL**, and **Azure SQL Managed Instance**
+ **CosmosDB**
- No need for schema or Index management
- Ensure low latency access to data from around the world

5. Describe the benefits and usage of Azure Marketplace
+ [Azure Marketplace](https://docs.microsoft.com/en-us/marketplace/azure-marketplace-overview) is an online store that contains thousands of IT software applications and services built by industry-leading technology companies
