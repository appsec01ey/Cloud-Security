### Managed Compute Services

- Cloud providers offer different service models to simplify this:
  - IaaS – Infrastructure as a Service
  - PaaS – Platform as a Service
  - SaaS – Software as a Service
  - Serverless

| IAAS                                  | PAAS                                  |
|---------------------------------------|---------------------------------------|
| ![IAAS Image](https://github.com/user-attachments/assets/e1c82139-385f-43a4-a504-b270b1bca34e)| ![PAAS Image](https://github.com/user-attachments/assets/eb59bf2b-eef8-414f-861d-6704a2ccc4fc) |

<img width="480" height="298" alt="image" src="https://github.com/user-attachments/assets/87fe49c4-ac32-4bb5-bc5f-914b87d5225f" />


- #### IAAS
  - Example :
    - Deploying a Java app on an Azure VM: Create VM (Linux/Windows) > Install Java runtime > Deploy your app > Configure load balancing, scaling, and OS patches yourself.
    - Similar to running apps on servers in your own data center but on Azure’s infrastructure

- #### PAAS
  - Example :
    - Deploying a Java app using Azure App Service: Upload your code and configuration.
    - Azure takes care of OS, Java runtime, scaling, load balancing, and availability automatically. 


- #### Creating and Deploying a web app using Azure App Services
  - Go to the Azure Portal > Search for "App Services" and click "Create".
  - Basics tab:
    - Subscription: Choose your subscription.
    - Resource Group: Create new or use existing.
    - Name: This becomes part of your URL, e.g., mywebapp.azurewebsites.net.
    - Publish: Choose "Code" (or Docker Container).
    - Runtime stack: e.g., .NET, Node.js, Python, Java. // If you select code u need to choose RT env
    - Operating System: Windows or Linux.
    - Region: Choose a region allowed in your subscription (e.g., East US, West Europe). 
  - Database > Create DB if needed
  - Container > Choose Nginx in sample
  - Networking // Keep Default
  - Monitor+Secure > You can integrate with Defender for Cloud
  - Review + Create > Create
 
  - ##### Key Features post deployment
    - Custom Domain + SSL
    - Deployment Slots
    - Scale Up / Scale Out
    - Monitoring - Alerts , Metrics , Logs etc
    - API Management (Cors Implementation)
    - Authentication (Add IDP like Google, Microsoft, Apple, OIDC etc
    - Backups
   
  - #### Resources :
    - Azure App Services:
      - https://medium.com/@devopswithyoge/use-azure-app-service-like-a-pro-part-1-1bf34512ef0d [3 parts]  

  - ### Microservices :
    - Microservices architecture breaks applications into small, independent services—each can be built with the most suitable programming language and technology stack.
    <img width="382" height="77" alt="image" src="https://github.com/user-attachments/assets/9e4eaacf-68cf-4cbe-bf46-a3a71a76b664" />
    - For ex, u can build movieservice in java ,  customerservice in python and so on
    - This flexibility creates a challenge for deployment because each microservice might have different runtime needs.
    - Solution : Containers

  - ### Containerization :
    - Containerization is a way to package an application along with everything it needs to run — like the code, libraries, and settings — into a single unit called a container. This container can then be easily moved and run on any computer or cloud environment without worrying about compatibility issues.
    - Containers share the host OS kernel but have their own isolated user space i.e One Container doesnt affect other containers , all run independently.
    - Each container runs in its own lightweight environment, separate from other containers.
    - Hence, We create Docker Image for each microservice which contains Application Runtime, Application Code and Dependencies.
   
  - #### Azure Container Instances :
    - Go to Container Instances > Create > Choose Config and create a container
    - Problem : Orchestration of containers ; Solution : Kubernetes / Service Fabric

  - #### AKS Azure Kubernetes Services :
    - Resources : https://youtu.be/Nyusm9NeyKc

  - ##### Why Container Orchestration?
    - Just running containers isn’t enough — you need orchestration to handle:
    - Auto-scaling: Run more/less containers based on demand (e.g., 10 instances of A, 15 of B).
    - Service Discovery: Avoid hardcoding URLs; orchestrator keeps track of where each service lives.
    - Load Balancing: Distribute traffic across multiple containers automatically.
    - Resiliency & Self-Healing: Detect failing instances, replace them automatically.
    - Zero-Downtime Deployments: Roll out version upgrades without interrupting service.

- ### Serverless :
  - Serverless is a cloud model where you only write and deploy your code, and the cloud provider automatically takes care of all servers, scaling, and maintenance. You pay only when your code runs, not for idle servers.
  - Example:
    - A company wants to resize images uploaded by users. With Azure Functions (serverless), they just write a small function:
      “When a new image is uploaded to Blob Storage, resize it to 3 different sizes.”

    - Azure automatically:
      - Triggers the function on each upload
      - Allocates compute resources only for the execution
      - Scales up if thousands of images arrive at once
      - Scales down to zero when idle
     
    - Resources : https://medium.com/@sadoksmine8/azure-functions-building-serverless-applications-a396a026d810

- ### SAAS (Software as a Service) :
  - SaaS = centrally hosted software delivered over the internet, usually on a subscription basis.
  - Users access the software through a browser or app without worrying about servers or infrastructure.
  - User responsibility limited to configuration & usage rest all is managed via Cloud provider


- ## Shared Responsibility Model :

 
