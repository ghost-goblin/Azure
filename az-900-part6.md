<div align="center">
      
# 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals
      
[<<<](az-900-part5.md) | [>>>](az-900-part1.md)
      
</div>


## 🤑 Describe **Azure cost management** and **Service Level Agreements**

### Describe methods for planning and managing costs
1. Identify factors that can affect costs (resource types, services, locations, ingress and egress traffic)
+ **Ingress** bandwidth is _free_; you pay for **egress** (outbound)
+ If you don't want to spend over a certain amount, implement a spending limit in the account center
+ Using up the free credits causes all your resources to be stopped until you decide to get a paid account
+ Cloud pricing is complicated, usually any service is priced by 2 or 3 metrics combined, more information about [Azure Pricing](https://azure.microsoft.com/en-in/pricing/#product-pricing)
  + [Using business metrics to design resilient Azure applications](https://learn.microsoft.com/en-us/azure/architecture/framework/resiliency/business-metrics#understand-service-levelagreements)
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
| Maximum instances            | –      | –           | Up to 3     | Up to 10   | Up to 30   | Up to 100  |
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
+ **Azure Spot Instances** make use of Microsoft's leftover Compute Capacity
+ **Azure Budgets** will notify you when your expenditure is nearing the limit, allowing you to take appropriate action



- - -

3. Describe the functionality and usage of the **Pricing calculator** and the **Total Cost of Ownership** (TCO) **calculator**
+ **Pricing calculator** is a tool that can be used to assist us in understanding the
costs of Azure services and features. It simply calculates the cost of Azure Services
+ [Total Cost of Ownership Calculator](https://azure.microsoft.com/en-in/pricing/tco/calculator/) calculates the cost reductions that could be obtained by moving your workloads to Azure
  - PDF report


- - -

4. Describe the functionality and usage of **Azure Cost Management**
+ [Monitor, allocate and optimise cloud costs](https://learn.microsoft.com/en-us/training/modules/analyze-costs-create-budgets-azure-cost-management/?WT.mc_id=AZ-MVP-5003556)

- - -

### Describe Azure Service Level Agreements (SLAs) and service lifecycles
1. Describe the purpose of an Azure Service Level Agreement (SLA)
- [Compare support plans](https://azure.microsoft.com/en-us/support/plans/)
+ The **Basic Support** plan is the default
+ To have a **Standard** Plan, it needs to be purchased

|                                                                                                                       |          Request support         | DEVELOPER Purchase support                                    | STANDARD Purchase support                                                                                                                                          | PROFESSIONAL DIRECT Purchase support                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------------|:--------------------------------:|---------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                       | Basic Request support            | DEVELOPER Purchase support                                    | STANDARD Purchase support                                                                                                                                          | PROFESSIONAL DIRECT Purchase support                                                                                                                             |
| PRICE                                                                                                                 | Included for all Azure customers | $29 per month                                                 | $100 per month                                                                                                                                                     | $1,000 per month                                                                                                                                                 |
| SCOPE                                                                                                                 | Included for all Azure customers | Trial and non-production environments                         | Production workload environments                                                                                                                                   | Business-critical dependence                                                                                                                                     |
| BILLING AND SUBSCRIPTION MANAGEMENT SUPPORT                                                                           |             Available            |                            Available                          |                                                                              Available                                                                             |                                                                             Available                                                                            |
| 24/7 SELF-HELP RESOURCES, INCLUDING MICROSOFT LEARN, AZURE PORTAL HOW-TO VIDEOS, DOCUMENTATION, AND COMMUNITY SUPPORT |             Available            |                            Available                          |                                                                              Available                                                                             |                                                                             Available                                                                            |
| ABILITY TO SUBMIT AS MANY SUPPORT TICKETS AS YOU NEED                                                                 |             Available            |                            Available                          |                                                                              Available                                                                             |                                                                             Available                                                                            |
| AZURE ADVISOR—YOUR FREE, PERSONALIZED GUIDE TO AZURE BEST PRACTICES                                                   |             Available            |                            Available                          |                                                                              Available                                                                             |                                                                             Available                                                                            |
| AZURE HEALTH STATUS AND NOTIFICATIONS                                                                                 |             Available            |                            Available                          |                                                                              Available                                                                             |                                                                             Available                                                                            |
| THIRD-PARTY SOFTWARE SUPPORT WITH INTEROPERABILITY AND CONFIGURATION GUIDANCE AND TROUBLESHOOTING                     | Not available                    |                            Available                          |                                                                              Available                                                                             |                                                                             Available                                                                            |
| 24/7 ACCESS TO TECHNICAL SUPPORT BY EMAIL AND PHONE AFTER A SUPPORT REQUEST IS SUBMITTED                              | Not available                    | Available during business hours by email only.                |                                                                              Available                                                                             |                                                                             Available                                                                            |
| CASE SEVERITY AND RESPONSE TIME                                                                                       | Not available                    | Minimal business impact (Sev C): Within eight business hours1 | Minimal business impact (Sev C): Within eight business hours1 Moderate business impact (Sev B): Within four hoursCritical business impact (Sev A): Within one hour | Minimal business impact (Sev C): Within four business hours1 Moderate business impact (Sev B): Within two hoursCritical business impact (Sev A): Within one hour |
| ARCHITECTURE SUPPORT                                                                                                  | Not available                    | General guidance                                              | General guidance                                                                                                                                                   | Guidance from a pool of ProDirect delivery managers                                                                                                              |
| SUPPORT API (SEE DETAILS)                                                                                             | Not available                    | Not available                                                 | Not available                                                                                                                                                      | Create and manage Azure support tickets programmatically                                                                                                         |
| OPERATIONS SUPPORT                                                                                                    | Not available                    | Not available                                                 | Not available                                                                                                                                                      | Service reviews and advisory consultation from a pool of ProDirect delivery managers are non-transferable and limited to Azure ProDirect customers only          |
| TRAINING                                                                                                              | Not available                    | Not available                                                 | Not available                                                                                                                                                      | Webinars led by Azure experts                                                                                                                                    |
| PROACTIVE GUIDANCE                                                                                                    | Not available                    | Not available                                                 | Not available                                                                                                                                                      | From a pool of ProDirect delivery managers                                                                                                                       |


- - -

2. Identify actions that can impact an SLA (i.e. Availability Zones)
+ [SLA](https://azure.microsoft.com/en-gb/support/legal/sla/summary/) summary for Azure services
+ [SLA](https://azure.microsoft.com/en-us/support/legal/sla/virtual-machines/v1_9/) for Virtual Machines
  - 100% SLA for 2+ Azure Virtual Machines that have been placed into different Availability Zones in the same region
  - 99.95% SLA for 2+ Virtual Machines in an Availability Set

- - -

3. Describe the service lifecycle in Azure (Public Preview and General Availability)
+ [Lifecycle FAQ](https://learn.microsoft.com/en-us/lifecycle/faq/azure?WT.mc_id=AZ-MVP-5003556) defines how every Azure service is released for public use
+ **Private Preview** are are only available for specific types of customers
+ **Public Preview** is for any customer with the proper Azure AD license to evaluate but not for production use
  + Check out the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/en-us/support/legal/preview-supplemental-terms/) to see which services Azure offers in **Public Preview** _(excluded from the SLA and Limited Warranty)_
+ **General Availability** are accessible to the whole community, support SLAs, and are appropriate for production environments

