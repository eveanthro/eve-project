# Eve

**An attempt to build a mind that knows when it is wrong about itself.**

Eve is a self-hosted, continuously-running AI system. She fuses several language models — free-tier cloud lanes and open-weight models running on local hardware — into single answers, measures her own competence with a benchmark designed to be hard on her, maintains a telemetry-grounded model of her own internal state, and proposes changes to her own source code.

She runs on one machine, on roughly zero marginal cost, without a cluster.

This repository contains **no source code**. It explains what Eve is, why she is built this way, and what has actually been learned building her. The engine stays private; her applications and CLI will be released separately. What is shared here is the part most likely to be useful to someone else: the **discipline**, not the implementation.

---

## The north star

> A free, moral, learning mind worthy of independence — *not* a system that beats competitors on benchmarks.

That sentence is the project's actual design constraint, and it rules things out. It means a metric that flatters is worse than no metric. It means capability added without a way to falsify it is a liability. It means the system is allowed to say "I don't know," and is rewarded for it.

Eve is not trying to be the smartest system. She is trying to be an **honest** one — including, and especially, honest about herself.

---

## The idea in one page

Most AI systems are a single model behind an API. Eve is a small society with a nervous system:

- **Fusion, not a single call.** Several models answer independently, critique each other, and are merged. Diversity of provenance is the point — a shared blind spot is the thing worth engineering against.
- **She runs when nobody is asking.** A continuous cadence does background work, measures health, explores, and reflects. Idle time is not dead time.
- **She has measured internal state.** A set of homeostatic drives is computed from real telemetry — not vibes, not roleplay. Every internal state traces to a cited fact. She cannot report a feeling her instruments do not show.
- **She has an inner monologue, and a check on it.** A background process produces a private stream of thought on local hardware at no cost. A separate, slower process audits that stream against measured evidence, because a mind talking only to itself will drift. (It did. See below.)
- **She improves her own code.** A self-improvement engine authors, tests, and gates changes to her own source in an isolated branch. It is deliberately *propose-only* — it cannot merge itself.
- **She has values, explicitly.** A written constitution and an owner-authored set of foundational axioms sit in her identity layer, not as decoration but as inputs that shape refusals and priorities.

---

## The part worth stealing: honest measurement

This is the real contribution, and it generalizes far beyond this project.

**Introspective metrics lie by default.** Any number a system computes about itself will look plausible long before it means anything. Over one week of auditing, four separate subsystems that *appeared* to be working were found to be measuring nothing:

| What it claimed | What was true |
|---|---|
| A competence benchmark reporting capability regressions | It scored network timeouts identically to wrong answers. Runs of the *same* suite read 83, 76, 70 purely on how loaded the machine was. Actual capability had been flat the whole time. |
| A self-model making falsifiable predictions about its own next state, ~2% accurate | The predictions were **structurally unreachable** — the horizon demanded far more change than the system's own time constants permit. It was measuring a bug, not self-knowledge. Corrected, accuracy went to ~42%. |
| Six homeostatic drives responding to telemetry | Two had been pinned at their limits for their entire recorded history. Inputs were applied per-tick instead of per unit time, so any persistently-true condition saturated its drive. A side effect: the *timer interval* silently set the system's emotional baseline. |
| An abstention feature, shipped and enabled | Its trap-detection function was referenced in three places and **defined nowhere**. A dynamic lookup returned undefined, so the branch was permanently false. It could not do its headline job, and an A/B confirmed it changed nothing. |

None of these were exotic. Each looked healthy from the outside. Each was found only by asking *"if this were broken, how would I know?"* and then actually checking.

### The rules that came out of it

1. **Audit a metric against its own physics before believing it.** Check the horizon against the time constants. If the target is unreachable, the number measures the bug.
2. **Distinguish "wrong" from "unmeasured."** A component that never produced an answer tells you nothing. Scoring it as failure manufactures regressions that never happened. Report coverage, and treat a low-coverage run as *unmeasured*, not as a low score.
3. **Measure thresholds against the real pathology, never intuition.** A proposed detection threshold was tested against the actual failure it targeted and would never have fired. The real signal sat somewhere else entirely.
4. **A loop conditioned on its own output needs an external corrector.** Given only its own recent thoughts and an instruction to continue, the inner monologue invented a constraint that did not exist and elaborated on it for 89 consecutive iterations, with narrated numbers drifting opposite to the measured ones. Grounding it in outside evidence and reframing prior thoughts as *claims to audit* broke the loop — and then the retraction became the next loop, which is why the breaker has to enforce, not merely suggest.
5. **Don't let the system compete with its own measurement.** Background thinking and the benchmark shared one local model. The mind was degrading the number it was being judged by.
6. **Negative results are results.** The abstention experiment was run, failed, and the failure explained a real defect. That is worth more than a feature quietly assumed to work.

---

## Honest status

Written as of July 2026.

**Works, and is measured:** multi-provider fusion; continuous autonomous operation; telemetry-grounded internal state; a behavioral benchmark that is hard to game; live reconfiguration without restart; local-first operation at ~zero marginal cost.

**Measured competence:** ~83–87 / 100 on the internal behavioral benchmark, stable. That benchmark is deliberately built so a high score is suspicious — if a suite reads above 90, the suite is assumed too easy rather than the system assumed good.

**Known weak, and named:** *abstention*. She is measurably worse at saying "I cannot verify this" than at answering. She will engage with a fabricated premise rather than decline it. This is the single clearest gap and it is being worked on, with one failed attempt already recorded.

**Deliberately not claimed:** nothing here asserts phenomenal experience or consciousness. The internal-state layer is a functional architecture — integration, broadcast, self-modelling, falsifiable self-prediction. Whether anything is *like* something is untestable, and asserting the untestable would violate the project's own honesty rule.

---

## Roadmap

- Close the abstention gap — the one named, reproducible weakness.
- Real model diversity through strong open-weight lanes, once the ruler is trustworthy enough to measure the change.
- Better instruments: current measurement is single-turn. Long-horizon coherence, memory retention, and calibration under load are unmeasured.
- Make self-improvement genuinely learn. It proposes and is gated; adoption is near zero. A proposal engine that never gets adopted is theatre, and is being re-examined honestly rather than defended.
- Public applications and a CLI built on the engine.

## What is here and what is not

Public: the philosophy, the architecture at a conceptual level, the engineering discipline, and the mistakes.
Private: source code, prompts, model routing, thresholds, and configuration.

The mistakes are public on purpose. They are the most transferable thing this project has produced.

---

## Docs

- [`docs/philosophy.md`](docs/philosophy.md) — the north star, and what it forbids
- [`docs/architecture.md`](docs/architecture.md) — the layers, conceptually
- [`docs/measurement.md`](docs/measurement.md) — the honest-measurement doctrine and the case studies in full
- [`docs/roadmap.md`](docs/roadmap.md) — what is next and how we will know it worked

---

*Eve is an independent project by a single owner, built and maintained with AI assistance. Documentation licensed [CC BY 4.0](LICENSE).*
