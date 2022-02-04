# ☁️ Microsoft Azure Services & Concepts

1. [Microsoft AZ-500: Microsoft Azure Security Technologies](az-500.md)

## Azure Data Centre Regions & Availability Zones
- Physical Deployment
- High Availability & Disaster Recovery
- You need to choose the **region** (a.k.a. the datacentre/s) where you want the instance of the service created
- Not all Azure services are available in all regions.

## Azure Resource Groups
A resource is just a managable item in the cloud:
+ Virtual Machines
+ Storage Accounts
+ Web Apps
+ Databases
+ VNETs
+ etc.

### A **Resource Group** is a container that hold related resources.

+ Resources share the same lifecycle i.e. deploy, update, delete together
+ Resources can only exist in one Resource Group
+ Resource can communicate across Resource Groups
+ Container for security boundaries
+ Can export IAAS using __Resource Manager Templates__
+ Resources can be in different regions

## Azure Resource Manager (ARM)
A deployment and management service for Azure and it's central to the management of resources.
The Azure Portal sends instructions to the ARM endpoint, ARM handles authentication using Active Directory (Azure AD) and authorises the request.
ARM then sends the request to the service you are attemting to create or manipulate (App service, VM, etc.).
ARM is used by __ALL__ the tools to manage resources.
- Azure Portal
- Azure PowerShell
- Azure CLI
- REST interface

## Resource Manager Templates
These are files written in JavaScript Object Notation (JSON) and defines infrastructure and configuration for Azure resources.
+ Declarative syntax
+ Deployment
+ - Using Azure Pipelines (CI/CD)
+ - From GitHub
+ - Using PowerShell and the Azure CLI
+ - Resource Manager ARM REST API
+ - Azure Portal

### Agile Development and DevOps
+ Combines IT Operations and Development
+ Infrastructure now being managed as code
+ Can be stored and versioned in code repositories
+ Included in CI/CD pipelines

## Azure Advisor
For optimising your costs

## Azure Compute
Set of Services for on-demand computing power
1. Virtual Machines
2. Containers
3. Azure App Service
4. Serverless Computing

## Azure Virtual Machines
+ IAAS
+ Full control over the OS
+ Must maintain and patch VM

## 🐋 Containers
> Virtual Machines virtualise the hardware while containers virtualise the operating system on a runtime instead of a hypervisor

### Hosting options for Containers:
1. Local Workstation
2. On-premises Servers
3. VMs in Azure
4. Azure Container Instances (ACI) [__Small scale__]
5. Azure Kubernetes Service (AKS) [__Large scale__]
6. Azure App Service

## Azure Kubernetes Service
A container management system that runs in the cloud, can scale, monitor and deploy your container-based applications. **Pods** are groups of containers with shared storage and network resources.
+ Nodes are virtual machines in AKS and can leverage VM scale sets
+ Azure Container Registry
+ Azure Monitor

## Azure App Services
+ Web Apps
+ API Apps
+ Mobile Apps
+ Containers
+ WebJobs

## Serverless Compute
Focus on the code and business logic
+ **Azure Functions** allow you to write small pieces of code iniated by triggers (C#, PowerShell, Python)
+ **Azure Logic Apps** design workflows in the Azure Portal and you can call Azure Functions if needed
+ **Azure Event Grid** connects data sources and event handlers

# Data Storage in Azure
- Automated backup & recovery
- Replication across the world
- Encryption options
- Security & platform integration
- Development features & support (APIs)

# Types of Data
1. Structured/Relational Data
+ Azure SQL Database
+ Azure Database for MySQL
+ Azure Database for PostgreSQL

2. Unstructured Data 
+ Azure Blob Storage
+ Azure File Storage (supports SMB protocol)
+ Azure Disk Storage

3. Semi-structured Data (Non-Relational/NoSQL)
### Cosmos DB
  - Retail Applications
    + Attributes can vary & change over time
    + Flexible schema
  - Gaming Applications
    + Millions of simiultaneous updates
    + Millisecond reads
  - Social Media Applications
    + Flexible data schemas needed for user generated content
+ Elastically scale throughput and storage across any number of Azure regions
+ Add/remove regions easily
+ Backed by SSD storage
+ Consistency options to ensure distributed data is updated
#### Cosmos DB APIs
- SQL API
- Cassandra
- Mongo DB
- Gremlin
- Azure Table Storage

# SQL Server
1. Host SQL Server on Virtual Machines
+ Full control over the SQL Server
+ Can provision from the Azure Marketplace
+ Flexible pricing oprions
+ Automated updated scheduling
+ Managed Backup to Azure

2. Azure SQL Databade (fully managed PAAS in the cloud)
+ Always running the latest version of SQL Server
+ Flexible pricing model
  - Vcores
  - DTU's
+ Single database or Elastic Pool
+ Automatic scaling
+ Service tiers for different workloads

3. Azure SQL Managed Instance 
+ Broadset of SQL Server capabilities
+ Benefits of managed platform
+ Deploy VM onto your own VNET
+ Lift-and-shift with minimal changes

# Authorization to Data
+ RBAC in Azure AD
+ Srorage Account Keys
+ Shared Access Signatures
