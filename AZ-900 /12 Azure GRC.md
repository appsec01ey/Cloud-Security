### GRC

### 1. Azure Policy Overview

- Azure Policy helps ensure that your Azure resources stay compliant with defined rules and standards. It allows you to **create, assign, and manage policies** across multiple subscriptions and resource groups.
- A set of rules that resources must adhere to. Ensures compliance automatically.
- Non-compliant resources are marked but continue to function.

#### Initiative
- A **group of policies** used to manage multiple rules at once.
- Can be assigned to a **management group, subscription, or resource group**.
- Examples of pre-defined initiatives: **Azure Security Benchmark**,  **UK OFFICIAL / UK NHS** standards, **HIPAA** (US healthcare regulation)
- Assignment Levels: **Management group**, **Subscription**, **Resource group**
- Compliance Dashboard: Provides an **aggregated view** of compliance. Can drill down to **specific resources or policies**. Evaluation occurs approximately **every hour**.

#### Example Policies
- Allow creation of VMs only of specific sizes.
- Restrict resource creation to certain regions.
- Automatically tag resources with the same tags as their resource group.
- Make Multi-Factor Authentication (MFA) mandatory for certain accounts.
- 
#### How Policy Works
1. Create or select a policy/initiative.
2. Assign it at the desired level (management group, subscription, resource group).
3. Existing resources are evaluated:
   - **Non-compliant resources** are marked.
   - No change to resource behavior.
4. Policies are evaluated approximately **every hour**.

### Examples of Default Initiatives
- **ASC Default rules:**
  - Enable threat detection for Azure resources
  - Implement security for internal traffic
  - Protect sensitive data
  - Connect private networks
  - Encrypt sensitive data at rest

- **Other standards:** PCI, HIPAA, UK NHS, etc.

---

### 2. Azure Blueprints:



