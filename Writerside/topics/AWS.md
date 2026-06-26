# AWS ecosystem

### Attribute Key
*   **Management:** `Serverless` | `Fully Managed` | `Self-Managed` | `Physical`
*   **Scaling:** `Implicit` (Auto) | `Explicit` (Rules) | `Manual` (Static)
*   **Pricing:** `Execution/Req` | `Provisioned` | `Volume` | `Fixed`
*   **Scope:** `Global` | `Regional` | `Zonal` | `Local`
*   **State:** `Stateless` | `Stateful`

---

### 1. Compute & Container Services
| Sub-category                | Service Instance               | Management    | Scaling  | Pricing        | Scope     | State     |
|:----------------------------|:-------------------------------|:--------------|:---------|:---------------|:----------|:----------|
| **IaaS / Virtualization**   | Amazon EC2 (On-Demand/Spot/RI) | Self-Managed  | Explicit | Provisioned    | Zonal     | Stateful  |
| **Simplified VPS**          | Amazon Lightsail               | Fully Managed | Manual   | Fixed          | Zonal     | Stateful  |
| **Serverless Compute**      | AWS Lambda                     | Serverless    | Implicit | Execution      | Regional  | Stateless |
|                             | AWS Fargate                    | Serverless    | Implicit | Provisioned    | Zonal/Reg | Stateless |
|                             | AWS App Runner                 | Serverless    | Implicit | Provisioned    | Regional  | Stateless |
| **PaaS / Orchestration**    | AWS Elastic Beanstalk          | Fully Managed | Explicit | Provisioned    | Regional  | Stateful  |
|                             | AWS Batch                      | Fully Managed | Explicit | Provisioned    | Regional  | Stateless |
| **Hybrid & Edge**           | AWS Outposts                   | Self-Managed  | Manual   | Fixed          | Local     | Stateful  |
|                             | AWS Wavelength                 | Fully Managed | Manual   | Provisioned    | Zonal     | Stateless |
|                             | VMware Cloud on AWS            | Fully Managed | Explicit | Provisioned    | Regional  | Stateful  |
| **Container Registry**      | Amazon ECR                     | Fully Managed | Implicit | Volume         | Regional  | Stateful  |
| **Container Orchestration** | Amazon ECS                     | Fully Managed | Explicit | Provisioned    | Regional  | Stateless |
|                             | Amazon EKS                     | Fully Managed | Explicit | Provisioned    | Regional  | Stateless |
|                             | Red Hat OpenShift (ROSA)       | Fully Managed | Explicit | Provisioned    | Regional  | Stateful  |
| **Modernization Tools**     | AWS App2Container              | Tool (CLI)    | N/A      | Free           | Global    | Stateless |
| **Compute Governance**      | EC2 Auto Scaling               | Fully Managed | Explicit | Volume/Prov    | Regional  | Stateless |
|                             | EC2 Image Builder              | Fully Managed | Manual   | Volume         | Regional  | Stateless |
| **Ecosystem Support**       | Serverless App Repository      | Serverless    | Implicit | Resource-based | Global    | Stateless |
|                             | Amazon Linux 2023              | N/A (OS)      | N/A      | Free           | Global    | N/A       |

### 2. Storage Services
| Sub-category             | Service Instance            | Management    | Scaling  | Pricing     | Scope      | State     |
|:-------------------------|:----------------------------|:--------------|:---------|:------------|:-----------|:----------|
| **Object Storage**       | Amazon S3 (All Tiers)       | Serverless    | Implicit | Volume/Req  | Global/Reg | Stateful  |
| **Block Storage**        | Amazon EBS                  | Fully Managed | Manual   | Provisioned | Zonal      | Stateful  |
| **Elastic File Systems** | Amazon EFS (+ Archive)      | Serverless    | Implicit | Volume      | Regional   | Stateful  |
| **Specialized File Sys** | FSx for Lustre              | Fully Managed | Explicit | Provisioned | Zonal/Reg  | Stateful  |
|                          | FSx for NetApp ONTAP        | Fully Managed | Explicit | Provisioned | Zonal/Reg  | Stateful  |
|                          | FSx for OpenZFS             | Fully Managed | Explicit | Provisioned | Zonal/Reg  | Stateful  |
|                          | FSx for Windows File Server | Fully Managed | Explicit | Provisioned | Zonal/Reg  | Stateful  |
| **High-Speed Caching**   | Amazon File Cache           | Fully Managed | Implicit | Provisioned | Regional   | Stateless |
| **Data Protection**      | AWS Backup                  | Serverless    | Implicit | Volume      | Regional   | Stateful  |
|                          | Elastic Disaster Recovery   | Fully Managed | Manual   | Provisioned | Regional   | Stateful  |
| **Hybrid Storage**       | AWS Storage Gateway         | Fully Managed | Manual   | Provisioned | Local/Reg  | Stateful  |

### 3. Database Services
| Sub-category          | Service Instance             | Management    | Scaling  | Pricing     | Scope     | State    |
|:----------------------|:-----------------------------|:--------------|:---------|:------------|:----------|:---------|
| **Relational (SQL)**  | Amazon Aurora (+ I/O Opt)    | Fully Managed | Explicit | Provisioned | Regional  | Stateful |
|                       | Amazon RDS (Engines)         | Fully Managed | Explicit | Provisioned | Regional  | Stateful |
|                       | RDS for Db2 / on VMware      | Fully Managed | Manual   | Provisioned | Reg/Local | Stateful |
| **Non-Relational**    | Amazon DynamoDB              | Serverless    | Implicit | Req/Prov    | Regional  | Stateful |
|                       | Amazon Keyspaces (Cassandra) | Serverless    | Implicit | Request     | Regional  | Stateful |
| **In-Memory / Cache** | Amazon ElastiCache           | Fully Managed | Explicit | Provisioned | Zonal/Reg | Stateful |
|                       | Amazon MemoryDB              | Fully Managed | Explicit | Provisioned | Regional  | Stateful |
| **Graph Databases**   | Amazon Neptune / Analytics   | Fully Managed | Explicit | Provisioned | Regional  | Stateful |
| **Time Series**       | Amazon Timestream            | Serverless    | Implicit | Volume/Req  | Regional  | Stateful |
| **Document Stores**   | Amazon DocumentDB            | Fully Managed | Explicit | Provisioned | Zonal/Reg | Stateful |
| **Simplified DB**     | Lightsail Managed Databases  | Fully Managed | Manual   | Fixed       | Zonal     | Stateful |

### 4. Intelligence & AI Services (inc. Analytics)
| Sub-category             | Service Instance                                                     | Management    | Scaling   | Pricing      | Scope     | State     |
|:-------------------------|:---------------------------------------------------------------------|:--------------|:----------|:-------------|:----------|:----------|
| **Generative AI**        | Amazon Bedrock                                                       | Serverless    | Implicit  | Token/Req    | Regional  | Stateless |
|                          | Amazon PartyRock                                                     | Serverless    | Implicit  | Free/Usage   | Global    | Stateless |
| **ML Lifecycle**         | Amazon SageMaker AI (All)                                            | Fully Managed | Explicit  | Provisioned  | Regional  | Stateful  |
| **Pre-trained APIs**     | Rekognition, Polly, Lex, Translate, Comprehend, Textract, Transcribe | Serverless    | Implicit  | Request      | Regional  | Stateless |
| **Specialized AI**       | Forecast, Fraud Det, Personalize, Kendra, Monitron, Amazon Q         | Fully Managed | Implicit  | Req/Vol      | Regional  | Stateless |
| **Industry AI**          | HealthLake, HealthScribe, Panorama, Comprehend Medical               | Fully Managed | Implicit  | Volume/Req   | Regional  | Stateful  |
| **Experimental AI**      | DeepComposer, DeepRacer                                              | Fully Managed | Manual    | Fixed/Usage  | Global    | Stateless |
| **Serverless Analytics** | Amazon Athena / QuickSight                                           | Serverless    | Implicit  | Req/User     | Regional  | Stateless |
| **Data Warehousing**     | Amazon Redshift (Prov/Srvls)                                         | FM/Serverless | Expl/Impl | Prov/Req     | Regional  | Stateful  |
| **Big Data Process**     | EMR, MSK, Glue, Lake Formation                                       | Fully Managed | Explicit  | Provisioned  | Regional  | Stateful  |
| **Real-time Stream**     | Kinesis (Streams, Firehose, Video)                                   | Fully Managed | Explicit  | Volume       | Regional  | Stateless |
| **Data Governance**      | DataZone, FinSpace, Entity Res, Clean Rooms, Data Exchange           | Fully Managed | Implicit  | Subscription | Regional  | Stateful  |
| **Search & Viz**         | OpenSearch / OS Serverless                                           | FM/Serverless | Expl/Impl | Prov/Req     | Zonal/Reg | Stateful  |

### 5. Networking & Content Delivery Services
| Sub-category             | Service Instance                  | Management    | Scaling  | Pricing       | Scope     | State     |
|:-------------------------|:----------------------------------|:--------------|:---------|:--------------|:----------|:----------|
| **Network Isolation**    | Amazon VPC / VPC Lattice          | Fully Managed | Implicit | Data Transfer | Regional  | Stateless |
| **DNS Services**         | Amazon Route 53                   | Serverless    | Implicit | Request       | Global    | Stateless |
| **Content Delivery**     | Amazon CloudFront                 | Serverless    | Implicit | Volume/Req    | Global    | Stateless |
| **Load Balancing**       | ELB (ALB, NLB, GLB, CLB)          | Fully Managed | Implicit | LCU/Hour      | Regional  | Stateless |
| **Private Connectivity** | Direct Connect / Site-to-Site VPN | Fully Managed | Manual   | Provisioned   | Reg/Local | Stateless |
| **Network Hubs**         | Transit Gateway / PrivateLink     | Fully Managed | Implicit | Volume        | Regional  | Stateless |
| **API & Service Mgmt**   | API Gateway, App Mesh, Cloud Map  | Serverless    | Implicit | Request       | Regional  | Stateless |
| **Cellular Network**     | Private 5G / Integrated Wireless  | Fully Managed | Manual   | Fixed/Prov    | Local     | Stateless |
| **Zero Trust Access**    | AWS Verified Access               | Serverless    | Implicit | Request       | Regional  | Stateless |

### 6. Security, Identity & Compliance Services
| Sub-category             | Service Instance                        | Management    | Scaling  | Pricing    | Scope      | State     |
|:-------------------------|:----------------------------------------|:--------------|:---------|:-----------|:-----------|:----------|
| **IAM / SSO**            | IAM, IAM Identity Center, Cognito       | Serverless    | Implicit | User/Req   | Global     | Stateful  |
| **Threat Monitoring**    | GuardDuty, Inspector, Macie, Detective  | Serverless    | Implicit | Volume     | Regional   | Stateless |
| **Encryption & Secrets** | KMS, CloudHSM, Secrets Manager          | Serverless    | Implicit | Key/Req    | Regional   | Stateful  |
| **Edge Defense**         | WAF / WAF Captcha, Shield               | Serverless    | Implicit | Rule/Req   | Global/Reg | Stateless |
| **Perimeter Security**   | Network Firewall, Firewall Mgr          | Fully Managed | Implicit | Volume     | Regional   | Stateless |
| **Compliance Audit**     | Artifact, Audit Manager                 | Serverless    | Implicit | Free/Usage | Global     | Stateless |
| **Infrastructure ID**    | Certificate Manager / Directory Service | Fully Managed | Manual   | Fixed/Prov | Regional   | Stateful  |
| **Resource Sharing**     | Resource Access Manager (RAM)           | Serverless    | Implicit | Free       | Regional   | Stateless |

### 7. Management, Governance & Developer Tools
| Sub-category                | Service Instance                                        | Management    | Scaling  | Pricing     | Scope      | State     |
|:----------------------------|:--------------------------------------------------------|:--------------|:---------|:------------|:-----------|:----------|
| **Observability**           | CloudWatch / Grafana/Prometheus                         | Fully Managed | Implicit | Volume      | Regional   | Stateful  |
| **Governance Audit**        | CloudTrail, Config, Organizations                       | Serverless    | Implicit | Volume      | Global/Reg | Stateful  |
| **Ops Management**          | Systems Manager (All tools)                             | Fully Managed | Implicit | Free/Usage  | Regional   | Stateful  |
| **Infrastructure as Code**  | CloudFormation, Proton, Service Catalog                 | Serverless/FM | Implicit | Request     | Regional   | Stateless |
| **Optimization**            | Compute Optimizer, Trusted Advisor                      | Serverless    | Implicit | Free        | Regional   | Stateless |
| **Health & Review**         | Well-Architected Tool / Health                          | Serverless    | Implicit | Free        | Regional   | Stateless |
| **Landing Zone/Compliance** | Control Tower, Launch Wizard, License Mgr               | Fully Managed | Manual   | Fixed/Prov  | Regional   | Stateful  |
| **User Interface**          | Console App / User Notifications                        | Serverless    | Implicit | Free        | Global     | Stateless |
| **IDE & Debugging**         | Cloud9, CloudShell, X-Ray                               | Fully Managed | Explicit | Provisioned | Regional   | Stateless |
| **CI/CD Pipeline**          | CodeArtifact, Build, Commit, Deploy, Pipeline, Catalyst | Fully Managed | Explicit | Volume/Prov | Regional   | Stateful  |
| **Quality Tooling**         | Corretto / Fault Injection Service                      | Tool/FM       | Manual   | Free/Usage  | Global     | Stateless |
| **AI Dev Assistance**       | Amazon Q Developer (incl. Chat)                         | Serverless    | Implicit | Req/User    | Global     | Stateless |

### 8. Application Integration & Business Apps
| Sub-category            | Service Instance                          | Management    | Scaling  | Pricing      | Scope     | State     |
|:------------------------|:------------------------------------------|:--------------|:---------|:-------------|:----------|:----------|
| **Workflows**           | Step Functions, SWF, MWAA                 | Serverless/FM | Implicit | Execution    | Regional  | Stateless |
| **Messaging / Queues**  | SQS, SNS, MQ                              | Serverless/FM | Implicit | Request      | Regional  | Stateless |
| **Event Orchestration** | EventBridge, AppFlow, B2B Interchange     | Serverless    | Implicit | Request      | Regional  | Stateless |
| **Distributed Ledger**  | Managed Blockchain                        | Fully Managed | Explicit | Provisioned  | Regional  | Stateful  |
| **Omnichannel Comms**   | Connect, Chime/SDK, SES, Pinpoint         | Fully Managed | Implicit | Request/User | Regional  | Stateless |
| **Enterprise SaaS**     | AppFabric, WorkMail, WorkDocs             | Fully Managed | Manual   | User/Month   | Regional  | Stateful  |
| **VDI / Cloud Desktop** | WorkSpaces [Apps, Core, Web], Thin Client | Fully Managed | Explicit | User-based   | Zonal/Reg | Stateful  |

### 9. Migration & Specialized Tech
| Sub-category             | Service Instance                          | Management    | Scaling  | Pricing      | Scope                     | State     |
|:-------------------------|:------------------------------------------|:--------------|:---------|:-------------|:--------------------------|:----------|
| **Migration Planning**   | App Discovery / Migration Hub             | Fully Managed | Implicit | Usage        | Regional                  | Stateless |
| **Data/App Migration**   | MGN (App Migration), DMS                  | Fully Managed | Explicit | Provisioned  | Regional                  | Stateless |
| **Legacy Modernization** | Mainframe Modernization                   | Fully Managed | Manual   | Provisioned  | Regional                  | Stateful  |
| **Physical Transfer**    | Snow Family [Snowball, SB Edge]           | Physical      | Manual   | Fixed/Usage  | Local $\rightarrow$ Cloud | Stateful  |
| **Online Transfer**      | DataSync / Transfer Family                | Fully Managed | Implicit | Volume       | Regional                  | Stateless |
| **IoT Management**       | IoT Core, Greengrass, Device Defender/Mgr | Serverless/FM | Implicit | Request/Vol  | Reg/Local                 | Stateful  |
| **Industrial IoT**       | SiteWise, TwinMaker, FleetWise            | Fully Managed | Implicit | Volume       | Regional                  | Stateful  |
| **Media Production**     | Elemental [All], Nimble Studio, IVS       | Fully Managed | Explicit | Provisioned  | Regional                  | Stateful  |
| **Quantum Computing**    | Braket                                    | Fully Managed | Manual   | Execution    | Regional                  | Stateless |
| **Satellite Comms**      | Ground Station                            | Fully Managed | Manual   | Antenna-time | Regional                  | Stateless |
