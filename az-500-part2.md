# [Microsoft AZ-500](az-500-index.md): Microsoft Azure Security Technologies

## 🛡️ Implement platform protection (15-20%)

# 🕸️👨‍👨‍👧‍👦 Implement advanced network security
## Secure the connectivity of hybrid networks
## Secure the connectivity of virtual networks
### Network Security Group (NSG)
+ Filter traffic to and from Azure resources
+ Contains security rules to allow or deny inbound/outbound traffic
+ Evaluated by priority using 5-tuple information
  1. Source Address
  2. Source Port
  3. Destination Address
  4. Destination Port
  5. Protocol
+ VMs
+ Subnets
### Role-based Access Groups
+ Security Principals
+ Roles

## 🔥🧱 Create and configure **Azure Firewall**
- Managed network security service that protects your Azure network resources
- Full stateful
- High Availability
- Unrescrticted scalability
## create and configure Azure Firewall Manager
## create and configure **Azure Application Gateway**
- Web traffic load balancer
- Routes traffic at **OSI Layer 7**
- Can route traffic based on the URL
    - Autoscaling
    - SSL Termination
    - Connection Draining
    - Web Application Firewall
    - URL-based routing
## create and configure Azure Front Door
## create and configure Web Application Firewall (WAF)
## configure a resource firewall, including storage account, Azure SQL, Azure Key Vault, or Azure App Service
## configure network isolation for Web Apps and Azure Functions
## implement Azure Service Endpoints
## implement Azure Private Endpoints, including integrating with other services
## implement Azure Private Links
## implement **Azure DDoS Protection**
- Two Servicwe Tiers
    1. Basic
    2. Standard _(Additional mitigation capabilities)_
- Instant on protection
- Traffic monitoring
- Adaptive tuning
- Attack analytics, metrics and alerting

# 🕸️🖥️ Configure advanced security for compute
## configure Azure Endpoint Protection for virtual machines (VMs)
## Implement and manage security updates for VMs
## configure security for container services
## manage access to Azure Container Registry
## configure security for serverless compute
## configure security for an Azure App Service
## configure encryption at rest
## configure encryption in transit
