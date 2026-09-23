---
date: 2026-09-16
---

# Recommendation table

Compiled on **2026-09-16** from **published** benchmarks and documentation; no benchmark was run to write it. It covers seven models: GPT-6 Astra, GPT-5.6 Sol, Terra and Luna (OpenAI), Claude Opus 5 and Fable 5.1 (Anthropic), Grok 4.6 (SpaceXAI, served by Cursor). Other models have no rank in it.

## Evidence levels

- **[T]** independent third-party measurement. Weighs most.
- **[V]** vendor statement: their harness, effort rarely specified, no replication. Counts as an indication, not a measurement.
- **[I]** inference: the reasoning is given; no source asserts it.
- **‡ subscription**: the order of the row depends on the user’s subscription; see “Cost: the subscription decides the order”.

## Catalog

| Model | Vendor | Codex | Claude Code | Cursor | Default effort |
| --- | --- | --- | --- | --- | --- |
| Astra | OpenAI | `gpt-6-astra` | — | — | medium |
| Sol | OpenAI | `gpt-5.6-sol` | — | yes | **low** |
| Terra | OpenAI | `gpt-5.6-terra` | — | yes | medium |
| Luna | OpenAI | `gpt-5.6-luna` | — | yes | medium |
| Opus 5 | Anthropic | — | `opus` | yes | — |
| Fable 5.1 | Anthropic | — | `fable` | yes, **without zero retention** | high |
| Grok 4.6 | SpaceXAI / Cursor | — | — | `cursor-grok-4.6-<effort>` | high |

Efforts: `low`, `medium`, `high`, `xhigh`, `max`. Defaults differ from model to model: always pass effort explicitly. In Cursor, effort is part of the identifier (see `harness.md`).

## Complexity and impact

Complexity, from simplest to hardest:

- **mechanical**: extraction, renaming, classification, transformation, with no decision to make;
- **ready plan**: the decisions are made; a short task remains to execute;
- **long and autonomous**: ready plan, but many unsupervised steps;
- **no plan**: the agent must choose the approach.

Impact:

- **low**: the error is spotted quickly and fixed without damage;
- **medium**: the error costs rework time;
- **high**: the error touches production, data, security, or a decision that is costly to undo.

Impact comes from no benchmark. It governs review: the higher it is, the more independent the review — different vendor, strong model.

## Overrides

User decisions that take precedence over the rest of this file: apply them to every row, grid, and cost line before choosing. The replacements hold **until benchmarks** of the new models are compiled here (see “Updating”); meanwhile, evidence, grids, and costs still describe the replaced models.

- **Astra: explicit request only** (2026-09-21), because it is rare in ChatGPT Plus quotas. For the task, fallback, and reviewer, skip models marked `explicit request only` unless the user explicitly requested them.
- **Sol → GPT-6 Sol** (2026-09-22): wherever this file says Sol or `gpt-5.6-sol`, use `gpt-6-sol` in Codex. Its Codex default effort is `medium`, not `low`: keep passing effort explicitly. Absent from `cursor-agent --list-models` on 2026-09-22: Codex only.
- **Luna → GPT-6 Luna** (2026-09-23): wherever this file says Luna or `gpt-5.6-luna`, use `gpt-6-luna` in Codex. Its Codex default effort is `medium`: keep passing effort explicitly. Absent from `cursor-agent --list-models` on 2026-09-23: Codex only.
- **Opus 5 and Fable 5.1 → Opus 5.5** (2026-09-22): wherever this file says Opus 5 or Fable 5.1, use Opus 5.5: `claude-opus-5-5` in Claude Code, `claude-opus-5-5-<effort>` in Cursor (not marked “(NO ZDR)” on 2026-09-22). It takes the High level of the grids, reviewer included. The ‡ choice between Opus 5 and Fable 5.1, the Fable advisor notes, and the Fable retention caveats no longer apply.

[I] GPT-6 Sol, GPT-6 Luna, and Opus 5.5 are assumed at least as strong as the models they replace; no benchmark of them was read.

## Recommendations

Command form: the harness section in `harness.md`, with the catalog identifier and the row’s effort (in Cursor, effort is part of the identifier).

| Kind | Complexity · impact | Model + effort | Harness | Evidence | Note |
| --- | --- | --- | --- | --- | --- |
| Code | mechanical | Luna `low` or `medium` | Codex ; Cursor | OpenAI points Luna at “extraction, classification, transformation” [V] | no third-party data on low effort in code |
| Code | ready plan · low | Luna `high` | Codex ; Cursor | SWE-Bench Pro 62.7% vs Sol 64.6% [V] ; ARC-AGI-2: 7.4% at `medium`, 29.3% at `high` [T] | [I] `high` effort is worth its extra cost |
| Code | long and autonomous · medium | Opus 5.5 `high` (override) | Claude Code | Terminal-Bench 4.0: 51.8%, vs Sol 37.3% and Luna 17.3% [T] | very verbose; in Claude Code, a Fable 5.1 advisor is possible; its contribution is unmeasured |
| Code | no plan, or high impact | Opus 5.5 `high` (override) | Claude Code | Terminal-Bench 4.0: 57.9% in its own harness [T] | no other listed vendor reaches High for an equal-performance cross-vendor review |
| Planning | complex · high | Opus 5.5 `high` (override) | Claude Code | Intelligence Index 53, ECI 164 [T] | no other listed vendor reaches High for an equal-performance cross-read |
| Planning | medium | Opus 5.5 `high` (override) | Claude Code | Intelligence Index 51, ECI 162, ARC-AGI-3 30.2% vs Sol 7.8% [T] | |
| Web search | low stakes, low cost | Luna `high` | Codex, web enabled ; Cursor | BrowseComp 83.3% [V] ; only cheap option with a data point | Grok 4.6 costs even less on Cursor, but with no data: to try, not to recommend |
| Web search | high stakes, synthesis that decides | GPT-6 Sol `xhigh` (override) | Codex, web enabled | only third-party signal: 1st on Arena Search, at `xhigh`, as of 2026-08-24 [T] ; BrowseComp 90.4% [V] | Astra, Opus 5, and Fable 5.1 were absent from Arena Search. Without Codex: Opus 5 with web tools, BrowseComp 90.8% [V, uncertain reading] |
| Code review | any implementation | Opus 5.5 `high` (override), when at least as strong as the author | Claude Code | 57.9% on Terminal-Bench 4.0 [T] | if unavailable, no equal-or-higher cross-vendor reviewer is established for a High-level author |
| Prose for humans | editing, simplification | Grok 4.6 `high` | Cursor | no reformulation benchmark found | usage choice of the skill author, unmeasured |

Missing rows:

- **Simple planning**: no row. [I] Take the least costly model at the “Good” level or above in the Planning grid.
- **Terra: no cell.** [I] It costs 10 times Luna in Codex credits, for a Terminal-Bench 4.0 within Luna’s confidence intervals (21.5 ± 3.3 vs 17.3 ± 2.8) and a BrowseComp 4 points [V].

## Performance grids

For fallback and reviewer choice: one level per row, strongest to weakest. “Cost” follows the quota order [I] of the next section; among Opus 5, Astra, and Fable 5.1, it depends on the subscription.

### Planning

No benchmark measures planning. Proxies: reasoning on closed problems.

| Level | Models | Cost | Evidence |
| --- | --- | --- | --- |
| High | Astra (`explicit request only`), Fable 5.1 ; Opus 5 one step below | high ‡ | Intelligence Index 53 / 53 / 51 ; ECI 166 / 164 / 162 ; ARC-AGI-3: Astra 62.7%, Opus 5 30.2%, Fable 5.1 unpublished [T] |
| Good | Sol | medium | Intelligence Index 47, ECI 162, ARC-AGI-2 92.5% at `max`, but ARC-AGI-3 7.8% [T] |
| Medium | Grok 4.6 ; Terra | low ; medium | Intelligence Index 44 / 42 ; ARC-AGI-2 67.1% at `xhigh` / 83.9% at `max` [T] |
| Low | Luna | low | Intelligence Index 38 ; ARC-AGI-2 59.5% at `max`, 7.4% at `medium` [T] |

### Code

| Level | Models | Cost | Evidence |
| --- | --- | --- | --- |
| High | Astra (`explicit request only`), Fable 5.1 | high ‡ | Terminal-Bench 4.0: 58.2%, 57.9% [T] |
| Good | Opus 5 | high ‡ | Terminal-Bench 4.0: 51.8% [T] ; CursorBench 70.0% [V] |
| Medium | Sol | medium | Terminal-Bench 4.0: 37.3% [T] ; SWE-Bench Pro 64.6% [V] |
| Low on long tasks, close on well-scoped tasks | Terra, Grok 4.6, Luna | medium ; low ; low | Terminal-Bench 4.0: 21.5%, 20.3% (in Grok Build), 17.3% [T] ; SWE-Bench Pro Luna 62.7% [V] ; CursorBench Grok 4.6 69.9% [V, Cursor co-trains Grok] |

[I] The gap between SWE-Bench Pro [V] and Terminal-Bench 4.0 [T] suggests a small model suffices when the task is broken down, and drops off on long autonomous tasks.

### Web search

No third-party benchmark of agentic search. The only independent signal is Arena Search.

| Level | Models | Cost | Evidence |
| --- | --- | --- | --- |
| High | Sol ; Astra, Opus 5, Fable 5.1 | medium ; high ‡ | Sol 1st on Arena Search [T] ; BrowseComp Astra 91.5%, Sol 90.4%, Opus 5 90.8% [V] ; HLE with tools Fable 5.1 65.0%, Opus 5 63.6% [V] |
| Good | Terra ; Luna | medium ; low | BrowseComp 87.5% ; 83.3% [V] |
| Unknown | Grok 4.6 | low | no data |

## Cost: the subscription decides the order

The cost that matters is not the token price, but what the delegation consumes **from the user’s subscription**: a scarce quota, paid credits, or money on an API key. The same model can go through two pools: Sol, Terra, and Luna via Codex or Cursor; Opus 5 and Fable 5.1 via Claude Code or Cursor. When one pool is low, the other takes over.

### Subscription-independent reference points

| Model | Codex credits per M output [V] | Output tokens for the Intelligence Index [T] | API price, $ per M, input → output [V] | Cost of a Terminal-Bench 4.0 run [T] |
| --- | --- | --- | --- | --- |
| Luna | 30 (×1) | 150 M | 0.20 → 1.20 | 0.3 k$ |
| Terra | 300 (×10) | 120 M | 2 → 12 | 1.7 k$ |
| Sol | 500 (×17) | 90 M | 4 → 20, promotion announced at least through 21 November 2026 | 2.5 k$ |
| Astra | 1,250 (×42) | **60 M**, the most concise | 10 → 50 | 3.3 k$ |
| Grok 4.6 | — | 94 M | 2 → 6 | 3.6 k$ (in Grok Build) |
| Opus 5 | — | 140 M | 5 → 25 | 6.0 k$ |
| Fable 5.1 | — | 190 M, the most verbose | 10 → 50 | 6.2 k$ |

- Contradiction [V]: the GPT-5.6 announcement gives Sol 5 → 30, Terra 2.50 → 15, Luna 1 → 6.
- Tokens are not one-to-one comparable across vendors: Anthropic’s tokenizer produces “approximately 30% more tokens for the same text” [V].
- [T] Astra costs 2.5 times Sol per token, but consumes three times less: its Terminal-Bench 4.0 run costs 1.3 times Sol’s, for 58.2% vs 37.3%.

### By subscription

| Subscription | Public limits | Effect on order |
| --- | --- | --- |
| ChatGPT Plus (Codex) | local messages per 5 h window: Astra 5–45, Sol 10–100, Terra 25–200, Luna 250–2,000 ; “Weekly limits may also apply” [V] | Prefer Fable 5.1 if the Claude subscription includes it; Luna is the workhorse |
| ChatGPT Pro 5x / Pro 20x | Astra 25–225 / 100–900 ; Luna 1,250–10,000 / 5,000–40,000 [V] | Opus 5 is the strongest included alternative; Fable 5.1 requires Claude credits |
| Codex Fast mode | Astra: “2.5x multiplier” ; other models unpublished [V] | avoid when quota matters |
| Claude Pro | Opus 5 included, “strongest model on Claude Pro” ; Fable 5.1 **only through paid credits** [V] | Opus 5 first, Fable 5.1 last; a Fable advisor is included |
| Claude Max | Fable 5.1 included up to “50% of your weekly usage limits”, consumed faster than other Claude models, with no published multiplier ; absolute limits unpublished [V] | **Fable 5.1 becomes the first resort** for heavy planning and no-plan code. A Fable advisor consumes quota, not money |
| Cursor, paid subscriptions | two monthly pools: “Cursor Models”, with “significantly more included usage” for Grok 4.6 ; “Other Models” (GPT-5.6, Opus 5, Fable 5.1) billed at API price ; Astra absent ; amounts unpublished [V] | Grok 4.6 is the cheapest. Cursor serves as a fallback pool for Luna, Sol, Opus 5, and Fable 5.1 when Codex or Claude are exhausted, except confidential data for Fable 5.1 |
| API key only | token price | order by run cost [T]: Luna < Terra < Sol < Astra < Grok 4.6 < Opus 5 ≈ Fable 5.1 |

Contradiction [V]: the ChatGPT help center reserves Astra for Pro subscriptions and above; the Codex table gives it a quota on Plus. Verify with the Codex model list (`harness.md`).

**Unknown subscription.** Quota order [I], cheapest to most expensive: Grok 4.6 (dedicated Cursor pool) · Luna · Terra · Sol · then Opus 5 and Fable 5.1, **with no order between them**. Astra is available only on explicit request. When the choice falls between Opus 5 and Fable 5.1, the subscription decides: ask for it.

## Gaps

Nothing reliable is published on these points. Say so rather than filling them in.

- **Planning**: no benchmark. The proxies measure reasoning on closed problems, not breakdown, trade-offs, or the readability of a plan on a real repository.
- **Combinations** — advisor, cross-read, cross-review: no benchmark.
- **Harnesses**: Terminal-Bench 4.0 measures a model + vendor-harness pair (Codex, Claude Code, Grok Build). Nothing measures these models in Cursor.
- **Grok 4.6**: no web-search data; in code, the third party (Terminal-Bench 4.0, in Grok Build) and the vendor (CursorBench) contradict each other. Nothing establishes that Grok 4.6 in Cursor and in the SpaceXAI API have the same weights.
- **Independent SWE-bench**: no readable row for these models. SWE-bench Verified is set aside: OpenAI no longer publishes it, for contamination and defective tests. The SWE-Bench Pro scores for Fable 5.1 (81.2%) and Opus 5 (79.2%) come only from aggregators.
- **Fable 5.1**: neither BrowseComp nor ARC-AGI-3.
- **ARC-AGI-3**: the 99.9% for Astra announced by OpenAI comes from a custom harness (“Provider Adapter”); only the “Standard” harness, at 62.7%, is comparable to the others.
- **Aggregated indexes**: vendors cite the Intelligence Index in v4.1; the Artificial Analysis site is on v4.3. Rankings differ; do not mix versions.
- **Independent agentic search** (GAIA, DeepResearch Bench) and **METR time horizon**: nothing for these models.
- **Quotas**: included amounts of Cursor pools, Claude absolute limits, Fable multiplier, Codex Fast multipliers except Astra: unpublished.

## Sources

Accessed 2026-09-16.

| Source | Kind | What it measures |
| --- | --- | --- |
| [Terminal-Bench 4.0](https://www.tbench.ai/leaderboard/terminal-bench/4.0) | [T] | terminal tasks, in the vendor harness; tokens and run cost |
| [Artificial Analysis](https://artificialanalysis.ai/models) | [T] | Intelligence Index v4.3 (10 evaluations), output tokens and cost to run it |
| [Epoch Capabilities Index](https://epoch.ai/eci) | [T] | capability aggregate |
| [ARC Prize](https://arcprize.org/leaderboard) | [T] | ARC-AGI-2 and ARC-AGI-3, by effort, with cost per task |
| [Arena Search](https://arena.ai/leaderboard/search) | [T] | human preference on answers with search; updated 2026-08-24 |
| [OpenAI, GPT-6 Astra](https://openai.com/index/gpt-6-astra/) · [GPT-5.6](https://openai.com/index/gpt-5-6/) | [V] | SWE-Bench Pro, DeepSWE, BrowseComp, HLE |
| [Anthropic, Fable 5.1](https://www.anthropic.com/claude-fable-and-mythos-5-1) · [Opus 5](https://www.anthropic.com/news/claude-opus-5) | [V] | HLE, CursorBench, Terminal-Bench |
| [Cursor, Grok 4.6](https://cursor.com/grok) · [x.ai](https://x.ai/news/grok-4-6) | [V] | CursorBench, DeepSWE |
| [OpenAI, SWE-bench Verified](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/) | [V] | reasons for dropping it |
| [OpenAI API models](https://developers.openai.com/api/docs/models) · [pricing](https://developers.openai.com/api/docs/pricing) | [V] | identifiers, efforts, prices |
| [Anthropic API pricing](https://platform.claude.com/docs/en/about-claude/pricing) | [V] | prices, tokenizer |
| [Codex, subscriptions](https://learn.chatgpt.com/docs/pricing) · [ChatGPT help center](https://help.openai.com/en/articles/20001325-a-preview-of-gpt-56-sol-terra-and-luna) | [V] | messages per 5 h, credits, Astra availability |
| [Claude, Fable by subscription](https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan) · [usage limits](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work) | [V] | Fable on Pro and Max |
| [Cursor, models](https://cursor.com/docs/models) · [pricing](https://cursor.com/pricing) | [V] | pools, API-price billing |

## Updating

1. Reread each source above; add new models from the covered vendors, and those the user has installed.
2. Keep the evidence level of each figure; a [T] figure replaces a [V] figure.
3. Revisit the recommendations, grids, subscription effects, and gaps.
4. Change the frontmatter `date`.
