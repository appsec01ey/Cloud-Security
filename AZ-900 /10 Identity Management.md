### Identity Management

#### What is Identity Management?
Identity management refers to the processes and technologies used to **identify, authenticate, and authorize users or entities** accessing resources in a cloud environment.  
It ensures that the **right individuals or applications have the right access to the right resources at the right time**.

#### Why Identity Management is Needed

#### 1. Diverse Resources
- Cloud resources: virtual machines, databases, storage, network services.
- Applications in the cloud: 
  - Internal (used by employees) 
  - External (used by customers or partners)

#### 2. Varied Identities
- **Human identities:** internal employees, external partners, customers.
- **Non-human identities:** applications, bots, or services that interact with resources automatically.

#### 3. Complex Access Needs
- Users may need to: Start/stop virtual servers, Access internal applications, Perform specific actions in cloud apps
- Applications may need programmatic access for automation.

#### Key Goals of Identity Management
1. **Identification**: Knowing who is accessing the system.  
2. **Authentication**: Verifying the identity of the user or application.  
3. **Authorization**: Controlling what actions can be performed on which resources.  
4. **Access Management**: Assigning and enforcing permissions consistently.  

---

### **Concepts**
1. **Authentication** – Verifies the user.  
2. **Authorization** – Grants access to resources.  
3. **Avoid localized identity management** – Centralized solutions are better.  
4. **Single Sign-On (SSO)** – Authenticate once, access multiple services efficiently.  

- Centralized identity management, supported by solutions like **Microsoft Entra ID**, simplifies authentication, authorization, and access control across an enterprise environment.

--- 

### Microsoft Entra ID

- Microsoft Entra ID is **Azure’s cloud-based identity and access management service**, formerly known as **Azure Active Directory (Azure AD)**.  
- It helps organizations **manage users, authenticate identities, and control access** to applications and resources in a centralized way.

#### **Key Features**

#### 1. **User and Identity Management**
- Create and manage users (internal employees, external partners, customers).  
- Manage non-human identities like applications, bots, or services.  
- Store and secure user credentials centrally.

#### 2. **Authentication**
- Verify that a user or application is **who they claim to be**.  
- Supports multiple authentication methods:
  - Passwords
  - Multi-factor authentication (MFA)
  - External identity providers (Google, Facebook, etc.)
  - Passwordless options (biometric, hardware keys)

#### 3. **Authorization and Access Control**
- Define **roles and permissions** for users and applications.  
- Control access to resources like:
  - Azure services (VMs, storage, databases)
  - Enterprise applications
  - SaaS apps (Salesforce, ServiceNow, etc.)
- Implement **conditional access policies** based on risk, location, device, or user role.

#### 4. **Single Sign-On (SSO)**
- Authenticate once and access **multiple applications and services** without repeated logins.  
- Reduces friction for users and improves security.

#### 5. **Security and Compliance**
- Centralized identity management reduces risk of credential misuse.  
- Supports:
  - Conditional access
  - Identity protection
  - Monitoring and auditing for compliance requirements

---

### Task : 
- Here we saw a basic overview of Microsoft Entra ID [ User, Groups, Roles and Administrators, External Identities(Invite external users (e.g., partners, vendors) to access your apps using Google, Facebook, or Microsoft accounts, with controlled access and conditions.) etc.

---

### RBAC 

- RBAC is a key part of **authorization** in Azure. It lets you **assign permissions based on roles**, ensuring that users or applications have the right access to the right resources.
- Three Parts of a Role Assignment
  - **Who** – The principal: User / Group / Service principal (application) / Managed identity  
  - **Role** – The permissions: Built-in roles (e.g., Owner, Contributor, Reader) / Custom roles  
  - **Scope** – Where the role applies: Management group / Subscription / Resource group / Individual resource
- **Assign roles at the highest scope possible** (preferably at the management group level).
  - This ensures: **Centralized access management** , **Simplified permissions** , **Inheritance** of permissions down to subscriptions, resource groups, and resources.

---

### Microsoft Entra Connect (Hybrid Identity)

- When organizations use **Active Directory (AD) on-premises** and **Microsoft Entra ID in Azure**, they often want a **unified identity** for their users across both environments.  
- **Microsoft Entra Connect** enables this by synchronizing on-premises AD with Microsoft Entra ID.

#### 1. What Microsoft Entra Connect Does

- **Synchronizes user identities** between on-premises Active Directory and Microsoft Entra ID (formerly Azure AD).
- **Includes passwords** as part of the synchronization.
- Ensures users have a **single identity** across on-premises and cloud environments.
- Provides **seamless integration** between on-premises and cloud directories.

---

### Microsoft Entra Domain Services 
- Resources  : https://youtu.be/ZqOaZ3Oeeko

---

### Conditional Access
- **Conditional Access** is a feature in Microsoft Entra ID (formerly Azure Active Directory) that enables you to control how users access your applications and resources.  
- It uses **signals** (such as user identity, location, device state, risk level, etc.) to decide **whether to allow, block, or challenge** an access request.
- Evaluates **conditions** whenever a user or application tries to access a resource. Based on those conditions, **grants**, **blocks**, or **requires additional steps** (like MFA).
- Enforces policies automatically in real time.

#### Key Signals Used in Conditional Access
- **User/Group**: Who is trying to access the resource.
- **Application**: Which app/resource is being accessed.
- **Location**: From where (IP address, country, etc.).
- **Device State**: Compliant or non-compliant device, managed or unmanaged.
- **Risk Level**: User risk or sign-in risk (from Microsoft’s Identity Protection).

#### Common Access Decisions
- **Allow Access**: If all conditions are met.
- **Block Access**: If the request violates policy.
- **Grant Access with Additional Requirements**:
  - Multi-factor authentication (MFA)
  - Require compliant device
  - Require app protection policies

--- 

### Passwordless Authentication:

- **Resources** : https://www.alifconsulting.com/post/password-less-authentication
