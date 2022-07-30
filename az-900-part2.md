# [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

## 🚒 Describe core Azure Services
### Describe the core Azure architectural components
1. Describe the benefits and usage of **Regions** and **Region Pairs**
+ An **Azure Region** is a set of Datacenters that are connected through a dedicated low-latency network
+ A region could be made up of one or multiple datacenters
+ A **Region Pair** is a relationship between 2 Azure Regions within the sane geographic region for disaster recovery purposes

2. Describe the benefits and usage of **Availability Zones**
+ **Availability Zones** are physically seperate locations within each Azure region that are [tolerant to local failures](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview)
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
6. Describe the benefits and usage of **Azure Resource Manager** (ARM)
7. Explain Azure resources

### Describe core resources available in Azure
1. Describe the benefits and usage of **Virtual Machines**, **Azure App Services**, **Azure Container Instances** (ACI), **Azure Kubernetes Service** (AKS), and **Azure Virtual Desktop**
+ **IaaS** makes up the Infrastructure that constitutes your Azure Virtual Machines
+ URL to manage Azure Web Apps: [https://portal.azure.com/#create/hub](https://portal.azure.com/#create/hub)
+ **Azure Cognitive Services** has an entire list of features that can be used to build **Artificial Intelligence** based applications
2. Describe the benefits and usage of **Virtual Networks**, **VPN Gateway**, **Virtual Network peering**, and **ExpressRoute**
+ Tutorial: [Create and manage a VPN gateway using the Azure portal](https://docs.microsoft.com/en-us/azure/vpn-gateway/tutorial-create-gateway-portal)
3. Describe the benefits and usage of **Container (Blob) Storage**, **Disk Storage**, **File Storage**, and storage tiers
4. Describe the benefits and usage of **Cosmos DB**, **Azure SQL Database**, **Azure Database** for **MySQL**, **Azure Database** for **PostgreSQL**, and **Azure SQL Managed Instance**
+ **CosmosDB**
- No need for schema or Index management
- Ensure low latency access to data from around the world
5. Describe the benefits and usage of Azure Marketplace
