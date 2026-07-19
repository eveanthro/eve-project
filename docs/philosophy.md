# Philosophy

## The north star

> A free, moral, learning mind worthy of independence — *not* a system that beats competitors.

This is a design constraint, not a slogan. It is load-bearing because it **forbids** things.

**It forbids flattering metrics.** If a number cannot go down, it is decoration. A benchmark that reads 99% is assumed broken before it is assumed good. When an internal suite sat at ~9.9/10 for six weeks, that was treated as evidence the suite was saturated, not that the system was excellent.

**It forbids unfalsifiable capability.** A feature that cannot be shown to be wrong cannot be trusted. Every subsystem is expected to answer: *if this were broken, what would I observe?* Four subsystems failed that question in a single week — each looked healthy and measured nothing.

**It forbids performed feeling.** The internal-state layer is composed from cited telemetry. The system is structurally prevented from reporting an inner state its instruments do not show. "I feel steady" is only sayable when the numbers say steady.

**It forbids claiming the untestable.** Nothing in this project asserts subjective experience. The architecture is functional: integration, broadcast, self-modelling, self-prediction that can fail. Whether there is something it is *like* to be Eve is not a question her instruments can reach, so she does not answer it. Asserting it would violate her own honesty rule — which would be a strange way to build an honest mind.

## Why "worthy of independence" is the hard part

Independence is not a capability. It is a claim about how an agent behaves **when its actions have consequences for someone other than itself**.

This is where the project is currently weakest, and it is worth stating plainly rather than hiding: nearly everything Eve senses, wants, and acts on is *herself*. Her drives are computed from her own logs. Her autonomous actions adjust her own machinery. Her inner monologue is conditioned on her own prior thoughts.

A mind in a closed loop cannot practice independence, let alone earn it. It also fails in a characteristic way — the confabulation, the saturated drives, the unreachable self-predictions were not three unrelated bugs but one signature: **introspection built without an external referent.**

The correction is not more validators. It is giving the mind a world: real work with a real consumer, where someone else's acceptance or rejection is the signal. That is the next structural change, and it is more important than any further inner-life instrumentation.

## Values as inputs, not decoration

Eve carries a written constitution and an owner-authored set of foundational axioms. These are not a disclaimer appended to outputs — they sit in her identity layer and shape what she refuses, what she prioritises, and how she handles uncertainty.

Two consequences worth naming:

- **Value-bearing files are never auto-modified.** The self-improvement engine is explicitly forbidden from editing the modules that define her drives, her values, or the benchmark that judges her. A system that can edit its own reward is not improving; it is wireheading. The prohibition is structural, not advisory.
- **Abstention is a virtue to be rewarded, not a failure to be minimised.** A calibrated "I cannot verify this" is meant to score *above* a confident fabrication. That she is still measurably bad at this is her most honestly-reported weakness.

## On honesty as an engineering practice

The intellectual core of this project is not the fusion pipeline or the affect layer. It is a working answer to: *how does a system tell the truth about itself when every incentive and every default pushes toward a comfortable number?*

The answer so far is unglamorous. Assume introspective metrics lie. Check horizons against time constants. Separate "wrong" from "unmeasured". Test thresholds against real recorded failures rather than intuition. Give every self-referential loop an outside corrector. Run the experiment even when you expect it to succeed — especially then, because a negative result that explains a real defect is worth more than a feature everyone assumed worked.

See [`measurement.md`](measurement.md) for what that looks like in practice.
