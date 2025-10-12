\# Day 1 - Introduction to Cloud Computing and AWS



\## 1️⃣ What is Cloud Computing?

Cloud computing is the delivery of computing services — like \*\*servers, storage, databases, networking, software, and analytics\*\* — over the internet (“the cloud”) instead of your own physical computer or on-premises server.



\*\*Key points:\*\*

\- No need to buy and maintain physical servers.  

\- Pay only for what you use (cost-effective).  

\- Scale resources up or down easily (elasticity).  

\- Accessible from anywhere in the world via the internet.  



---



\## 2️⃣ Data Centers and Availability Zones (AZs)

AWS organizes its infrastructure into \*\*Regions\*\* and \*\*Availability Zones (AZs)\*\*.



\- \*\*Data Center:\*\* A physical building with servers, networking equipment, and storage.  

\- \*\*Availability Zone (AZ):\*\* An isolated data center within a region. Each AZ has independent power, networking, and cooling.  

\- \*\*Region:\*\* A group of multiple AZs located in a specific geographical area (e.g., Mumbai, US East).  



\*\*Benefits:\*\*  

\- High availability (if one AZ fails, others continue running).  

\- Fault tolerance (multiple AZs reduce downtime).  



---



\## 3️⃣ Different Cloud Providers

Popular cloud service providers:  

\- \*\*AWS (Amazon Web Services)\*\* – Largest and most popular.  

\- \*\*Microsoft Azure\*\* – Good for Windows-based environments.  

\- \*\*Google Cloud Platform (GCP)\*\* – Strong in AI and data analytics.  

\- \*\*IBM Cloud\*\* – Focuses on enterprise solutions.  

\- \*\*Oracle Cloud\*\* – Strong in databases and enterprise applications.  



---



\## 4️⃣ Types of AWS Cloud Services

AWS services are categorized based on how much control you have over the infrastructure:



\### a) IaaS (Infrastructure as a Service)

\- You manage applications, OS, and data; AWS manages the hardware.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*EC2:\*\* Virtual servers to run applications  

&nbsp; - \*\*EBS:\*\* Storage volumes for EC2  

&nbsp; - \*\*VPC:\*\* Virtual private network for your resources  

\- \*\*Use case:\*\* Hosting websites, databases, or apps where you need full control over the environment.  



\### b) PaaS (Platform as a Service)

\- AWS manages the underlying infrastructure and platform; you focus on deploying your apps.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*Elastic Beanstalk:\*\* Automatically deploys and scales apps  

&nbsp; - \*\*RDS:\*\* Managed relational databases like MySQL, PostgreSQL  

\- \*\*Use case:\*\* Web apps and databases without managing OS or servers.  



\### c) SaaS (Software as a Service)

\- Fully managed applications accessible via a browser.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*WorkMail:\*\* Email service  

&nbsp; - \*\*Chime:\*\* Video conferencing  

\- \*\*Use case:\*\* Use applications without worrying about servers or infrastructure.  



\### d) FaaS / Serverless (Function as a Service)

\- Run code without managing servers; pay only for execution.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*Lambda:\*\* Run functions triggered by events  

&nbsp; - \*\*API Gateway:\*\* Create serverless APIs  

\- \*\*Use case:\*\* Automation, event-driven apps.  



---



\## 5️⃣ Types of Cloud Deployment

\- \*\*Public Cloud:\*\* Shared resources over the internet (e.g., AWS global regions).  

\- \*\*Private Cloud:\*\* Dedicated resources for one organization (e.g., AWS Outposts).  

\- \*\*Hybrid Cloud:\*\* Mix of public and private clouds; some apps run in AWS public cloud, some on-premises.  

\- \*\*Multi-Cloud:\*\* Using multiple providers (AWS + Azure + GCP) for different needs.  



---



\## 6️⃣ Features Provided by Cloud Providers

\- \*\*Scalability:\*\* Add or remove resources easily.  

\- \*\*Elasticity:\*\* Automatically scale applications based on demand.  

\- \*\*Cost Efficiency:\*\* Pay only for what you use.  

\- \*\*High Availability:\*\* Multiple regions and AZs reduce downtime.  

\- \*\*Security:\*\* IAM, encryption, and compliance certifications (ISO, SOC, GDPR).  

\- \*\*Global Reach:\*\* Deploy resources worldwide.  

\- \*\*Wide Service Portfolio:\*\* Compute, storage, networking, database, ML, IoT, security, DevOps, and more.  



---



\## 7️⃣ Popular AWS Services (Overview)



| Service | Type | Description |

|---------|------|-------------|

| \*\*EC2\*\* | IaaS | Virtual servers for apps and websites |

| \*\*S3\*\* | IaaS | Scalable object storage for files/data |

| \*\*RDS\*\* | PaaS | Managed relational databases |

| \*\*Lambda\*\* | FaaS | Run serverless code in response to events |

| \*\*VPC\*\* | IaaS | Isolated virtual network for resources |

| \*\*CloudFront\*\* | CDN | Global content delivery network |

| \*\*IAM\*\* | Security | Manage users, roles, and permissions |

| \*\*DynamoDB\*\* | PaaS | Fully managed NoSQL database |

| \*\*Elastic Beanstalk\*\* | PaaS | Deploy and scale web apps easily |

| \*\*CloudWatch\*\* | Monitoring | Monitor resources, logs, and alerts |

\# Day 1 - Introduction to Cloud Computing and AWS



\## 1️⃣ What is Cloud Computing?

Cloud computing is the delivery of computing services — like \*\*servers, storage, databases, networking, software, and analytics\*\* — over the internet (“the cloud”) instead of your own physical computer or on-premises server.



\*\*Key points:\*\*

\- No need to buy and maintain physical servers.  

\- Pay only for what you use (cost-effective).  

\- Scale resources up or down easily (elasticity).  

\- Accessible from anywhere in the world via the internet.  



---



\## 2️⃣ Data Centers and Availability Zones (AZs)

AWS organizes its infrastructure into \*\*Regions\*\* and \*\*Availability Zones (AZs)\*\*.



\- \*\*Data Center:\*\* A physical building with servers, networking equipment, and storage.  

\- \*\*Availability Zone (AZ):\*\* An isolated data center within a region. Each AZ has independent power, networking, and cooling.  

\- \*\*Region:\*\* A group of multiple AZs located in a specific geographical area (e.g., Mumbai, US East).  



\*\*Benefits:\*\*  

\- High availability (if one AZ fails, others continue running).  

\- Fault tolerance (multiple AZs reduce downtime).  



---



\## 3️⃣ Different Cloud Providers

Popular cloud service providers:  

\- \*\*AWS (Amazon Web Services)\*\* – Largest and most popular.  

\- \*\*Microsoft Azure\*\* – Good for Windows-based environments.  

\- \*\*Google Cloud Platform (GCP)\*\* – Strong in AI and data analytics.  

\- \*\*IBM Cloud\*\* – Focuses on enterprise solutions.  

\- \*\*Oracle Cloud\*\* – Strong in databases and enterprise applications.  



---



\## 4️⃣ Types of AWS Cloud Services

AWS services are categorized based on how much control you have over the infrastructure:



\### a) IaaS (Infrastructure as a Service)

\- You manage applications, OS, and data; AWS manages the hardware.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*EC2:\*\* Virtual servers to run applications  

&nbsp; - \*\*EBS:\*\* Storage volumes for EC2  

&nbsp; - \*\*VPC:\*\* Virtual private network for your resources  

\- \*\*Use case:\*\* Hosting websites, databases, or apps where you need full control over the environment.  



\### b) PaaS (Platform as a Service)

\- AWS manages the underlying infrastructure and platform; you focus on deploying your apps.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*Elastic Beanstalk:\*\* Automatically deploys and scales apps  

&nbsp; - \*\*RDS:\*\* Managed relational databases like MySQL, PostgreSQL  

\- \*\*Use case:\*\* Web apps and databases without managing OS or servers.  



\### c) SaaS (Software as a Service)

\- Fully managed applications accessible via a browser.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*WorkMail:\*\* Email service  

&nbsp; - \*\*Chime:\*\* Video conferencing  

\- \*\*Use case:\*\* Use applications without worrying about servers or infrastructure.  



\### d) FaaS / Serverless (Function as a Service)

\- Run code without managing servers; pay only for execution.  

\- \*\*Examples:\*\*  

&nbsp; - \*\*Lambda:\*\* Run functions triggered by events  

&nbsp; - \*\*API Gateway:\*\* Create serverless APIs  

\- \*\*Use case:\*\* Automation, event-driven apps.  



---



\## 5️⃣ Types of Cloud Deployment

\- \*\*Public Cloud:\*\* Shared resources over the internet (e.g., AWS global regions).  

\- \*\*Private Cloud:\*\* Dedicated resources for one organization (e.g., AWS Outposts).  

\- \*\*Hybrid Cloud:\*\* Mix of public and private clouds; some apps run in AWS public cloud, some on-premises.  

\- \*\*Multi-Cloud:\*\* Using multiple providers (AWS + Azure + GCP) for different needs.  



---



\## 6️⃣ Features Provided by Cloud Providers

\- \*\*Scalability:\*\* Add or remove resources easily.  

\- \*\*Elasticity:\*\* Automatically scale applications based on demand.  

\- \*\*Cost Efficiency:\*\* Pay only for what you use.  

\- \*\*High Availability:\*\* Multiple regions and AZs reduce downtime.  

\- \*\*Security:\*\* IAM, encryption, and compliance certifications (ISO, SOC, GDPR).  

\- \*\*Global Reach:\*\* Deploy resources worldwide.  

\- \*\*Wide Service Portfolio:\*\* Compute, storage, networking, database, ML, IoT, security, DevOps, and more.  



---



\## 7️⃣ Popular AWS Services (Overview)



| Service | Type | Description |

|---------|------|-------------|

| \*\*EC2\*\* | IaaS | Virtual servers for apps and websites |

| \*\*S3\*\* | IaaS | Scalable object storage for files/data |

| \*\*RDS\*\* | PaaS | Managed relational databases |

| \*\*Lambda\*\* | FaaS | Run serverless code in response to events |

| \*\*VPC\*\* | IaaS | Isolated virtual network for resources |

| \*\*CloudFront\*\* | CDN | Global content delivery network |

| \*\*IAM\*\* | Security | Manage users, roles, and permissions |

| \*\*DynamoDB\*\* | PaaS | Fully managed NoSQL database |

| \*\*Elastic Beanstalk\*\* | PaaS | Deploy and scale web apps easily |

| \*\*CloudWatch\*\* | Monitoring | Monitor resources, logs, and alerts |



