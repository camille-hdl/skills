---
date: 2026-09-24
---

# Recommendation table

Compiled on **2026-09-24** from **published** benchmarks and documentation; no benchmark was run to write it. It ranks GPT-6 Astra, Sol and Luna (OpenAI), Claude Opus 5.5 (Anthropic), and Grok 4.7 (SpaceXAI, served by Cursor). GPT-5.6 Terra and Claude Fable 5.1 remain installed but have no recommended cell. Older versions remain selectable in some CLIs; they are not ranked here.

## Evidence levels

- **[T]** independent third-party measurement. Weighs most; a measured agent is still a model **plus a harness**.
- **[V]** vendor statement or vendor-run evaluation. Effort and harness may differ; no independent replication implied.
- **[I]** inference or usage choice: the reasoning is given; no benchmark directly asserts it.
- **No data** means no published result for that model and task was found; it is not a zero score.

Percentages from different benchmarks, efforts, and harnesses are not interchangeable. Differences of a few points can be run-to-run noise.

## Catalog

Checked against `codex debug models`, `cursor-agent --list-models`, and `claude --help` on 2026-09-24. Cursor's listed identifiers, rather than API IDs, are the invocation source of truth.

| Model | Vendor | Codex | Claude Code | Cursor | Default effort |
| --- | --- | --- | --- | --- | --- |
| Astra | OpenAI | `gpt-6-astra` | — | — | medium |
| Sol | OpenAI | `gpt-6-sol` | — | — | medium |
| Luna | OpenAI | `gpt-6-luna` | — | — | medium |
| Opus 5.5 | Anthropic | — | `claude-opus-5-5` | `claude-opus-5-5-<effort>` | medium [V] |
| Grok 4.7 | SpaceXAI / Cursor | — | — | `grok-4.7-<effort>` | high [V] |
| Terra, no recommended cell | OpenAI | `gpt-5.6-terra` | — | `gpt-5.6-terra-<effort>` | medium |

Codex supports `low`, `medium`, `high`, `xhigh`, `max` (and `ultra` for some models); pass effort explicitly. Opus 5.5 supports `low` through `max`; Grok 4.7 supports `low` through `xhigh`. Cursor also lists `-fast` variants; use the identifier **without** `-fast` to conserve its pool. GPT-6 Sol and Luna were absent from Cursor's list on this date. See `harness.md` for CLI permissions and web access. [OpenAI models](https://developers.openai.com/api/docs/models), [Anthropic Opus 5.5](https://platform.claude.com/docs/en/models/opus-5-5/overview), [Cursor Grok 4.7](https://cursor.com/docs/models/grok-4-7) [V].

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

Impact comes from no benchmark. It governs review: the higher it is, the more independent the review — different vendor and a capable model.

## Overrides

- **Astra: explicit request only** (user decision, 2026-09-21). Skip it for the task, fallback, and reviewer unless the user explicitly requests it. Its Plus quota is scarce: 5–45 local messages per five-hour window [V].

The previous Sol, Luna, and Opus substitutions are incorporated into the catalog, recommendations, grids, and costs below. Their replacements now have published measurements; no model substitution remains pending. The preference for Grok on human-facing prose remains unmeasured and is marked [I] in its row.

## Recommendations

Command form: use `harness.md` with the catalog identifier and the row's effort. For example, `codex exec --ephemeral -s workspace-write -m gpt-6-luna -c model_reasoning_effort="max" - < brief.md`; `claude -p --model claude-opus-5-5 --effort high < brief.md`; or `cursor-agent -p -f --sandbox enabled --model grok-4.7-high --output-format text < brief.md`. Use read-only permissions for planning, research, and review. Cursor requires `-f --sandbox enabled` for web or shell in print mode.

| Kind | Complexity · impact | Model + effort | Harness | Evidence | Note |
| --- | --- | --- | --- | --- | --- |
| Code | mechanical | Luna `low` or `medium` | Codex | [I] lowest Codex credit rate; focused high-volume positioning [V] | Check output; no low-effort coding measurement here. |
| Code | ready plan · low | Luna `max` | Codex | Rails feature tickets: 18.3% at `max` vs Sol 21.7% at `medium`, a small gap, for $0.191 vs $0.453 per run [T] | [I] Good for checkable, bounded work; escalate failed or ambiguous tasks. |
| Code | long and autonomous · medium | Opus 5.5 `medium`, escalate to `high` if needed | Claude Code | Rails tickets 33.3% at `medium` [T]; AA Terminal-Bench 4.0 57% at `high` [T] | Default `medium` saves quota. |
| Code | no plan, or high impact | Opus 5.5 `high` | Claude Code | AA Intelligence Index 54 and Terminal-Bench 4.0 57% at `high` [T]; Cognition FrontierCode 54.6%, effort unstated [T] | [I] Raise effort for hard code; review independently. |
| Planning | complex · high | Opus 5.5 `xhigh` | Claude Code | AA Intelligence Index 56 at `xhigh`, 58 at `max` [T] | [I] Reasoning and knowledge-work proxies, not a planning test; cross-read costly decisions. |
| Planning | medium | Opus 5.5 `medium` | Claude Code | AA Index 51 at `medium`; Opus exceeds the other listed non-Astra models at their measured peaks [T] | [I] Medium effort conserves quota; no direct planning score. |
| Web search | low stakes, low cost | Luna `high` | Codex, web enabled | No direct search score for GPT-6 Luna; $0.10/$0.50 per M tokens [V] | [I] Cheapest included Codex choice; verify sources. Grok's Cursor pool may be cheaper in quota, but its search quality is unmeasured. |
| Web search | high stakes, synthesis that decides | Opus 5.5 `high` | Claude Code, `WebSearch,WebFetch` | Parallel Search Intelligence 75.5, first, on 2026-09-22 [T] | [I] Parallel used its own search harness; Claude Code may differ. Sol 6 has no comparable search result. |
| Code review | routine | Opus 5.5 `high` for code by Sol, Luna, Grok, or Astra; independent Opus 5.5 `high` plus Sol `high` for Opus-authored code | Claude Code; Codex | AA Coding Agent Index: Opus 66 in Claude Code, Sol 57 in Codex at `max` [T]; Dam Secure recall: Sol 63.75% vs Opus 56.25% at `high` [T] | [I] Opus supplies the equal-tier primary review; Sol adds a different vendor. The recall test plants only 16 security bugs and cannot rank general review. |
| Code review | security-sensitive | Same primary reviewer as above; add Grok 4.7 `high` for code by OpenAI or Anthropic | Claude Code; Cursor | Grok recalled 77.5% vs Sol 63.75% and Opus 56.25% on 16 planted security bugs, five runs each at `high` [T] | [I] The Grok pass is a specialist check, not an equal-tier replacement for an Opus reviewer. Grok used 282k reasoning tokens and 18m per PR in that test; inspect false positives and the served model. |
| Prose for humans | editing, simplification | Grok 4.7 `high` | Cursor | no reformulation benchmark found | [I] Carried-forward usage preference; judge the output. |

Missing rows:

- **Simple planning**: [I] Use Luna for checkable plans; Sol `high` when the plan requires decisions. No benchmark directly measures plan quality.
- **Terra: no cell.** [I] [Artificial Analysis](https://artificialanalysis.ai/articles/gpt-5-6-has-landed) found the installed GPT-5.6 Terra dominated by its Sol or Luna peers on intelligence versus cost (2026-07-09) [T]; the newer GPT-6 choices strengthen the reason to skip it. This is a cost choice, not a claim that Terra cannot solve a task.
- **Fable 5.1: no cell.** [I] It remains available in Claude Code and Cursor, but Opus 5.5 leads it in the measured Intelligence Index (58 vs 53 at `max`) [T], Coding Agent Index (66.0 vs 62.2) [T], Parallel search (75.5 vs 69.3) [T], and Rails feature tickets (33.3% vs 31.7%, a small gap) [T]. Opus also has lower published API token rates ($4/$20 vs $10/$50) [V]. These comparisons do not prove superiority on every task.

## Performance grids

For fallback and reviewer choice, use measured tiers, then the subscription pools below. Tiers are approximate; a model's position is not proof that it beats every model in a lower tier on every task.

### Planning

No benchmark directly measures planning. [Artificial Analysis Intelligence Index v4.3.2](https://artificialanalysis.ai/models/claude-opus-5-5-medium) combines reasoning and work proxies; the September 2026 results below are from its API harness, not the three agent CLIs [T].

| Level | Models | Cost to this subscriber | Evidence |
| --- | --- | --- | --- |
| High | Opus 5.5; Astra (`explicit request only`) | Claude Max quota; scarce Codex Plus quota | AA Index 58 at Opus `max`, Astra 53 at `max` [T] |
| Good | Sol; Grok 4.7 | Codex Plus; Cursor Models pool | AA Index 48 at Sol `max`, 46 at Grok `xhigh`; Grok uses about 81k output tokens per Index task [T] |
| Medium | Luna | small Codex Plus draw | AA Index 37 at Luna `max` [T] |
| Unranked | Terra | Codex Plus or Cursor Other Models | Its older cost/performance frontier is dominated [T]. |

[ARC Prize's verified results](https://arcprize.org/results/anthropic-claude-opus-5-5) add a reasoning check [T]: on ARC-AGI-2, Opus 5.5 scores 93.3% at `high`, [Astra](https://arcprize.org/results/openai-gpt-6-astra) 95.0% at `max`, and [Luna](https://arcprize.org/results/openai-gpt-6-luna) 59.3% at `max`. ARC-AGI-2 is near saturation for the strongest models; these are not planning scores. On ARC-AGI-3's **standard** harness, Astra scores 62.71% and Luna 0.10% at `max`; Opus 5.5 has no published score. ARC-AGI-3's provider-adapter scores use a different harness and are excluded from this comparison. No current Sol or Grok score was found.

### Code

| Level | Models | Cost to this subscriber | Evidence |
| --- | --- | --- | --- |
| High | Opus 5.5; Astra (`explicit request only`) | Claude Max quota; scarce Codex Plus quota | AA Coding Agent Index: Opus 66.0 in Claude Code, Astra 61.6 in Codex, both at `max` [T]; AA Terminal-Bench 4.0 with mini-swe-agent: both 59.6% (Opus `max`, Astra `xhigh`) [T]; Rails: Opus 33.3% `medium`, Astra 53.3% `max` [T] |
| Good | Sol; Grok 4.7 | Codex Plus; Cursor Models pool | AA Coding Agent Index: Sol 57 in Codex at `max`, Grok 56 in Grok Build at `xhigh` [T]; Rails: Sol 21.7% `medium`, Grok 31.7% `high` [T] |
| Scoped only | Luna | smallest Codex Plus draw | AA Coding Agent Index 41 in Codex at `max`; Rails tickets 18.3% `max` and 11.7% `medium` [T] |
| Unranked | Terra | Codex Plus or Cursor Other Models | No new comparison with the current models. |

AA Coding Agent Index scores measure a model in its **native** harness: Codex, Claude Code, or Grok Build. They do not establish the same result in Cursor. AA's separate Terminal-Bench 4.0 API evaluation uses mini-swe-agent and scores Opus 59.6% at `max`; its Claude Code Coding Agent run scores 63.1% on the Terminal-Bench component [T]. The vendor's Opus figure is 66.4% at `xhigh` [V]; different setups do not establish a reproducible advantage. The vendor's Grok 4.7 figure is 37.6% [V], while AA reports about 33% in Grok Build [T].

[Cognition's FrontierCode leaderboard](https://cognition.com/frontiercode) places Opus 5.5 first at 54.6%, then Astra 53.3%, Sol 49.3%, and Grok 4.7 47.6% [T]; it does not state effort. [Anthropic](https://www.anthropic.com/claude-opus-5-5) identifies its 54.6% result as default `medium` effort [V].

GPT-6 Luna is cheaper, but not uniformly stronger than GPT-5.6 Luna: AA Coding Agent Index falls from 43.2 to 41.1 at `max` while task cost falls about 60% [T]. On Rails tickets, the new Luna rises from 0% to 11.7% at `medium`, but falls from 26.7% to 18.3% at `max` [T]. Its scoped-work recommendation rests on cost and checkability [I].

**Agents on Rails (2026-09-24 snapshot).** Rails' [Stage 2](https://rubyonrails.org/2026/9/9/agents-on-rails-stage-2) uses 20 feature tickets against one Rails app. Its [leaderboard and method](https://rubyonrails.org/ai) run each ticket three times per model and effort in the same minimal shell harness, without internet or agent scaffolding, with 90-minute, 400-step, and $60 caps; the app suite and hidden feature checks must pass. The Stage 2 article describes default-effort runs; the live leaderboard also includes later max-effort runs. Opus 5.5 `medium` scored 33.3%, Grok 4.7 `high` 31.7%, Sol `medium` 21.7%, Luna `max` 18.3%, and Astra `max` 53.3% [T]. A few points are within run-to-run noise. [I] Feature tickets, MVC conventions, repository navigation, and tests transfer conceptually to PHP/Symfony; Ruby APIs, app conventions, hidden checks, and this harness do **not** predict a Symfony pass rate. PHP benchmarks exist: [Laravel's benchmark](https://laravel.com/blog/which-ai-model-is-best-for-laravel) [V, Laravel tests its own Boost], [RuBench's Laravel tasks](https://arxiv.org/abs/2607.06411) [T], and [Octomind's mixed PHP/Symfony repositories](https://octomind.run/blog/coding-agent-benchmark-real-prs) [V for its own agent]. None publishes a head-to-head for these five current models on Symfony.

### Web search

The only current direct third-party search result among the selected models found here is [Parallel's 2026-09-22 leaderboard](https://parallel.ai/leaderboard): a common search/extraction harness on DSQA, HLE, and WISER, not Codex, Claude Code, or Cursor [T]. The older Arena Search lead and BrowseComp numbers concern superseded models; they do not transfer.

| Level | Models | Cost to this subscriber | Evidence |
| --- | --- | --- | --- |
| High in Parallel's harness | Opus 5.5; Astra (`explicit request only`) | Claude Max quota; scarce Codex Plus quota | Search Intelligence 75.5 and 70.8 respectively [T] |
| Unranked | Sol; Luna; Grok 4.7; Terra | Codex Plus; Cursor Models pool; Codex Plus or Cursor Other Models | No directly comparable published search score for these exact models. |

## Cost: the subscription decides the order

Cost assumptions: **ChatGPT Plus (Codex), Claude Max, and Cursor Pro**. The relevant cost is depletion of three separate included pools. API rates are reference points, not a subscriber's direct bill; effort, caching, context, retries, and token use affect cost per completed task.

### Subscription-independent reference points

Standard short-context API prices in dollars per million **input → output** tokens [V]; Codex credits per million output tokens [V]. Prices can rise for long context and fast processing.

| Model | Codex output credits | API input → output | Useful efficiency observation |
| --- | --- | --- | --- |
| Luna | 12.5 (×1) | $0.10 → $0.50 | AA Index task $0.07 at `max`, using 51k output tokens per task [T]. |
| Terra | 300 (×24) | $2 → $12 | Older model, no recommended cell. |
| Sol | 250 (×20) | $2 → $10 | AA Index task $1.06 at `max`, using 31k output tokens per task [T]. |
| Astra | 1,250 (×100) | $10 → $50 | Explicit request only. |
| Grok 4.7 | — | $2 → $6 | AA finds about 81k output tokens per Index task at `xhigh` [T]. |
| Opus 5.5 | — | $4 → $20 | AA Coding Agent Index at `max`: $13.04/task, 21% above Opus 5 [T]; Anthropic reports 40% lower cost at default `medium` effort [V]. |

Prices: [OpenAI API](https://developers.openai.com/api/docs/pricing), [Codex credits](https://learn.chatgpt.com/docs/pricing), [Anthropic](https://www.anthropic.com/claude-opus-5-5), [Cursor](https://cursor.com/docs/models/grok-4-7) [V]. Task token/cost observations: [Artificial Analysis, 2026-09-22](https://artificialanalysis.ai/articles/gpt-6-sol-and-luna-push-the-cost-efficiency-frontier) and [Grok 4.7, 2026-09-21](https://artificialanalysis.ai/articles/benchmarking-grok-4-7) [T]. Different benchmark workloads and tokenizers prevent a direct tokens-per-task ranking across vendors.

### By subscription

| Subscription | Public limits as of 2026-09-24 | Effect on order |
| --- | --- | --- |
| ChatGPT Plus (Codex) | Estimated local messages per 5 h: Luna 350–3,000; Sol 15–150; Astra 5–45. Weekly limits may apply; Fast consumes 2.5× credits [V]. | Luna is the workhorse; Sol is the intermediate tier. Astra remains explicit request only. |
| Claude Max | Opus 5.5 is included; Max 5× or 20× has five-hour and weekly limits shared with Claude Code. Absolute limits and an Opus-specific multiplier are unpublished [V]. | Opus 5.5 is the included high-capability pool; `medium` preserves quota for tasks that pass there. |
| Cursor Pro | Separate monthly **Cursor Models** pool for Grok 4.7, with more included use, and **Other Models** for Opus 5.5 at API rates. Grok standard $2/$6, Fast $4/$12 per M; Fast is the default speed tier on Pro [V]. | Grok can conserve the Other Models pool; select a non-`-fast` identifier when quota matters. Opus in Cursor is a fallback if Claude Max is low. GPT-6 Sol/Luna are absent from the local Cursor list. |
| API key | Usage billed by tokens at published rates [V]. | Separate paid path, outside the three subscriptions. |

[Codex Plus limits](https://learn.chatgpt.com/docs/pricing), [Claude Max limits](https://support.claude.com/en/articles/11049741-what-is-the-max-plan), [Opus availability](https://www.anthropic.com/claude/opus), [Cursor pools](https://prod.cursor.com/help/models-and-usage/usage-limits), [Grok pricing/speed](https://cursor.com/docs/models/grok-4-7) [V]. Check the live usage dashboards before a large delegation; the actual remaining allowance is account-specific.

**Quota order [I].** Within Codex, Luna < Sol < Astra. Grok spends a separate Cursor Models pool; Opus spends Claude Max or Cursor Other Models. There is no defensible single cheapest-to-costliest order across the three subscriptions without their remaining balances and actual task token use.

## Gaps

Nothing reliable is published on these points. Say so rather than filling them in.

- **Planning:** no benchmark tests the quality of a plan for a real repository. AA's Index and agentic-work scores are proxies.
- **Search:** no current Codex/Claude Code/Cursor head-to-head for Sol 6, Luna 6, Opus 5.5, and Grok 4.7. Parallel's search harness is different; the old Arena Search and BrowseComp scores cannot be assigned to replacements.
- **PHP/Symfony:** Rails Stage 2 is relevant but not a Symfony result. Published Laravel and mixed-PHP suites have not tested this full current set; no Symfony-specific head-to-head found.
- **Review:** Dam Secure measures 16 security vulnerabilities, five runs per model at `high`; it is too narrow for a general code-review ranking, and its Grok run used Vercel rather than Cursor.
- **Harnesses:** AA's Coding Agent Index combines native harnesses; Rails uses one shared minimal harness. No published result measures all selected models in the exact CLI setups. Opus 5.5 may automatically fall back to an older Claude model on flagged requests in Claude Code [V].
- **Benchmark quality:** OpenAI estimates about 30% of SWE-bench Pro tasks are broken; an Anthropic internal 478-task subset is nearly saturated and not comparable to its public leaderboard. SWE-bench Verified has known contamination and defective tests. FrontierCode 1.1 restricts solution-bearing internet access, but its rubric includes subjective judgments. Do not rank these models from a few points on those sets.
- **Combinations:** no measured benefit for an advisor, second reviewer, or cross-read on these exact models. Cross-vendor review is an impact rule [I], not a benchmark result.
- **Quotas:** exact Claude Max allowance and model multiplier, Cursor included pool sizes, and actual remaining balances are not public. API cost per token does not establish subscription cost per task.

## Sources

Accessed 2026-09-24. Dates below are publication dates or leaderboard snapshots. The named organization ran the evaluation unless otherwise stated.

| Source | Kind | What it measures |
| --- | --- | --- |
| [Artificial Analysis: GPT-6 Sol/Luna](https://artificialanalysis.ai/articles/gpt-6-sol-and-luna-push-the-cost-efficiency-frontier) (2026-09-22), [Opus 5.5](https://artificialanalysis.ai/articles/claude-opus-5-5) (2026-09-22), [Grok 4.7](https://artificialanalysis.ai/articles/benchmarking-grok-4-7) (2026-09-21), [Coding Agents](https://artificialanalysis.ai/agents/coding-agents) (2026-09-24 snapshot), [Terminal-Bench 4.0](https://artificialanalysis.ai/evaluations/terminalbench-4-0) | [T] | Intelligence Index v4.3.2, native-harness Coding Agent Index v1.5, separate mini-swe-agent Terminal-Bench runs, effort, token use, task cost. |
| [Artificial Analysis: GPT-5.6 family](https://artificialanalysis.ai/articles/gpt-5-6-has-landed) (2026-07-09) | [T] | Terra's intelligence-versus-cost frontier. |
| [Agents on Rails](https://rubyonrails.org/ai) (2026-09-24 snapshot), [Stage 2 method](https://rubyonrails.org/2026/9/9/agents-on-rails-stage-2) (2026-09-09, regraded 2026-09-15) | [T] | Rails feature tickets, shared harness, three runs per ticket and effort. |
| [Parallel Search Capability](https://parallel.ai/leaderboard) (2026-09-22) | [T] | DSQA, HLE, WISER with common Parallel search and extraction. |
| [ARC Prize: Opus 5.5](https://arcprize.org/results/anthropic-claude-opus-5-5), [Luna](https://arcprize.org/results/openai-gpt-6-luna) (2026-09-22), [Astra](https://arcprize.org/results/openai-gpt-6-astra) (2026-09-02) | [T] | Verified ARC-AGI-2 and ARC-AGI-3 scores by effort and harness. |
| [Dam Secure security review](https://docs.damsecure.ai/blog/openai-gpt-6-sol-closes-in-on-deepseek-v4-1-flash-security-benchmark/) (2026-09-24) | [T] | 16 planted vulnerabilities, five reviews per model at high effort. |
| [FrontierCode 1.1](https://cognition.com/frontiercode) (updated 2026-09-22) | [T] for its own runs | Mergeability rubric and tests; excludes solution-bearing web lookups. |
| [OpenAI: Sol and Luna](https://openai.com/index/introducing-gpt-6-sol-and-luna/) (2026-09-22), [API models/prices](https://developers.openai.com/api/docs/models) | [V] | FrontierCode, DeepSWE, AutomationBench claims; model positioning and API prices. |
| [Anthropic: Opus 5.5](https://www.anthropic.com/claude-opus-5-5) (2026-09-22), [model reference](https://platform.claude.com/docs/en/models/opus-5-5/overview) | [V] | Terminal-Bench, FrontierCode, efficiency, effort, price. |
| [SpaceXAI: Grok 4.7](https://x.ai/news/grok-4-7) (2026-09-21), [Cursor Grok 4.7](https://cursor.com/docs/models/grok-4-7) | [V] | Terminal-Bench, CursorBench, model effort and pool pricing. |
| [Codex subscriptions](https://learn.chatgpt.com/docs/pricing), [Claude Max](https://support.claude.com/en/articles/11049741-what-is-the-max-plan), [Cursor pools](https://prod.cursor.com/help/models-and-usage/usage-limits) (2026-09-24 snapshot) | [V] | Included usage and credits. |
| [OpenAI, SWE-bench Pro audit](https://openai.com/index/separating-signal-from-noise-coding-evaluations/) (2026-07-08), [Anthropic cost/effort guide](https://platform.claude.com/docs/en/about-claude/models/optimizing-for-cost-and-intelligence) (2026-09 snapshot) | [V] | Broken tasks and saturated subset caveats. |
| [Laravel benchmark](https://laravel.com/blog/which-ai-model-is-best-for-laravel) (2026-03-18), [Octomind](https://octomind.run/blog/coding-agent-benchmark-real-prs) (2026-07-31) | [V] | Vendor-run tests of Laravel Boost and Octomind's own agent; neither compares the current five models. |
| [RuBench](https://arxiv.org/abs/2607.06411) (2026-07) | [T] | Laravel tasks with older models, without a current five-model comparison. |

## Updating

1. Reread each source above and the live CLI catalogs; add only available models from the covered vendors.
2. Keep each figure's evidence level, date, effort, and harness; prefer a [T] figure over a [V] figure only when they measure the same thing.
3. Revisit recommendations, grids, subscription effects, benchmark defects, and gaps.
4. Change the frontmatter `date`.
