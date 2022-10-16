<div align="center">
      
# 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals
      
[<<<](az-900-part3.md) | [>>>](az-900-part5.md)
      
</div>

## ⚔️ Describe general security and network security features

### Describe Azure security features
1. Describe basic features of **Microsoft Defender** for **Cloud**, including policy compliance, security alerts, secure score, and resource hygiene
+ **[Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)** is a Cloud Security service
  - Detect threats targeting Azure services including Azure App Service, Azure SQL and Azure Storage Account
  - Classify your data in Azure SQL and get assessments for potential vulnerabilities
  - Limit exposure to brute force attacks
  - Assess resources, subscriptions, and organization for security issues and shows your security posture in **Secure Score**
  - **Security Alerts** that are powered by _Microsoft Threat Intelligence_
  - Enforce **Security Policies** from the top down
    - Set your policies to run on management groups, across subscriptions, and even for a whole tenant
    - Apply secure configuration standards across your resources.

- - -

2. Describe the functionality and usage of **Azure Key Vault**
+ **[Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/basic-concepts)** is a cloud service for securely storing and accessing secrets
+ Hardware Security Module (HSM)
+ Use **Azure Resource Graph Explorer** to count the number of Key Vaults accross multiple Azure subscriptions
  - Secrets Management
  - Key Management
  - TLS Certificate management

- - -

3. Describe the functionality and usage of **Microsoft Sentinel**
+ Microsoft's Security information and event management **[SIEM](https://learn.microsoft.com/en-us/azure/sentinel/overview)**

- - -

4. Describe the functionality and usage of **Azure Dedicated Hosts**
+ **[Azure Dedicated Hosts](https://azure.microsoft.com/en-gb/services/virtual-machines/dedicated-host/)** provides physical servers that host one or more Azure virtual machines
+ Your server is dedicated to your organisation and workloads – capacity isn’t shared with other customers


- - -

### Describe Azure network security
1. Describe the _concept of defense in depth_ (DiD)
+ **Defense in Depth** is an approach to cybersecurity in which a series of defensive mechanisms are layered in order to protect valuable data and information
+  If one mechanism fails, another steps up immediately to thwart an attack


| Layers of Security                        |
| :-----------------------------------------|
| Building security                         |
| Physical network security                 |
| OS patches                                |
| Network & Firweall settings _(perimeter)_ |
| Application settings                      |
| Authentication platform                   |
| User accounts                             |
| Devices                                   |
| Data                                      |


- - -

2. Describe the functionality and usage of **Network Security Group** (NSG)
+ Checks all traffic travelling over a subnet against a set of rules before allowing it in or out
+ How do I create a [Network Security Group](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview)? ... _just like with anything in Azure, you just create a **resource**_
+ Filter traffic to and from Azure resources
+ Contains security rules to allow or deny inbound/outbound traffic
+ Evaluated by priority using 5-tuple information:
  1. Source Address
  2. Source Port
  3. Destination Address
  4. Destination Port
  5. Protocol
+ VMs _(at the NIC level)_
+ Subnets
  - _Allow RDP traffic via NSG rules_
  - _Allow HTTP traffic via NSG rules_
    -  Install a **IIS** web server:
      + Server Manager > Add Roles and Features > `http://localhost/`

```ps1
# Install IIS server role
Install-WindowsFeature -name Web-Server -IncludeManagementTool

# Remove default htm file
Remove-Item C:\inetpub\wwwroot\iisstart.htm

# Add a new htm file that displays server name
Add-Content -Path "C:\inetpub\wwwroot\iisstart.htm" -Value $("Hello World from " + $env:computername)

```


- - -


3. Describe the functionality and usage of **Azure Firewall**
- [Azure Firewall](https://learn.microsoft.com/en-us/azure/firewall/overview) is a cloud-native and intelligent network firewall security service
  - Part of the **perimeter** security
  - **Full stateful** Managed network security service that protects your Azure network resources
  - Parent [policies](https://learn.microsoft.com/en-us/azure/firewall-manager/policy-overview) can be overridden from inheritance with stricter settings
  - Configure **NAT** ruless, **Application Rules** _(for that can be accessed over the internet (HTTP))_, custom **DNS**, DNS proxy
    - Prioritise security rules using 5-tuple information:
      1. Source Address
      2. Source Port
      3. Destination Address
      4. Destination Port
      5. Protocol



- - -


4. Describe the functionality and usage of **Azure DDoS protection**
- **[Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview)** provides enhanced DDoS mitigation features to defend against DDoS attacks
- Two Service Tiers
    1. Basic
    2. Standard _(Additional mitigation capabilities)_
- Instant on protection
- Traffic monitoring
- Adaptive tuning
- Attack analytics, metrics and alerting
