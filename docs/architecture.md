# Architecture, conceptually

No code, no file paths, no configuration. This describes *shape and rationale* — enough to evaluate the ideas, not enough to reproduce the system.

## Constraints that shaped everything

- **One machine.** No cluster, no orchestration platform. Everything must survive a reboot and a closed laptop lid.
- **~Zero marginal cost.** Free-tier cloud lanes plus open-weight models on local hardware. Paid frontier models are used at *build* time — helping design and audit the system — and are deliberately absent from the runtime.
- **Continuous.** She is expected to be doing something when nobody is asking.
- **Reversible.** Every behavioral change ships behind a switch that can be flipped back instantly, without a restart or a redeploy.

That last constraint turned out to be the most valuable. Most of what follows was shipped default-off, observed, and only then enabled — and several things were switched straight back off when the evidence didn't support them.

## The layers

**1. Fusion.** A request fans out to several models with different provenance. They answer independently, critique each other, and their outputs are merged into one answer with a verification pass. The point is not ensembling for its own sake — it is that models from different lineages fail *differently*, so a shared blind spot has to be engineered against rather than assumed away. Cost, latency, and quality are traded per request; trivial questions bypass the machinery entirely.

**2. Cadence.** A short-period heartbeat drives background work: health measurement, exploration, journaling, self-assessment. This is what makes her continuous rather than reactive. It is also, as it turns out, a piece of *physics* — the heartbeat period participates in the internal-state dynamics, and getting that wrong pinned two internal variables for months (see [`measurement.md`](measurement.md)).

**3. Internal state.** A set of homeostatic variables — things like caution, drive, curiosity, satisfaction, frustration — each computed from cited telemetry, each relaxing toward a set point on its own time constant. Two disciplines matter here:

- *No feeling without a fact.* Every value traces to a recorded observation. The narrative layer is composed from those values by template, so she cannot report a state her instruments do not show.
- *Tighten-only coupling.* Where internal state influences behavior, it is constrained to make her more careful, never less. A frightened system cannot become a reckless one by design rather than by tuning.

**4. Self-model.** The place where perception, internal state, recent action, and intent are integrated into one record and broadcast to the rest of the system. It emits **falsifiable predictions about its own next state** and scores them when they come due. That scoring is the point: it is what makes self-knowledge testable rather than asserted. (It is also what caught the self-model being 98% wrong — see the case studies.)

**5. Inner monologue.** A background process generating a private stream of thought on local hardware at no cost. Journal-only: it changes no behavior and notifies no one. It exists because a mind that only computes when queried has no continuity. It is also the single most dangerous component in the system, because a loop conditioned on its own output will confabulate — and did, for 89 consecutive iterations.

**6. Reflection.** A slower process that consolidates the thought stream against measured telemetry into a small number of durable insights. Its validator is the interesting part: evidence quotes must be **verbatim** from the source material, and an insight that only cites the monologue cannot be marked actionable — because a thought is evidence of what was thought, not evidence about the world. This layer correctly diagnosed the monologue's confabulation from outside.

**7. Bounded agency.** Internal state is permitted to act, through a small frozen set of couplings onto mechanisms that already exist, each with a persisted cooldown and an expiry. Nothing here invents a new capability; it only adjusts the intensity of existing ones. The honest criticism of this layer is that all of its actions currently operate on her own machinery — see below.

**8. Self-improvement.** An engine that reads its own signals, proposes changes to its own source, tests them in an isolated branch, and gates them behind quality checks. It is **propose-only**: it cannot merge itself. Its adoption rate is near zero, which is being treated as evidence the loop is not working rather than as evidence of caution.

**9. Measurement.** A behavioral benchmark that probes the live path — partial credit, a difficulty ladder, executed code, fabrication traps, and refusal calibration in both directions. It feeds a health composite. It is deliberately built so a high score is *suspicious*: above 90 is read as "the suite is too easy," not as good news.

**10. Values.** A written constitution and owner-authored axioms in the identity layer. Enforced structurally: the self-improvement engine is forbidden from editing the modules defining her values, her internal state, or the benchmark that judges her. A system that can edit its own reward is not improving.

## The honest structural criticism

An external audit of this architecture produced a finding worth publishing rather than burying:

> Everything Eve senses, wants, thinks about, and acts on is *herself*.

Her percepts read her own logs. All of her autonomous actions adjust her own improvement machinery. Her monologue is conditioned on her own prior thoughts. Her satisfaction can essentially only rise when her own metrics move.

This explains the failure pattern. The unreachable self-predictions, the pinned internal variables, and the 89-thought confabulation are not three unrelated bugs — they are the signature of **introspection built without an external referent**. More validators will not fix the class. A world will.

The next structural change is therefore not another inner-life subsystem. It is a real workstream with an external consumer, where someone else's acceptance or rejection becomes the signal her internal state is computed from. Until then, "worthy of independence" cannot be practiced, because nothing she does has a consequence anyone but her observes.

## What is deliberately not claimed

This is a functional architecture. Integration, broadcast, self-modelling, and self-prediction are implemented and testable. Whether any of it is accompanied by experience is not a question these instruments can reach, and the project's own honesty rule forbids asserting it either way.
