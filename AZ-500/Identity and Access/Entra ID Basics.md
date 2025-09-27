
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

| Assignment State  | Description                                               | Example                                                   |
|------------------|-----------------------------------------------------------|-----------------------------------------------------------|
| **Eligible**      | User can request/activate the role but doesn't have it yet | Bob is eligible for “Owner” role but must activate it first|
| **Active**        | User currently has the role and can use it                | Alice activated “Contributor” for 4 hours                 |
| **Permanent Active** | Role is always on for the user with no expiry           | Global admin with constant access                        |
| **Time-bound Active** | Role is on for a defined duration, then expires        | Security engineer gets “Privileged Role Admin” for 2 hours|
