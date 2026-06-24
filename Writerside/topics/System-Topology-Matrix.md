# System Topology Matrix

*Focus: The external state of the infrastructure and the path to resiliency.*

| Quad | Coordinates <BR>{Temporal nature,<BR> Composition,<BR> Behavior} | Classification            | Mandate      | Failure as            |
|:-----|:-----------------------------------------------------------------|:--------------------------|:-------------|:----------------------|
| 1    | Static,<BR> Homogeneous,<BR> Predictable                         | Deterministic Reliability | Avoidance    | An Anomaly            |
| 2    | Static,<BR> Homogeneous,<BR> Volatile                            | Systemic Fragility        | Containment  | A Catalyst            |
| 3    | Static,<BR> Heterogeneous,<BR> Predictable                       | Static Complexity         | Precision    | A Config Error        |
| 4    | Static,<BR> Heterogeneous,<BR> Volatile                          | Stochastic Chaos          | Triage       | An Inevitability      |
| 5    | Dynamic,<BR> Homogeneous,<BR> Predictable                        | Managed Elasticity        | Optimization | A Scaling Event       |
| 6    | Dynamic,<BR> Homogeneous,<BR> Volatile                           | Uniform Volatility        | Redundancy   | Background Frequency  |
| 7    | Dynamic,<BR> Heterogeneous,<BR> Predictable                      | Orchestrated Diversity    | Abstraction  | An Abstraction Leak   |
| 8    | Dynamic,<BR> Heterogeneous,<BR> Volatile                         | Probabilistic Resiliency  | Invariance   | An Invariant Property |


**The Deterministic Mindset (Q1, Q3, Q5)**
*   **Topology Focus:** Reliability, Precision, Optimization.
*   **Dominant CCM Constructs:** `Standard`, `Truth/Axiom`, `Model`.
*   **Cognitive Mode:** **Deductive $\rightarrow$ Institutionalized**.
*   **Epistemic Logic:** "The system is a machine with known parts; if we follow the **Standard** and maintain the **Axiom** of reliability, failure is an anomaly to be avoided."
*   **Failure Mode:** When these engineers encounter Q4 or Q8, they suffer from **Dogma**. They try to apply "Hardening" to a system that requires "Invariance," leading to systemic fragility.

**2. The Reactive Mindset (Q2, Q4, Q6)**
*   **Topology Focus:** Containment, Triage, Redundancy.
*   **Dominant CCM Constructs:** `Heuristic`, `Guess`, `Stereotype`.
*   **Cognitive Mode:** **Inductive $\rightarrow$ Orthodox**.
*   **Epistemic Logic:** "The system is volatile; we rely on **Heuristics** (fast shortcuts) and **Guesses** to contain the blast radius. We use **Stereotypes** of previous failures to triage current incidents."
*   **Failure Mode:** These engineers often get stuck in the **"Decay Path."** They stop building Models and start relying entirely on Heuristics, leading to "Expert Manual Intervention" (Q4) rather than systemic evolution.

**3. The Resilient Mindset (Q7, Q8)**
*   **Topology Focus:** Abstraction, Invariance.
*   **Dominant CCM Constructs:** `Heresy`, `Model`, `Intuition`.
*   **Cognitive Mode:** **Inductive/Deductive $\rightarrow$ Peripheral**.
*   **Epistemic Logic:** "Failure is an invariant property of the system. We must use high-resolution **Models** to build self-healing loops and embrace the **Heresy** of Chaos Engineering (intentionally breaking the system) to prove invariance."
*   **Failure Mode:** These engineers risk drifting into **Myth**. If they trust the "Self-healing" abstraction too much, they lose sight of the physical reality, leading to "Abstraction Leaks" (Q7).
