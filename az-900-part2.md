<div align="center">
      
# 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals
    
[<<<](az-900-part1.md) | [>>>](az-900-part3.md)
      
</div>
  

## 🚒 Describe core Azure Services

### Describe the core Azure architectural components
1. Describe the benefits and usage of **Regions** and **Region Pairs**
+ An **Azure Region** is a set of Datacenters that are connected through a dedicated low-latency network
+ A region could be made up of one or multiple datacenters
+ A **Region Pair** is a relationship between 2 Azure Regions within the sane geographic region for disaster recovery purposes

- - -

2. Describe the benefits and usage of **Availability Zones**
+ **Availability Zones** are physically seperate locations within each Azure region that are [tolerant to local failures](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview)     
+ Azure Data Centre Regions & Availability Zones
  - Physical Deployment
  - High Availability & Disaster Recovery
  - You need to choose the **region** (a.k.a. the datacentre/s) where you want the instance of the service created
  - Not all Azure services are available in all regions

- - -

3. Describe the benefits and usage of **Resource Groups**
+ A resource is just a managable item in the cloud:
  + Virtual Machines
  + Storage Accounts
  + Web Apps
  + Databases
  + VNETs    
+ A **Resource Group** is a logical container where you are creating your Azure resources
+ A **Resource Group** created in one region can contain the resources created in the other regions
+ If you go to the `Access Control (IAM)` section of the resource, you will see that the _permissions_ are inherited from the Resource Group
+ Resources share the same lifecycle i.e. deploy, update, delete together
+ Resources can only exist in one Resource Group
+ Resource can communicate across Resource Groups
+ Container for security boundaries
+ Can export IAAS using __Resource Manager Templates__

- - -

4. Describe the benefits and usage of **Subscriptions**
+ To use Azure's cloud-based services, you must first purchase a subscription
+ There's **no limit** to the number of subscriptions a single user can be included on
+ Highest level Azure resource
+ Each subscription has a unique ID
+ Subscriptions have quotas
+ A subscription is the parent of the Resource Group


- - -

5. Describe the benefits and usage of **Management Groups**
+ Organise multiple Azure subscriptions or other Management Groups and apply governance policies across subscriptions
+ A **Management Group** tree can support up to **6** levels of depth
+ The root **Management Group**'s display name is Tenant root group and operates itself as a Management Group _(the ID is the same value as the Azure AD tenant ID)_
+ **Azure role-based access control** (RBAC) is used for all _resource access_ & _role definitions_

- - -

6. Describe the benefits and usage of **[Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview)** (ARM)
- **IaC** - Ifrastucture as Code
+ A deployment and management service for Azure and it's central to the management of resources
+ The Azure Portal sends instructions to the ARM endpoint, ARM handles authentication using Active Directory (Azure AD) and authorises the request
+ ARM then sends the request to the service you are attemting to create or manipulate (App service, VM, etc.)
+ ARM is used by __ALL__ the tools to manage resources
  - Azure Portal
  - Azure PowerShell
  - Azure CLI
  - REST interface (an architectural style or design pattern for APIs)
+ Azure provides 4 levels of hierarchical scope:

| Scope             | Level           |
| :---------------- |:---------------:|
| Management Groups | 1               |
| Subscriptions     | 2               |
| Resource Groups   | 3               |
| Resources         | 4               |

      
+ [ARM Templates](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/syntax) __(JSON format)__

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```
- - -


7. Explain Azure resources
+ A **Resource Group** is a container that hold related resources.
  + Resources share the same lifecycle i.e. deploy, update, delete together
  + Resources can only exist in one Resource Group
  + Resource can communicate across Resource Groups
  + Container for security boundaries
  + Can export IAAS using __Resource Manager Templates__
  + Resources can be in different regions

- - -

### Describe core resources available in Azure
1. Describe the benefits and usage of **Virtual Machines**, **Azure App Services**, **Azure Container Instances** (ACI), **Azure Kubernetes Service** (AKS), and **Azure Virtual Desktop**
+ Virtual Machines virtualise the hardware while containers virtualise the operating system on a runtime instead of a hypervisor
+ **IaaS** makes up the Infrastructure that constitutes your Azure Virtual Machines
+ URL to manage Azure Web Apps: [https://portal.azure.com/#create/hub](https://portal.azure.com/#create/hub)
  

#### Compute services - _executing code on the cloud_
+ **Virtual Machines**
  - IaaS
  + Each virtual network in Azure needs to be assigned to an address space: `15.0.0.0/16`
  + Each Virtual Machine has a [Resource Health blade](https://learn.microsoft.com/en-us/azure/service-health/resource-health-overview)
  + Full control over the OS
  + Must maintain and patch VM
  - Take an existing machine from your environment into the cloud - _a copy_
  - Windows or Linux operating systems - several of each
  - A "slice" of physical machine shared with other customers
  - Full control over it, as if it was your machine
  - Over 200 Virtual Machine types to choose from
  - Number of CPU cores, CPU speed, RAM size, temporary disk size, IOPS, etc.
  - [Tutorial](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal): Create a Windows virtual machine in the Azure portal  


+ **[VM Scale Sets](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/overview)** (VMSS)
  + **1000** virtual machines can be managed under a single VM Scale Set
  - Elasticity
  - 2 or more VMs running the exact same code
  - A **Load Balancer** in front to direct traffic randomly to one of the machines
  - Autoscaling: add more and reduce machines on demand
  - Can handle up to 100 VMs in a single scale set
  - Can be configured to increase that to 1000 VMs in a single scale set
  - [Tutorial](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/flexible-virtual-machine-scale-sets-portal): create virtual machines in a scale set using Azure portal


+ **App Services** (Web apps)
  - HTTP-based PaaS for hosting web applications, REST APIs and mobile back ends
  - Give your **code** and **configuration** to Azure, and they will run it
    + Web & API Apps
    + Mobile Apps
    + Docker containers (Windows and Linux)
    + WebJobs (Functions & Logic Apps)
      - .NET
      - .NET Core
      - Java
      - Ruby
      - Node.js
      - PHP
      - Python
  - **Azure Load Balancer** works at the **Layer 4** of OSI Reference Model using the TCP and UDP protocols to manage transaction traffic and direct it to several identical VMs
    + High availability for your application
    + Front-end IP configuration ccontains one or more public IP addresses
    + VMs connect to a load balancer using their virtual NIC
    + A back-end address pool contains the IP addresses of the virtual NICs connected to the load balancer
  - **[Application Gateway](https://learn.microsoft.com/en-us/azure/app-service/environment/integrate-with-application-gateway)** understands the **HTTP** protocol _(Layer 7)_ and can make load balancing decisions based on the **URL** path _while a load balancer cannot_
    - optional **Web Application Firewall** (WAF)

- - -      

#### Configuring TLS/SSL Certificates
  + Protocols that are used to secure communication between different machines
  + If you buy a SSL certificate to secure your App Service, it will consist of **two** keys; the public key and the private key
  + The private key never leaves the server and will always stay on the certificate owner's machine, it is used to encrypt / decrypt the payloads
  + If any client wishes to communuicate withe the server, the client will use their public key to encrypt their request
  + The server processes the request and generates a response, encrypts the respinse using the private key and sends it back to the client
  + TLS provides privacy and data integrity between communicating applications by encrypting the payload
  + The public key is packaged into the SSL certificate and shared with clients (i.e. web browsers)
  - SSL protocol is depreciated, **TLS** (Transport Layer Security) has replaced it
  + SSL/TLS certificates can vbe purchased from trusted authorities. They establish the authenticity of the certificates.
  + In HTTPS, the communication is encrypted using TLS (formerly SSL)
  + To use SSL with custom domains, you need to buy and configure a SSL certificate
  + The SSL certificate will be stotred in **Azure Key Vault**
  + To bind a custom SSL certifictae, your App Service plan must be in Basic, Standard, Premium, or Isolated Tier
  + You need to prove the ownership of the custom domain and add a CNAME record
  + Bind the hostname and the certificate in SSL Bindings
    - **IP Based SSL** _(A single certificate for an ip)_
    - **SNI SSL** _(Assign multiple SSL cetificates to a public IP address on a server based on the requested domain name, the server will then return the corresponding certificate)_

      
- - -


+ **[Azure Container Instances](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-overview)** (ACI)
  - Containers contain everything the app needs to run in a "container image"
  - Fastest and easiest to deploy
  + Hosting options for Containers:
    1. Local Workstation
    2. On-premises Servers
    3. VMs in Azure
    4. Azure Container Instances (ACI) [__Small scale__]
    5. Azure Kubernetes Service (AKS) [__Large scale__]
    6. Azure App Service
+ **[Azure Kubernetes Service](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes)** (AKS)
  + A container management system that runs in the cloud, can scale, monitor and deploy your container-based applications
  + **Pods** are groups of containers with shared storage and network resources
  + Nodes are virtual machines in AKS and can leverage VM scale sets
  + Azure Container Registry
  + Azure Monitor
    - runs on a cluster of servers _(enterprise-grade)_
  + Deploy a container on AKS
    - The Azure CLI
    - The Azure portal
    - Azure PowerShell
    - Using template-driven deployment options (Azure Resource Manager templates)
      - Create an **Azure Kubernetes Service** > `Create a resource`
      - `Workloads` > `Add with YAML`
     
```yml
apiVersion: apps/v1

kind: Deployment

metadata:

   name: nginx

spec:

   replicas: 1

   selector:

      matchLabels:

          app: nginx

   template:

      metadata:

           labels:

               app: nginx

      spec:

           containers:

            - name: nginx

              image: nginx:1.15.2

              ports:

               - containerPort: 80
```

+ Create a Load Balancer service for the container
  - `Services and ingresses` > `Add with YAML`

```yml
apiVersion: v1

kind: Service

metadata:

   name: whizlab-service

spec:

   type: LoadBalancer

   ports:

     - port: 80

   selector:

       app: nginx
```
      
      
+ **Windows Virtual Desktop**
  - **VDI**s - a virtual Windows desktop session that runs in the cloud

- - -

2. 🌐 Describe the benefits and usage of **Virtual Networks**, **VPN Gateway**, **Azure DNS**, **Virtual Network peering**, and **ExpressRoute**
- A **[Virtual Network](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)** emulates a physical network
  - **System routes** are automatically created and assigned to each subnet
    - can't be created or removed but can be overridden with _Custom Routes_
  - _Custom Routes:_
    - **[User-defined routes](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview)** changes the way traffic is routed and override default System Routes
- A **[VPN Gateway](https://learn.microsoft.com/en-us/azure/vpn-gateway/design)** sends encrypted traffic between an Azure virtual network and an on-premises location over the public Internet
- **Azure DNS** is a hosting service for domain names:
  + Supports private DNS Zones for name resolution in VNETs
  + **Anycast Networking** to answer DNS queries
  + Purchase domain names from third-party domain providers _(like [GoDaddy](https://www.godaddy.com/))_
  + Azure DNS currently does not support DNSSEC
- **[Point-to-Site VPN](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-about)** lets you create a secure connection to your virtual network from an **individual** client computer
- A **Site-to-Site VPN** gateway connection is a connection over IPsec/IKE (IKEv1 or IKEv2) VPN tunnel, connections can be used for cross-premises and hybrid configurations and requires a VPN device located on-premises that has a public IP address assigned to it
- **[Virtual Network peering](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)** connects 2 or more Virtual Networks in Azure 
  - Traffic between virtual machines in peered virtual networks uses the **Microsoft backbone infrastructure**
- **ExpressRoute** is _a high speed private connection to Azure_

#### Tutorials:
+ [Create and manage a VPN gateway using the Azure portal](https://docs.microsoft.com/en-us/azure/vpn-gateway/tutorial-create-gateway-portal)
+ [Create a site-to-site VPN connection in the Azure portal](https://learn.microsoft.com/en-us/azure/vpn-gateway/tutorial-site-to-site-portal)


- - -

3. 💾 Describe the benefits and usage of **Container (Blob) Storage**, **Disk Storage**, **File Storage**, and **Storage Tiers**
- Automated backup & recovery
- Replication across the world
- Encryption options
- Security & platform integration
- Development features & support:
  + REST API
+ [Storage accounts](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview) contain an Azure object with a unique namespace
+ A single subscription can have up to **250** storage accounts per region
+ Each storage account can store up to **5 Petabytes**
+ Create a storage account in the Azure Portal and the CLI
1. **Standard** Performance Tier
      + storing blobs, files, tables, queues and Azure VMs
2. **Premium** Performance Tier
      + unmanaged VM disks only
#### Storage Types    
1. **Blob**
      - Text + Binary Data
2. **File**
      - Create a [Server Message Block](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-quick-create-use-windows) (SMB) file share
      - Create a [Network File System](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-quick-create-use-linuxhttps://learn.microsoft.com/en-us/azure/storage/files/storage-files-quick-create-use-linux) (NFS) file share
      - Azure Files REST API
3. **Queue**
      - A messaging service for messaging between application components
4. **Table**
      - NoSQL database in the cloud
      - Highly scalable
#### Set a [Blob Storage Access Tiers](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-online-manage?tabs=azure-portal) at the Blob level
+ **Blob storage** is optimized for storing massive amounts of unstructured data
1. **🔥 Hot**
    - optimised for frequent access of objects
2. **❄️ Cool**
    - optimised for frequent storing large amounts of data that is infrequently accessed and stored for at least 30 days
3. **🗃️ Archive** 
    - optimised for frequent data that can tolerate several hours of retrieval latency _(180 days)_


 ```sh
# Change the storage account tier to Cool
az storage account update \
    --resource-group <resource-group> \
    --name <storage-account> \
    --access-tier Cool
```
      
  
1. **Block blobs** store text and binary data
      + made up of blocks of data that can be managed individually, up to about 190.7 TiB
2. **Append blob** are made up of blocks like block blobs but are optimized for append operations i.e. logging data from virtual machines
3. **Page blobs** store random access files
      + store virtual hard drive (VHD) files and serve as disks for Azure virtual machine, up to 8 TiB in size

+ Azure managed disks are _block-level_ storage volumes that are managed by Azure and used with Azure Virtual Machine
  - Ultra disks
  - Premium solid-state drives (SSD)
  - Standard SSDs
  - Standard hard disk drives (HDD)
+ **Locally-Redundant Storage** (LRS)
  - simple,low-cost replication, duplicates your data **3** times inside a _single data center_
+ **Zone-Redundant Storage** (ZRS)
  - high availability & durability, replicated synchronously across **3** availability zones
+ **Geo-Redundant Storage** (GRS)
  - replicates data **3** times synchronously inside a single physical location across **2** regions
+ **Geo-Zone-Redundant storage** (GZRS)
  - replicated across **3** Azure _availability zones_ & duplicated to a secondary geographic area for disaster recovery
+ **Read-access Geo-Redundant Storage** (RA-GRS)
  - cross-regional replication with _read access only_



- - -

4. Describe the benefits and usage of **Cosmos DB**, **Azure SQL Database**, **Azure Database** for **MySQL**, **Azure Database** for **PostgreSQL**, and **Azure SQL Managed Instance**
+ Types of Data:
  + **Structured/Relational Data**
    + Azure SQL Database
      + Host SQL Server on Virtual Machines
      + Full control over the SQL Server
      + Can provision from the Azure Marketplace
      + Flexible pricing oprions
      + Automated updated scheduling
      + Managed Backup to Azure
      + Azure Database for MySQL
          + Always running the latest version of SQL Server
          + Flexible pricing model
            - Vcores
            - DTU's
          + Single database or Elastic Pool
          + Automatic scaling
          + Service tiers for different workloads
      + Azure Database for PostgreSQL
      + **Azure SQL Managed Instance** 
          + Broadset of SQL Server capabilities
          + Benefits of managed platform
          + Deploy VM onto your own VNET
          + Lift-and-shift with minimal changes
  + **Unstructured Data** 
    + Azure Blob Storage
    + Azure File Storage (supports SMB protocol)
    + Azure Disk Storage
  + **Semi-structured Data** (_Non-Relational/NoSQL_)
    + **Cosmos DB**
      - No need for schema or Index management
      - Ensure low latency access to data from around the world
      + Elastically scale throughput and storage across any number of Azure regions
      + Add/remove regions easily
      + Backed by SSD storage
      + Consistency options to ensure distributed data is updated
      - Retail Applications
        + Attributes can vary & change over time
        + Flexible schema
      - Gaming Applications
        + Millions of simiultaneous updates
        + Millisecond reads
      - Social Media Applications
        + Flexible data schemas needed for user generated content
    + **Cosmos DB API**s
      - SQL API
      - Cassandra
      - Mongo DB
      - Gremlin
      - Azure Table Storage

+ **[Azure Data Lake](https://learn.microsoft.com/en-us/power-bi/transform-model/dataflows/dataflows-azure-data-lake-storage-integration)** service is used for storing  data that is infrequently used
+ Use **Azure SQL**, **Azure PostgreSQL**, or **COSMOS DB** for frequently accessed data
+ **Private endpoints** allows your private VNET to access Azure services such as **Storage**, **Cosmos DB**, and **SQL Database** privately by disabling public access
+ A **private endpoint** is a network interface that uses a _private IP Address_ from your virtual network and securely connects you to a service _(powered by Azure Private Link)_

- - -

5. Describe the benefits and usage of Azure Marketplace
+ [Azure Marketplace](https://docs.microsoft.com/en-us/marketplace/azure-marketplace-overview) is an online store within the Azure Portal to find all of the __third-party__ virtual machine and other offers

- - -
      
6. Identify options for moving files, including **AzCopy**, **Azure Storage Explorer**, and **Azure File Sync**
+ **AzCopy** is a command-line tool that moves data into and out of Azure Storage
  + `azcopy [command] [arguments] --[flag-name]=[flag-value]`
+ **Microsoft Azure Storage Explorer** is a standalone app that makes it easy to work with Azure Storage data on Windows, macOS, and Linux
+ [Azure File Sync](https://learn.microsoft.com/en-us/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-portal%2Cproactive-portal) to centralize your organization's file shares in Azure Files
  + **Cloud Tiering** - most frequestly accessed files are replicated locally, while infrequently accessed files are stored in Azure
  + **Storage Sync Service** resource into a resource group of your subscription

- - -

7. Describe migration options, including **Azure Migrate** and **Azure Data Box**
+ **Azure Migrate** is a unified migration platform to start, run, and track your migration to Azure
+ **Azure Data Box** for **offline** data transfer when you are limited by time, network, or cost
      
- - -

8. Describe the purpose of **[Azure Arc](https://learn.microsoft.com/en-us/azure/azure-arc/overview)**
+ Manage your entire environment together by projecting your existing non-Azure and/or on-premises resources into Azure Resource Manager
