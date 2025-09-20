### Networking in Azure

#### Azure Virtual Network (VNet)
- Your **own private, isolated network** in Azure (like a corporate LAN in the cloud).
- Network traffic within a VNet is **isolated** from other VNets and the internet.

#### Key Points
- **Security:** Protects resources and communication from external users.
- **Region-bound:** Each VNet belongs to a **specific Azure region**.
- **Control Traffic:** You control inbound and outbound traffic to/from the VNet.
- **Resource Placement:** Best practice is to deploy **all Azure resources (VMs, DBs, storage)** inside a VNet.
---
### Subnets :
#### What Are Subnets?
  - **Subnets = subdivisions** inside a Virtual Network (VNet).
  - Used to group and isolate resources based on access needs.

#### Why Subnets Are Needed
- Different resources have different access requirements. Example: Load balancer (public), VMs & databases (private).
- Subnets allow you to **separate public-facing resources** from **private/internal resources**.
---
### Creating a Virtual Network (VNet) and Assigning a VM

#### 1. Create a Virtual Network
- Go to **Azure Portal → Search “Virtual Networks” → Create**.
- Choose a **Resource Group** (e.g., `VirtualNetworkRG`).
- Name the VNet (e.g., `MyFirstVirtualNetwork`).
- **Address Space:** Default `10.0.0.0/16` (≈65,000 addresses).
- Each VNet belongs to **one Azure region**.

#### 2. Configure Subnets
- VNet can have multiple subnets:
  - **Private Subnet:** e.g., `10.0.0.0/24` (256 addresses).
  - **Public Subnet:** e.g., `10.0.1.0/24` (256 addresses).
- Subnets separate public-facing vs. internal resources.
- All resources inside the VNet (across subnets) can still communicate privately.

#### 3. Deploy a Virtual Machine into the VNet
- Go to **Virtual Machines → Create VM**.
- Choose the **same Resource Group and Region** as the VNet.
- In **Networking** tab:
  - Select the VNet (e.g., `MyFirstVirtualNetwork`).
  - Choose the appropriate **Subnet** (public or private).
- VM will be assigned to that subnet after creation.
---

### Azure Virtual Network – IPs & Peering

#### 1. Private & Public IP Addresses
- **Private IP**: Assigned automatically to every VM in a VNet (free).
- IP comes from the **subnet’s range** (e.g., 10.0.1.0/24).
- **Public IP**: Optional; needed for internet access; can be **Dynamic** or **Static** (paid).
- Best practice: Use private IPs for internal communication.

#### 2. VM Communication in a VNet
- All VMs in the same VNet can **communicate via private IP**, even across different subnets.
- Example: VM in Private Subnet ↔ VM in Public Subnet.

#### 3. VNet Peering
- **Connects two separate VNets** so resources can communicate privately.
- Works across:
  - **Same region** or **different regions**.
- Steps:
  1. Go to VNet → **Peerings → Add**.
  2. Give peering names on both VNets.
  3. Select the second VNet and allow traffic.
- After peering, VMs in both VNets can talk over **private IPs**.

#### DDOS protection 
- **Basic**: Always on, free, automatic. **Standard**: Paid, advanced protection, analytics + support.
- Enable/disable at the **Virtual Network level** in Azure Portal.
