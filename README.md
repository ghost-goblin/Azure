<div align='center'>

# ☁️ Microsoft Azure Services & Concepts

</div>

### 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

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


## 🖼️ Configuring TLS/SSL Certificates
+ Protocols that are used to secure communication between different machines
+ If you buy a SSL certificate to secure your App Service, it will consist of **two** keys; the public key and the private key
+ The private key never leaves the server and will always stay on the certificate owner's machine, it is used to encrypt / decrypt the payloads
+ If any client wishes to communuicate withe the server, the client will use their public key to encrypt their request
+ The server processes the request and generates a response, encrypts the respinse using the private key and sends it back to the client
+ TLS provides privacy and data integrity between communicating applications by encrypting the payload
+ The public key is packaged into the SSL certificate and shared with clients (i.e. web browsers)
  - SSL protocol is depreciated, **TLS** (Transport Layer Security) has replaced it

> SSL/TLS certificates can vbe purchased from trusted authorities. They establish the authenticity of the certificates.

+ In HTTPS, the communication is encrypted using TLS (formerly SSL)
+ To use SSL with custom domains, you need to buy and configure a SSL certificate
+ The SSL certificate will be stotred in **Azure Key Vault**
+ To bind a custom SSL certifictae, your App Service plan must be in Basic, Standard, Premium, or Isolated Tier
+ You need to prove the ownership of the custom domain and add a CNAME record
+ Bind the hostname and the certificate in SSL Bindings
  - **IP Based SSL** _(A single certificate for an ip)_
  - **SNI SSL** _(Assign multiple SSL cetificates to a public IP address on a server based on the requested domain name, the server will then return the corresponding certificate)_
