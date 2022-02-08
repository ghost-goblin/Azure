# Manage identity and access (30-35%)
## 🧑‍🤝‍🧑 Manage Identity and Access

### Azure Active Directory
+ Microsoft's multi-tenant cloud-based directory and identity management service
+ Can be intergrated with an existing Windows Server Active Directory
+ Uses HTTPS queries instead of LDAP
+ Has a flat structure i.e. no GPOs / OUs

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
