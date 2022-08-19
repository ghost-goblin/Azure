# [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals

## 🧑‍🤝‍🧑 Describe identity, governance, privacy, and compliance features

### Describe core Azure identity services
1. Explain the difference between **authentication** and **authorization**

2. Define **Azure Active Directory**
+ Microsoft's multi-tenant cloud-based directory and identity management service
+ Can be intergrated with an existing Windows Server Active Directory
+ Uses HTTPS queries instead of LDAP
+ Has a flat structure i.e. no GPOs / OUs
#### Azure AD User Types:
+ Cloud Identities
  - Local Azure AD
  - External Azure AD
+ Hybrid Identities
  - Directory-synchronized
+ Guest Identities
  - Azure AD B2B Collaboration
  - External Identities


## Implement Conditional Access policies, including multifactor authentication
##### Conditional Access Policies (if [something] => do [something])
##### Conditions
  - Users & Groups
  - Cloud Apps
  - Sign-in Risk
  - Device Platform & State
  - Location
  - Client Apps
##### Controls
  - MFA
  - Compliant Device
  - Approved Client App
  - Terms of Use
  - Custom & Session Controls
#### Managed Identities
##### Credentials in Code
+ Keeping service credentials in application configuartion is not secure
+ Credentials can get checked into source control or the configuration file can get compromised
+ **Azure Key Vault** is more secure but the code still needs to use Azure Active Directory credentials to login to Key Vault
+ Issue with many Azure services such as Azure SQL Database, Storage Account, Key Vault, etc.

> Our goal is to remove Azure service credentials from code without breaking the functionality

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


## Implement Azure AD Identity Protection
####  Azure AD Security Options
1. Self-Service Password Reset (SSPR)
+ Reduces support desk password change issues
+ Azure AD Premium P1 license required
+ Direct users to Registration URL: [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup)
+ Enable with Azure portal
+ Password writeback (Azure AD Premium P1 License) _(In order for Azure AD Connect to write the cloud based password change back to the local Acrive Directory)_


# 🛠️ Manage Applicaion Access
+ Azure AD IDaaS (Identity as a Service)
+ Application types
  - Third-party or internal
  - Pre-integrated or proxied
+ Automated user provisioning and access
  - SCIM 2.0 (provides a way for an application to talk to Azure AD)
  - Available on select SaaS apps




3. Describe the functionality and usage of **Azure Active Directory**
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
- - -

+ Manage external identities by using Azure AD
  + Azure AD Domain Services Intergration
    + Azure AD Hybrid Join
      + Azure AD Connect
      + Access to external URLs
      + Configure SCP (Service Connection Point) internally
      + Configure Active Directory Federation Service (ADFS) if required
+ 1. **Password Hash Synchronization** (PHS)
  - TCP 443 traffic (no VPN)
  - Hash of a hash passwords in the cloud
  - If channel fails, sign-in works
+ 2. **Pass-through Authentication** (PTA)
  - Does not store any password hashes
  - Password validation requests are sent to Windows Server Active Directory via pass-through authentication
  - Need one or more (3 is recommended) **lightweight agents** installed on existing servers
  - Agents have acces to on-premises Active Directory Domain Services
  - They need outbound access to the Internet and access to your Domain Controllers
  - Authenticating the user account locally
  - If channel fails, sign-in fails


+ Manage Administrative Units
  + Azure AD user and group container analogous to organizational units (OU) in local Active Directory
  + Locally organise your Azure AD users
  + Delegate administrative permissions

+ 🔐 Manage secure access by using Azure AD
    + Configure Azure AD Privileged Identity Management (PIM)
  + Monitor privleged acess for Azure AD **Privileged Identity Management** (PIM)
  + Configure access reviews
  + Activate and configure PIM - to delegate access to PIM, a **Global Administrator** can assign other users to the Privileged Administrator Role
  + Implemention conditional access policies _including_ Multi-Factor Autentication (MFA)
  + Configure Azure AD Identity Protection
  + Microsoft recommends ZERO permanently active assignments
  + Know who can manage assignments for other admins in PIM: 
     + Azure AD roles: Only **Privileged Role Administrators** and **Global Administrator**
     + Azure resource roles: Only **subscription admin**, **resource Owner**, **resource User Access Administrators**


+ Create and manage a managed identity for Azure resources
  + Managed identity types are **system assigned** (lowest effort on tems of lifecycle management) and **user assigned** (can be shared across multiple resources)
+ Managed Service Identities for Azure Services
  + A service of AAD (Azure Active Directory)
  + Provides Azure services with an automatically managed idenntity. You can use this identity to authenticate to any service that supports Azure AD authentication, without any credentials in your code
  + Provides **authentication** NOT authorizaton
  + The new name for the service formerly known as **Managed Service Identity** (MSI)
+ Types of Managed Identities
  + 1. **System-Assigned**
    + Enable directly on an Azure service instance
    + One per each Azure service instance
    + Gets cleaned up if Azure services instance is deleted
    + Widely supported by Azure resources
  + 2. **User-Assigned**
    + Created as standalone Azure resource
    + Can be assigned to one or more Azure service instances
    + Lifecycle is seperate from the lifecycle of Azure service to which it's assigned
    + Might be in preview for some resources

+ Manage Azure AD groups
  + Security
  + Microsoft 365
  + Owners
  + Assigned Membership
  + Dynamic Membership _(Azure AD populates the group based on the properties of a user account)_
  + Group-Assigned Roles & Licenses

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
+ Creating & Managing Groups with PowerShell 

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

4. Describe the functionality and usage of **Conditional Access**, **Multi-Factor Authentication** (MFA), and **Single Sign-On** (SSO)
+ Integrate single sign-on (SSO) and identity providers for authentication
  + The **synchronized identity** model is the most common (SSO)
  + Azure AD Connect and **password writeback** facilitate this model
  + Password writeback is required for **AAD self-service password reset**
  + **Pass Through Authentications** (PTA) forwards request to on-prem AD (log-on hours)
  + Two types of auth for service pricipals: **secret** or **certificate**
+ Multi-Factor Authentication
  + Azure hosted MFA Service
  + Global Administrators get Azure MFA for free
  + Registration URL Endpoint: [https://aka.ms/mfasetup](https://aka.ms/mfasetup)




# 🔑 Manage Access Control
## Configure Azure role permissions for management groups, subscriptions, resource groups, and resources

#### Authorization to Data
+ RBAC in Azure AD
+ Srorage Account Keys
+ Shared Access Signatures

### Describe Azure governance features
1. Describe the functionality and usage of **Role-Based Access Control** (RBAC)
2. Describe the functionality and usage of **resource locks**
3. Describe the functionality and usage of **tags**
4. Describe the functionality and usage of **Azure Policy**
5. Describe the functionality and usage of **Azure Blueprints**
6. Describe the **Cloud Adoption Framework** for Azure

### Describe privacy and compliance resources
1. Describe the Microsoft core tenets of **Security**, **Privacy**, and **Compliance**
2. Describe the purpose of the **Microsoft Privacy Statement**, **Online Services Terms** (OST) and **Data Protection Amendment** (DPA)
3. Describe the purpose of the **Trust Center**
4. Describe the purpose of the **Azure compliance documentation**
5. Describe the purpose of **Azure Sovereign Regions** (Azure Government cloud services and Azure China cloud services)
