# [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

## ⚔️ Describe general security and network security features

### Describe Azure security features
1. Describe basic features of **Microsoft Defender** for **Cloud**, including policy compliance, security alerts, secure score, and resource hygiene
+ **[Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)** is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection Platform (CWPP) for all of your Azure, on-premises, and multicloud (Amazon AWS and Google GCP) resources


- - -

2. Describe the functionality and usage of **Azure Key Vault**
+ **[Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/basic-concepts)** is a cloud service for securely storing and accessing secrets

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


- - -

2. Describe the functionality and usage of **Network Security Group** (NSG)
+ How do I create a [Network Security Group](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview)? ... _just like with anything in Azure, you just create a **resource**_
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


- - -


3. Describe the functionality and usage of **Azure Firewall**
- [Azure Firewall](https://learn.microsoft.com/en-us/azure/firewall/overview) is a cloud-native and intelligent network firewall security service
- Managed network security service that protects your Azure network resources
- Full stateful
- High Availability
- Unrescrticted scalability


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
