# ☁️ Microsoft Azure Services & Concepts

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
+ Declaractive syntax
+ Deployment
+ - Using Azure Pipelines (CI/CD)
+ - From GitHub
+ - Using PowerShell and the Azure CLI
+ - Resource Manager ARM Rest API
+ - Azure Portal

### Agile Development and DevOps
+ Combines IT Operations and Development
+ Infrastructure now being managed as code
+ Can be stored and versioned in code repositories
+ Included in CI/CD pipelines

## Azure Advisor
