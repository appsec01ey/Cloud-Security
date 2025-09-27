
- We talked about Entra ID
- Users
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
