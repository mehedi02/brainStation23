# design freight management system 
We will use **Azure** Cloud Environment to deploy our application. As it has all the components and can talk to each other without any issue
We will use **AKS**(Azure Kubernetes Cluster) to deploy our application. Our application has frontend developed using React and backend developed using Dot net core. We will use Azure SQL database. Our frontend and backend will be deployed in AkS cluster. Frontend can retrieve and save data to Azure SQL database using dot net core api. Our business logic will be implemented in dot net core.
So frontend and backend will have its own deployment, pods, services. Frontend and backend can talk to each other through api.

When we create AKS cluster it will create **ALB**(Azure load balancer) but we will use **Azure Application Gateway** with **istio** service mesh to handle traffic coming from outside.
Azure Application gateway give us **WAF** (Web Application Firewall) which will protect us from different exploit like cross site scripting, sql injection etc.
Istio will be used as ingress controller i.e it will route the incoming traffic from outside through application gateway to respective pods container using internal services
We will **LetsEncrypt** SSL certificate to use https protocol. LetsEncrypt certificate expire after 3 month, we need handle that using **Azure automation** script using **powershell** and update ssl certificate in application gateway.

We can easily scale our cluste under load using auto-scaling feature present in AkS

We can develop CI/CD pipeline using **Azure DevOps**. It is a very powerful tool in Azure and we can easily set-up Build and release pipeline interactively using its rich UI interface. It has lot of integration with other azure services. 

We will host our docker images in **Azure Container registry** as it has nice integration with azure devops. We can push our code to github but we will use **Azure repos** to push our code.
We can use **Terraform** with **Azure DevOps** to create our deployment. Using Terraform with Azure DevOps we can create up and running cluster within a minute.

As a disasters recovery, we can use **Geo-replication** features for **Azure SQL database** in Azure. Which will save our valuable data in any outage. Due to outage we will lost our cluster and other components. But we can easily create the cluster same as before using Terraform with Azure DevOps. And also, our data is preserved due to geo-replication
Azure DevOps can also use for alert strategies. We can use azure **logic apps** with Azure DevOps to send email alert when any problem rises in Azure DevOps
We can integrate different unit test or test script in Azure DevOps

For logging we can use **Azure log analytics**, which will give us insight about our cluster, its health, resource consumption, container logs etc. using this information we can take important decision.

For Secrets, configuration files, other certificates we can use **Azure key vault**. We can retrieve sensitive  data from Azure key vault to aks cluster securely.
