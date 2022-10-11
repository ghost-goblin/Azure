<div align="center">

# 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

[<<<](az-900-part6.md) | [>>>](az-900-part2.md)
      
</div>


## ☁️ Describe Cloud Computing
### Identify the benefits and considerations of using cloud services
1. Identify the benefits of cloud computing, such as **High Availability**, **Scalability**, **Elasticity**, **Agility**, and **Disaster Recovery**
+ **High Availability** is a system specifically designed to be resilient when some component of the system fails (with no single point of failures)
  + What percentage of time does a system respond properly to requests, expressed as a percentage over time
+ **Availability** is the accessibility of an application or system by end-users
      
| What causes unavailabilty?                      |
| :---------------------------------------------- |
| Networking outage                               |
| Application failure                             |
| Power outage                                    |
|Problems with external systems such as databases |

      
+ **Scalability** is the long-term planning and implementations to deal with the increase / decrease in demand
+ **Elasticity** is the ability to aquire / release resources as and when it is needed
+ **Agility** - the ability to respond to change "rapidly" based on changes to market or environment; ensuring fast time to market
+ **Disaster Recovery** is the ability to recover from a big failure within an acceptable period of time, with an acceptable amount of data lost

- - -

2. Identify the differences between **Capital Expenditure** (CapEx) and **Operational Expenditure** (OpEx)
+ **Capital Expenditure** occurs when a company spends money, utilizes collateral, or incurs debt to purchase a new asset or enhance value to an existing one
  - One of the downsides of CapEx is that the money invested cannot be deducted immediately from your taxes
+ **Operational Expenditure** is a daily cost required to keep the business operational

- - -

3. Describe the **consumption-based model**
+  The **consumption-based model** relies on the fundamental philosophy that customers pay according to the amounts of services that they use or consume

- - -

### Describe the differences between categories of cloud services
1. Describe the **Shared Responsibility Model**
```sh
      (Less Control)
           ++
          ++++
         ++++++
       ++ SAAS ++ > Hosted Applications/apps
     ++++++++++++++
    +++++ PAAS +++++ > Development tools, database management, operating systems
  +++++++++++++++++++
 ++++++++ IAAS ++++++++ > VMs, Servers + storage, Networking firewalls/security, Data center physical plant/building
++++++++++++++++++++++++
      (More Control)
 ```


+ No matter where an application sits within the Cloud Pyramid, the user and the cloud provider share some level of responsibility
+ The cloud provider has the most responsibility at the top of the pyramid and the least responsibility at the bottom of the pyramid

- - -

2. Describe **Infrastructure-as-a-Service** (IaaS)
+ Manage the OS and software that runs on that infrastructure
+ The most popular IaaS service in Azure is called **Azure Virtual Machines**
  + SQL Server on Azure VM
+ The ability to remote into the VM is usually reserved for IaaS services

- - -

3. Describe **Platform-as-a-Service** (PaaS)
+ Azure App Service
+ Azure SQL Managed Instance
+ Azure SQL Database (DBaaS)

- - -

4. Describe serverless computing
+ **Azure Functions** are designed for backend batch applications that are continuously running
+ **Logic Apps** are designed for automated workloads:
  - Schedule and send email notifications using Office 365 when a specific event happens, for example, a new file is uploaded
  - Route and process customer orders across on-premises systems and cloud services
  - Move uploaded files from an SFTP or FTP server to Azure Storage



- - -

5. Describe **Software-as-a-Service** (SaaS)
+ **Software as a service** allows users to connect to and use cloud-based apps over the Internet

- - -

6. Identify a service type based on a use case
- Benefits of Cloud 
   + Cost savings - both real and accounting
   + Availability & Scalability
   + Reliability & Predictability
   + Security & Goverance
   + Manageability
   + Global reach
   + Range of ready on-demand services
   + Range of tools

- - -

### Describe the differences between types of cloud computing
1. Define cloud computing
+ The ability to rent cloud computing resources on demand
2. Describe Public cloud
> "The public cloud is defined as computing services offered by third-party providers over the public Internet, making them available to anyone who wants to use or purchase them."
3. Describe Private cloud
> "The private cloud is defined as computing services offered either over the Internet or a private internal network and only to select users instead of the general public."
4. Describe Hybrid cloud
> "A hybrid cloud—sometimes called a cloud hybrid—is a computing environment that combines an on-premises datacenter (also called a private cloud) with a public cloud, allowing data and applications to be shared between them."

- - -

5. Compare and contrast the three types of cloud computing
+ IaaS vs. PaaS vs. SaaS
+ Cloud pricing is complicated
+ Usually any service is priced by 2 or 3 metrics combined
