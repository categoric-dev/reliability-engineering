# Pillars of Software Scaling

## Dichotomies That Slice Through the Spectrum

| Dichotomy                                | What it separates                                                 | Where Async & Reactive sit                                                                                                                                     |
|------------------------------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Imperative vs Declarative**            | *What you do* (imperative) vs *what you want* (declarative).      | Reactive → Declarative; Async can be used in both, but its non‑blocking nature is a *concurrency* trait rather than a declarative one.                         |
| **Synchronous vs Asynchronous**          | Blocking calls vs non‑blocking calls.                             | Async → Asynchronous; Reactive is *usually* asynchronous but can wrap synchronous sources (e.g., `Mono.fromCallable`).                                         |
| **Blocking vs Non‑Blocking**             | Operations that block a thread vs operations that don’t.          | Async → Non‑blocking; Reactive → Non‑blocking (via event loops).                                                                                               |
| **Thread‑Based vs Scheduler/Event‑Loop** | Use of OS threads for work vs single‑threaded event loop.         | Async → Thread‑based (unless using virtual threads). Reactive → Scheduler/event‑loop.                                                                          |
| **Back‑pressure vs No Back‑pressure**    | Ability to ask “how many items do you want?” vs no such contract. | Reactive → Back‑pressure; Async (plain `Future`) → No back‑pressure.                                                                                           |
| **Stateful vs Stateless**                | Components that keep internal mutable state vs purely functional. | Reactive streams are often *stateless* (each element flows through operators), but you can add stateful operators. Async callbacks may hold state in closures. |
| **Local vs Distributed**                 | All code runs on a single machine vs across multiple nodes.       | Both can be local or distributed; Reactive streams are often used in micro‑service pipelines, Async I/O is used everywhere.                                    |
