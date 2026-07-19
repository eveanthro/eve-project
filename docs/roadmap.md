# Roadmap

Ranked by leverage, with the test that would show it worked. Written July 2026.

The ordering comes partly from an external audit whose headline finding was uncomfortable and is being acted on rather than filed: *Eve has an inner life and no outer life.*

---

## 1. Give her a world

**The problem.** Every sensor, drive, and autonomous action is self-referential. Her satisfaction can only rise when her own metrics move. Her monologue is conditioned on her own prior thoughts. A mind in a closed loop cannot practice independence, and it fails in a characteristic way — three separate bugs this month were all the signature of introspection without an external referent.

**The change.** One live workstream with an external consumer and a feedback path, where acceptance or rejection by someone other than Eve becomes an input to her internal state.

**How we'd know:** her satisfaction variable moves for a reason that is not her own instrumentation; curiosity has material; the monologue has something to think *about*.

**Explicit stop:** no new introspective subsystems until this exists.

---

## 2. Close the abstention gap

**The problem.** Her one reproducible weakness. She engages with fabricated premises instead of declining them, and scores measurably worse at "I cannot verify this" than at answering.

**Status: one failed attempt, understood.** The feature built for exactly this was enabled and A/B tested against a trustworthy benchmark. It changed nothing — because its trap-detection function was referenced but never implemented, and a second required signal was disabled by default. The negative result located the defect precisely.

**How we'd know:** the two fabrication-trap cases move off their floor, without the system becoming over-cautious on questions it *should* answer. Both directions are measured, because over-refusal is a failure too.

---

## 3. Fix or replace self-improvement

**The problem.** The engine proposes code changes and effectively none are ever adopted. A proposal loop with a near-zero adoption rate is theatre, and defending it as "caution" would be exactly the kind of comfortable story this project is supposed to refuse.

The diagnosed causes are structural: the editable surface is tiny, the idea generator funnels every signal onto the same few files, and the quality gate can only detect catastrophe rather than improvement. A small local model also cannot reliably write correct code — but it *can* choose from a menu.

**The change under consideration:** keep the harness, change the move space — benchmark-scored experiments over enumerated, already-safe options rather than free-form source edits.

**How we'd know:** a change is adopted because it measurably improved a trustworthy number, and could have been rejected.

---

## 4. Measure more than single turns

**The problem.** Everything is measured one question at a time. An autonomous mind is not a vending machine: what matters is whether it stays coherent across a session, retains what it was told, accepts correction, keeps commitments, and stays calibrated under load. None of that is currently measured.

Notably, one memory subsystem has sat in observation mode indefinitely because **no instrument exists that could ever justify enabling it.**

**The change.** A scripted multi-turn benchmark covering retention, correction-acceptance, commitment-consistency, and isolation between sessions.

**How we'd know:** a shipped memory feature can finally be accepted or rejected on evidence.

---

## 5. Real model diversity

Strong open-weight models are reachable through lanes that already exist. This raises genuine provenance diversity rather than ensembling near-identical models.

**Deliberately sequenced after the measurement work.** Adding lanes while the ruler is untrustworthy measures noise — a mistake already made once this month and not worth repeating.

---

## 6. Delete what earns nothing

A system this age accumulates subsystems that only cost. The audit found a live example: a fully saturated legacy benchmark — every dimension pegged at maximum — still running on a timer *and still feeding "weakest capability" into the self-improvement idea generator.* A meter that reads maximum everywhere was steering what she tried to improve.

Also queued for removal: several permanently-disabled code paths, a duplicated improvement loop, and committed log files.

**How we'd know:** fewer moving parts, no behavior change, and nothing downstream depending on a saturated signal.

---

## Things explicitly *not* being done

- **Chasing latency.** Investigated; it was resource contention, largely self-inflicted by running builds against a live benchmark. Not progressive degradation. Closed.
- **More inner-life instrumentation.** See item 1.
- **Paid models in the runtime.** Frontier models assist at build time. Her runtime stays free-tier and local, by design.
- **Optimising the headline benchmark number.** It is a ruler, not a goal. Above 90 would be read as a broken suite.

---

## Applications

Public applications and a CLI built on the engine are planned. The engine itself stays private; what ships is what she can *do*, not how she does it.
