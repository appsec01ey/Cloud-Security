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

---

### Azure Firewall
- **Azure Firewall** is a **managed, cloud-based network security service**.
- It acts as a **stateful firewall** — if you allow certain traffic in one direction, return traffic is automatically allowed.
- It filters and controls **inbound, outbound, and internal (east-west)** traffic for Azure Virtual Networks.

#### Key Benefits
- **Centralized Control**  
  - One Azure Firewall instance can manage traffic for **multiple VNets** across **multiple subscriptions**.
  - Example: 10 VNets + 100 VMs managed via a single firewall.

- **Scalable & Managed**  
  - Microsoft handles availability, scaling, and updates.
  - No need to deploy or maintain firewall appliances.

- **Integrated Monitoring**  
  - Works with **Azure Monitor** to track logs, metrics, and alerts related to firewall activity.
  - Enables auditing and investigation of traffic patterns.

#### Difference Between Azure Firewall and Web Application Firewall (WAF)

| **Azure Firewall** | **Web Application Firewall (WAF)** |
|-------------------|-----------------------------------|
| Protects the entire **network/VNet**. | Protects specific **web apps** behind an App Gateway or Load Balancer. |
| Filters and allows/blocks **any type of traffic** based on rules. | Shields web apps from **application-layer attacks** (e.g., OWASP Top 10: SQL injection, cross-site scripting). |
| Can span **multiple VNets/subscriptions**. | Tied to one web app or gateway. |

---

### Network Security Groups (NSG) 
- **NSG** = An **internal firewall** for Azure Virtual Networks.
- Controls **inbound and outbound traffic** between Azure resources **inside** a VNet.
- Works at **subnet** or **network interface** level (VM NIC).

#### Key Features
- Configure **rules** to allow/deny traffic based on:
  - **Source / Destination IP address**
  - **Protocol** (TCP/UDP)
  - **Port numbers**
- Rules have **priorities**: lower number = higher priority.

#### Typical Use Cases
- Allow only **HTTP (80)** & **HTTPS (443)** to a web server VM.
- Allow **DB access only from app servers**, block from others.
- Restrict **outbound internet traffic** from VMs to specific IPs.

#### NSG vs Azure Firewall
| **Azure Firewall** | **NSG** |
|-------------------|---------|
| External firewall at VNet edge – stops traffic **before entering**. | Internal firewall inside VNet – controls traffic **between subnets/NICs**. |
| Centralized, stateful, can protect multiple VNets across subscriptions. | Attached at subnet/NIC level; granular control per resource. |
| Good for network-wide policies. | Good for VM-level or subnet-level policies. |

---

### Azure Private Link & Private Endpoint 
- **Azure Private Link**: Enables **private access** to Azure PaaS services (like Azure SQL Database, Azure Storage, Cosmos DB) over a **private IP** within your VNet.  
- **Private Endpoint**: A **network interface** with a private IP in your VNet used to connect securely to the Azure service via Private Link.  

#### Why We Need Them  
- By default, Azure PaaS services (SQL, Storage, Cosmos DB, etc.) have **public IPs**.  
- Communication between your VM/app and these services happens **over the Internet** if public endpoints are used.  
- For **security & compliance**, traffic should remain within Microsoft’s internal backbone network — no exposure to the public Internet.  

#### How It Works  
1. You have a **VM inside a VNet** running a web application.  
2. The app connects to an **Azure SQL Database (PaaS)**.  
3. By creating a **Private Endpoint** for the SQL Database:
   - The SQL Database gets a **private IP** inside your VNet.
   - Your VM communicates to SQL Database privately using that IP.
4. All traffic stays on the **Microsoft backbone**, isolated from the Internet.

#### Key Benefits  
- **Private, secure communication** between your resources and Azure PaaS services.  
- Eliminates exposure of data to the public Internet.  
- Works for multiple Azure services: Storage, Cosmos DB, SQL Database, etc.  
- Centralized management in the **Private Link Center** in Azure Portal.
  
#### Provider–Consumer Model  
- **Provider** = Azure managed service (e.g., Azure SQL Database).  
- **Consumer** = Your resource in a VNet (e.g., VM/web app).  
- **Private Link** = Service enabling private connectivity.  
- **Private Endpoint** = The private IP in your VNet that connects to the provider.

---
