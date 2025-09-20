### Networking in Azure

#### Azure Virtual Network (VNet)
- Your **own private, isolated network** in Azure (like a corporate LAN in the cloud).
- Network traffic within a VNet is **isolated** from other VNets and the internet.

#### Key Points
- **Security:** Protects resources and communication from external users.
- **Region-bound:** Each VNet belongs to a **specific Azure region**.
- **Control Traffic:** You control inbound and outbound traffic to/from the VNet.
- **Resource Placement:** Best practice is to deploy **all Azure resources (VMs, DBs, storage)** inside a VNet.

### Subnets :
#### What Are Subnets?
  - **Subnets = subdivisions** inside a Virtual Network (VNet).
  - Used to group and isolate resources based on access needs.

#### Why Subnets Are Needed
- Different resources have different access requirements. Example: Load balancer (public), VMs & databases (private).
- Subnets allow you to **separate public-facing resources** from **private/internal resources**.


