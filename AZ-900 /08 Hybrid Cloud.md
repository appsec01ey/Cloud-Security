### Hybrid Cloud:

| Model        | Hosted Where?         | Cost Model              | Ownership & Control               | Example Use Case                                 |
|--------------|---------------------- |------------------------- |----------------------------------- |--------------------------------------------------|
| **Public**   | Cloud provider        | Operational (pay-as-you-go) | Cloud provider                | Startup running all workloads on Azure           |
| **Private**  | Own data center       | Capital + operational   | Organization                      | Government hosting sensitive apps internally     |
| **Hybrid**   | Mix of both           | Mixed                   | Shared responsibility             | On-prem app talking to Azure Cosmos DB           |

---
### 1. Azure VPN and Express Route

#### Azure VPN :
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
