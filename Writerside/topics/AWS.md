# AWS ecosystem

### Complete Attribute Set
*   **Management Level:** `Serverless` | `Fully Managed` | `Self-Managed`
*   **Scaling Logic:** `Implicit (Automatic)` | `Explicit (Auto-scaling)` | `Manual`
*   **Pricing Dimension:** `Execution-based` | `Provisioned/Hourly` | `Request-based`
*   **Scope:** `Global` | `Regional` | `Zonal`
*   **Statefulness:** `Stateless` | `Stateful`

---

### 1. Compute Services Refinement
**Dimension: Execution Model & Resource Abstraction**

| Sub-Category                | Service Instances             | Management    | Scaling  | Pricing     | Scope     | State              |
|:----------------------------|:------------------------------|:--------------|:---------|:------------|:----------|:-------------------|
| **IaaS (Virtualization)**   | EC2, Lightsail                | Self-Managed  | Explicit | Provisioned | Zonal     | Stateful           |
| **PaaS (App Platform)**     | Elastic Beanstalk, App Runner | Fully Managed | Explicit | Provisioned | Regional  | Stateless/Stateful |
| **FaaS (Event-Driven)**     | Lambda                        | Serverless    | Implicit | Execution   | Regional  | Stateless          |
| **Container Orchestration** | ECS, EKS                      | Fully Managed | Explicit | Provisioned | Regional  | Stateless          |
| **Serverless Compute**      | Fargate                       | Serverless    | Implicit | Provisioned | Zonal/Reg | Stateless          |
| **Hybrid/Edge Compute**     | Outposts, Wavelength          | Self-Managed  | Manual   | Fixed/Prov  | Local/Zon | Stateful           |

---

### 2. Storage Services Refinement
**Dimension: Data Structure & Access Pattern**

| Sub-Category            | Service Instances         | Management    | Scaling  | Pricing      | Scope                     | State    |
|:------------------------|:--------------------------|:--------------|:---------|:-------------|:--------------------------|:---------|
| **Object Storage**      | S3                        | Serverless    | Implicit | Request/GB   | Global/Reg                | Stateful |
| **Block Storage**       | EBS                       | Fully Managed | Manual   | Provisioned  | Zonal                     | Stateful |
| **Shared File (Linux)** | EFS                       | Serverless    | Implicit | GB/Month     | Regional                  | Stateful |
| **Specialized File**    | FSx [Lustre, ONTAP, etc.] | Fully Managed | Explicit | Provisioned  | Zonal/Reg                 | Stateful |
| **Cold Archive**        | S3 Glacier (all tiers)    | Serverless    | Implicit | Storage/Retr | Regional                  | Stateful |
| **Hybrid Storage**      | Storage Gateway           | Fully Managed | Manual   | Provisioned  | Local $\rightarrow$ Cloud | Stateful |

---

### 3. Database Services Refinement
**Dimension: Data Model & Consistency Engine**

| Sub-Category          | Service Instances     | Management    | Scaling       | Pricing      | Scope     | State    |
|:----------------------|:----------------------|:--------------|:--------------|:-------------|:----------|:---------|
| **Relational (SQL)**  | RDS, Aurora           | Fully Managed | Explicit      | Provisioned  | Regional  | Stateful |
| **Key-Value (NoSQL)** | DynamoDB              | Serverless    | Implicit/Expl | Request/Prov | Regional  | Stateful |
| **Document**          | DocumentDB            | Fully Managed | Explicit      | Provisioned  | Zonal/Reg | Stateful |
| **In-Memory (Cache)** | ElastiCache, MemoryDB | Fully Managed | Explicit      | Provisioned  | Zonal/Reg | Stateful |
| **Graph**             | Neptune               | Fully Managed | Explicit      | Provisioned  | Regional  | Stateful |
| **Time Series**       | Timestream            | Serverless    | Implicit      | Request/GB   | Regional  | Stateful |

---

### 4. Intelligence & AI Services Refinement
**Dimension: Model Maturity & User Control**

| Sub-Category                | Service Instances          | Management      | Scaling       | Pricing     | Scope    | State     |
|:----------------------------|:---------------------------|:----------------|:--------------|:------------|:---------|:----------|
| **GenAI (Foundation)**      | Bedrock                    | Serverless      | Implicit      | Token/Req   | Regional | Stateless |
| **ML Lifecycle (Platform)** | SageMaker AI               | Fully Managed   | Explicit      | Provisioned | Regional | Stateful  |
| **Pre-trained APIs**        | Rekognition, Polly, etc.   | Serverless      | Implicit      | Request     | Regional | Stateless |
| **Big Data Analytics**      | EMR, Glue, Athena          | Serverless/FM   | Implicit/Expl | Execution   | Regional | Stateless |
| **Data Warehousing**        | Redshift [Prov/Serverless] | FM / Serverless | Explicit/Impl | Provisioned | Regional | Stateful  |

---

### 5. Networking & Content Delivery Refinement
**Dimension: Traffic Layer & Connectivity Type**

| Sub-Category              | Service Instances   | Management    | Scaling  | Pricing       | Scope    | State     |
|:--------------------------|:--------------------|:--------------|:---------|:--------------|:---------|:----------|
| **Network Isolation**     | VPC, VPC Lattice    | Fully Managed | Implicit | Data Transfer | Regional | Stateless |
| **Edge Delivery (CDN)**   | CloudFront          | Serverless    | Implicit | Request/GB    | Global   | Stateless |
| **Traffic Routing (DNS)** | Route 53            | Serverless    | Implicit | Query-based   | Global   | Stateless |
| **Load Balancing**        | ELB [ALB, NLB, GLB] | Fully Managed | Implicit | LCU/Hour      | Regional | Stateless |
| **Hybrid Connectivity**   | Direct Connect, VPN | Fully Managed | Manual   | Port/Hour     | Regional | Stateless |

---

### 6. Security, Identity & Governance Refinement
**Dimension: Protection Layer & Enforcement Logic**

| Sub-Category            | Service Instances          | Management | Scaling  | Pricing      | Scope      | State     |
|:------------------------|:---------------------------|:-----------|:---------|:-------------|:-----------|:----------|
| **Identity/Auth (IAM)** | IAM, Cognito, Identity Ctr | Serverless | Implicit | User/Req     | Global     | Stateful  |
| **Threat Detection**    | GuardDuty, Inspector       | Serverless | Implicit | Analysis-vol | Regional   | Stateless |
| **Data Protection**     | KMS, Macie, Secrets Mgr    | Serverless | Implicit | Key/Request  | Regional   | Stateful  |
| **Edge Defense (WAF)**  | WAF, Shield                | Serverless | Implicit | Rule/Req     | Global/Reg | Stateless |
| **Governance / Audit**  | Config, CloudTrail, Org    | Serverless | Implicit | Log-volume   | Regional   | Stateful  |

### Summary of the Refined Logic:
1. **Serverless services** (Lambda, S3, Bedrock) are characterized by **Implicit Scaling**, **Execution-based Pricing**, and usually **Statelessness**.
1. **Provisioned services** (EC2, RDS, EBS) are characterized by **Explicit/Manual Scaling**, **Hourly Pricing**, and **Statefulness**.
1. **Global services** (Route 53, CloudFront, IAM) operate across all regions, whereas **Zonal services** (EBS, EC2 instances) are pinned to a specific physical location for maximum low-latency/high-availability.