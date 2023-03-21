<div align="center">

# 🛡️ [Microsoft MS-500](ms-500-index.md): Microsoft 365 Security Administration
### 🏠 [HOME](README.md)
### ✏️ Go through the [Implement and manage identity and access](https://learn.microsoft.com/en-us/training/paths/implement-manage-identity-access/) learning path

[<<<](ms-500-part4.md) | [>>>](ms-500-part2.md)
      
</div>

- - -

## 🧑👨‍ [Create, configure, and manage identities](https://learn.microsoft.com/en-us/training/modules/create-configure-manage-identities/) 🧑‍👩


| Azure Active Directory                        | Local Active Directory      |
|-----------------------------------------------|-----------------------------|
| Multi-tenant                                  | Single-tenant               |
| Perimeter-free                                | Perimeter-based             |
| Flat structure                                | X.500 structure             |
| DNS based domains                             | DNS for objects             |
| MS Graph API for queries                      | LDAP for queries            |
| SAML, OAuth, WS-Federation for authentication | Kerberos for authentication |
| Administrative Units                          | OUs & Group Policy          |



#### Types of AD users:
1. ☁️ Cloud identities
2. 🗂️ Directory-synchronized identities
3. 👺 Guest users


| Azure AD Components |
|---------------------|
| Tenant              |
| Domains             |
| Users               |
| Groups              |
| Apps                |
| Devices             |


      
### Create, configure, and manage groups

#### Types of AD Groups:
1. Security groups
2. Microsoft 365 groups

#### Group Membership Types:
1. **Assigned** 
    - Members are added and maintained manually
2. **[Dynamic](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/groups-dynamic-membership)**
    - Members are added based on rules

+ After you delete a user, the account remains in a suspended state for **30 days**
   + The account and it's properties can be restored
     
   
### Configure and manage device registration
+ MDM like Intune

      
### Create custom security attributes and assign to Azure AD objects

- - -


## ✨ [Explore Identity Synchronization](https://learn.microsoft.com/en-us/training/modules/introduction-to-identity-synchronization/)

### Types of Authentication in Microsoft 365:
1. **Cloud-only**
2. **Directory synchronization with Pass-Through authentication** (PTA)
3. **Single Sign-On** (SSO) **with AD FS**


- - -

## 🤖 [Implement and manage hybrid identity](https://learn.microsoft.com/en-us/training/modules/implement-manage-hybrid-identity/)

### 🌉 Plan, design, and implement Azure Active Directory Connect
+ **Azure AD Connect** bridges an organizations on-premises Active Directory with your cloud-based Azure Active Directory
    - If you're installing **Azure AD Connect** for the first time, [choose the custom installation path](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-install-custom)

1. **Synchronization**

```ps1
Import-Module ADSync
Get-ADSyncScheduler
Start-ADSyncSyncCycle -PolicyType Delta
# Run the following command to force a complete sync but note that the length of sync time would be greatly increased
Start-ADSyncSyncCycle -PolicyType Initial
````

      
      
2. **Password hash synchronization**
[![Enable password hash synchronization](https://learn.microsoft.com/en-us/training/wwl-sci/implement-manage-hybrid-identity/media/single-sign-on-fd559a4b.png)](https://learn.microsoft.com/)
+ When you install **Azure AD Connect** by using the `Express Settings` option, **Password Hash Synchronization** is automatically enabled

3. **Pass-through authentication**
+ Validates passwords directly against on-premises **Active Directory**
+ Sign in to both on-premises and cloud-based apps using the same password
+ A Pass-through authentication agent is installed on the same server as Azure AD Connect and the feature is enabled on your tenant


4. **Federation integration**
[![Azure AD Connect to connect to an AD FS farm](https://learn.microsoft.com/en-us/training/wwl-sci/implement-manage-hybrid-identity/media/sc300-federation-setup-dialog-f995542d.png)](https://learn.microsoft.com/)
+ Azure AD hands off the authentication process to a separate trusted authentication system such as **Active Directory Federation Services** (AD FS)
+ Specify the servers where you want to install AD FS
+ Specify the Web Application Proxy servers
    -  The **Web Application Proxy server** is deployed in your perimeter extranet network and supports external authentication requests

5. **Health monitoring**
+ `InvalidSoftMatch` error
   + 2 objects with different SourceAnchor `immutableId` have the same value for the `ProxyAddresses` and/or `UserPrincipalName` attributes
   + Generate a report by [Azure AD Connect Health](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-health-sync) for sync

### Azure AD Connect design concepts
#### `sourceAnchor`
+ The `sourceAnchor` attribute, also called `immutableId`, is defined as an attribute immutable during the lifetime of an object
+ Uniquely identifies an object as being the same object on-premises and in Azure AD
#### `objectGuid`
+ The attribute `objectGuid` is used for a single forest on-premises
+ Used to express settings in **Azure AD Connect**

### [Azure AD Connect: Enabling device writeback](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-device-writeback)
1. Install Azure AD Connect
2. Enable device writeback in Azure AD Connect
3. Verify Devices are synchronized to Active Directory
4. Enable Conditional Access
+ If you reset a password in Azure AD of a synced user, the password will be overwritten
+ If you join a computer to Azure AD, an object will be provisioned in the `RegisteredDevices` container
      
      
#### Azure AD sign-in
+ Azure AD uses `userPrincipalName` (UPN) to authenticate the user


| Azure AD Connect provisioning engine             |
|--------------------------------------------------|
| SQL Database on SSD                              |
| (< import) **Active Directory forest** (export >)|
| Connector Space (CS)                             |
| Metaverse (MV)                                   |
| Connector Space (CS)                             |
| (< import) **Azure AD** (export >)               |



### 🚑 Implement Azure Active Directory Connect Health
[![Verify agent was installed](https://learn.microsoft.com/en-us/training/wwl-sci/implement-manage-hybrid-identity/media/install-5-01ef9e2e.png)](https://learn.microsoft.com/)
+ **Azure AD Premium**
+ **Global Administrator** in Azure AD
+ The Azure AD Connect Health agent is installed on each targeted server
+ The Azure service endpoints have outbound connectivity
+ Outbound connectivity is based on IP addresses
+ TLS inspection for outbound traffic is filtered or disabled
+ Firewall ports on the server are running the agent
+ The agent requires the following firewall ports to be open so that it can communicate with the Azure AD Connect Health service endpoints:
    + TCP port 443
    + TCP port 5671 _(the latest version of the agent doesn't require port 5671, ppgrade to the latest version so that only port 443 is required)_
+ PowerShell version 4.0 or newer is installed
+ FIPS (Federal Information Processing Standard) is disabled
 
#### [How to troubleshoot an AD Connect Instance](https://support.pingidentity.com/s/article/PingOne-How-to-troubleshoot-an-AD-Connect-Instance)
+ `Event Viewer` in Administrative Tools > `Windows Logs` > `Application`
+ `https://{insert host name or IP address of AD Connect Server}/ADConnect/config.aspx`

- - -

## 👺 [Implement and manage external identities](https://learn.microsoft.com/en-us/training/modules/implement-manage-external-identities/)
[![Manage external collaboration](https://learn.microsoft.com/en-us/training/wwl-sci/implement-manage-external-identities/media/external-user-state-diagram.png)](https://learn.microsoft.com/)
+ **B2B collaboration** is a capability of Azure AD External Identities that lets you collaborate with users and partners outside of your organization.


- - -

## 👨‍👩‍👧 [Manage secure user access in Microsoft 365](https://learn.microsoft.com/en-us/training/modules/manage-secure-user-access-microsoft-365/)
### Enable multifactor authentication
+ Something the user knows (Password)
+ Something the user owns (Device)
+ Something the user is (Biometrics)

### Implement **Azure AD Smart Lockout**
+ Edit the group policy that includes the organization's account lockout policy
    - Browse to Group Policy Management tool > Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy
+ **Azure Active Directory** > Authentication methods > Password protection

- - -

## 👨‍💻 [Manage user authentication](https://learn.microsoft.com/en-us/training/modules/manage-user-authentication/)
### Passwordless authentication methods
1. Windows Hello
2. FIDO2 security keys
3. Microsoft Authenticator
4. SMS
5. Certificate-based authrentication
6. Temporary Access Pass

### Enable FIDO2 security key method
+ `Azure Active Directory` > `Security` > `Authentication methods` > `Authentication method policy`
+ Under the method **FIDO2 Security Key**, choose the following options:
    - `Enable` - Yes or No
    - `Target` - All users or Select users

- - -

## 🔒 [Plan, implement, and administer Conditional Access](https://learn.microsoft.com/en-us/training/modules/plan-implement-administer-conditional-access/)
+ Azure AD Conditional Access (CA) analyzes signals such as user, device, and location, to automate decisions and enforce organizational access policies for resource

### Block access by location with Azure AD Conditional Access
1. A subscription to **Azure Active Directory Premium**
2. A federated **Azure Active Directory tenant**

### Named locations
+ `Azure Active Directory` > `Security` > `Conditional Access` > `Named locations`

### [Troubleshooting sign-in problems with Conditional Access](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/troubleshoot-conditional-access)
+ `Azure Active Directory` > `Sign-ins`

### [Conditional access for VPN connectivity using Azure AD](https://learn.microsoft.com/en-us/Windows-server/remote//remote-access/how-to-aovpn-conditional-access)
+ From the Azure Active Directory Admin center, create a new certificate
+ An EAP-TLS client cannot connect unless the NPS (Network Policy Server i.e. RADIUS) server completes a revocation check of the certificate chain
   + Add the reg keys

- - -

## 🕵 [Plan and implement privileged access](https://learn.microsoft.com/en-us/training/modules/plan-implement-privileged-access/)


- - -


## 😎 [Plan and implement entitlement management](https://learn.microsoft.com/en-us/training/modules/plan-implement-entitlement-management/)
+ Privileged identity management (PIM) is a service in Azure AD for managing access to privileged resources
   + Time-based role activation
   + Approval-based role activation
1. Open `Azure AD Privileged Identity Management`


> To use PIM, you need EMS E5 or Azure AD Premium P2      

- - -

## 👀 [Manage Azure AD Identity Protection](https://learn.microsoft.com/en-us/training/modules/manage-azure-active-directory-identity-protection/)

| Risk detection type                | Description                                                                                                 |
|------------------------------------|-------------------------------------------------------------------------------------------------------------|
| Anonymous IP address               | Sign in from an anonymous IP address (for example: Tor browser, anonymizer VPNs)                            |
| Atypical travel                    | Sign in from an atypical location based on the user's recent sign ins                                       |
| Malware-linked IP address          | Sign in from a malware-linked IP address                                                                    |
| Unfamiliar sign in properties      | Sign in with properties we've not seen recently for the given user                                          |
| Leaked credentials                 | Indicates that the user's valid credentials have been leaked                                                |
| Password spray                     | Indicates that multiple usernames are being attacked using common passwords in a unified brute-force manner |
| Azure AD threat intelligence       | Microsoft's internal and external threat intelligence sources have identified a known attack pattern        |
| New country                        | This detection is discovered by Microsoft Defender for Cloud Apps (MDCA)                                    |
| Activity from anonymous IP address | This detection is discovered by MDCA                                                                        |


### Implement and manage user risk policy
[![Sign-in risk policy](https://learn.microsoft.com/en-us/training/wwl-sci/manage-azure-active-directory-identity-protection/media/identity-protection-security-overview.png)](https://learn.microsoft.com/)
+ [Configure and enable risk policies](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies)
1. Sign-in risk policy
   + Require a secure password change when user risk level is **High**
2. User risk policy
   + Require Azure AD MFA when sign-in risk level is **Medium** or **High**
      
### Exercise enable sign-in risk policy
[![User risk policy](https://learn.microsoft.com/en-us/training/wwl-sci/manage-azure-active-directory-identity-protection/media/browse-identity-protection.png)](https://learn.microsoft.com/)
+ Sign in to the [Azure portal](https://portal.azure.com/) using a **Global administrator account**
    + On the **Azure Active Directory** blade > Manage > select Security
    + On the **Security** blade, in the left navigation, select **Identity protection**
    + In the **Identity protection blade**, in the left navigation, select **User risk policy**



- - -
      
<div align="center">

[<<<](ms-500-part4.md) | [>>>](ms-500-part2.md)
      
</div>
