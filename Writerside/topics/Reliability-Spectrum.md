# Reliability Spectrum

## Concepts and Properties

| Concept               | Scope of Failure            | Goal                                            |
|-----------------------|-----------------------------|-------------------------------------------------|
| **Fault Isolation**   | Localized component         | Containment                                     |
| **Fault Tolerance**   | Localized component         | Prevention of disruption                        |
| **High Availability** | Broad (including component) | Minimizing downtime, high uptime                |
| **Resilience**        | Broad (including component) | Quick recovery from failures                    |
| **Disaster Recovery** | Large-scale (site outage)   | Restoration of service after catastrophic event |


| Concept               | Synchronous?     | Automation/Coupling | Human In The Loop  | Restorative |
|-----------------------|------------------|---------------------|--------------------|-------------|
| **Fault Isolation**   | ✅ (strong)       | ✅ (high)            | ❌ (low-medium)     | ❌           |
| **Fault Tolerance**   | ✅ (strong)       | ✅ (high)            | ❌ (low-medium)     | ✅           |
| **High Availability** | ❌ (mostly async) | ✅ (medium-high)     | ❌ (low-medium)     | ✅           |
| **Resilience**        | ⚪ (mix)          | ✅ (medium-high)     | ⚪ (policy tuning)  | ✅           |
| **Disaster Recovery** | ❌ (async)        | ⚪ (low)             | ✅ (human approval) | ✅           |

## When to Pick Which Strategy

| Business Goal                                                    | Recommended Concept(s) |
|------------------------------------------------------------------|------------------------|
| Reduce the blast radius of failures and prevent cascading issues | **Fault Isolation**    |
| Zero‑downtime, data correctness on every request                 | **Fault Tolerance**    |
| Continuity under load spikes + ability to recover from failures  | **Resilience**         |
| Recover after a catastrophic site failure, minimal data loss     | **Disaster Recovery**  |
| Keep a service online with minimal latency, tolerate node churn  | **High Availability**  |

## Relationship Between System Concepts

| Concept                    | Description                                                                                                                                        |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **Fault Tolerance**        | A technique used to achieve high availability by preventing failures from causing system downtime.                                                 |
| **Resilience**             | A broader concept than fault tolerance, encompassing strategies for dealing with *all* failures, including those not prevented by fault tolerance. |
| **Disaster Recovery (DR)** | A subset of business continuity planning, focused on restoring systems after a major disruptive event.                                             |

| Concept                    | Definition / Core Idea                                                                                        | Relationship / Additional Notes                                                                                                           |
|----------------------------|---------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **Fault Isolation**        | Separating system components so that a failure in one part does not spread to others.                         | Essential for effective fault tolerance; limits the scope of a failure, enabling it to be tolerated.                                      |
| **Fault Tolerance**        | Techniques that allow a system to continue operating in the presence of faults (e.g., redundancy, fail‑over). | A tool for achieving high availability; contributes to resilience but does not cover all failure scenarios.                               |
| **Resilience**             | The overall ability of a system to anticipate, absorb, recover from, and adapt to failures.                   | Broader than fault tolerance; includes strategies for failures that fault tolerance cannot prevent or handle.                             |
| **High Availability (HA)** | The design goal of keeping a system operational most of the time.                                             | Uses fault‑tolerant components plus monitoring, alerting, and rapid recovery procedures.                                                  |
| **Disaster Recovery (DR)** | A subset of business continuity planning focused on restoring data and services after a major event.          | Requires broader strategies (data backup, site fail‑over) beyond fault tolerance; fault tolerance can aid DR but is not sufficient alone. |

## 1.  What the words actually mean {collapsible="true"}

| Term                       | Core idea                                                                                                                                      | Typical focus                                                 |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| **Fault Isolation**        | The system *fails safely* rather than failing catastrophically.                                                                                | Rapid detection, scope limitation, rollback mechanisms.       |
| **Fault Tolerance**        | The system *continues to operate correctly* when one or more components fail.                                                                  | Zero‑downtime, built‑in redundancy (spares, hot‑standby).     |
| **High Availability (HA)** | The system is designed so that *downtime is very small* (usually measured in milliseconds to minutes).                                         | Redundancy, rapid fail‑over, load balancing.                  |
| **Resilience**             | The system can *adapt to a wide range of adverse conditions* (failures, load spikes, network partitions) and still deliver acceptable service. | Self‑healing, graceful degradation, dynamic re‑configuration. |
| **Disaster Recovery (DR)** | The ability to *restore service after a catastrophic event* (data center outage, natural disaster, ransomware).                                | Backup/replication, RTO/RPO planning, recovery procedures.    |


| Term                  | What you *build*                               | What you *measure*                      | Where it is most critical                          |
|-----------------------|------------------------------------------------|-----------------------------------------|----------------------------------------------------|
| **Fault tolerance**   | Redundant components, automatic fail‑over code | “Zero downtime” for a specific failure  | HPC simulation jobs, cloud microservices           |
| **High availability** | Standby servers, load balancers, health checks | Uptime percentage (e.g., 99.999%)       | Web‑apps, SaaS platforms                           |
| **Resilience**        | Self‑healing architecture, adaptive scheduling | Recovery time after *any* adverse event | Distributed microservices, edge computing          |
| **Disaster recovery** | Backups, cross‑region replication, DR plans    | RTO/RPO goals                           | Enterprise data stores, critical business services |

## 2.  How the four concepts show up in the three “forms” of distributed computing {collapsible="true"}

| Trait                 | HPC Cluster                                                                                                                                                                                        | Grid Computing                                                                                                                                                                | Cloud Computing                                                                                                                                                                                                                                                                                                                                     |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Fault tolerance**   | •Checkpoint/restart: jobs periodically save state to shared storage. •Spare nodes (hot or cold) that replace failed compute nodes without user intervention. •MPI fault‑tolerant libraries (ULFM). | •Job resubmission on other sites when a resource fails. •Data replication across multiple sites (Globus data transfer). •Resource broker detects dead nodes and removes them. | •Multi‑AZ or multi‑region deployment of stateless services. •Auto‑scaling groups with health checks that replace unhealthy instances. •Managed services (RDS, DynamoDB) provide built‑in replication and failover.                                                                                                                                  |
| **High availability** | •Cluster manager (SLURM, PBS) can fail‑over to a standby controller. •Compute nodes are in a shared‑nothing configuration, so one node’s failure doesn’t bring down the whole cluster.             | •Grid middleware (Globus, ARC) runs a standby “grid‑broker” in each federation. •Load‑balancing of user portals across multiple sites.                                        | •Elastic Load Balancer (ELB) or Application Gateway distributes traffic to healthy instances. •Automatic DNS fail‑over (Route 53, CloudFront) to keep services reachable. •Multi‑AZ RDS with synchronous replication.                                                                                                                               |
| **Resilience**        | •Dynamic job scheduling: if a node fails, the scheduler reallocates unfinished work to other nodes. •Adaptive resource management: increase compute capacity during a spike.                       | •Federation of grids can “shift” workloads to other federations when one is overloaded or offline. •Data replication across sites gives read‑scale resilience.                | •Microservice architecture: each service can restart independently; circuit breakers prevent cascading failures. •Auto‑scaling, spot‑instance replacement, and graceful shutdowns allow the system to keep running during maintenance or traffic surges. •Chaos engineering (Gremlin, Chaos Mesh) deliberately injects failures to test resilience. |
| **Disaster recovery** | •Off‑site backup of checkpoint files and job logs. •Physical migration of the cluster to a secondary site (rare but possible).                                                                     | •Data replication across continents; long‑term archival of datasets. •Cross‑site job migration to recover from a site failure.                                                | •Backups of databases (RDS snapshots, DynamoDB point‑in‑time recovery). •Multi‑region replication of storage (S3 cross‑region replication, EBS snapshots). •Recovery Point Objective (RPO) and Recovery Time Objective (RTO) defined in SLAs. •Disaster‑recovery drills using services such as AWS CloudFormation StackSets or Azure Site Recovery. |

> **Take‑away** – All four concepts are present, but the *implementation* and *severity of failures they target* differ.

---

## 3.  Trait “fingerprints” – what makes each concept unique in a given environment {collapsible="true"}

| Concept               | What it looks like on **HPC**                                                                                            | What it looks like on **Grid**                                                                                                        | What it looks like on **Cloud**                                                                                                           |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **Fault tolerance**   | *Zero‑downtime* for long‑running simulations: checkpoint/restart keeps a job alive even if a node dies.                  | *Graceful job resubmission*: the grid middleware automatically re‑queues jobs on healthy sites.                                       | *Zero‑downtime stateless services*: health checks replace failed instances instantly.                                                     |
| **High availability** | *Cluster‑wide uptime*: a standby head node takes over if the active one fails.                                           | *Federated HA*: multiple grid portals, each with a local broker; traffic is load‑balanced.                                            | *Elastic load balancers* and *multi‑AZ deployments* keep web apps reachable even if an AZ goes down.                                      |
| **Resilience**        | *Adaptive scheduling*: the scheduler can move jobs to spare nodes when a node fails or is taken offline for maintenance. | *Federation shift*: workloads can be shifted to a different federation if one is overloaded or offline.                               | *Microservice self‑healing*: circuit breakers and retries let services recover from transient failures without human intervention.        |
| **Disaster recovery** | *Off‑site checkpoint backup*: in case the entire facility is lost, jobs can be resumed on a secondary site.              | *Cross‑continent data replication*: the grid keeps copies of data in multiple federations so a regional disaster doesn’t wipe it out. | *Cross‑region replication* and *automatic backups*: a data loss in one region can be recovered from another region’s copy within the RTO. |

## 4.  Bottom line

> **Fault isolation** and **fault tolerance** are *techniques*,   
> **Resilience** is a *property* of the whole system,   
> **High availability** is a *quantitative measure*, and   
> **Disaster recovery** is a *process* that kicks in only after a catastrophic event.

In any distributed system you’ll need to decide which of these concepts (or all of them) are required by the workload and then choose the right mix of hardware, software, and operational practices to deliver it.
