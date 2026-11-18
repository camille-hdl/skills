---
date: 2026-11-18
---

# Recommendation table

Compiled on 2026-11-18 from published benchmarks and documentation. The [sources](#sources) say which were read on that date and which were retained from 2026-11-10, 2026-10-16, or 2026-10-01. No benchmark, inference request, or delegated agent was run for this update. Published availability and a local model listing do not confirm account access.

Read [benchmark notes](benchmark-notes.md) when comparing Fable 5.2 with Opus 5.5, inspecting newly discovered models or agents, or updating this table. The notes record recommendation changes and their reasons.

## Evidence levels

- [T] is a measurement by an evaluator independent of the model vendor. The evaluator's product, grading, and harness can still affect the result.
- [V] is a vendor statement or vendor-run evaluation. Verify quoted third-party results at their original source.
- [I] is an inference or usage choice, with its reason stated.
- No data means no applicable published result was found. It is not a zero score.

Keep model version, effort, benchmark revision, and harness together. Scores from different setups are not interchangeable. Small differences without uncertainty estimates do not establish a reliable winner. The routing tiers below are [I], informed by the cited measurements.

## Catalog

Checked on 2026-11-18 with `codex debug models` and `claude --help`. `cursor-agent --list-models` failed that day with "Authentication required", so the Cursor column keeps the 2026-11-10 list and the GPT-6.2 rows are unchecked there. See [harness.md](harness.md) for discovery commands and access verification.

| Model | Vendor | Codex | Claude Code | Cursor | Default |
| --- | --- | --- | --- | --- | --- |
| GPT-6.2 Astra | OpenAI | `gpt-6.2-astra` | N/A | Not checked | Codex `low`, local catalog; the API guide starts new integrations at `medium` [V] |
| GPT-6.2 Sol | OpenAI | `gpt-6.2-sol` | N/A | Not checked | Codex `low`, local catalog; the API guide starts new integrations at `medium` [V] |
| GPT-6.1 Sol, previous generation | OpenAI | `gpt-6.1-sol` | N/A | N/A | Codex `low`, local catalog; API `medium` [V] |
| GPT-6 Luna | OpenAI | `gpt-6-luna` | N/A | N/A | `medium`, local catalog |
| Opus 5.5 | Anthropic | N/A | `claude-opus-5-5` | `claude-opus-5-5-<effort>` | `medium` [V] |
| Sonnet 5.5 | Anthropic | N/A | `claude-sonnet-5-5` | `claude-sonnet-5-5-<effort>` | Claude Code `medium`; API `high` [V] |
| Haiku 5.5 | Anthropic | N/A | `claude-haiku-5-5` | `claude-haiku-5-5-thinking-<effort>`; `claude-haiku-5-5-<effort>` is labeled No Thinking | API `medium` [V] |
| Fable 5.2 | Anthropic | N/A | `claude-fable-5-2`; needs Claude Code 2.1.321 or later | `claude-fable-5-2-<effort>`, `low` through `max`; every variant is marked NO ZDR | API `high`; Claude Code and apps `medium` [V] |
| Grok 4.7 | SpaceXAI / Cursor | N/A | N/A | `grok-4.7-<effort>` | `high` [V] |
| GPT-6.1 Terra, candidate | OpenAI | `gpt-6.1-terra` | N/A | N/A; Cursor lists only `gpt-5.6-terra-<effort>` | Codex `low`, local catalog |

Pass effort explicitly. Local Codex lists `low`, `medium`, `high`, `xhigh`, and `max`, plus `ultra` for Astra 6.2, Sol 6.2 and 6.1, and Terra. `ultra` can delegate automatically and has no measured recommendation here. The local catalog offers Fast and Ultrafast for Sol 6.2 but only Fast for Astra 6.2, and sets a 500K-token context for Sol 6.2 and 272K for Astra 6.2. The API accepts 1.05M [V]. Anthropic's CLI accepts `low` through `max`, including `xhigh`. Its help names the aliases `opus`, `sonnet`, and `fable`. Pass Haiku by its exact ID, and pass `claude-fable-5-2` rather than the alias so the version is explicit. Grok's listed range is `low` through `xhigh`. Prefer Cursor identifiers without `-fast` when preserving quota. No Cursor Haiku configuration is measured. AA's Claude Code runs use adaptive thinking, so the thinking IDs are the closer match [I]. GPT-6 Astra, Sol 6/6.1, Luna 6, and Terra 6.1 were absent from this account's Cursor list on 2026-11-10.

GPT-6.2 Astra replaces GPT-6 Astra (`gpt-6-astra`, still listed). Codex describes GPT-6.1 Sol as the previous generation. Fable 5.1 (`claude-fable-5-1`, Cursor `claude-fable-5-1-<effort>`) is still listed and priced. Fable 5.2 replaced it on 2026-11-10. Measurements of each older version stay attributed to it.

Specifications: [OpenAI catalog][openai-models], [GPT-6.2 Sol][openai-sol62], [GPT-6.2 Astra][openai-astra62], [GPT-6.2 guide][openai-guide62], [Sol 6.1][openai-sol], [Opus][opus-doc], [Sonnet][sonnet-vendor], [Haiku][haiku-doc], [Fable 5.2][fable-doc], [Fable 5.2 launch][fable-vendor], and [Grok][grok-doc] [V]. Older versions and other vendors are accounted for in the [discovery decisions](benchmark-notes.md#discovery-decisions).

## Complexity and impact

Complexity, from simplest to hardest:

- Mechanical work extracts, renames, classifies, or transforms without a decision.
- A ready plan leaves a bounded implementation to execute.
- Long autonomous work has a ready plan and many unsupervised steps.
- Work without a plan requires the agent to choose the approach.

Impact is low when an error is quickly spotted and reversible, medium when it causes substantial rework, and high when it affects production, data, security, or a costly decision. Impact governs review [I]; it is not a model benchmark.

## User and project preferences

This table holds general recommendations drawn from published measurements. Before applying it, read the model preferences documented for the user and the project: the request, `AGENTS.md`, `CLAUDE.md`, project documentation, and any memory or preference file the agent can read. A preference can replace a model, restrict a model to explicit requests, exclude a model, or fix the fallback and the reviewer. A preference wins over the table for the task, the fallback, and the review. Keep preferences out of this file; report each one applied (step 8 of `SKILL.md`).

"Sol" in this table means GPT-6.2 Sol (`gpt-6.2-sol`), released 2026-11-17 [V, [OpenAI][openai-62]]. Cells that keep GPT-6.1 Sol (`gpt-6.1-sol`, released 2026-09-29) name it in full and say why. "Astra" means GPT-6.2 Astra (`gpt-6.2-astra`), released the same day.

Astra has one recommended cell, complex planning on a ChatGPT plan. There it ties Fable 5.2 `high` on AA's index for about a quarter of the API cost per task [T]. In the other cells, Sol 6.2 or an Anthropic model reaches the same tier for less. Astra also draws the most from a ChatGPT plan. The Plus estimate is 6 to 50 messages per five hours, against 17 to 180 for Sol 6.2 [V, [Codex pricing][codex-price], read 2026-11-18]. Outside that cell, use it when a preference or the request names it.

Fable 5.2 leads Opus 5.5 at equal effort on FrontierCode 2.0 in Claude Code and on AA's Intelligence Index v5 [T], at a higher cost per task. It enters the cells those measurements cover: complex planning, unplanned or high-impact code, and higher-tier review. Opus stays the default wherever Fable's limits apply: a plan that excludes Fable or caps its share, a zero-retention requirement, or a cybersecurity task that Fable's safeguards block. See the [task comparison](benchmark-notes.md#fable-52-versus-opus-55).

## Recommendations

Use the catalog identifier and the row's effort with [harness.md](harness.md). Permissions follow the brief. Planning, research, and review use read-only access. Effort choices are [I] unless the evidence names that configuration.

| Kind | Complexity and impact | Model and effort | Harness | Evidence and reason |
| --- | --- | --- | --- | --- |
| Code | Mechanical | Luna `low` or `medium`; Haiku 5.5 `medium` when the Claude pool is preferred | Codex; Claude Code for Haiku | [I] Lowest listed Codex token rates [V]. FrontierCode 2.0 Luna `low` 4.0%/$0.023, `medium` 16.1%/$0.092; Haiku `medium` 14.1%/$0.097 [T]. FrontierCode grades feature changes, not mechanical work. |
| Code | Ready plan, low impact | Luna `max`; Haiku 5.5 `xhigh` when the Claude pool is preferred | Codex; Claude Code for Haiku | Rails combined 43.4% at about $0.19/run; FrontierCode 2.0 Luna `max` 22.7%/$0.174 and Haiku `xhigh` 22.9%/$0.226; native AA v2.1 Luna `max` 25.9/$0.19 [T]. [I] Same tier; small gaps without uncertainty keep Luna first. Sol `low` is a candidate at 33.1%/$0.40 on FrontierCode and 37.2/$0.33 on AA v2.1 [T], for 17 to 20 times Luna's Plus message draw [V]. Escalate failures. |
| Code | Ready plan, medium impact | Sol `medium`; `xhigh` for harder work | Codex | FrontierCode 2.0 `medium` 38.3%/$0.69, `xhigh` 39.8%/$0.98; native Coding Agent Index v2.1 45.4/$0.57 and 49.8/$0.90 [T]. [I] Sol 6.2 replaces GPT-6.1 Sol. At `medium` it scores 8 points above 6.1 `medium` (30.3%/$0.49) and above 6.1 `high` (35.1%/$0.65) at similar cost. Counterexample: at `max` on AA v2.1, 6.2 scores 48.6 against 6.1's 52.2, after a 14-point drop on SWE-Atlas-QnA, a code question-answering test [T]. `max` stays a candidate because Cognition ranks it first (43.8%/$1.29) and AA ranks it below `xhigh`. |
| Code | Long autonomous, medium impact | Opus 5.5 `xhigh`; Fable 5.2 `high` and Sol `max` are candidates | Claude Code | FrontierCode 2.0 Opus `xhigh` 44.7%/$5.18 versus `medium` 31.4%/$1.70 [T]. Rails combined `xhigh` 65.3%/$10.53 versus `medium` 56.1%/$3.84, 72.2% on its multi-step stage [T]. Fable 5.2 `high` scores 46.2%/$8.40 [T], a 1.5-point lead without uncertainty. No independent long-horizon test exists. Sol `max` scores 43.8% for $1.29, a quarter of Opus's cost, but trails Opus `max` by 9.6 points on AA v2.1 (48.6 versus 58.2) [T]. [I] The results conflict, so the cell keeps Opus. |
| Code | No plan or high impact | Fable 5.2 `high`; Opus 5.5 `xhigh` when Fable is excluded | Claude Code | FrontierCode 2.0 in Claude Code: Fable `high` 46.2%/$8.40, `xhigh` 50.2%/$17.73; Opus `high` 36.3%/$2.42, `xhigh` 44.7%/$5.18, `max` 47.3%/$12.82 [T]. Native AA v2.1: Fable `high` 58.2/$7.51, equal to Opus `max` 58.2/$12.61 [T]. AA's Stirrup run: Fable `high` 49.1%, Opus `max` 46.4% [T]. [I] Fable `high` about matches Opus `max` for two-thirds of its cost or less. `xhigh` stays a candidate because Cognition ranks it first, but AA's two runs put it 0.3 point above `high` or below it. Astra does not enter, with `max` at 44.2% on FrontierCode and 53.5 on AA v2.1 [T]. Counterexamples: Terminal-Bench 4.0 ties, and Vals' SWE-bench Multimodal favors Opus 70.2% versus 62.3% [T]. Independent review. |
| Planning | Simple and checkable | Luna `medium` | Codex | [I] Cost and checkability; no direct plan-quality test. |
| Planning | Medium, subscription-dependent | Sol `max` on a ChatGPT plan; Fable 5.2 `medium` on a Claude plan that includes Fable, otherwise Opus 5.5 `high` | Codex; Claude Code | AA Index v5.0.1: Sol `max` 57.3/$1.01, Fable `medium` 56.4/$3.80, Opus `high` 51.8/$3.46, Opus `medium` 48.2/$2.45 per task [T]. [I] Sol 6.2 replaces GPT-6.1 Sol (`max` 54.6/$1.27) because it scores higher for less. The gap between Fable and Sol is small and has no uncertainty estimate, so the user's pool decides. API cost proves no included-quota saving. No direct plan-quality test. |
| Planning | Complex or high impact, subscription-dependent | Fable 5.2 `high` on a Claude plan that includes Fable; Astra `xhigh` on a ChatGPT plan; otherwise Opus 5.5 `xhigh` | Claude Code; Codex | AA Index v5.0.1: Fable `high` 61.8/$9.08, `xhigh` 62.2/$14.83; Astra `xhigh` 61.6/$2.52, `max` 62.1/$4.00; Opus `xhigh` 57.4/$6.05, `max` 59.1/$10.04 [T]. [I] Proxy only. Fable `high` and Astra `xhigh` are 0.2 point apart, and both beat Opus `max`. Astra draws a ChatGPT plan about three times as fast as Sol [V]; where that pool must last, Sol `max` (57.3/$1.01) matches Opus `xhigh`. Independently check consequential assumptions. |
| Web research | Low stakes, lowest Codex draw | Luna `high`; Haiku 5.5 `medium` when the Claude pool is preferred | Codex, web enabled; Claude Code, web tools | Parallel Luna 61.9/$33.1, Haiku 62.9/$24.3 per 1,000 tasks [T]. [I] One point without uncertainty; effort and CLI transfer are unmeasured. |
| Web research | Moderate stakes, cost matters | GPT-6.1 Sol `high`; Sol 6.2 `high` is an unmeasured candidate | Codex, web enabled | Parallel score 70.4, $130/1,000 tasks for GPT-6.1 Sol [T]. Parallel's 2026-11-14 board has no GPT-6.2 row. [I] GPT-6.1 Sol stays until GPT-6.2 has a search result. Scores do not transfer between versions. Codex's search tools differ from Parallel's. |
| Web research | High stakes or decisive synthesis | Opus 5.5 `high`; Fable 5.2 `medium` is a candidate | Claude Code, web tools | Parallel, updated 2026-11-14: Fable 5.2 80.1/$2,426, Opus 76.1/$896, Sonnet 5.5 74.1/$796 per 1,000 tasks [T]. [I] Fable leads by 4 points without uncertainty, at 2.7 times the cost, with effort unstated, so Opus stays the default. Anthropic reports WANDR 82.1% versus Opus 72.3%, with Fable `medium` matching Opus's best for about 40% of the cost [V]. Validate sources; effort and CLI transfer are unmeasured. |
| Code review | Routine | Independent Opus 5.5 `high`; Fable 5.2 `high` or Opus `max` when the author's tier is higher; add GPT-6.1 Sol `xhigh` for Anthropic-authored code | Claude Code; Codex | [I] Review transfers the coding grid. On FrontierCode 2.0, Opus `high` 36.3% sits below Fable 5.2 `high` 46.2%, Opus `max` 47.3% and `xhigh` 44.7%, Astra `max` 44.2%, Sol `max` 43.8%, and Sonnet `max` 42.2% [T]. Retain Opus `high` for authors up to its tier. See the candidate assessment below. The GPT-6.1 Sol pass supplies vendor diversity, not a primary-review replacement. It keeps 6.1 because Sol 6.2 lost 14 points on AA's SWE-Atlas-QnA by omitting key facts more often [T], and launched with tighter cybersecurity safeguards [V]. Sol 6.2 `xhigh` (39.8% versus 33.0% on FrontierCode) is a candidate. |
| Code review | Security-sensitive | Same primary review; add Grok 4.7 `high` | Claude Code; Cursor | Dam Secure recall 77.5%, $9.28/PR, 18m23s [T]. [I] Specialist supplement. Fable 5.2 `high` is an unvalidated candidate for permitted data. Dam Secure measured Fable 5.1, not 5.2, and Anthropic says Fable's safeguards block most cybersecurity tasks, which Opus 4.8 then answers [V]. GPT-6.2 has no security-review result, and OpenAI tightened its safeguards for higher-risk cybersecurity assistance [V]. Neither replaces an equal-tier primary review. |
| Prose for humans | Editing and simplification | A documented user or project preference; otherwise Opus 5.5 `high` | Claude Code | [I] No reproducible direct reformulation comparison found. The fallback transfers the professional-output proxy: AA-Briefcase v1.1 `max`, read 2026-11-18, Sonnet 1815, Opus 1800, Fable 5.2 1785, Astra 1644, Sol 1612 [T]. |
| Professional documents | Complex analysis and presentation | Opus 5.5 `high`; Sonnet 5.5 `max` as an alternative | Claude Code | AA-Briefcase v1.1 combined Elo at `max`, read 2026-11-18: Sonnet 1815, Opus 1800, Fable 5.2 1785, Astra 1644, Sol 1612; GDPval-AA, read 2026-11-10: Opus 1866, Sonnet 1838, Fable 5.2 1831 [T]. [I] A 15-point Elo gap without uncertainty keeps the previous order. GPT-6.2 does not enter. Fable's higher Briefcase rubric score (66.1% versus 61.2%) is vendor-reported [V]. Professional-output proxy, not proof about literary style. |

Coding figures come from [Cognition's FrontierCode 2.0 data][frontier2-data], [AA's native-agent board][aa-code], and [Rails Stage 3 grading][rails-stage3]. Search uses [Parallel][parallel]; security review uses [Dam Secure][dam]. Reasoning and document proxies use AA's Intelligence Index v5.0.1 through its [Opus/Fable 5.2][aa-pair], [Astra/Fable 5.2][aa-astra-fable], and [Opus/Sol 6.2][aa-opus-sol] comparisons. The [sources](#sources) give each date, and the setups are described below.

## Performance grids

### Planning proxies

No cited benchmark grades a repository plan separately from execution. These tiers are [I], based on AA Intelligence Index v5.0.1 in its API evaluation, read 2026-11-18. They are not planning pass rates. Index v5 replaced v4.3.2 on 2026-10-27 with nine evaluations, five of them new or upgraded. v4.3.2 scores are not comparable and are not used here.

| Tier | Models and measured effort | Index [T] | API dollars/task [T] | Subscription pool |
| --- | --- | --- | --- | --- |
| Highest | Fable 5.2 `max` / `xhigh` / `high` | 64.6 / 62.2 / 61.8 | 26.54 / 14.83 / 9.08 | Claude plan, within the Fable cap |
| Highest | Astra `max` / `xhigh` / `high` | 62.1 / 61.6 / 60.1 | 4.00 / 2.52 / 2.07 | ChatGPT plan, fastest draw |
| High | Opus 5.5 `max` / `xhigh`; Sol `max`; Astra `medium` | 59.1 / 57.4; 57.3; 57.0 | 10.04 / 6.05; 1.01; 1.62 | Claude plan; ChatGPT plan |
| Good | Fable 5.2 `medium`; Sol `xhigh` / `high`; Sonnet 5.5 `max` | 56.4; 55.7 / 54.9; 54.5 | 3.80; 0.65 / 0.56; 10.02 | Claude plan; ChatGPT plan |
| Intermediate | Fable 5.2 `low`; Sol `medium`; Opus 5.5 `high`; Terra 6.1 `max`; Opus 5.5 `medium` | 53.9; 52.7; 51.8; 51.3; 48.2 | 3.10; 0.41; 3.46; 0.96; 2.45 | Claude plan; ChatGPT plan |
| Scoped | Haiku 5.5 `max`; Grok 4.7 `xhigh`; Luna `max` | 36.5; 35.5; 27.9 | 0.41; 7.77; 0.15 | Claude plan; Cursor Models; ChatGPT plan |
| Not installed | Gemini 4 Carbon `high`; Gemini 4 Hydrogen `xhigh` | 60.0; 53.9 | 7.76; not recorded | Antigravity CLI absent |

Source: [AA Astra/Fable 5.2][aa-astra-fable], [Opus/Sol 6.2][aa-opus-sol], and [Opus/Fable 5.2][aa-pair] comparisons, read 2026-11-18, with the [Index v5 announcement][aa-v5]. Terra 6.1, Haiku, Grok, Luna, Sonnet's cost, and Carbon are retained from the 2026-11-10 read. Older versions read GPT-6 Astra `max` 56.9/$6.24, GPT-6.1 Sol `max` 54.6/$1.27, and Fable 5.1 `max` 49.2 on v5. Fable 5.2 leads Opus at each equal effort from `medium` to `max`, by 4.8 (`xhigh`) to 10.0 (`high`) points, and also leads HLE-Diamond (80.2% versus 67.9% at `max`) [T]. Astra `max` leads Terminal-Bench-Science 0.1 (78.1%, against Fable 73.3% and Opus 59.0%) and trails Fable on HLE-Diamond (72.2%) [T, [AA][aa-gpt62]]. AA's figures for Anthropic models include default fallback. Their use in plans is [I].

### Code

[FrontierCode 2.0][frontier2], released by Cognition on 2026-10-27, grades whether a maintainer would merge the change across 132 private tasks. Failing a blocking check scores zero. On 2026-11-11, Cognition updated its cheating scanner to remove false positives and rescored every result, so pre-rescore figures are not comparable. Scores below are `new_score` from the [public data][frontier2-data], read 2026-11-18, in each model's native harness. The data give no uncertainty or run count.

| Tier [I] | Combination | Score [T] | API dollars/task [T] |
| --- | --- | --- | --- |
| Highest | Fable 5.2 `xhigh` / `max` / `high`, Claude Code | 50.2% / 48.2% / 46.2% | 17.73 / 55.87 / 8.40 |
| Highest | Opus 5.5 `max` / `xhigh`, Claude Code | 47.3% / 44.7% | 12.82 / 5.18 |
| High | Astra `max` / `xhigh` / `high` / `medium`, Codex | 44.2% / 44.1% / 43.6% / 42.2% | 5.97 / 4.29 / 3.95 / 2.47 |
| High | Sol `max`, Codex | 43.8% | 1.29 |
| High | Sonnet 5.5 `max`, Claude Code | 42.2% | 19.94 |
| Good | Sol `xhigh` / `high` / `medium` / `low`, Codex | 39.8% / 39.7% / 38.3% / 33.1% | 0.98 / 0.88 / 0.69 / 0.40 |
| Good | Fable 5.2 `medium` / `low`, Claude Code | 38.8% / 35.3% | 3.10 / 2.62 |
| Good | Opus 5.5 `high` / `medium`, Claude Code | 36.3% / 31.4% | 2.42 / 1.70 |
| Good | Sonnet 5.5 `xhigh`, Claude Code | 36.5% | 3.32 |
| Intermediate | Grok 4.7 `high`, Grok Build | 26.5% | 11.09 |
| Scoped | Haiku 5.5 `max` / `xhigh` / `medium`, Claude Code | 28.9% / 22.9% / 14.1% | 0.37 / 0.23 / 0.10 |
| Scoped | Luna `max` / `medium` / `low`, Codex | 22.7% / 16.1% / 4.0% | 0.17 / 0.09 / 0.02 |

Rescored older versions: GPT-6.1 Sol `max` 39.6%/$1.03, `high` 35.1%/$0.65, `xhigh` 33.0%/$0.70, `medium` 30.3%/$0.49; GPT-6 Astra `max` 44.0%/$6.68; Fable 5.1 `xhigh` 34.0%. Gemini 4 Carbon moved to Antigravity CLI on 2026-11-12 (`high` 42.6%/$5.06), and Gemini 4 Hydrogen scores 38.9%/$4.95 at `xhigh` there. Neither CLI is installed. Fable 5.2 is not monotonic by effort: `max` costs 3.2 times `xhigh` and scores 2.0 points lower. After the scanner update, its flagged internet-use rate is 0% to 0.15%. [AA's own FrontierCode 2.0 run][aa-v5], in its Stirrup harness and part of Intelligence Index v5, orders the top differently: Fable 5.2 `high` 49.1%, Astra `xhigh` 49.0%, Fable `max` 48.8%, Fable `xhigh` 47.6%, Opus `max` 46.4%, Sol `max` 44.4%, Opus `xhigh` 43.8% [T]. Do not mix the two harnesses' scores. Anthropic's launch table quotes Cognition's pre-rescore 49.1% and 45.5% [V, [launch][fable-vendor]]. OpenAI says Sol nearly matches Astra on FrontierCode 2.0 at about one-fifth of the cost [V, [OpenAI][openai-62]]; Cognition's data give 43.8% versus 44.2% at `max`, for $1.29 versus $5.97.

AA's [native coding-agent board][aa-code], read 2026-11-18, now runs Coding Agent Index v2.1: FrontierCode-AA 2.0, Terminal-Bench 4.1, and SWE-Atlas-QnA-AA, equally weighted, three attempts per task. Its v2.0 and v1.5 values are not comparable and are no longer used. Its publication date was not found.

| Tier [I] | Combination, Coding Agent Index v2.1 | Index [T] | API dollars/task [T] | Evaluated CLI version |
| --- | --- | --- | --- | --- |
| Highest | Fable 5.2 `xhigh` / `high`, Claude Code | 58.5 / 58.2 | 15.47 / 7.51 | 2.1.291 |
| Highest | Opus 5.5 `max`, Claude Code | 58.2 | 12.61 | 2.1.280 |
| High | Sonnet 5.5 `max`, Claude Code | 56.3 | 11.40 | 2.1.280 |
| High | Fable 5.2 `max` / `medium`, Claude Code | 55.7 / 53.0 | 44.22 / 2.89 | 2.1.291 |
| High | Astra `max` / `xhigh` / `high`, Codex | 53.5 / 53.1 / 52.3 | 5.12 / 3.20 / 2.37 | 0.166.0 |
| Good | Sol `xhigh` / `max` / `high` / `medium`, Codex | 49.8 / 48.6 / 47.5 / 45.4 | 0.90 / 1.22 / 0.76 / 0.57 | 0.166.0 |
| Good | Astra `medium`, Codex | 49.1 | 1.20 | 0.166.0 |
| Good | Terra 6.1 `max`, Codex | 48.6 | 1.53 | 0.163.0 and 0.166.0 |
| Good | Fable 5.2 `low`, Claude Code | 48.0 | 2.49 | 2.1.291 |
| Intermediate | Grok 4.7 `xhigh`, Grok Build | 41.6 | 15.35 | 1.0.40 |
| Scoped | Sol `low`, Codex | 37.2 | 0.33 | 0.166.0 |
| Scoped | Haiku 5.5 `max`, Claude Code | 29.6 | 2.25 | 2.1.289 |
| Scoped | Luna `max`, Codex | 25.9 | 0.19 | 0.154.0 |

Older versions on v2.1: GPT-6.1 Sol `max` 52.2/$1.51 (Codex 0.154.0), GPT-6 Astra `max` 53.1/$7.63, Fable 5.1 `max` 52.5/$11.70. Not installed: Gemini 4 Carbon `high` 55.5/$9.75 and Gemini 4 Hydrogen `xhigh` 52.3/$4.45 in Antigravity CLI; Devin Fusion's Opus `max` + Luna `high` router 58.4/$8.75. Sol 6.2's drop from 6.1 comes from SWE-Atlas-QnA (`max` 46.2% versus 59.9%). On Terminal-Bench it gains (58.1% versus 54.0%) and on FrontierCode-AA it ties (41.5% versus 42.5%) [T]. AA attributes the drop to 6.2 omitting key facts from its answers [T, [AA][aa-gpt62]]. A native Grok Build result does not establish the same result in Cursor. Transfer to another effort or harness is [I]. Newer CLI versions do not inherit measured gains automatically. AA flags Haiku's tiered pricing, so treat its task costs as provisional lower bounds [I]. AA's native runs include default fallback for every Anthropic entry. These are configuration results, not pure-model scores.

FrontierCode 1.1 Main (Cognition, native harnesses) is superseded for current ranking. Its figures stay in the [Fable 5.1 history](benchmark-notes.md#fable-51-history) and in the 2026-10-16 notes.

Terminal tasks do not favor Fable 5.2. In AA's Index v5 run, Terminal-Bench 4.0 gives Astra `max` 64.1%, Sol `max` 60.1%, Fable 5.2 `max` 59.6%, equal to Opus `max`, below Sonnet `max` 63.6% and Gemini 4 Carbon `high` 65.2% [T]. Vals, evaluating Fable at `high` on 2026-11-09, ties Fable 5.2 and Opus 5.5 at 65.15% on Terminal-Bench 4.0, puts Fable first on its Vals Index (71.31% ± 0.96, versus Sonnet 5.5 70.85%), and puts Opus ahead on SWE-bench Multimodal (70.21% versus 62.29%) [T, [Vals][vals-fable]]. Vals ran GPT-6.2 at `max` on 2026-11-17: Vals Index Astra 67.66% ± 0.94 and Sol 66.06% ± 0.91; Terminal-Bench 4.0 Astra 63.13% and Sol 60.61% [T, [Astra][vals-astra62], [Sol][vals-sol62]].

[Rails Stage 3][rails-stage3], October 13, adds seven multi-step tasks and regrades Stages 1 and 2 with fractional credit: failing a required check scores zero, optional checks add weighted credit. Its combined score averages 46 tasks (19 atomic, 20 feature, 7 multi-step), mostly three runs each, in a shared minimal harness with selective RubyGems access. Results [T]: Opus `xhigh` 65.3%/$10.53 per run, GPT-6 Astra `medium` 62.3%, GPT-6.1 Sol `xhigh` 60.8%/about $0.80, Opus `medium` 56.1%/$3.84, Luna `max` 43.4%/about $0.19. The article's text gives GPT-6 Astra 62.3% at both `medium` and `xhigh`; one may be a typo. Neither Fable version, GPT-6.2, Sonnet, nor Haiku was run; no newer Rails stage appeared by 2026-11-18. The Stage 2 pass rates used on 2026-10-01 stay only as history in the [notes](benchmark-notes.md#fable-51-history). Neither result is a Symfony pass rate.

### Web research

[Parallel][parallel], updated 2026-11-14 and read 2026-11-18, uses 100 questions each from DSQA, HLE, and WISER. It supplies Search Fast and Extract, disables code execution, and averages three scores. Reasoning settings can differ by model; exact effort is unstated in the table except Grok's.

| Tier [I] | Model | Search score [T] | API and tool dollars/1,000 tasks [T] |
| --- | --- | --- | --- |
| Highest in this setup | Fable 5.2 | 80.1 | 2,426 |
| High in this setup | Opus 5.5 | 76.1 | 896 |
| High in this setup | Sonnet 5.5 | 74.1 | 796 |
| High in this setup | Fable 5.1 | 73.4 | 1,762 |
| Good in this setup | GPT-6 Astra | 70.8 | 401 |
| Good in this setup | GPT-6.1 Sol | 70.4 | 130 |
| Intermediate in this setup | Grok 4.7 `medium` | 66.0 | 252 |
| Scoped in this setup | Haiku 5.5 | 62.9 | 24.3 |
| Scoped in this setup | Luna 6 | 61.9 | 33.1 |
| Not installed | Hy4; Gemini 4 Carbon; Kimi K3.1 Pro; Gemini 4 Hydrogen | 75.4; 74.2; 74.2; 72.7 | 94.4; 472; 268; 175 |
| Unranked | Terra 6.1 | 69.2 | 43.7 |
| Unranked | Astra 6.2; Sol 6.2 | No result | N/A |

These scores do not measure the three installed CLIs' web tools. Cost records may omit recovery attempts. Between the 2026-10-31 and 2026-11-14 boards, Opus moved from 75.4/$949 to 76.1/$896 and Terra from 69.7 to 69.2. Compare within one board. Fable 5.2's Parallel row shows no time per task.

### Code review

There is no general-review ranking here. Retain Opus `high` as the primary default for authors up to its inferred tier [I]. Check the author's exact configuration against step 5 in `SKILL.md`; choose a measured equal-or-higher tier when the default's inferred tier is insufficient.

Fable 5.2 `high` is the inferred higher-tier reviewer [I]. FrontierCode 2.0 gives it 46.2%/$8.40 versus Opus `high` 36.3%/$2.42 [T]. Use it, or Opus `max` (47.3%/$12.82), when the author's configuration sits above Opus `high`: Opus `xhigh`, Sonnet `max`, Astra at `medium` or above, or Sol `max`. Sol `xhigh` and below share Opus `high`'s Good tier. A Fable-authored change gets an independent Fable session or Opus `max`, plus the cross-vendor pass. Neither coding test directly establishes review quality.

Sonnet remains a candidate, not a demonstrated replacement [I]. FrontierCode 2.0 gives Sonnet `max` 42.2%/$19.94 and `xhigh` 36.5%/$3.32, versus Opus `xhigh` 44.7%/$5.18 and `high` 36.3%/$2.42 [T]. On AA's native v2.1 board, Sonnet `max` scores 56.3 versus Opus `max` 58.2 [T]. Neither result shows Sonnet above Opus at a comparable cost.

| Security-review setup | Grok 4.7 | Fable 5.1 | Opus 5.5 | Fable 5.2 / Sol 6.1 and 6.2 / Astra 6.2 / Sonnet 5.5 / Haiku 5.5 |
| --- | --- | --- | --- | --- |
| Dam Secure, 16 planted bugs, five runs per PR, `high` [T] | 77.5% recall, via Vercel | 62.5% recall | 56.25% recall | No data |

Source: [Dam Secure, 2026-09-24][dam], reread on 2026-10-01; its blog had no newer post on 2026-11-18. Fable 5.1's 62.5%/$7.31 per PR versus Opus's 56.25%/$1.92 is five extra detections over 80 reviews of only 16 distinct bugs. This is a weak signal without uncertainty, not a reliable security-review winner, and it does not transfer to Fable 5.2 [I]. Sol 6 scores 63.75%/$1.81; those figures do not belong to Sol 6.1 or 6.2.

Fable 5.2 has no independent security-review result. Anthropic says its safeguards block most cybersecurity tasks, such as penetration testing, exploit generation, and binary vulnerability work, and route them to Opus 4.8. It reports about 60% fewer cybersecurity blocks than Fable 5.1 [V, [launch][fable-vendor]]. Opus 4.8 can therefore answer a security review in Fable's place. Check the served model. Fable 5.2 remains an unvalidated specialist candidate. OpenAI launched GPT-6.2 with tighter safeguards for higher-risk cybersecurity assistance and plans reduced refusals for approved defenders through Daybreak [V, [OpenAI][openai-62]]. Endor tests code generation, not review; see the [Fable comparison](benchmark-notes.md#fable-52-versus-opus-55).

### Writing and professional outputs

| Use | Evidence | Routing consequence [I] |
| --- | --- | --- |
| Professional deliverables | AA-Briefcase v1.1 combined Elo at `max`, read 2026-11-18: Sonnet 1815, Opus 1800, Fable 5.2 1785, Astra 1644, Sol 1612; GDPval-AA Elo, read 2026-11-10: Opus 1866, Sonnet 1838, Fable 5.2 1831 [T] | Opus or Sonnet; these tests combine analysis, execution, and presentation. Fable 5.2 trails both on Elo, and GPT-6.2 trails further. Haiku is not a substitute here. |
| Human-facing prose and reformulation | No reproducible direct comparison found for the selected models | No measured default. Apply a documented preference; otherwise transfer the professional-output proxy [I]. Excluded reports are recorded in the notes. |

Source: AA's [Opus/Fable 5.2][aa-pair], [Astra/Fable 5.2][aa-astra-fable], [Opus/Sol 6.2][aa-opus-sol], and [Sonnet/Opus][aa-sonnet-opus] comparisons, read 2026-11-18. Elo shifts as AA adds models. The 2026-11-10 snapshot read Sonnet 1816 and Opus 1801. Compare only within one snapshot. Anthropic reports a higher Briefcase rubric score for Fable 5.2 (66.1% versus 61.2% for Opus) [V]. OpenAI says Astra sets new highs on professional-work evaluations [V, [OpenAI][openai-62]]; AA's Briefcase does not confirm it. Neither the Elo nor the rubric establishes superiority on every document or writing task.

## Cost: the subscription decides the order

Plans are separate pools: a ChatGPT plan pays for Codex, a Claude plan for Claude Code, and a Cursor plan for Cursor. Ask for the user's subscriptions when a row depends on them (step 4 of `SKILL.md`). API dollars cannot establish exact subscription cost per completed task.

| Model | Standard API input/output dollars per million [V] | Cache read dollars per million [V] | Codex output credits/million [V] |
| --- | --- | --- | --- |
| Luna 6 | 0.10 / 0.50 | N/A | 12.5 |
| Terra 6.1 | N/A | N/A | 125 |
| Sol 6.2 | 2 / 10; cache write 2.50 | 0.10 | 250 |
| Sol 6.1 | 2 / 10 | 0.10 | 250 |
| Astra 6.2 | 8 / 40; cache write 10 | 0.40 | 1,000 |
| Opus 5.5 | 4 / 20 | 0.20 | N/A |
| Sonnet 5.5 | 2 / 10 | 0.10 since 2026-10-07, previously 0.20 | N/A |
| Haiku 5.5 | 0.10 / 0.50 up to 100k-token prompts; 0.50 / 2.50 above | 0.01; 0.05 above 100k | N/A |
| Fable 5.2 | 8 / 40; fast mode 16 / 80 | 0.20 | N/A |
| Grok 4.7 | 2 / 6 | N/A | N/A |

Sources: [GPT-6.2 Sol][openai-sol62], [GPT-6.2 Astra][openai-astra62], and [Codex pricing][codex-price], read 2026-11-18; [Anthropic pricing][anthropic-price], read 2026-11-10, and [Haiku launch][haiku-vendor] for every Claude row; [OpenAI API][openai-price] and [Grok][grok-doc], read 2026-10-01. N/A means the price was not recorded here. Prices exclude tools, long context beyond Haiku's step, and special processing. GPT-6.2 doubles input and cache rates, and raises output by half, for requests above 272K input tokens; Fast costs twice Standard and Ultrafast three times until 2027-02-28, then six times [V]. Astra 6.2 costs 20% less than GPT-6 Astra ($10/$50, 1,250 credits) [V]. Haiku's price steps up five times above 100k-token prompts [V]; long agent sessions can cross that threshold [I]. Sonnet's cache read costs half of Opus's, and Fable 5.2's equals Opus's. Fable 5.1 stays at $10/$50 with $0.25 cache reads [V]. The benchmark task costs elsewhere in this table were measured at the prices of their run date; do not rescale them by a later price.

| Plan or access | Published limits and billing [V] | Routing implication [I] |
| --- | --- | --- |
| ChatGPT plan, Codex | Plus five-hour estimate: Luna 350 to 3,000, Terra 6.1 35 to 285, Sol 6.2 17 to 180, Sol 6.1 15 to 160, Astra 6.2 6 to 50; weekly limits may apply. Pro costs $100, $200, or $500 a month and has no five-hour limit. Fast uses included allowance at 2 times Standard for GPT-6.2 and 2.5 times for older models; Ultrafast at 6 times for GPT-6.2 and 8 times for Sol 6.1 and GPT-6 Astra. The pricing page lists Ultrafast on Pro $500; OpenAI's announcement adds Pro $200 for Sol 6.2. | Luna conserves this pool; Sol is intermediate; Astra draws about three times as fast as Sol. |
| Claude plan, Claude Code signed in with the subscription | Max: five-hour limits, a weekly limit across all models, and a separate weekly Fable limit. On Max, Ultra, and premium Team or Enterprise seats, Fable may use at most 50% of the weekly limit, uses it faster than other models, and adds no allowance. On Pro and standard seats, Fable runs on usage credits from the start. Launch week of Fable 5.2: one to three Fable resets on eligible plans. `claude -p` and the Agent SDK signed in with the plan draw these limits, not the API credits. A numeric per-task quota multiplier per model is unpublished. | Opus is the general default. Fable 5.2 takes the cells where it leads, within its cap. Fable's higher cost per task at equal effort makes it draw the cap quickly. Sonnet `max` costs more API dollars than Opus in AA's coding workload; its quota ratio is unmeasured. Haiku is the low-cost alternative inside this pool; its per-task quota draw is unpublished. |
| Claude plan, monthly API credits | Since 2026-10-07, Max 5x includes $100 and Max 20x $200 of Claude Platform credit per month; Team up to $500, pooled. Credits work with any model and expire at the end of each billing cycle. They cover `claude -p` and the Agent SDK run with an API key from the linked Console organization. They do not cover interactive Claude Code, IDE, desktop, web, or GitHub Action runs. | A second, dollar-denominated pool for non-interactive delegation. Choosing it is choosing the authentication: pass an API key from the linked organization. Benchmark API costs apply here directly. |
| Cursor Pro | Separate Cursor Models and Other Models pools. Grok and Composer draw the former; third-party models draw the latter. The page does not list which providers count as third-party. Grok Standard $2/$6, Fast $4/$12. | Grok preserves the third-party pool. Balances, routing, and subagents determine actual consumption. |
| API outside any plan | Token and tool billing on the provider's account. | Confirm a paid API path separately from included CLI access. |

Sources: [Codex][codex-price] and the [GPT-6.2 announcement][openai-62], read 2026-11-18; [Claude Max][max-plan] and [Fable limits][fable-plan], read 2026-11-10; [monthly API credits][claude-credits] and [Cursor pools][cursor-pools], read 2026-10-16; [Grok prices][grok-doc], read 2026-10-01. The credit amounts and start date come from the [Haiku launch][haiku-vendor] of 2026-10-07; the credits article states coverage and authentication. The Max plan page also names an Ultra plan with monthly API credits; its amounts were not recorded here.

Fable 5.2 costs more per task than Opus at equal effort [T]: FrontierCode 2.0 `high` $8.40 versus $2.42 and `xhigh` $17.73 versus $5.18; AA Index v5 `max` $26.54 versus $10.04. At a near-equal score it can cost less. Fable `high` comes within 1.1 points of Opus `max`'s FrontierCode score for $8.40 versus $12.82, and exceeds its Index score for $9.08 versus $10.04. See the [comparison notes](benchmark-notes.md#relative-cost-and-quota). No single quota multiplier follows.

## Gaps

- Planning is inferred from reasoning and professional-work tests. No direct independent plan-quality comparison was found.
- Fable 5.2 has no independent security-review or Rails result. GPT-6.2 Astra and Sol have no search, security-review, or Rails result.
- OpenAI's launch page returned HTTP 403 to a scripted read on 2026-11-18. Its claims were read through OpenAI's developer-forum announcement, whose charts are images without values. No vendor score from those charts is used.
- FrontierCode 2.0 data give no uncertainty or run count, and the 2026-11-11 rescore changed every score. Cognition, which runs it, is also quoted among Anthropic's launch testers.
- General review and literary style have no direct ranking here. Security recall, secure-code generation, and coding indices measure different work; the notes explain an excluded writing report.
- No exact CLI search head-to-head or current Symfony head-to-head was found.
- Anthropic evaluations can include fallbacks. Sonnet's AA API evaluation used a pre-release structured-output bug, fixed before release; AA planned reruns [T, [Sonnet article][aa-sonnet]]. Observe the actual served model.
- Coding sets can have contamination, defective tests, subjective grading, or scope penalties. Endor removes memorized solutions; FrontierCode zeros solution-bearing internet use. Compare revised scores.
- Review tiers transfer coding evidence [I]. A different vendor supplies independence, not a measured improvement on these combinations.
- Exact account access, remaining balances, and model-specific Claude quota multipliers are unverified. Listing and help text alone are insufficient. The Cursor list could not be read on 2026-11-18.
- Haiku 5.5's published task costs do not yet reflect its tiered pricing, and AA expects to rerun its over-refusing AutomationBench result [T, [AA Haiku][aa-haiku]]. No same-version security-review or Rails result was found.
- Rails' Stage 3 regrade, AA's Index v5, Coding Agent Index v2.1, and FrontierCode 2.0 with its 2026-11-11 rescore each break continuity with earlier figures. Compare only within one revision.

## Sources

Sources read on 2026-11-18 are marked "read 2026-11-18"; the others were retained from the 2026-11-10, 2026-10-16, or 2026-10-01 access. Dates are publication dates where given; a snapshot records a live page read, not a claimed publication date.

| Source | Date | Evidence and setup |
| --- | --- | --- |
| [GPT-6.2 announcement][openai-62], [GPT-6.2 Sol][openai-sol62], [GPT-6.2 Astra][openai-astra62], [GPT-6.2 guide][openai-guide62], [OpenAI changelog][openai-changelog] | 2026-11-17; read 2026-11-18 | [V] IDs, availability, prices, starting effort, ZDR eligibility, cybersecurity safeguards. The [launch page][openai-launch62] itself was unreadable (HTTP 403). |
| [FrontierCode 2.0][frontier2], [public data][frontier2-data] | Suite 2026-10-27; GPT-6.2 listed under 2026-11-09; rescore 2026-11-11; read 2026-11-18 | [T] 132 private tasks, native harnesses, `new_score` by effort, no uncertainty. |
| [AA GPT-6.2 article][aa-gpt62]; comparisons [Astra/Fable 5.2][aa-astra-fable], [Opus/Sol 6.2][aa-opus-sol], [Opus/Fable 5.2][aa-pair], [Sonnet/Opus][aa-sonnet-opus]; [Index v5][aa-v5] | Article 2026-11-17; v5 2026-10-27; read 2026-11-18 | [T] Intelligence Index v5.0.1, API with default fallback for Anthropic; FrontierCode 2.0 and Terminal-Bench 4.0 in Stirrup; Briefcase v1.1. Values from rendered comparison tables. |
| [AA coding agents][aa-code] | Coding Agent Index v2.1; read 2026-11-18 | [T] Native combinations and versions; three components, three attempts each. |
| [Vals Fable 5.2][vals-fable], [Vals Astra 6.2][vals-astra62], [Vals Sol 6.2][vals-sol62] | 2026-11-09 and 2026-11-17; read 2026-11-10 and 2026-11-18 | [T] Vals Index v2.2 and components with uncertainty; Fable at `high` (fallback rate 1.88%), GPT-6.2 at `max`. |
| [Parallel][parallel] | Updated 2026-11-14; read 2026-11-18 | [T] Search Fast/Extract, 300 questions, variable reasoning configuration. No GPT-6.2 row. |
| [Codex pricing][codex-price] | Read 2026-11-18 | [V] Plus estimates, Pro tiers, credits, Fast and Ultrafast multipliers. |
| [Dam Secure][dam] | 2026-09-24; blog index read 2026-11-18 | [T] Planted-bug review, `high`, five runs; routes differ. No newer post. |
| [Rails Stage 3][rails-stage3], [board][rails] | 2026-10-13; blog index read 2026-11-18 | [T] Minimal harness, fractional grading, 46 tasks, mostly three runs each. No newer stage. |
| [Fable 5.2 launch][fable-vendor], [Fable 5.2 documentation][fable-doc] | 2026-11-09; read 2026-11-10 | [V] ID, prices, default effort, retention, safeguards and fallbacks, vendor-run benchmark table. |
| [Anthropic pricing][anthropic-price], [Fable limits][fable-plan], [Claude Max][max-plan] | Read 2026-11-10 | [V] Claude token and cache prices; Fable cap, plan coverage, and Claude Code version requirement. |
| [AA Haiku][aa-haiku] | 2026-10-07; read 2026-10-16 | [T] Provisional costs, AutomationBench rerun caveat. |
| [Endor][endor] | 2026-09-24 | [T] Secure-code generation with Fable 5.1, Claude Code, 200 tasks/179 graded, memorization excluded; CLI versions differ. |
| [Haiku][haiku-doc], [Haiku launch][haiku-vendor] | Release 2026-10-07; read 2026-10-16 | [V] ID, default effort, tiered prices, credit amounts. |
| [OpenAI catalog][openai-models], [Sol 6.1][openai-sol], [API prices][openai-price] | Sol 6.1 release 2026-09-29; snapshots 2026-10-01 | [V] IDs, effort, and API prices. |
| [Opus][opus-doc], [Sonnet][sonnet-vendor] | Releases 2026-09-22, 2026-09-28 | [V] Specifications. |
| [Monthly API credits][claude-credits], [Cursor pools][cursor-pools] | Read 2026-10-16 | [V] Credit coverage by authentication; Cursor pools. |
| [Grok][grok-doc] | Snapshot 2026-10-01 | [V] Grok speed tiers and context pricing. |

## Updating

1. Search dated announcements, release notes, model cards, independent evaluator feeds, and agent leaderboards for new models, versions, and CLI harnesses. Start with the feeds, changelog, and vendor announcements named in [discovery decisions](benchmark-notes.md#discovery-decisions). Include vendors outside current recommendations. Record the cutoff and distinguish released, preview, announced, and inaccessible products.
2. Run `command -v` for known CLI names and newly discovered executable names. Read installed versions and `--help`. Read exposed model catalogs with [harness.md](harness.md); record failures and missing non-interactive catalogs. Compare with the previous inventory. Use listing commands without starting agents or installing software.
3. Give every newly released or newly considered model/harness a disposition: ranked for named tasks, unranked with missing evidence/access stated, or ignored with a reason. Record exact IDs, effort, visibility, retention flags, and harness version. Separate listing/documented availability from a verified inference request.
4. Reread retained sources and search newer revisions and counterexamples. Record publication/snapshot and access dates, task, metric, revision, effort, harness/version, and evidence level. Read public datasets or embedded results when dynamic charts omit values. Retrieval failures are gaps, not confirmation.
5. Rebuild grids and recommendations from comparable results. Mark proxy transfers [I]. Keep old measurements under the old model. Resolve contradictions by task/setup; avoid averaging unrelated scores or treating benchmark counts as real-world task frequencies. Retain the previous recommendation when small gaps lack uncertainty or applicable results conflict; record the challenger as a candidate.
6. Recheck prices, pools, caps, availability, and confidentiality, with the date of each check. Reassess the [Fable/Opus comparison](benchmark-notes.md#fable-52-versus-opus-55), retaining counterexamples beside the verdict. Do not write user or project preferences into this table or the notes.
7. Record every recommendation change and reason in [benchmark notes](benchmark-notes.md). Update examples and `SKILL.md`; update `README.md` when descriptions or links change. Verify actual catalog IDs, source links, local pointers, table structure, and the final diff.
8. Set both frontmatter `date` and compilation date after completion. Distinguish sources reread this time from retained older snapshots. Finish when every discovery/change is accounted for and every number has dated, named evidence.

[aa-pair]: https://artificialanalysis.ai/models/comparisons/claude-opus-5-5-vs-claude-fable-5-2
[aa-astra-fable]: https://artificialanalysis.ai/models/comparisons/gpt-6-2-astra-vs-claude-fable-5-2
[aa-opus-sol]: https://artificialanalysis.ai/models/comparisons/claude-opus-5-5-vs-gpt-6-2-sol
[aa-sonnet-opus]: https://artificialanalysis.ai/models/comparisons/claude-sonnet-5-5-vs-claude-opus-5-5
[aa-gpt62]: https://artificialanalysis.ai/articles/openai-has-the-2-model-in-the-intelligence-index-with-the-release-of-gpt-6-2-astra-and-gpt-6-2-sol
[aa-sonnet]: https://artificialanalysis.ai/articles/claude-sonnet-5-5
[aa-code]: https://artificialanalysis.ai/agents/coding-agents
[aa-haiku]: https://artificialanalysis.ai/articles/claude-haiku-5-5
[rails]: https://rubyonrails.org/ai
[rails-stage3]: https://rubyonrails.org/2026/10/13/agents-on-rails-stage-3
[parallel]: https://parallel.ai/leaderboard
[dam]: https://docs.damsecure.ai/blog/openai-gpt-6-sol-closes-in-on-deepseek-v4-1-flash-security-benchmark/
[endor]: https://www.endorlabs.com/learn/opus-5-5-6x-cheaper-and-2x-faster-than-fable-5-1-but-memorization-keeps-it-off-the-top-spot
[openai-models]: https://developers.openai.com/api/docs/models
[openai-sol]: https://developers.openai.com/api/docs/models/gpt-6.1-sol
[openai-sol62]: https://developers.openai.com/api/docs/models/gpt-6.2-sol
[openai-astra62]: https://developers.openai.com/api/docs/models/gpt-6.2-astra
[openai-guide62]: https://developers.openai.com/api/docs/guides/latest-model
[openai-62]: https://community.openai.com/t/gpt-6-2-astra-and-sol-are-now-available/1417531
[openai-launch62]: https://openai.com/index/introducing-gpt-6-2-astra-sol/
[openai-changelog]: https://developers.openai.com/api/docs/changelog
[openai-price]: https://developers.openai.com/api/docs/pricing
[codex-price]: https://learn.chatgpt.com/docs/pricing
[opus-doc]: https://platform.claude.com/docs/en/models/opus-5-5/overview
[fable-doc]: https://platform.claude.com/docs/en/models/fable-5-2/overview
[sonnet-vendor]: https://www.anthropic.com/claude-sonnet-5-5
[haiku-doc]: https://platform.claude.com/docs/en/models/haiku-5-5/overview
[haiku-vendor]: https://www.anthropic.com/news/claude-haiku-5-5
[anthropic-price]: https://platform.claude.com/docs/en/about-claude/pricing
[claude-credits]: https://support.claude.com/en/articles/17154008-monthly-api-credits-for-max-and-team-plans
[fable-plan]: https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan
[max-plan]: https://support.claude.com/en/articles/11049741-what-is-the-max-plan
[cursor-pools]: https://prod.cursor.com/help/models-and-usage/usage-limits
[grok-doc]: https://cursor.com/docs/models/grok-4-7
[fable-vendor]: https://www.anthropic.com/claude-fable-and-mythos-5-2
[frontier2]: https://cognition.com/frontiercode
[frontier2-data]: https://cognition.com/data/frontier-code-2.0/data.json
[aa-v5]: https://artificialanalysis.ai/articles/artificial-analysis-intelligence-index-v5
[vals-fable]: https://www.vals.ai/models/anthropic_claude-fable-5-2
[vals-astra62]: https://www.vals.ai/models/openai_gpt-6.2-astra
[vals-sol62]: https://www.vals.ai/models/openai_gpt-6.2-sol
