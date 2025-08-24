# Dichotomies

### Dependability vs Resiliency

Robustness denotes a system’s ability to preserve acceptable performance and reliability amid variations in design parameters, operating conditions, environmental factors, or faults. This capability is realized through `Dependability` and `Resilience`. Dependability is the degree to which a system can be trusted to perform its intended functions without failure. Resiliency is the capacity of a system to absorb disturbances, recover rapidly from faults or adverse conditions, and continue operation with minimal degradation.

Dependability
: Prevention & safe operation under normal conditions

Resiliency
: Recovery & continuity under disruption

### Resiliency vs Robustness

`Dependability` and `Resiliency` provide the foundational trustworthiness and recovery capability that underpin `Robustness`; additional design elements such as fault‑tolerance, adaptive control, and performance stability under variability must also be incorporated to achieve true robustness. `Resiliency` and `Robustness` overlap in graceful degradation (dropping functionality gracefully), but their primary goals differ: resiliency → recovery; robustness → performance resilience. Robustness is the ability of a system to maintain acceptable performance across a wide range of operating conditions, including variations and uncertainties, resisting functional degradation.

Resiliency
: is about continuity and rapid recovery after an event

Robustness
: concerns sustaining performance under stress.

### Repeatability vs Reproducibility

Conventional manufacturing relies on repeatable, cost‑efficient production of standardized goods. Discovery‑oriented work, by contrast, embraces uncertainty and iterative learning cycles to create systems that address complex, evolving needs. Its guiding principle is reproducibility—ensuring outcomes are robust and transferable across contexts.

Repeatability
: is the consistency of results obtained when an experiment or measurement is repeated under identical conditions by the same operator using the same equipment

Reproducibility
: is the consistency of results achieved when independent researchers repeat the experiment under varying conditions or with different equipment, thereby demonstrating that the findings are generalizable beyond a single laboratory setting.


### Acceptance vs Mitigation

In formal safety assessment, one first states the assumptions about potential hazards; the second step is to decide whether to `accept` those residual risks or to implement controls that `mitigate` them.

Acceptance
: A formally documented decision to retain the residual risk that remains after initial hazard identification and control measures. The risk is judged to be within acceptable limits—whether defined by organisational tolerance, regulatory thresholds, or a cost‑benefit analysis—and no further action is deemed necessary beyond monitoring.

Mitigation
: The systematic implementation of control measures—engineering, procedural, administrative or safety‑instrumentation changes—intended to reduce the residual risk below the established acceptable threshold. Mitigation actions are selected, designed, and validated to improve safety performance before acceptance is considered.
