
- We talked about Entra ID
- Users : We created a user say User A
- Groups :

| Feature                          | **Security Group**                             | **Microsoft 365 Group**                     |
|---------------------------------|------------------------------------------------ |---------------------------------------------|
| **Main Use**                    | Grant permissions to resources                  | Enable collaboration (shared resources)     |
| **Email/Shared Mailbox**         | No                                             | Yes (auto-provisioned)                      |
| **Shared Workspace (Planner, SP)** | No                                           | Yes                                         |
| **License Requirement**          | None (just Azure AD)                           | Requires Microsoft 365 licensing for members|
| **Membership Types**             | Assigned or Dynamic user , Dynamic Device      | Assigned or Dynamic user , Dynamic Device   |
| **Integration**                  | Azure AD apps, RBAC, SharePoint permissions    | Microsoft 365 apps (Teams, Planner, Outlook)|


| Membership Type       | Applies To | How Members Are Added                                   | Typical Use Case                          |
|----------------------|------------|--------------------------------------------------------|-------------------------------------------|
| **Assigned**          | Users & Devices | Manually added/removed by an admin                     | Small static groups with manual control   |
| **Dynamic User**      | Users only | Automatically based on **user** attributes/rules        | All HR staff, all users in a location     |
| **Dynamic Device**    | Devices only | Automatically based on **device** attributes/rules      | All corporate devices, all Windows 11 PCs |


- We created a VM ; User A can't see the VM , Why ? Permissions
- Permissions : RBAC
- RBAC :
  - It controls **who** can do **what** on **which resources**.
  - **Who** = Users, groups, service principals, or managed identities.
  - **What** = Actions they can perform (read, write, delete, manage).
  - **Which resources** = Scope of access (management group, subscription, resource group, or specific resource).

  | Role                        | What It Does                                                              |
|-----------------------------|---------------------------------------------------------------------------|
| **Owner**                   | Full access to everything, including managing access                      |
| **Contributor**             | Create & manage resources but **cannot** grant access                     |
| **Reader**                  | View resources only                                                       |
| **User Access Administrator** | Manage who has access to what (but not manage the resources themselves)  |

  - Roles can be assigned at management group > sub > resource grp > resources
