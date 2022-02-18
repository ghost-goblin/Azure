# [Microsoft AZ-500](az-500-index.md): Microsoft Azure Security Technologies

## 🛡️ Implement platform protection (15-20%)

# 🕸️👨‍👨‍👧‍👦 Implement advanced network security
## Secure the connectivity of hybrid networks
## Secure the connectivity of virtual networks
### Network Security Group (NSG)
+ How do I create a Network Security Group? ... _just like with anything in Azure, you just create a **resource**_
+ Filter traffic to and from Azure resources
+ Contains security rules to allow or deny inbound/outbound traffic
+ Evaluated by priority using 5-tuple information
  1. Source Address
  2. Source Port
  3. Destination Address
  4. Destination Port
  5. Protocol
+ VMs (At the NIC level)
+ Subnets

### Role-based Access Groups
+ Principle of Least Privilege - user is given the minimum levels of access – or permissions – needed to perform their job functions
+ Security Principals - a security ID for applications or services
+ Roles
  - **Owner** has full access to all resources and grant access
  - **Contributor** can create/manage all resource, cannot grant access
  - **Reader** can view existing resources
  - **User Access Administrator** lets you mange user access
+ Scope
  - Adding the _Owner_ role at the _management group scope_ allows users in group to manage everything within all subscriptions
  - Adding the _Reader_ role at the _subscription scope_ allows users in that group to view all resource groups and resources in that subscription
  - Assigning the _Contributor_ role to an app at the _resource group_ scope allows it to manage resources within that group alone

## 🔥🧱 Create and configure **Azure Firewall**
- Managed network security service that protects your Azure network resources
- Full stateful
- High Availability
- Unrescrticted scalability
## Create and configure Azure Firewall Manager
## Create and configure **Azure Application Gateway**
- Web traffic load balancer
- Routes traffic at **OSI Layer 7**
- Can route traffic based on the URL
    - Autoscaling
    - SSL Termination
    - Connection Draining
    - Web Application Firewall
    - URL-based routing
## Create and configure Azure Front Door
## Create and configure Web Application Firewall (WAF)
## Configure a resource firewall, including storage account, Azure SQL, Azure Key Vault, or Azure App Service
## Configure network isolation for Web Apps and Azure Functions
## Implement Azure Service Endpoints
## Implement Azure Private Endpoints, including integrating with other services
## Implement Azure Private Links
## Implement **Azure DDoS Protection**
- Two Servicwe Tiers
    1. Basic
    2. Standard _(Additional mitigation capabilities)_
- Instant on protection
- Traffic monitoring
- Adaptive tuning
- Attack analytics, metrics and alerting

- - -

# 🕸️🖥️ Configure advanced security for compute
## Configure Azure Endpoint Protection for virtual machines (VMs)
## Implement and manage security updates for VMs
## Configure security for container services
## Manage access to Azure Container Registry
## Configure security for serverless compute
## Configure security for an Azure App Service
## Configure encryption at rest
## Configure encryption in transit
