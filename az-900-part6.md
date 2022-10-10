<div align="center">
      
# 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals
      
[<<<](az-900-part5.md) | [>>>](az-900-part1.md)
      
</div>


## 🤑 Describe **Azure cost management** and **Service Level Agreements**

### Describe methods for planning and managing costs
1. Identify factors that can affect costs (resource types, services, locations, ingress and egress traffic)
+ More information about Azure Pricing can be found [here](https://azure.microsoft.com/en-in/pricing/#product-pricing)
+ [App Service Pricing](https://azure.microsoft.com/en-in/pricing/details/app-service/windows/):
    - **Free**
    - **Shared Environment** for dev/test
    - **Basic Dedicated** environment for dev/test
    - **Standard** Run production workloads
    - **Premium** Enhanced performance and scale
    - **Isolated High-Performance**, Security and Isolation


|                              | Free   | Shared      | Basic       | Standard   | Premium    | Isolated   |
|------------------------------|--------|-------------|-------------|------------|------------|------------|
| Web, mobile or API apps      | 10     | 100         | Unlimited   | Unlimited  | Unlimited  | Unlimited  |
| Disk space                   | 1 GB   | 1 GB        | 10 GB       | 50 GB      | 250 GB     | 1 TB       |
| Maximum instances            | –      | –           | Up to 3     | Up to 10   | Up to 30*  | Up to 100  |
| Custom domain                | –      | Supported   | Supported   | Supported  | Supported  | Supported  |
| Auto Scale                   | –      | –           | –           | Supported  | Supported  | Supported  |
| Hybrid Connectivity          | –      | –           | Supported   | Supported  | Supported  | Supported  |
| Virtual Network Connectivity | –      | –           | Supported   | Supported  | Supported  | Supported  |
| Private Endpoints            | –      | –           | Supported   | Supported  | Supported  | Supported  |
| Compute Type                 | Shared | Shared      | Dedicated   | Dedicated  | Dedicated  | Isolated   |
| Pay as you go price          | Free   | $0.013/hour | $0.075/hour | $0.10/hour | $0.20/hour | $0.40/hour |


- - -

2. Identify factors that can reduce costs (reserved instances, reserved capacity, hybrid use benefit, spot pricing)
+ Azure **Reserved Instances** often offer 40% or more savings off of the price of pay-as-you-go virtual machines


- - -

3. Describe the functionality and usage of the **Pricing calculator** and the **Total Cost of Ownership** (TCO) **calculator**
+ [Total Cost of Ownership Calculator](https://azure.microsoft.com/en-in/pricing/tco/calculator/)


- - -

4. Describe the functionality and usage of **Azure Cost Management**
+ [Monitor, allocate and optimise cloud costs](https://learn.microsoft.com/en-us/training/modules/analyze-costs-create-budgets-azure-cost-management/?WT.mc_id=AZ-MVP-5003556)

- - -

### Describe Azure Service Level Agreements (SLAs) and service lifecycles
1. Describe the purpose of an Azure Service Level Agreement (SLA)
+ [Using business metrics to design resilient Azure applications](https://learn.microsoft.com/en-us/azure/architecture/framework/resiliency/business-metrics#understand-service-levelagreements)
+ Check out the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/en-us/support/legal/preview-supplemental-terms/) to see which services Azure offers in **Public Preview** _(excluded from the SLA and Limited Warranty)_

- - -

2. Identify actions that can impact an SLA (i.e. Availability Zones)
+ [SLA](https://azure.microsoft.com/en-gb/support/legal/sla/summary/) summary for Azure services


- - -

3. Describe the service lifecycle in Azure (Public Preview and General Availability)
+ [Lifecycle FAQ](https://learn.microsoft.com/en-us/lifecycle/faq/azure?WT.mc_id=AZ-MVP-5003556) defines how every Azure service is released for public use
