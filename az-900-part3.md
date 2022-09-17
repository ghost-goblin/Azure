# [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

## 🔨 Describe core solutions and management tools on Azure 

### Describe core solutions available in Azure
1. Describe the benefits and usage of **Internet of Things** (IoT) **Hub**, **IoT Central**, and **Azure Sphere**
+ [Azure IoT Hub](https://azure.microsoft.com/en-gb/services/iot-hub/#overview) provides a cloud-hosted solution back-end to connect any device virtually
+ **Azure IoT Central** is a ready-made UX and API surface for connecting and managing devices at scale, delivering reliable data for business insights. It preassembles platform as a service (PaaS) offerings, bringing together each service beneath it for an easy-to-configure, comprehensive, and secure IoT offering
+ **Azure Sphere** is a secured IoT platform for building solutions that start in silicon and extend through the OS and the cloud. Securely connect, manage, and protect new and existing intelligent devices

- - -

2. Describe the benefits and usage of **Azure Synapse Analytics**, **HDInsight**, and **Azure Databricks**
+ Azure Synapse Analytics is a limitless analytics service that brings together data integration, enterprise data warehousing and big data analytics.
+ Azure HDInsight is a managed, full-spectrum, open-source analytics service in the cloud for enterprises. With HDInsight, you can use open-source frameworks such as Hadoop, Apache Spark, Apache Hive, LLAP, Apache Kafka, and more, in your Azure environment
+ Azure Databricks is a data analytics platform optimized for the Microsoft Azure cloud services platform. Azure Databricks offers three environments for developing data intensive applications: Databricks SQL, Databricks Data Science & Engineering, and Databricks Machine Learning

- - -

3. Describe the benefits and usage of **Azure Machine Learning**, **Cognitive Services** and **Azure Bot Service**
+ **Azure Cognitive Services** has an entire list of features that can be used to build **Artificial Intelligence** based applications
- - -

4. Describe the benefits and usage of serverless computing solutions that include **Azure Functions** and **Logic Apps**
+ Azure Functions uses code to perform an action whereas Azure Logic Apps use workflow triggered by an event
+ **[Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview)** is a cloud-based platform for creating and running automated workflows that integrate your apps, data, services, and systems

- - -

5. Describe the benefits and usage of **Azure DevOps**, **GitHub**, **GitHub Actions**, and **Azure DevTest Labs**
+ Azure DevOps is a collection of services that allow teams to share their code, track their work, and deploy and ship software:
    - Azure Boards
    - Azure Pipelines
    - Azure Repos
    - Azure Artifacts
    - Azure Test Plans
+ Azure DevTest Labs is a service for easily creating, using, and managing infrastructure-as-a-service (IaaS) virtual machines (VMs) and platform-as-a-service (PaaS) environments in labs

- - -

### Describe Azure management tools
1. Describe the functionality and usage of the **Azure Portal**, **Azure PowerShell**, **Azure CLI**, **Cloud Shell**, and **Azure Mobile App**
+ Managing Users with PowerShell
```ps1
Connect-AzureAD #sign in
$domain = "domain.onmicrosoft.com"
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
```
+ Creating & Managing Groups with PowerShell 

```ps1
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
```

```ps1
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
- - -

2. Describe the functionality and usage of **Azure Advisor**
- For optimising your costs

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
4. Describe the functionality and usage of **Azure Monitor**
- - -
5. Describe the functionality and usage of **Azure Service Health**
