# [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

## ☁️ Describe Cloud Computing
### Identify the benefits and considerations of using cloud services
1. Identify the benefits of cloud computing, such as **High Availability**, **Scalability**, **Elasticity**, **Agility**, and **Disaster Recovery**
+ **High Availability** is the _percentage_ (%) of the time system response to the user request i.e. how long a system component is operational
+ **Availability** is the accessibility of an application or system by end-users
> What causes unavailabilty?
>> Networking outage
>>> Application failure
>>>> Power outage
>>>>> Problems with external systems such as databases
+ **Scalability** is the long-term planning and implementations to deal with the increase / decrease in demand
+ **Elasticity** is the ability to aquire / release resources as and when it is needed
+ **Agility** refers to the ability of an organization to rapidly develop, test, and launch software applications that drive business growth _(addition of business value)_
+ **Disaster Recovery** is an organization's ability to respond to and recover from an event that negatively affects business operations

2. Identify the differences between **Capital Expenditure** (CapEx) and **Operational Expenditure** (OpEx)
+ **Capital Expenditure** occurs when a company spends money, utilizes collateral, or incurs debt to purchase a new asset or enhance value to an existing one
+ **Operational Expenditure** is a daily cost required to keep the business operational

3. Describe the **consumption-based model**
+  The **consumption-based model** relies on the fundamental philosophy that customers pay according to the amounts of services that they use or consume

### Describe the differences between categories of cloud services
1. Describe the **Shared Responsibility Model**
```sh
           ++> Less Control
          ++++
         ++++++
       ++ SAAS ++ > Hosted Applications/apps
     ++++++++++++++
    +++++ PAAS +++++ > Development tools, database management, operating systems
  +++++++++++++++++++
 ++++++++ IAAS ++++++++ > VMd, Servers & storage, Networking firewalls/security, Data center physical plant/building
++++++++++++++++++++++++ > More Control
 ```
+ No matter where an application sits within the Cloud Pyramid, the user and the cloud provider share some level of responsibility
+ The cloud provider has the most responsibility at the top of the pyramid and the least responsibility at the bottom of the pyramid
+ Building security
+ Physical network security
+ Physical computer security
+ OS patches
+ Network & Firweall settings
+ Application settings
+ Authentication platform
+ User accounts
+ Devices
+ Data
2. Describe **Infrastructure-as-a-Service** (IaaS)
+ Manage the OS and software that runs on that infrastructure
+ The most popular IaaS service in Azure is called **Azure Virtual Machines**
+ The ability to remote into the VM is usually reserved for IaaS services
3. Describe **Platform-as-a-Service** (PaaS)
+ Azure App Service
4. Describe serverless computing
+ Azure Functions
+ Logic Apps
5. Describe **Software-as-a-Service** (SaaS)
6. Identify a service type based on a use case

### Describe the differences between types of cloud computing
1. Define cloud computing
+ The ability to rent cloud computing resources on demand
2. Describe Public cloud
3. Describe Private cloud
4. Describe Hybrid cloud
5. Compare and contrast the three types of cloud computing
