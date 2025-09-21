### Azure Resource Hierarchy

<img width="685" height="629" alt="image" src="https://github.com/user-attachments/assets/fc328160-1d03-4fa8-b1c4-f72b5d378049" />

- **Management Groups:** Management groups help you manage access, policies, and compliance across multiple subscriptions. Any conditions applied to a management group automatically get inherited by all subscriptions within it, ensuring consistent governance.
  
- **Subscriptions:** Subscriptions act as a logical boundary that links user accounts to the resources they create. Each subscription comes with limits or quotas on resource usage. Organizations use subscriptions to manage costs, resources, and workloads for different teams, projects, or environments (e.g., Dev, Test, Prod).
  
- **Resource Groups:** A resource group is a logical container where you deploy and manage Azure resources like virtual machines, web apps, databases, and storage accounts. It helps in organizing related resources and applying access control and policies at a group level.
  
- **Resources:** Resources are the individual services deployed in Azure, such as virtual machines, storage accounts, and SQL databases. Every resource must belong to a resource group, inheriting its policies and access settings.
