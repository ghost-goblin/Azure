# Manage identity and access (30-35%)
## 🧑‍🤝‍🧑 Manage Identity and Access

### Azure Active Directory
+ Microsoft's multi-tenant cloud-based directory and identity management service
+ Can be intergrated with an existing Windows Server Active Directory
+ Uses HTTPS queries instead of LDAP
+ Has a flat structure i.e. no GPOs / OUs

### Azure AD User Types
+ Cloud Identities
  - Local Azure AD
  - External Azure AD
+ Hybrid Identities
  - Directory-synchronized
+ Guest Identities
  - Azure AD B2B Collaboration
  - External Identities

### 🔑 Azure AD Security Options
1. Self-Service Password Reset (SSPR)
+ Reduces support desk password change issues
+ Azure AD Premium P1 license required
+ Direct users to Registration URL: [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup)
+ Enable with Azure portal
+ Password writeback (P1) _(In order for Azure AD Connect to write the cloud based password change back to the local Acrive Directory)_

2. Multi-Factor Authentication
+ Azure hosted MFA Service
+ Global Administrators get Azure MFA for free
+ Registration URL Endpoint: [https://aka.ms/mfasetup](https://aka.ms/mfasetup)

### Configure Azure Active Directoty Identities
+ The **synchronized identity** model is the most common (SSO)
+ Azure AD Connect and **password writeback** facilitate this model
+ Password writeback is required for **AAD self-service password reset**
+ **Pass Through Authentications** (PTA) forwards request to on-prem AD (log-on hours)
+ Two types of auth for service pricipals: **secret** or **certificate**
+ Managed identity types are **system assigned** (lowest effort on tems of lifecycle management) and **user assigned** (can be shared across multiple resources)

```ps1
Find-Module AzureAD
Install-Module AzureAD
Import-Module -Name AzureAD

### Get credentials to connect
$AzureADCredentials = Get-Credential -Message "Login to Azure AD"
### Connect to tenant
Connect-AzureAD -Credential $AzureADCredentials

Get-Command -Module AzureAD
```
### Authorization to Data
+ RBAC in Azure AD
+ Srorage Account Keys
+ Shared Access Signatures

```ps1
### Working with roles
Connect-AzureAD
Get-AzureADDirectoryRole
$CompanyAdminRole = Get-AzureADDirectoryRole | Where-Object {$_.DisplayName -eq "Comapany Administrator"}
Get-AzureADDirectoryRoleMember -ObjectId $CompanyAdminRole.ObjectId

### Get a list of all Roles
Get-AzureADDirectoryRoleTemplate
```
### Managing Users with PowerShell
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
### Creating & Managing Groups with PowerShell 
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

### Configure Secure Access using Azure AD
+ Monitor privleged acess for Azure AD **Privileged Identity Management** (PIM)
+ Configure access reviews
+ Activate and configure PIM - to delegate access to PIM, a Global Admin can assign other users to the Privileged Administrator Role
+ Implemention conditional access policies _including_ Multi-Factor Autentication (MFA)
+ Configure Azure AD Identity Protection
+ Microsoft recommends ZERO permanently active assignments
+ Know who can manage assignments for other admins in PIM: 
    + Azure AD roles: Only **Privileged Role Administrators** and **Global Administrator**
    + Azure resource roles: Only **subscription admin**, **resource Owner**, **resource User Access Administrators**

> For the exam, know how to configure Privileged Identity Management and the configuration options for PIM access reviews

+ Know how to configure Azure AD **Conditional Access**
+ Know what Identity Protection brings to Conditional Access (_sign-in risk_)
+ Know licencing required for AD Identity Protection

#### Azure AD Hybrid Join
+ Azure AD Connect
+ Access to external URLs
+ Configure SCP (Service Connection Point) internally
+ Configure Active Directory Federation Service (ADFS) if required

### Manage Applicaion Access
+ Azure AD IDaaS (Identity as a Service)
+ Application types
  - Third-party or internal
  - Pre-integrated or proxied
+ Automated user provisioning and access
  - SCIM 2.0 (provides a way for an application to talk to Azure AD)
  - Available on select SaaS apps

### Manage Access Control
#### Conditional Access Policies (if [something] => do [something])
#### Conditions
  - Users & Groups
  - Cloud Apps
  - Sign-in Risk
  - Device Platform & State
  - Location
  - Client Apps
#### Controls
  - MFA
  - Compliant Device
  - Approved Client App
  - Terms of Use
  - Custom & Session Controls

## 🛡️ Implement Platform Protection

## 🗡️ Manage Security Operations

## 🔒 Secure Data & Applications
### Configuring TLS/SSL Certificates
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

### Managed Identities
#### Credentials in Code
+ Keeping service credentials in application configuartion is not secure
+ Credentials can get checked into source control or the configuration file can get compromised
+ **Azure Key Vault** is more secure but the code still needs to use Azure Active Directory credentials to login to Key Vault
+ Issue with many Azure services such as Azure SQL Database, Storage Account, Key Vault, etc.

> Our goal is to remove Azure service credentials from code without breaking the functionality

#### Managed Service Identities for Azure Services
+ A service of AAD (Azure Active Directory)
+ Provides Azure services with an automatically managed idenntity. You can use this identity to authenticate to any service that supports Azure AD authentication, without any credentials in your code
+ Provides **authentication** NOT authorizaton
+ The new name for the service formerly known as **Managed Service Identity** (MSI)

### Types of Managed Identities
1. System-Assigned
+ Enable directly on an Azure service instance
+ One per each Azure service instanc
+ Gets cleaned up if Azure services instance is deleted
+ Widely supported by Azure resources

2. User-Assigned
+ Created as standalone Azure resource
+ Can be assigned to one or more Azure service instances
+ Lifecycle is seperate from the lifecycle of Azure service to which it's assigned
+ Might be in preview for some resources

### Configure Managed Service Identities (MSI) for Microsoft Azure Resources

#### STEP 1
##### Create Identity
Create system-assigned or user-assigned identity for your client service

#### STEP 2
##### Give Permission
In the target Azure service, assign permissions to the client identity

### Azure Services that support Managed Identities for Azure Resources
+ Azure Virtual Machines
+ Azure VM Scale Sets
+ Azure App Service, Functions, Logic Apps
+ Azure Blueprints
+ Azure Container Instances
+ Azure API Management

### Azure Services that support Azure AD Authentication
+ Azure Key Vault
+ Azure SQL
+ Azure Service Bus
+ Azure Storage (Blobs & Queues)
+ Azure Event Hubs
+ Azure Analysis Services
