# FT: Sync vs. Async

Yes – the move from *synchronous* fault‑tolerance (think checkpoint‑restart on a fixed set of compute nodes) to *asynchronous* fault‑tolerance, resilience, disaster recovery and high‑availability in the cloud and micro‑service world forced a new way of thinking about operations.  In that environment “reliability” became an *engineering discipline* rather than a side‑effect of manual job scheduling, and that is what gave birth to the SRE (Site Reliability Engineering) model.

Below I unpack why that happened, what it looks like in practice, and how the roles and responsibilities differ between the two worlds.

## 1.  “Sync” vs. “Async” – The core difference {collapsible="true"}

| Aspect               | HPC / Grid (synchronous)                                                                                                              | Cloud / Micro‑services (asynchronous)                                                                                            |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| **State**            | Global checkpoints; the entire job is paused, a snapshot is written, and only after a node recovers does the job resume.              | State lives in many independent services; recovery happens by re‑routing traffic, restarting containers, or replaying events.    |
| **Failure handling** | Manual (or semi‑automatic) resubmission of a job after a node fails; often requires operator intervention to decide where to restart. | Automated self‑healing: orchestrators (K8s, ECS) detect a failing pod, spin up a new one, or move traffic to a healthy instance. |
| **Consistency**      | Strong (global) – you must have the whole system in a consistent state before you can continue.                                       | Eventual or partial – individual services may be out of sync, but the system as a whole is designed to tolerate that.            |
| **Scale**            | Hundreds to low‑thousands of nodes, usually in a single data centre.                                                                  | Tens of thousands to millions of containers spread across many regions and clouds.                                               |
| **Change cadence**   | Low – big releases are infrequent, scheduled during maintenance windows.                                                              | High – continuous delivery / Git‑Ops, hot‑fixes in minutes, blue‑green or canary releases.                                       |

Because the cloud/micro‑service stack is *distributed* and *dynamic*, failures are no longer isolated to a single node but can cascade across dozens of services. That makes “fault‑tolerance” an *asynchronous* property: you cannot pause the whole system and wait for a node to come back up.  Instead, you design the system so that *any* failure can be detected and mitigated without stopping other parts of the application.

## 2.  Why that creates a new skill set  {collapsible="true"}

| Challenge                      | HPC / Grid Ops                                                         | Cloud/Micro‑service Ops                                                                                                     |
|--------------------------------|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Observability**              | Simple metrics: job queue length, node health.                         | Hundreds of metrics per service (latency, error rate, request volume), logs, traces – all need to be correlated.            |
| **Automation**                 | Schedulers (SLURM, PBS) + scripts to restart jobs.                     | Orchestrators (Kubernetes, ECS), CI/CD pipelines, infrastructure‑as‑code, automated rollback.                               |
| **Failure models**             | “Node dies” → restart job from checkpoint.                             | “Pod crashes”, “service becomes overloaded”, “network partition”, “partial data loss” – each requires a different response. |
| **Scale of human involvement** | One or two ops engineers per cluster, manual intervention is the norm. | Ops teams are small compared to development; they need to trust automation and focus on *policy* (SLOs, error budgets).     |
| **Reliability as a metric**    | “Jobs finished on time” or “no data loss”.                             | Service Level Objectives (SLOs) for latency, availability, error‑budget usage.                                              |

In a synchronous HPC/Grid environment, the “fault” is usually *one node* and the recovery path is well‑defined.  In an asynchronous cloud stack, a failure can be *any* part of a complex graph of services.  The traditional Ops mindset—“watch the node, restart it if it dies”—doesn’t scale.  What you need is a *policy‑driven, metrics‑first approach* that can automatically decide what to do and when.

## 3.  Enter SRE – a discipline born of those needs  {collapsible="true"}

### 3.1 What does an SRE do?

| Responsibility                       | Description                                                                                                              |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Define SLOs/SLIs**                 | Translate business expectations into measurable service level objectives (e.g., 99.95% request success, <200ms latency). |
| **Build observability**              | Instrument code for metrics, logs, traces; set up dashboards, alerts, and anomaly detection.                             |
| **Automate recovery**                | Write “self‑healing” logic: health checks, auto‑scaling, graceful degradation, retries, circuit breakers.                |
| **Capacity & cost planning**         | Model load, forecast scaling needs, and balance reliability with budget (error‑budget economics).                        |
| **Incident response & post‑mortems** | Run blameless post‑mortems, capture “lessons learned”, and drive continuous improvement.                                 |
| **Chaos engineering**                | Intentionally inject failures (latency, network drops) to validate resilience.                                           |
| **Policy & compliance**              | Define and enforce data‑retention, DR plans, and regulatory requirements.                                                |

### 3.2 Why the *explicit* emphasis on reliability engineering?

| Reason                               | Explanation                                                                                   |
|--------------------------------------|-----------------------------------------------------------------------------------------------|
| **Reliability is a product feature** | Users expect 99.9% uptime; it’s no longer an after‑thought.                                   |
| **Scale demands automation**         | You can’t manually monitor thousands of services; you need code‑driven policies.              |
| **Rapid change cadence**             | Continuous delivery means every commit can affect reliability; SREs enforce safety nets.      |
| **Complex failure surfaces**         | Asynchronous failures are harder to spot; observability + automated remediation is essential. |
| **Business risk**                    | Downtime costs money; having a formal reliability discipline reduces financial exposure.      |

In the HPC/Grid world, reliability was *implicitly* achieved by the architecture (checkpointing, batch scheduling) and a small ops team.  In the cloud world, reliability is *explicitly* engineered: you write code to detect failures, you set thresholds for error budgets, and you hold developers accountable for meeting SLOs.

## 4.  Practical differences in the day‑to‑day  {collapsible="true"}

| Task                  | HPC / Grid Ops                                                   | Cloud/Micro‑service SRE                                                                                 |
|-----------------------|------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Job failure**       | Manual resubmit, maybe after a checkpoint is created.            | Auto‑restart, blue‑green deploys; if the failure rate exceeds an error budget, a rollback is triggered. |
| **Scaling**           | Manual resource allocation (add more nodes to the cluster).      | Auto‑scaling groups, spot‑instance bidding, canary releases.                                            |
| **Monitoring**        | Cluster‑wide metrics dashboards; manual alerting on node health. | Service‑level dashboards, SLO dashboards, anomaly alerts that trigger automated scripts.                |
| **Disaster recovery** | Offline tape backup; manual site‑to‑site replication.            | Cross‑region data replication, continuous snapshots, automated failover orchestrated by the platform.   |
| **Security**          | Static configuration of compute nodes; patching via OS updates.  | Immutable containers, rolling updates, continuous security scanning integrated into the CI/CD pipeline. |

## 5.  The cultural shift {collapsible="true"}

| Culture           | HPC/Grid                                | Cloud/Micro‑services                                                                     |
|-------------------|-----------------------------------------|------------------------------------------------------------------------------------------|
| **Ownership**     | Ops owns the cluster, devs own the job. | Devs write reliability‑aware code; SREs own the service’s uptime.                        |
| **Feedback loop** | Long, scheduled maintenance windows.    | Short, continuous feedback via SLO dashboards and error‑budget alerts.                   |
| **Collaboration** | Ops ↔ devs, mostly on a per‑job basis.  | SRE ↔ devs, with shared responsibility for reliability (e.g., “SLO‑first” design).       |
| **Tooling**       | Custom scripts, batch job schedulers.   | Standard observability stacks (Prometheus/Grafana, OpenTelemetry), CI/CD pipelines, IaC. |

The result is that *reliability engineering* becomes a **core product function** in the cloud, rather than an after‑thought that only kicks in when something breaks. That is why we see dedicated SRE teams, SLO‑first development practices, and a whole ecosystem of tools built around observability and automated recovery.

## 6.  Bottom line

- **HPC/Grid ops** rely on *synchronous* fault‑tolerance: checkpoint/rollback, manual job resubmission, and a relatively small set of failure scenarios.  Reliability is baked into the architecture but not explicitly engineered.
- **Cloud/micro‑service ops** rely on *asynchronous* fault‑tolerance: self‑healing, auto‑scaling, distributed state.  Reliability becomes a *software engineering problem* that must be measured, automated, and continuously improved.

Because the latter environment is more dynamic, distributed, and failure‑prone, it demanded a new discipline—SRE—to manage reliability systematically. That is why we see an explicit emphasis on “Reliability Engineering” in the cloud world and not (or less so) in traditional HPC/Grid environments.
