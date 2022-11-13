<div align="center">

# 🛡️ [Microsoft MS-500](ms-500-index.md): Microsoft 365 Security Administration
### 🏠 [HOME](README.md)
### ✏️ Go through the [Implement and manage identity and access](https://learn.microsoft.com/en-us/training/paths/implement-manage-identity-access/) learning path

[<<<](ms-500-part4.md) | [>>>](ms-500-part2.md)
      
</div>

## 🧑‍ Create, configure, and manage identities


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
1. Cloud identities
2. Directory-synchronized identities
3. Guest users


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
2. **Dynamic**
    - Members are added based on rules

    
### Configure and manage device registration

      
- - -


## ✨ Explore Identity Synchronization

### Types of Authentication in Microsoft 365:
1. **Cloud-only**
2. **Directory synchronization with Pass-Through authentication** (PTA)
3. **Single Sign-On** (SSO) **with AD FS**


- - -

## 🤖 Implement and manage hybrid identity

### 🌉 Plan, design, and implement Azure Active Directory Connect
+ **Azure AD Connect** bridges an organizations on-premises Active Directory with your cloud-based Azure Active Directory
    - **Synchronization**
    - **Password hash synchronization**
    - **Pass-through authentication**
    - **Federation integration**
      - Azure AD hands off the authentication process to a separate trusted authentication system such as **Active Directory Federation Services** (AD FS)
    - **Health monitoring**

### Azure AD Connect design concepts
#### `sourceAnchor`
+ The `sourceAnchor` attribute, also called `immutableId`, is defined as an attribute immutable during the lifetime of an object
+ Uniquely identifies an object as being the same object on-premises and in Azure AD
#### `objectGuid`
+ The attribute `objectGuid` is used for a single forest on-premises
+ Used to express settings in **Azure AD Connect**


#### Azure AD sign-in
+ Azure AD uses `userPrincipalName` (UPN) to authenticate the user
