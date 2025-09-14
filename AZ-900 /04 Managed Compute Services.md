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
