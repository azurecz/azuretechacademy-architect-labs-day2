# Azure Technical Academy - Architect day2:  Architectures for running applications in cloud
Second day is focusing on application architectures in Azure.

Azure Stencils
* Go to Visio
* Open shapes
* Search for word "cloud" and click for Online results
* Download Microsoft Azure Cloud Icons
* If you have older Visio you can download older stencils directly and copy to Documents/My Shapes folder [here](https://architects.blob.core.windows.net/visio/CnE_CloudV2.7.vss?st=2019-05-20T05%3A27%3A00Z&se=2020-05-21T07%3A27%3A00Z&sp=rl&sv=2018-03-28&sr=b&sig=IELwMsknjeDR3E2fQcfyDa1lOG3hHIiHvLe4gyXMn0U%3D)
* If you are using different tool, download SVG library and import to tool of your choice [here](https://www.microsoft.com/en-us/download/details.aspx?id=41937)

Example solution
- schema https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/identity/azure-ad
- description https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/identity/azure-ad#architecture
- pricing https://azure.microsoft.com/en-us/pricing/calculator/
- example architectures [https://azure.microsoft.com/en-us/solutions/architecture/](https://azure.microsoft.com/en-us/solutions/architecture/)

Timing: 
- 10min intro 
- 50min design
- 20min presentation and recommended solution

# How to upload results of your work
* Download and install storage explorer [here](https://azure.microsoft.com/en-us/features/storage-explorer/)
* Open storage explorer and connect to storage (key will be active only for duration of our workshop)
    * Click on electricity plug icon on left side and select Use a storage account name and key
    * Use following Account Name: architects
    * Use following Account Key: <- will be provided at training date ->
    * Go to architects, Blob Containers, right-click and create container for your group
    * Upload results of your work to container with prefix scenario1 etc.

# Scenarios

## Scenario 1: Highly available traditional application
Application architecture
- .NET Framework based scalable web layer
- .NET Framework based application layer
- Microsoft SQL database

Requirements
- All components must be deployed with zone redundancy
- Design scalable web layer with ability to easily scale number of nodes based on load with advanced balancer (reverse proxy)
- Design highly available application layer as active/active with load balancer
- Web and application layers require IaaS due to legacy code that is using low-level OS calls
- Ensure TLS is terminated on security device with Web Application Firewall functionality
- Protect against DDoS
- To achieve high availability make sure solution use multiple availability zones
- Application has been tested to work with Azure SQL Database PaaS
- Application is accessing legacy systems on-premises, design private connectivity solution with leased line and IPSec VPN as backup
- Calculate composite Azure infrastructure SLA. Does it meet 99,9%?
- Ensure DR to different Azure region with RPO < 24h and RTO < 24h

## Scenario 2: Modern web-based application
Application architecture
- Node.JS web app
- PostgreSQL database
- A lot of static content (PDF files and images)
- Video content

Requirements
- To ease operations do not use IaaS, only PaaS
- Design application that can scale based on time of day and usage to ensure optimal user experience while saving costs
- Design solution for storing and serving static content in cost effective way and cache it close to user locations
- PDF files as well as records in database must have centralized joint full-text search capability
- Application is designed for customers and requires authentication and authorization, account management and integrations with Google and Facebook logins
- Users are uploading pictures of cars and we need to automatically check and povide feedback when they accidentaly upload picture of something else
- Users are uploading scanned paper forms and we need to parse information out of images
- There is requirement for 4 environments - dev, test, staging and production
- Design automated build and release with CI/CD pipeline
- Video content needs to be encoded to multiple bitrate streams so player can switch quality based on strenght of user connection, content need to be protected with Digital Rights Management

## Scenario 3: Microservices-based application with containers
Application architecture
- Mix of .NET Core and Java
- 30 containerized microservices
- Angular frontend
- Asynchronous operations between some services using publish/subscribe pattern
- Microsoft SQL database

Requirements
- Design secure and highly available store for container images
- Design container orchestration cluster to deploy microservices
- To ease development of Angular frontend design solution to streamline and manage APIs
- Externalize all stateful operations into PaaS including queing and database
- Design CI/CD pipeline

## Scenario 4: IoT application
Application architecture
- IoT devices capturing telemetry
- IoT gateway devices doing pre-processing including aggregations and anomaly detection
- Central streaming data processing and storing RAW data for deeper analysis (which by itself is not in scope of this project) and aggregated views for application and visualization using JSON-based NoSQL database

Requirements
- Use PaaS to connect and manage devices and collect data
- Find solution to prepare filtering, aggregation and anomaly detection logic in cloud while pushing it IoT gateway devices for processing
- Find serverless solution to process captured data, export to RAW storage, do stream analytics and write results to NoSQL database
- When anomaly is detected in stream analytics trigger code to create alarm and based on user preferences react by sending SMS, email or create incident in ITSM tool
- Web application will provided to customer to manage alerts and visualize data
- Use PowerBI solution, but not standalone - there is requirement to build this functionality into custom web applicatio mentioned earlier

## Scenario 5: Custom business applications built on top of Microsoft SaaS
Application architecture
- Business applications built on top of SaaS platforms (Sharepoint Online, Dynamics)

Requirements
- Provide solution for rapid application development with as little coding as possible
- Provide solution for distributing mobile applications to internal users
- Use serverless to provide integration logic and workflows between Sharepoint, Dynamics, Office365 and legacy systems

# Agenda and next steps 

Prerequisites: Notebook with Visio (or similar tool)

## Homework 1
TBD

## Contacts

### Tomas Kubica - Azure TSP at Microsoft
- https://www.linkedin.com/in/tkubica
- https://github.com/tkubica12
- https://twitter.com/tkubica

### Jaroslav Jindrich - Cloud Solutions Architect
- https://www.linkedin.com/in/jjindrich
- https://github.com/jjindrich
- https://twitter.com/jjindrich_cz
