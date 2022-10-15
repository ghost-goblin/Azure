<div align="center">
      
# 🧱 [Microsoft AZ-900](az-900-index.md): Microsoft Azure Fundamentals
      
[<<<](az-900-part4.md) | [>>>](az-900-part6.md)
      
</div>

## 🧑‍🤝‍🧑 Describe identity, governance, privacy, and compliance features

### Describe core Azure identity services

1. Explain the difference between **authentication** and **authorization**
+ **Authentication** is the process of proving that you are who you say you are
+ **Authorization** is the act of granting an authenticated party permission to do something

- - -
2. Define **Azure Active Directory**
+ Multi-tenant cloud service
+ Identity and Access Management Services
+ Control access to your **apps** and your **resources**
+ Can be used to require multi-factor authentication when accessing important organizational resources
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

- - -

3. Describe the functionality and usage of **Azure Active Directory**

+ Manage external identities by using Azure AD
  + Azure AD Domain Services Intergration
    + Azure AD Hybrid Join
      + **Azure AD Connect**
      + Access to external URLs
      + Configure SCP (Service Connection Point) internally
      + Configure Active Directory Federation Service (ADFS) if required

+ Manage **Administrative Units**
  + Azure AD user and group container analogous to organizational units (OU) in local Active Directory
  + Locally organise your Azure AD users
  + Delegate administrative permissions

+ Manage secure access by using Azure AD
  1. **Password Hash Synchronization** (PHS)
    - TCP 443 traffic (no VPN)
    - Hash of a hash passwords in the cloud
    - If channel fails, sign-in works
  2. **Pass-through Authentication** (PTA)
    - Does not store any password hashes
    - Password validation requests are sent to Windows Server Active Directory via pass-through authentication
    - Need one or more (3 is recommended) **lightweight agents** installed on existing servers
    - Agents have acces to on-premises Active Directory Domain Services
    - They need outbound access to the Internet and access to your Domain Controllers
    - Authenticating the user account locally
    - If channel fails, sign-in fails
  + Implemention conditional access policies _including_ Multi-Factor Autentication (MFA)
  + Enable [passwordless authentication](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-authentication-passwordless):
    - Windows Hello for Business (Biometric)
    - Microsoft Authenticator - _generate an OATH verification code_
    - FIDO2 security keys
  + Configure & monitor privleged access for Azure AD **[Privileged Identity Management](https://learn.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-configure)** (PIM):
    + Who can manage assignments for other admins in PIM: 
      + Azure AD roles: Only **Privileged Role Administrators** and **Global Administrator**
      + Azure resource roles: Only **subscription admin**, **resource Owner**, **resource User Access Administrators**
    - Activate and configure PIM
      - with PIM, use MFA to activate any role for users
  + **Microsoft Defender for Identity** _(formerly Azure Advanced Threat Protection ATP)_
    - Monitor users, entity behaviour and activities
  + Configure access reviews
  + Configure [Azure AD Identity Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection):
    - Anonymous IP address use
    - Atypical travel
    - Malware linked IP address
    - Unfamiliar sign-in properties
    - Leaked credentials
    - Password spray
  + Microsoft recommends ZERO permanently active assignments

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

+ Manage **Azure AD groups**
  + Security
  + Microsoft 365
  + Owners
  + Assigned Membership
  + Dynamic Membership _(Azure AD populates the group based on the properties of a user account)_
  + Group-Assigned Roles & Licenses

- - -

4. Describe the functionality and usage of **Conditional Access**, **Multi-Factor Authentication** (MFA), and **Single Sign-On** (SSO)
+ Conditional Access Policies (if [something] => do [something])
 + _Conditions:_
    - **Users & Groups**
    - **Cloud Apps**
    - **Sign-in Risk**
    - **Device Platform & State**
    - **Location**
    - **Client Apps**
+ _Controls:_
    - **MFA**
    - **Compliant Device**
    - **Approved Client App**
    - **Terms of Use**
    - **Custom & Session Controls**
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

+ Authorization to Data
  + RBAC in Azure AD
  + Storage Account Keys
  + Shared Access Signatures


+ Managed Identities
  + _Credentials in Code_:
    + Keeping service credentials in application configuartion is not secure
    + Credentials can get checked into source control or the configuration file can get compromised
    + **Azure Key Vault** is more secure but the code still needs to use Azure Active Directory credentials to login to Key Vault
    + Issue with many Azure services such as Azure SQL Database, Storage Account, Key Vault, etc.
      - Our goal is to remove Azure service credentials from code without breaking the functionality

+ Configure Managed Service Identities (MSI) for Microsoft Azure Resources
+ STEP 1
    + Create Identity
      + Create system-assigned or user-assigned identity for your client service
+ STEP 2
    + Give Permission
      + In the target Azure service, assign permissions to the client identity

+ Azure Services that support Managed Identities for Azure Resources
  + Azure Virtual Machines
  + Azure VM Scale Sets
  + Azure App Service, Functions, Logic Apps
  + Azure Blueprints
  + Azure Container Instances
  + Azure API Management

+ Azure Services that support Azure AD Authentication
  + **Azure Key Vault** - _cloud service for securely storing and accessing secrets_
  + Azure SQL
  + **[Azure Service Bus](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview)**
    - Data is transferred between different applications and services using **messages**
  + **Azure Storage** (Blobs & Queues)
  + Azure Analysis Services


+ Implement Azure AD Identity Protection
  +  Azure AD Security Options
    + 1. Self-Service Password Reset (SSPR)
      + Reduces support desk password change issues
      + Azure AD Premium P1 license required
      + Direct users to Registration URL: [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup)
      + Enable with Azure portal
      + Password writeback (Azure AD Premium P1 License) _(In order for Azure AD Connect to write the cloud based password change back to the local Acrive Directory)_

+ Manage Applicaion Access
  + Azure AD IDaaS (Identity as a Service)
    + **[Azure AD B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/overview)** is used for the _authentication_ and _authorisation_ of end users
  + Application types
    - Third-party or internal
    - Pre-integrated or proxied
  + Automated user provisioning and access
    - SCIM 2.0 (provides a way for an application to talk to Azure AD)
    - Available on select SaaS apps

- - -

### Describe Azure governance features

1. Describe the functionality and usage of **Role-Based Access Control** (RBAC)
+ Principle of Least Privilege - user is given the minimum levels of access – or permissions – needed to perform their job functions
+ Security Principals - a security ID for applications or services
+ **[Roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles)**
  - **Owner** has full access to all resources and grant access
  - **Contributor** can create/manage all resource, cannot grant access
  - **Reader** can view existing resources
  - **User Access Administrator** lets you mange user access
+ **Scope**
  - Adding the _Owner_ role at the _management group scope_ allows users in group to manage everything within all subscriptions
  - Adding the _Reader_ role at the _subscription scope_ allows users in that group to view all resource groups and resources in that subscription
  - Assigning the _Contributor_ role to an app at the _resource group_ scope allows it to manage resources within that group

- - -

2. Describe the functionality and usage of **resource locks**
+ Locks an Azure subscription, resource group, or resource to protect them from accidental user deletions and modifications - _the lock overrides any user permissions_
- - -

3. Describe the functionality and usage of **tags**
+ Metadata elements with key-value pairs can be applied to Azure resources
+ **Resource Group** _tags_ are not inherited to resources within the group

- - -

4. Describe the functionality and usage of **Azure Policy**
+ [Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/overview) helps to enforce organizational standards and to assess compliance at-scale
+ Can add restrictions on storage account SKUs, virtual machine instance types, and rules relating to tagging of resources and groups
+ If a policy is applied to a non-compliant resource, it will remain as is, and will no longer be compliant

- - -

5. Describe the purpose of **[resource locks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json)**
+ Lock a subscription, resource group, or resource to protect them from accidental user deletions and modifications


- - -


6. Describe the functionality and usage of **Azure Blueprints**
+ [Azure Blueprints](https://learn.microsoft.com/en-us/azure/governance/blueprints/overview) enables cloud architects and central information technology groups to define a repeatable set of Azure resources that implements and adheres to an organization's standards, patterns, and requirements
+ **Azure Blueprint Artifacts** are something that can be used to build the blueprint
  1. ARM Templates
  2. Resource Groups
  3. Azure RBAC
  4. Azure policies

- - -

7. Describe the **[Cloud Adoption Framework](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/)** for Azure
+ [Cloud Adoption Framework](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview) enables cloud architects, IT professionals, and business decision makers to achieve their cloud adoption goals


- - -

### Describe privacy and compliance resources
1. Describe the Microsoft core tenets of **Security**, **Privacy**, and **Compliance**
+ _[Can you trust your cloud provider?](https://azure.microsoft.com/en-in/blog/trusted-cloud-security-privacy-compliance-resiliency-and-ip/)_
+ **[Service Trust Portal](https://learn.microsoft.com/en-us/microsoft-365/compliance/get-started-with-service-trust-portal?view=o365-worldwide)** - content, tools, and other resources about how Microsoft cloud services protect your data, and how you can manage cloud data security and compliance for your organization
- - -

2. Describe the purpose of the **Microsoft Privacy Statement**, **Online Services Terms** (OST) and **Data Protection Amendment** (DPA)
+ **Online Services Terms** (OST) is a legal agreement between Microsoft and the customer detailing the obligations by both parties with respect to the processing and security of customer data and personal data

+ The **Data Protection Addendum** (DPA) defines data processing and security terms for online services:
  + Compliance with laws
  + Disclosure of processed data
  + Data Security, which includes security practices and policies, data encryption, data access, customer responsibilities, and compliance with auditing
  + Data transfer, retention, and deletion

- - -

3. Describe the purpose of the **Trust Center**
+ **[Trust Center](https://www.microsoft.com/en-gb/trust-center/product-overview)** handles your data securely and in compliance with privacy and legal requirements

- - -

4. Describe the purpose of the **Azure Compliance Documentation**
+ **[Azure compliance documentation](https://learn.microsoft.com/en-us/azure/compliance/)** provides you with detailed documentation about legal and regulatory standards and compliance on Azure

- - -

5. Describe the purpose of **Azure Sovereign Regions** (Azure Government cloud services and Azure China cloud services)
+ [Azure Government](https://learn.microsoft.com/en-us/azure/azure-government/documentation-government-welcome) -  US federal, state, local, or tribal government entities 

   
