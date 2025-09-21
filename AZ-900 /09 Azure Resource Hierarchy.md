### Azure Resource Hierarchy

<img width="685" height="629" alt="image" src="https://github.com/user-attachments/assets/fc328160-1d03-4fa8-b1c4-f72b5d378049" />


- Azure organizes everything in a hierarchy. Understanding this helps you manage access, policies, billing, and organization of resources effectively.

### 🟦 Tenant
- A **Tenant** represents a single instance of **Azure Active Directory (Azure AD)**.
- It is essentially your **organization’s identity and directory** in Microsoft’s cloud.
- All **users, groups, applications, and subscriptions** under your organization live inside this tenant.
- Think of the Tenant as the **top-level security and identity boundary**.

### 🟩 Management Groups
- **Purpose:** Help manage **access, policies, and compliance** across multiple subscriptions.
- Any **conditions or policies** applied to a management group automatically apply to:
  - All **subscriptions** under it,
  - All **resource groups** within those subscriptions,
  - And all **resources** inside those resource groups.
- You can build a **hierarchy of management groups** to reflect your org’s structure.

### 🟨 Subscriptions
- **Definition:** A logical boundary that links user accounts to the Azure resources they create.
- **Usage:**
  - Manage **costs, quotas, and access** per department, project, or environment (Dev, Test, Prod).
  - Each subscription has its own **billing, administrators, and limits**.
- **Limits:**
  - Subscriptions come with quotas (e.g., max vCPUs, number of VMs per region).
  - If you hit a hard limit, create a **new subscription**.
- **Flexibility:**
  - You can **move resources** between subscriptions.
  - You can **transfer subscription ownership** to another account.
  - **Subscriptions cannot be merged**, but they can be centrally managed via Management Groups.

### 🟦 Resource Groups
- **Definition:** A logical container where you deploy and manage related Azure resources.
- **Association:**
  - Each resource group belongs to **one subscription** at a time.
  - A **resource** can belong to **only one resource group**, but a resource group can hold many resources.
- **Region Flexibility:**
  - A resource group can host resources from **multiple regions**.
- **Management:**
  - Deleting a resource group deletes **all resources inside it**.
  - **Tags** on a resource group are **not inherited** by resources.
  - **Permissions/Roles** assigned at the resource group level **are inherited** by all resources.
- **Cost:**
  - Resource groups are **free** — you only pay for the resources inside.

### 🟧 Resources
- **Definition:** The individual services deployed in Azure.
- Examples: **Virtual Machines, Storage Accounts, SQL Databases, Key Vault, AKS clusters**, etc.
- Every resource must belong to **one resource group**.
- Resources inherit **policies and access settings** from their parent resource group.

---

