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
 
    
