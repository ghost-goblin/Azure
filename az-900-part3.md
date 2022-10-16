<div align="center">
      
# 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals
      
[<<<](az-900-part2.md) | [>>>](az-900-part4.md)
      
</div>
 

## 🔨 Describe core solutions and management tools on Azure 

### Describe core solutions available in Azure
1. Describe the benefits and usage of **Internet of Things** (IoT) **Hub**, **IoT Central**, and **Azure Sphere**
+ [Azure IoT Hub](https://azure.microsoft.com/en-gb/services/iot-hub/#overview) provides a cloud-hosted solution back-end to connect any device virtually
+ **Azure IoT Central** is a ready-made UX and API surface for connecting and managing devices at scale, delivering reliable data for business insights
+ **[Azure Sphere](https://learn.microsoft.com/en-us/azure-sphere/product-overview/what-is-azure-sphere)** is a secured IoT platform for building solutions that start in silicon and extend through the OS and the cloud
  - Securely connect, manage, and protect new and existing intelligent devices

- - -

2. Describe the benefits and usage of **Azure Synapse Analytics**, **HDInsight**, and **Azure Databricks**
+ **Azure Synapse Analytics** is a limitless analytics service that brings together data integration, enterprise data warehousing and big data analytics
+ **Azure HDInsight** is a managed, full-spectrum, open-source analytics service in the cloud for enterprises:
  - Hadoop
  - Apache Spark
  - Apache Hive
  - LLAP
        - Apache Kafka
+ **[Azure Databricks](https://learn.microsoft.com/en-us/azure/databricks/scenarios/what-is-azure-databricks#apache-spark-based-analytics-platform)** is an Azure-optimized _Apache R Spark-based_ analytics platform that is completely managed, quick, simple, and collaborative
  - create fully managed, dynamically auto-scalable Apache Spark clusters


- - -

3. Describe the benefits and usage of **Azure Machine Learning**, **Cognitive Services** and **Azure Bot Service**
+ **[Azure Machine Learning](https://learn.microsoft.com/EN-US/azure/machine-learning/overview-what-is-azure-machine-learning)** is a cloud service for accelerating and managing the machine learning project lifecycle
+ **Azure Cognitive Services** has an entire list of features that can be used to build **Artificial Intelligence** based applications
+ **Azure Bot Service** provides an integrated development environment for bot building
- - -

4. Describe the benefits and usage of serverless computing solutions that include **Azure Functions** and **Logic Apps**
+ **[Azure Functions](https://learn.microsoft.com/en-us/azure/azure-functions/functions-overview)** allows you to write small pieces of code iniated by triggers (C#, PowerShell, Python)
  - Build a web API Using the HTTP trigger, create an endpoint for your web apps
  - Build a serverless workflow utilizing durable functions, chain a sequence of functions together
  - Respond to database changes when a document is generated or modified in Cosmos DB, run custom logic
  - Process data in real-time, use SignalR and Functions to react to data in real-time
+ **[Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview)** design workflows in the Azure Portal and you can call Azure Functions if needed
+ **Azure Event Grid** connects data sources and event handlers

- - -

5. Describe the benefits and usage of **Azure DevOps**, **GitHub**, **GitHub Actions**, and **Azure DevTest Labs**
+ **Azure DevOps** is a collection of services that allow teams to share their code, track their work, and deploy and ship software:
  + Agile Development and DevOps
  + Combines IT Operations and Development
  + Infrastructure now being managed as code
  + Can be stored and versioned in code repositories
  + Included in CI/CD pipelines
    - Azure Boards
    - Azure Pipelines
    - Azure Repos
    - Azure Artifacts
    - Azure Test Plans
+ **[GitHub Actions](https://learn.microsoft.com/en-us/azure/developer/github/github-actions)** helps you automate your software development workflows from within GitHub
+ **[Azure DevTest Labs](https://learn.microsoft.com/en-us/azure/devtest-labs/devtest-lab-overview)** is a service for easily creating, using, and managing infrastructure-as-a-service (IaaS) virtual machines (VMs) and platform-as-a-service (PaaS) environments in labs
  + Create Windows and Linux training and demo environments, or sandbox resource groups for exploring Azure, by using reusable ARM templates and artifacts
    + Use the Azure CLI command-line tool to manage VMs and environments
  + Test app versions and scale up load testing by creating multiple test agents and environments
  + Create development or testing environments from continuous integration and deployment (CI/CD) tools

- - -

### Describe Azure management tools
1. Describe the functionality and usage of the **Azure Portal**, **Azure PowerShell**, **Azure CLI**, **Cloud Shell**, and **Azure Mobile App**

+ **Azure Portal** is a web-based GUI console where you can manage subscriptions
+ **Azure PowerShell** can be used for automation and DevOps     
      
```ps1
Install-Module Az -Force -AllowClobber
#sign in
Connect-AzureAD 
$domain = "domain.onmicrosoft.com"

### Managing Users with Azure PowerShell
$passwordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password = "p@ssword1"

### Get the existing user
Get-AzureADUser -SearchString "PE"
Get-AzureADUser -Filter "State eq 'PE'"

### Create a new user storing all the parameters in a hash table
$user = @{
  City = "Pennsylvania"
  Country = "United States"
  DisplayName = "Michael Scott"
  JobTitle = "Regional Manager"
  UserPrincipalName = mscott@domain
  PasswordProfile = $PasswordProfile
  PostalCode = "19001"
  State = "PE"
  Street Address = "Dunder Mifflin Paper Company, Inc."
  Surname = "Scott"
  TelephoneNumber = "215-867-5309"
  AccountEnabled = $true
  UsageLocation = "US"
}

### pass the hash table of parameters
$newUser = New-AzureADUser @user

### Creating & Managing Groups with PowerShell 

Find-Module AzureAD
Install-Module AzureAD
Import-Module -Name AzureAD

### Get credentials to connect
$AzureADCredentials = Get-Credential -Message "Login to Azure AD"
### Connect to tenant
Connect-AzureAD -Credential $AzureADCredentials

Get-Command -Module AzureAD

### Working with roles
Connect-AzureAD
Get-AzureADDirectoryRole
$CompanyAdminRole = Get-AzureADDirectoryRole | Where-Object {$_.DisplayName -eq "Comapany Administrator"}
Get-AzureADDirectoryRoleMember -ObjectId $CompanyAdminRole.ObjectId

### Get a list of all Roles
Get-AzureADDirectoryRoleTemplate

$group = Get-AzureADGroup -SearchString "Information Technology"
### Get all the members &  the owner
Get-AzureADGroupOwner -ObjectId $group.ObjectId

### Create a new group hash table
$group = @{
  DisplayName = "Marketing Group"
  MailEnabled = $false
  MailNickName = "MarketingGroup"
  SecurityEnabled = $true
}
$newGroup = New-AzureADGroup @group

### Update the group description
Set-AzureADGroup -ObjectId $newGroup.ObjectId -Description "Group for the Marketing Department"
```
+ **Azure CLI** is a command line interface for Azure:
  + The real benefit is **automation**

```sh     
az login
az account   
az group
      az group list
      az group create

# Create a NIC
az network nic create \
--resource-group ContosoResourceGroup \
--name ContosoNIC4 \
--location eastus \
--subnet ContosoVM1Subnet \
--private-ip-address 10.0.0.10 \
--vnet-name ContosoVM1VNET

# Create a VM
az vm create \
--resource-group ContosoResourceGroup \
--name ContosoDC01 \
--location eastus \
--image Win2019Datacenter \
--admin-username adminuser \
--nics ContosoNIC4
```

+ **Cloud Shell** is a cloud hosted shell environment
  - access through **Azure Portal**
  - mount storage (Storage Account)
  - Azure Cloud Shell needs the following to operate:
    1. A resource group
    2. A storage account
    3. A file share


+ **Azure Mobile App** is designed to work with **Azure App Service**:
  - Authentication
  - Data query
  - Offline data synchronization
      

- - -

2. Describe the functionality and usage of **Azure Advisor**
- **[Azure Advisor](https://learn.microsoft.com/en-us/azure/advisor/advisor-overview)** analyzes your account usage and makes recommendations for you based on its set rules
  + Reliability _(formerly called High Availability)_
  + Security
  + Performance
  + Cost
  + Operational Excellence

- - -
3. Describe the functionality and usage of **Azure Resource Manager** (ARM) templates
+ These are files written in JavaScript Object Notation (JSON) and defines infrastructure and configuration for Azure resources.
  + Declarative syntax
  + Deployment
    - Using Azure Pipelines (CI/CD)
    - From GitHub
    - Using PowerShell and the Azure CLI
    - Resource Manager ARM REST API
    - Azure Portal


- - -


4. Describe the functionality and usage of **Azure Monitor**, including **Log Analytics**, **Azure Monitor alerts**, and **Application Insights**
+ **[Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/overview)**: for collecting, analyzing, and acting on the availability and performance of your applications and services
  - **Metrics** and **Logs** are the 2 main diagnostic data
    - Identify your issues with the help of these diagnostic data
  - Create **alerts** as well in Azure based on the metrics and logs
  - A _Resource blade_ called **Service Health** allows you to monitor the health of deployed resources (VMs, Apps, Containers) and generate alerts based on health
  - **[Log Analytics workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-workspace-overview)** - log data from Azure Monitor and other Azure services
  - **Application Insights** is an extension of Azure Monitor and provides Application Performance Monitoring

      
- - -

5. Describe the functionality and usage of **Azure Service Health**
+ **[Azure Service Health](https://learn.microsoft.com/en-us/azure/service-health/overview)** keeps you informed about the health of your cloud resources:
    1. Azure status
    2. Service health
    3. Resource health
