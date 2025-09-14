### Azure Virtual Machines 

#### Understanding Virtualization:

##### Before Virtualization:
- One physical server [CPU + RAM + Storage] = One application.
- Resulted in:
  - Underutilized resources ; High costs ; Inefficiency

##### What is Virtualization?
  - **Virtualization** is the process of running **multiple virtual machines (VMs)** on a **single physical server**.
  - It is enabled by a special software called a **Hypervisor**.

##### Benefits of Virtualization:
- **Improved Resource Utilization** : VMs share CPU, memory, and storage on a single server.
- **Flexibility**  : Easily create, delete, or move virtual machines as needed.
- **Cost Efficiency**  : Maximizes use of existing hardware.
- **Scalability & Portability**  : VMs can be replicated or moved across environments easily.

```
### 🧩 Real-Life Example: How Virtualization Is Used

#### 🏢 Scenario: Hosting Internal Apps in a Company

A medium-sized company needs to run:
- HR System
- Finance App
- Dev/Test Environments
- Internal Website
- File Server

#### 🔴 Before Virtualization:
- 5 physical servers (one per app).
- Problems:
  - Underutilized resources (low CPU/RAM usage).
  - High hardware and energy costs.
  - Difficult to scale or manage.

#### ✅ After Virtualization:
- 1 high-powered physical server + **Hypervisor**
- 5 **Virtual Machines**, each hosting one app.

#### 🎯 Benefits:
- **Better resource usage** (shared CPU/RAM)
- **Cost-effective** (one server vs five)
- **Easy to manage & scale**
- **Isolation** between apps (one crash doesn’t affect others)
- **Fast backup & recovery** (VM snapshots)
- **Flexible deployment**

#### ☁️ Cloud Extension:
- Instead of on-premises VMs, company moves to cloud (e.g., Azure).
- Same virtualization — but managed by cloud provider.
- No hardware, no maintenance, instant scalability.

> 💡 Virtualization allows multiple apps to run independently on the same physical hardware — increasing efficiency, reducing cost, and improving manageability.

```

### Azure VM 

- In corporate DC apps are deployed on physical servers
- In cloud we rent virtual servers to deploy apps ;  VM = Virtual Servers in Azure Cloud

#### Features :
- Create and Manage virtual servers on-demand.
- Full control over:
  - **Start**, **Stop**, **Restart**, **Delete** VM instances.
  - **Attach disks** (OS & data).
  - **Configure networking** (e.g., public IPs).
  - **Install any OS** (Windows/Linux) and custom applications.
    
  - **Scalability & Availability**
  - Use **Auto Scaling** to:
    - Increase VMs when traffic is high.
    - Decrease when load drops — saves cost.

  - Use **Load Balancers** to:
    - Distribute traffic across multiple VMs.
    - Prevent single points of failure.

  ```
    ### 💡 Real-World Example:
  
  > You want to host a high-traffic e-commerce app.
  
  - You deploy 3 VMs, each running a web server.
  - Add a **Load Balancer** to split traffic across VMs.
  - Set up **Auto Scaling**:
    - Scale to 6 VMs on Black Friday.
    - Scale down to 2 VMs during off-hours.
  - Attach **managed disks** for storage.
  - Assign **public IPs** for access.
  
  ```

 ----
    
### Creating a VM in Azure :

1. Login to portal.azure.com > Search for Virtual Machines in search box > Virtual Machine > Create > Virtual Machine
2. Create a Resource Group

#### Resource Groups : 

- A Resource Group in azure is a logical container for resources such as VMs, databases, storage accounts, and virtual networks.
- It lets you organize, manage, monitor, and control access to related Azure resources as one unit.

- Key Features :
  - Logical Grouping: Keep related resources together for easier management.
  - Role-Based Access Control (RBAC): Apply permissions at the group level instead of individually.
  - Deployment & Lifecycle: Deploy or delete resources in bulk.
  - Tagging & Billing: Track cost and usage by grouping.

```
Example 1: Web Application Environment

You build a web app needing:
- App Service (website hosting)
- SQL Database (user data)
- Storage Account (images/files)
- Virtual Network (secure communication)

All go into one resource group: RG-WebApp-Prod.

```

3. Add Virtual Machine Name
4. Select Region and Image [OS] you want
5. Select Size : Processing power , Memory and Storage
6. Select Inbound ports :
   - 22, 80 [443 for https] // Here we need 22 to ssh into the VM and execute commands to install softwares and all
   - **Note** : This will allow all IP addresses to access your virtual machine.This is only recommended for testing.Use the Advanced controls in the Networking tab to create rules to limit inbound traffic to known IP addresses.
7. Review and Create -> Final Validation - Takes a minute or so
8. Create the VM and Download the private key which will be used to login to VM via ssh


---- 

### Connecting to VM 

1. Go to VM -> Select your VM -> Click on  Connect
2. Connect

   ```
   Now Connect has 2 options :

   1. Connect (Direct RDP/SSH) : Here the VM gets a public IP and we can connect to the VM via RDP 3389 [Windows] or SSH 22 [Linux]
      But the VM is publicly exposed to the internet , to prevent this we can use Azure Bastion

   2. Connect via Bastion :
       Bastion is basically a Jumpbox server that lets you connect to your VM securely over SSL (port 443) through the Azure portal — no public IP required on the VM
  
   ```
   <img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/0dfcfaec-fa60-4947-88be-7b98d979ee54" />

3. Connect using SSH using Azure CLI > Select Bash > Execute commands 

- ##### We installed nginx and hosted a static web page (/var/www/html/index.html)

- ##### Now while creating a VM , we can go to Advanced tab > add our commands to install and perform small tasks in custom data section

- ##### Availability Set:
  - An Availability Set ensures Azure distributes VMs across fault and update domains to protect against hardware failures and maintenance events.
  - Fault Domain (FD) – Isolates VMs across physical hardware to prevent downtime from rack-level failures.
  - Update Domain (UD) – Staggers VM reboots during planned maintenance to avoid simultaneous downtime.

  ```
    Availability Set
  ├── Fault Domain 1
  │   ├── Update Domain 1 → VM1
  │   └── Update Domain 2 → VM2
  ├── Fault Domain 2
      ├── Update Domain 1 → VM3
      └── Update Domain 2 → VM4

  ```

- ##### Virtual Machine Scale Set:
  - Allows to create and Manage a group of VMs [supports 1000 VMs per Scale set]
  - Allows Auto Scaling (to add or delete the VMs as required) ; Manual Scaling is also available
  - We can create all VMs with same template or flexible template (custom data ; cloudinit we saw earlier)
  - Allows to add a Load Balancer to distribute the traffic among the VMs
  - Also helps to attain High availability by spreading VMs across Availability Zones or Fault Domains

- ##### Static IP:
  - While creating a VM we can go to Networking > Public IP > Assign a static IP so that when we restart or stop start a VM , the IP remains same
  - Public IP is charged per IP per hour.
 
- ##### Dedicated Hosts:
  - Dedicated Hosts in Azure are physical servers that are dedicated to your organization’s workloads. These hosts are not shared with any other customers, unlike the regular Azure VMs, which share underlying physical hardware with other tenants.
  - Benefits : Isolation , Compliance ,  Licensing Optimization

- ##### Site Recovery:
  - Azure Site Recovery (ASR) is a disaster recovery (DR) solution offered by Azure to help businesses protect their critical workloads and applications from outages, ensuring business continuity.
  - Go to VM > Go to Site Recovery > Select Region and replicate your VM in the region 
