### Hybrid Cloud:

| Model        | Hosted Where?         | Cost Model              | Ownership & Control               | Example Use Case                                 |
|--------------|---------------------- |------------------------- |----------------------------------- |--------------------------------------------------|
| **Public**   | Cloud provider        | Operational (pay-as-you-go) | Cloud provider                | Startup running all workloads on Azure           |
| **Private**  | Own data center       | Capital + operational   | Organization                      | Government hosting sensitive apps internally     |
| **Hybrid**   | Mix of both           | Mixed                   | Shared responsibility             | On-prem app talking to Azure Cosmos DB           |

---
### 1. Azure VPN and Express Route

#### 1. Azure VPN :
- **Encrypted connection** from on-premises to Azure **over the internet**.
- Suitable for secure connectivity but uses public internet.
- Two types:
  - **Point-to-Site (P2S)** VPN:
    - From a **single computer** to Azure.
    - Good for developers or admins needing individual access.
  - **Site-to-Site (S2S)** VPN:
    - From your **on-premises VPN device/gateway** to the **Azure VPN Gateway** in a virtual network.
    - Connects entire on-premises networks to Azure.
    - Requires:
      - VPN device/gateway on-premises.
      - Azure VPN Gateway in Azure Virtual Network.
    -  **Resources :** https://medium.com/globant/configure-azure-site-site-vpn-to-on-premise-network-93f7a04eee9b
#### 2. Azure ExpressRoute :
- **Private connectivity** between on-premises and Azure Virtual Network.
- **Does not use the internet**.
- Provides:
  - **High bandwidth**.
  - **High reliability**.
  - **High security** (private circuit).
- Note:
  - Traffic is **not encrypted** because it’s already private.

---

### Azure Arc
- **Azure Arc** is Microsoft Azure’s **hybrid and multi-cloud management platform**.
- It lets you **centrally manage** infrastructure and services running:
  - On-premises
  - Other public clouds (AWS, Google Cloud, etc.)
  - Edge environments

#### Why Do We Need It?
- Without Azure Arc, managing resources (like Kubernetes clusters) across **multiple environments** is complex.
- There’s a risk of **inconsistent configurations** and **manual errors**.
- Azure Arc provides **one central place** in Azure Portal to view and manage all these resources.

#### Capabilities of Azure Arc
- **Kubernetes**: Centrally manage clusters across Azure, AWS, GCP, and on-premises.
- **VMs & Servers**: Manage on-premises physical or virtual servers.
- **Databases**: Manage SQL Server instances and even deploy Azure SQL Database anywhere.
- **VMware Resources**: Manage VMware environments from Azure.
