---
date: 2026-10-01
---

# Recommendation table

Compiled on 2026-10-01 from published benchmarks and documentation, accessed on that date. No benchmark or delegated agent was run for this update. Published availability and a local model listing do not confirm account access.

Read [benchmark notes](benchmark-notes.md) when comparing Fable 5.1 with Opus 5.5, inspecting newly discovered models or agents, or updating this table. The notes record recommendation changes and their reasons.

## Evidence levels

- [T] is a measurement by an evaluator independent of the model vendor. The evaluator's product, grading, and harness can still affect the result.
- [V] is a vendor statement or vendor-run evaluation. Verify quoted third-party results at their original source.
- [I] is an inference or usage choice, with its reason stated.
- No data means no applicable published result was found. It is not a zero score.

Keep model version, effort, benchmark revision, and harness together. Scores from different setups are not interchangeable. Small differences without uncertainty estimates do not establish a reliable winner. The routing tiers below are [I], informed by the cited measurements.

## Catalog

Checked on 2026-10-01 with `codex debug models`, `cursor-agent --list-models`, and `claude --help`. See [harness.md](harness.md) for discovery commands and access verification.

| Model | Vendor | Codex | Claude Code | Cursor | Default |
| --- | --- | --- | --- | --- | --- |
| GPT-6 Astra | OpenAI | `gpt-6-astra` | N/A | N/A | `medium`, local catalog |
| GPT-6.1 Sol | OpenAI | `gpt-6.1-sol` | N/A | N/A | Codex `low`, local catalog; API `medium` [V] |
| GPT-6 Luna | OpenAI | `gpt-6-luna` | N/A | N/A | `medium`, local catalog |
| Opus 5.5 | Anthropic | N/A | `claude-opus-5-5` | `claude-opus-5-5-<effort>` | `medium` [V] |
| Sonnet 5.5 | Anthropic | N/A | `claude-sonnet-5-5` | `claude-sonnet-5-5-<effort>` | Claude Code `medium`; API `high` [V] |
| Fable 5.1, specialist candidate | Anthropic | N/A | `claude-fable-5-1` | `claude-fable-5-1-<effort>` | `high` [V]; Cursor marks every listed variant NO ZDR |
| Grok 4.7 | SpaceXAI / Cursor | N/A | N/A | `grok-4.7-<effort>` | `high` [V] |
| GPT-5.6 Terra, unranked | OpenAI | `gpt-5.6-terra` | N/A | `gpt-5.6-terra-<effort>` | `medium`, local catalog |

Pass effort explicitly. Local Codex lists `low`, `medium`, `high`, `xhigh`, and `max`, plus `ultra` for Astra and Sol. `ultra` can delegate automatically and has no measured recommendation here. Anthropic's CLI accepts `low` through `max`, including `xhigh`. Grok's listed range is `low` through `xhigh`. Prefer Cursor identifiers without `-fast` when preserving quota. GPT-6 Astra, Sol 6/6.1, and Luna 6 are absent from this account's Cursor list.

Specifications: [OpenAI catalog][openai-models], [Sol 6.1][openai-sol], [Opus][opus-doc], [Sonnet][sonnet-vendor], [Fable][fable-doc], and [Grok][grok-doc] [V]. Older versions and other vendors are accounted for in the [discovery decisions](benchmark-notes.md#discovery-decisions).

## Complexity and impact

Complexity, from simplest to hardest:

- Mechanical work extracts, renames, classifies, or transforms without a decision.
- A ready plan leaves a bounded implementation to execute.
- Long autonomous work has a ready plan and many unsupervised steps.
- Work without a plan requires the agent to choose the approach.

Impact is low when an error is quickly spotted and reversible, medium when it causes substantial rework, and high when it affects production, data, security, or a costly decision. Impact governs review [I]; it is not a model benchmark.

## Overrides

- Use GPT-6.1 Sol for every Sol recommendation and invocation, following the user decision of 2026-09-30 [I]. It now has its own [AA measurements dated 2026-09-29][aa-sol]. Older GPT-6 Sol scores remain attributed to that older model.
- Use Astra only when the user explicitly requests it for the task, fallback, or reviewer, following the decision of 2026-09-21 [I]. The published Plus estimate remains 5 to 45 messages per five hours [V, [Codex pricing][codex-price]].

Fable 5.1 has no general exclusion. The user's conditional removal decision of 2026-10-01 is not activated: planning lacks a direct test, and security coding and review have contrary measurements. See the [task comparison](benchmark-notes.md#fable-51-versus-opus-55).

## Recommendations

Use the catalog identifier and the row's effort with [harness.md](harness.md). Permissions follow the brief. Planning, research, and review use read-only access. Effort choices are [I] unless the evidence names that configuration.

| Kind | Complexity and impact | Model and effort | Harness | Evidence and reason |
| --- | --- | --- | --- | --- |
| Code | Mechanical | Luna `low` or `medium` | Codex | [I] Lowest listed Codex token rates [V]; no low-effort coding score used. |
| Code | Ready plan, low impact | Luna `max` | Codex | Rails tickets 18.3% at $0.191/run [T]. [I] Cheap, checkable work; escalate failures. |
| Code | Ready plan, medium impact | Sol `medium`; `xhigh` for harder work | Codex | Native Coding Agent Index 61.4/$0.70 per task at `medium`, 62.9/$1.04 at `xhigh` [T]. [I] Measured intermediate option above Luna. |
| Code | Long autonomous, medium impact | Opus 5.5 `medium` | Claude Code | FrontierCode 1.1 Main 54.64%/$0.802 at `medium` [T]. [I] Good default; greater effort is not consistently better. |
| Code | No plan or high impact | Opus 5.5 `high` | Claude Code | AA Index 54 at `high` [T]; FrontierCode 53.99% at `high` versus 54.64% at `medium` [T]. [I] Retain for ambiguous work, with independent review. |
| Planning | Simple and checkable | Luna `medium` | Codex | [I] Cost and checkability; no direct plan-quality test. |
| Planning | Medium | Sol `max` | Codex | AA Index 52/$0.72 per task [T] versus Opus `medium` 51/$1.34 [T]. [I] Reasoning proxy and API efficiency; included quota may change the choice. |
| Planning | Complex or high impact | Opus 5.5 `xhigh` | Claude Code | AA Index 56 at `xhigh`, 58 at `max` [T]. [I] Proxy only; independently check consequential assumptions. |
| Web research | Low stakes, lowest Codex draw | Luna `high` | Codex, web enabled | Parallel score 61.9, $33.1/1,000 tasks [T]. [I] Effort transfer to Codex is unmeasured. |
| Web research | Moderate stakes, cost matters | Sol `high` | Codex, web enabled | Parallel score 70.4, $130/1,000 tasks [T]. [I] New measured model, different search tools in Codex. |
| Web research | High stakes or decisive synthesis | Opus 5.5 `high` | Claude Code, web tools | Parallel score 75.4, highest on its 2026-09-30 board [T]. [I] Validate sources; effort and CLI transfer are unmeasured. |
| Code review | Routine | Sonnet 5.5 `max`; add Sol `xhigh` for Anthropic-authored code | Claude Code; Codex | Native coding tier 68.4 versus Opus 66.0 [T]. [I] Equal or higher coding tier for the primary review; Sol adds another vendor. General review quality is unmeasured. |
| Code review | Security-sensitive | Same primary review; add Grok 4.7 `high` | Claude Code; Cursor | Dam Secure recall 77.5%, $9.28/PR, 18m23s [T]. [I] Specialist supplement. Fable `high` is another candidate for permitted data, with 62.5% recall versus Opus 56.25%; neither replaces an equal-tier primary review. |
| Prose for humans | Editing and simplification | Grok 4.7 `high` | Cursor | [I] Existing usage preference; no reproducible direct reformulation comparison used. |
| Professional documents | Complex analysis and presentation | Opus 5.5 `high`; Sonnet 5.5 `max` as an alternative | Claude Code | AA-Briefcase combined Elo at `max`: Opus 1822, Sonnet 1811 [T]. [I] Professional-output proxy, not proof about literary style. |

Coding figures come from [AA's native-agent board][aa-code] and [Cognition's public dataset][frontier-data]. Rails uses its [minimal harness][rails]. Search uses [Parallel][parallel]; security review uses [Dam Secure][dam]. Reasoning and document proxies use [AA's Opus/Fable comparison][aa-pair], [Sol page][aa-sol-model], and [Sonnet evaluation][aa-sonnet]. All were accessed 2026-10-01; the setups are described below.

## Performance grids

### Planning proxies

No cited benchmark grades a repository plan separately from execution. These tiers are [I], based on AA Intelligence Index v4.3.2 in its API evaluation. They are not planning pass rates.

| Tier | Models and measured effort | Index [T] | Included pool |
| --- | --- | --- | --- |
| High | Opus 5.5 `max`; Sonnet 5.5 `max` | 58; 56 | Claude Max |
| Good | Fable 5.1 `max`; Astra `max`, explicit request only; Sol `max` | 53; 53; 52 | Claude Max with Fable cap; Codex Plus |
| Intermediate | Grok 4.7 `xhigh` | 46 | Cursor Models |
| Scoped | Luna `max` | 37 | Codex Plus |
| Unranked | Terra; other discovery candidates | No current planning comparison used | See discovery notes |

Sources: [Opus/Fable][aa-pair], [effort comparison][aa-efforts], [Sol][aa-sol-model], [Sonnet][aa-sonnet-model], [Astra][aa-astra], [Grok][aa-grok], and [Luna][aa-luna]. Opus's lower-effort scores are 51 at `medium`, 54 at `high`, and 56 at `xhigh` [T]. Their use in plans is [I].

### Code

AA Coding Agent Index combines DeepSWE v1.1, Terminal-Bench 4.0, and SWE-Atlas-QnA in each model's native CLI. Index values use a 0 to 100 scale. API task costs are not subscription deductions.

| Tier [I] | Combination | Index [T] | API dollars/task [T] | Evaluated CLI version |
| --- | --- | --- | --- | --- |
| High | Sonnet 5.5 `max`, Claude Code | 68.4 | 14.19 | 2.1.280 |
| High | Opus 5.5 `max`, Claude Code | 66.0 | 13.04 | 2.1.280 |
| Good | Sol `xhigh`, Codex | 62.9 | 1.04 | 0.154.0 |
| Good | Sonnet 5.5 `xhigh`, Claude Code | 62.9 | 3.33 | 2.1.280 |
| Good | Fable 5.1 `max`, Claude Code with fallback | 62.2 | 12.39 | 2.1.259 to 2.1.263 |
| Good | Astra `max`, Codex, explicit request only | 61.6 | 7.47 | 0.151.0 to 0.153.4 |
| Good | Sol `medium`, Codex | 61.4 | 0.70 | 0.154.0 |
| Intermediate | Grok 4.7 `xhigh`, Grok Build | 56.3 | 8.82 | 1.0.40 |
| Scoped | Sonnet 5.5 `medium`, Claude Code | 45.9 | 0.62 | 2.1.280 |
| Scoped | Luna `max`, Codex | 41.1 | 0.18 | 0.154.0 |

Source: [AA coding-agent board][aa-code], 2026-10-01 snapshot, including its embedded public results. A native Grok Build result does not establish the same result in Cursor. Transfer to another effort or harness is [I], including Opus `medium`/`high` recommendations. Newer CLI versions do not inherit measured gains automatically.

[FrontierCode 1.1 Main][frontier-data] measures mergeable changes separately [T]. Native harness scores: Opus `medium` 54.64%, Astra `max` 53.26%, Sonnet `xhigh` 52.09%, Fable `medium` 50.91%, Sol `medium` 50.23%, Grok `high` 47.59%, and Luna `max` 42.42%. Sonnet falls to 46.21% at `max`. Use `new_score`, which excludes flagged solution-bearing internet use; `correct` is not the revised score. CLI versions are unstated. [Cognition's changelog][frontier] added Sonnet on September 28 and Sol 6.1 on September 29.

AA's separate mini-swe-agent API test gives Sonnet `max` about 64% on Terminal-Bench 4.0 versus Opus `max` 59.6% [T, [Sonnet][aa-sonnet], [Opus][aa-opus]]. The native Claude Code component is 66.2%/63.1% [T]. Anthropic reports Sonnet 70.6% and Opus `xhigh` 66.4% in its own setup [V, [launch][sonnet-vendor]]. These are three distinct comparisons.

[Rails Stage 2][rails-method] measures 20 feature tickets on Fizzy, three runs per model/effort, hidden checks, and a shared minimal shell harness without internet. Its 2026-10-01 [board][rails] still has Opus `medium` 33.3%, Fable `high` and `max` 31.7%, Sol 6 `medium` 21.7%, and Luna `max` 18.3% [T]. Sol 6.1 and Sonnet 5.5 have no result there. Opus's 1.6-point gap is one success among 60 runs. It establishes neither broad superiority nor a Symfony pass rate.

### Web research

[Parallel][parallel], updated 2026-09-30, uses 100 questions each from DSQA, HLE, and WISER. It supplies Search Fast and Extract, disables code execution, and averages three scores. Reasoning settings can differ by model; exact effort is unstated in the table.

| Tier [I] | Model | Search score [T] | API and tool dollars/1,000 tasks [T] |
| --- | --- | --- | --- |
| High in this setup | Opus 5.5 | 75.4 | 949 |
| High in this setup | Fable 5.1 | 72.7 | 1,655 |
| Good in this setup | Astra, explicit request only | 70.8 | 401 |
| Good in this setup | Sol 6.1 | 70.4 | 130 |
| Scoped in this setup | Luna 6 | 61.9 | 33.1 |
| Unranked | Sonnet 5.5; Grok 4.7; Terra | No same-version result | N/A |

These scores do not measure the three installed CLIs' web tools. Cost records may omit recovery attempts. The previous 75.5/69.3 Opus/Fable snapshot is superseded, not a measured trend on fixed runs.

### Code review

There is no general-review ranking here. The primary reviewer uses the code grid as a proxy [I]; Sonnet's stronger coding index is not a review measurement.

| Security-review setup | Grok 4.7 | Fable 5.1 | Opus 5.5 | Sol 6.1 / Sonnet 5.5 |
| --- | --- | --- | --- | --- |
| Dam Secure, 16 planted bugs, five runs per PR, `high` [T] | 77.5% recall, via Vercel | 62.5% recall | 56.25% recall | No data |

Source: [Dam Secure, 2026-09-24][dam], reread on 2026-10-01. Its Sol 6 result is 63.75%; that score does not belong to Sol 6.1. Fable's advantage is a counterexample, not proof of better general review. Endor tests generated secure code, not review; see the [Fable comparison](benchmark-notes.md#fable-51-versus-opus-55).

### Writing and professional outputs

| Use | Evidence | Routing consequence [I] |
| --- | --- | --- |
| Professional deliverables | AA-Briefcase combined Elo: Opus `max` 1822, Sonnet `max` 1811, Fable `max` 1678; GDPval-AA Elo: 1846, 1844, 1735 [T] | Opus or Sonnet; these tests combine analysis, execution, and presentation. |
| Human-facing prose and reformulation | No reproducible direct comparison used for the selected models | Retain the Grok preference as [I]; excluded reports are recorded in the notes. |

Sources: [AA comparison][aa-pair] and [Sonnet evaluation][aa-sonnet]. AA's September 22 Opus article reported Fable's Briefcase Elo as 1679, versus 1678 now. It also noted Fable's slightly better rubric subscore. Neither rounding nor the aggregate establishes superiority on every document or writing task.

## Cost: the subscription decides the order

The existing assumptions are ChatGPT Plus, Claude Max, and Cursor Pro [I]. These are separate pools. API dollars cannot establish exact subscription cost per completed task.

| Model | Standard API input/output dollars per million [V] | Codex output credits/million [V] |
| --- | --- | --- |
| Luna 6 | 0.10 / 0.50 | 12.5 |
| Sol 6.1 | 2 / 10 | 250 |
| Astra | 10 / 50 | 1,250 |
| Opus 5.5 | 4 / 20 | N/A |
| Sonnet 5.5 | 2 / 10 | N/A |
| Fable 5.1 | 10 / 50 | N/A |
| Grok 4.7 | 2 / 6 | N/A |

Sources: [OpenAI API][openai-price], [Codex credits][codex-price], [Anthropic references][fable-doc], [Sonnet launch][sonnet-vendor], and [Grok][grok-doc], accessed 2026-10-01. Prices exclude tools, caching, long context, and special processing. Sol 6.1 cached input is $0.10/million versus Sol 6's $0.20 [V]. Fable cached input is $0.25 versus Opus $0.20 [V]; the 2.5-times input/output ratio is not a cached-token ratio.

| Subscription | Published limits and billing [V] | Routing implication [I] |
| --- | --- | --- |
| Codex Plus | Five-hour estimate: Luna 350 to 3,000, Sol 6.1 15 to 160, Astra 5 to 45; weekly limits may apply. Fast uses included allowance at 2.5 times Standard. | Luna conserves this pool; Sol is intermediate. Astra remains explicit request only. |
| Claude Max | Five-hour and weekly limits shared with Claude Code. Fable may use at most 50% of the existing weekly allowance; it adds no allowance. A numeric Fable/Opus per-task quota multiplier is unpublished. | Opus is the general default; Fable remains a specialist candidate. Sonnet `max` costs more API dollars than Opus in AA's coding workload; its quota ratio is unmeasured. |
| Cursor Pro | Separate Cursor Models and Other Models pools. Grok/Composer draw the former; Anthropic models draw the latter. Grok Standard $2/$6, Fast $4/$12. | Grok preserves the third-party pool. Balances, routing, and subagents determine actual consumption. |
| API | Token and tool billing, outside these subscriptions | Confirm a paid API path separately from included CLI access. |

Sources: [Codex][codex-price], [Claude Max][max-plan], [Fable limits][fable-plan], [Cursor pools][cursor-pools], and [Grok prices][grok-doc], accessed 2026-10-01. On Claude Pro, Fable uses paid usage credits from the start [V].

Fable/Opus cost depends on workload [T]: AA Intelligence Index `max` costs $7.63/$5.98 per task, but native Coding Agent Index `max` costs $12.39/$13.04. Opus is cheaper in the former and about 5% more expensive in the latter. [Comparison notes](benchmark-notes.md#fable-51-versus-opus-55) include Rails, Parallel, and Endor costs. No single quota multiplier follows.

## Gaps

- Planning is inferred from reasoning and professional-work tests. No direct independent plan-quality comparison was found.
- General review and literary style have no direct ranking here. Security recall, secure-code generation, and coding indices measure different work; the notes explain an excluded writing report.
- No exact CLI search head-to-head or current Symfony head-to-head was found.
- Anthropic evaluations can include fallbacks. Sonnet's AA API evaluation used a pre-release structured-output bug, fixed before release; AA planned reruns [T, [Sonnet article][aa-sonnet]]. Observe the actual served model.
- Coding sets can have contamination, defective tests, subjective grading, or scope penalties. Endor removes memorized solutions; FrontierCode zeros solution-bearing internet use. Compare revised scores.
- Review tiers transfer coding evidence [I]. A different vendor supplies independence, not a measured improvement on these combinations.
- Exact account access, remaining balances, and model-specific Claude quota multipliers are unverified. Listing and help text alone are insufficient.

## Sources

All accessed 2026-10-01. Dates are publication dates where given; a snapshot records a live page read, not a claimed publication date.

| Source | Date | Evidence and setup |
| --- | --- | --- |
| [AA Opus][aa-opus], [Opus/Fable][aa-pair], [efforts][aa-efforts] | 2026-09-22; comparison snapshots 2026-10-01 | [T] Intelligence Index v4.3.2, API effort/default fallback; Stirrup for Briefcase work. |
| [AA Sol 6.1][aa-sol], [model][aa-sol-model] | 2026-09-29; snapshot 2026-10-01 | [T] Same-version API reasoning/cost and native Codex coding. |
| [AA Sonnet][aa-sonnet], [model][aa-sonnet-model] | 2026-09-28; snapshot 2026-10-01 | [T] API effort sweeps, mini-swe-agent, pre-release caveat. |
| [AA coding agents][aa-code] | Snapshot 2026-10-01 | [T] Native combinations/versions; embedded page data includes values absent from text extraction. |
| [AA Grok][aa-grok], [Sol/Luna 6][aa-luna], [Astra][aa-astra] | 2026-09-21, 2026-09-22, 2026-09-09 | [T] Same-version reasoning and efficiency. |
| [FrontierCode][frontier], [public data][frontier-data] | Additions 2026-09-28/29; snapshot 2026-10-01 | [T] Native runs, v1.1 Main `new_score`, mergeability/internet corrections. |
| [Rails][rails], [Stage 2][rails-method] | Method 2026-09-09; board snapshot 2026-10-01 | [T] Minimal harness, 20 tickets, three runs each. |
| [Parallel][parallel] | Updated 2026-09-30 | [T] Search Fast/Extract, 300 questions, variable reasoning configuration. |
| [Dam Secure][dam] | 2026-09-24 | [T] Planted-bug review, `high`, five runs; routes differ. |
| [Endor][endor] | 2026-09-24 | [T] Secure-code generation, Claude Code, 200 tasks/179 graded, memorization excluded; CLI versions differ. |
| [OpenAI catalog][openai-models], [Sol][openai-sol], [changelog][openai-changelog], [API prices][openai-price], [Codex prices][codex-price] | Sol release 2026-09-29; snapshots 2026-10-01 | [V] IDs, effort, prices, credits, and limits. |
| [Opus][opus-doc], [Fable][fable-doc], [Sonnet][sonnet-vendor] | Releases 2026-09-22, 2026-09-01, 2026-09-28 | [V] Specifications and vendor-run coding figures. |
| [Fable limits][fable-plan], [Claude Max][max-plan] | Snapshot 2026-10-01 | [V] Shared usage/Fable cap, not a per-task multiplier. |
| [Cursor pools][cursor-pools], [Grok][grok-doc] | Snapshot 2026-10-01 | [V] Pools, speed tiers, and context pricing. |

## Updating

1. Search dated announcements, release notes, model cards, independent evaluator feeds, and agent leaderboards for new models, versions, and CLI harnesses. Include vendors outside current recommendations. Record the cutoff and distinguish released, preview, announced, and inaccessible products.
2. Run `command -v` for known CLI names and newly discovered executable names. Read installed versions and `--help`. Read exposed model catalogs with [harness.md](harness.md); record failures and missing non-interactive catalogs. Compare with the previous inventory. Use listing commands without starting agents or installing software.
3. Give every newly released or newly considered model/harness a disposition: ranked for named tasks, unranked with missing evidence/access stated, or ignored with a reason. Record exact IDs, effort, visibility, retention flags, and harness version. Separate listing/documented availability from a verified inference request.
4. Reread retained sources and search newer revisions and counterexamples. Record publication/snapshot and access dates, task, metric, revision, effort, harness/version, and evidence level. Read public datasets or embedded results when dynamic charts omit values. Retrieval failures are gaps, not confirmation.
5. Rebuild grids and recommendations from comparable results. Mark proxy transfers [I]. Keep old measurements under the old model. Resolve contradictions by task/setup; avoid averaging unrelated scores or treating benchmark counts as real-world task frequencies.
6. Recheck prices, pools, caps, availability, confidentiality, and user overrides. Activate a conditional exclusion only when supported, retaining counterexamples beside the decision.
7. Record every recommendation change and reason in [benchmark notes](benchmark-notes.md). Update examples and `SKILL.md`; update `README.md` when descriptions or links change. Verify actual catalog IDs, source links, local pointers, table structure, and the final diff.
8. Set both frontmatter `date` and compilation date after completion. Distinguish sources reread this time from retained older snapshots. Finish when every discovery/change is accounted for and every number has dated, named evidence.

[aa-opus]: https://artificialanalysis.ai/articles/claude-opus-5-5
[aa-pair]: https://artificialanalysis.ai/models/comparisons/claude-opus-5-5-vs-claude-fable-5-1
[aa-efforts]: https://artificialanalysis.ai/models/releases/comparisons/claude-opus-5-5-vs-claude-fable-5-1
[aa-sol]: https://artificialanalysis.ai/articles/gpt-6-1-sol-replaces-gpt-6-sol-after-just-7-days-with-near-astra-intelligence
[aa-sol-model]: https://artificialanalysis.ai/models/gpt-6-1-sol/
[aa-sonnet]: https://artificialanalysis.ai/articles/claude-sonnet-5-5
[aa-sonnet-model]: https://artificialanalysis.ai/models/claude-sonnet-5-5
[aa-code]: https://artificialanalysis.ai/agents/coding-agents
[aa-grok]: https://artificialanalysis.ai/articles/benchmarking-grok-4-7
[aa-luna]: https://artificialanalysis.ai/articles/gpt-6-sol-and-luna-push-the-cost-efficiency-frontier
[aa-astra]: https://artificialanalysis.ai/articles/benchmarking-gpt-6-astra
[frontier]: https://cognition.com/frontiercode
[frontier-data]: https://cognition.com/data/frontiercode-leaderboard/data.json
[rails]: https://rubyonrails.org/ai
[rails-method]: https://rubyonrails.org/2026/9/9/agents-on-rails-stage-2
[parallel]: https://parallel.ai/leaderboard
[dam]: https://docs.damsecure.ai/blog/openai-gpt-6-sol-closes-in-on-deepseek-v4-1-flash-security-benchmark/
[endor]: https://www.endorlabs.com/learn/opus-5-5-6x-cheaper-and-2x-faster-than-fable-5-1-but-memorization-keeps-it-off-the-top-spot
[openai-models]: https://developers.openai.com/api/docs/models
[openai-sol]: https://developers.openai.com/api/docs/models/gpt-6.1-sol
[openai-changelog]: https://developers.openai.com/api/docs/changelog
[openai-price]: https://developers.openai.com/api/docs/pricing
[codex-price]: https://learn.chatgpt.com/docs/pricing
[opus-doc]: https://platform.claude.com/docs/en/models/opus-5-5/overview
[fable-doc]: https://platform.claude.com/docs/en/models/fable-5-1/overview
[sonnet-vendor]: https://www.anthropic.com/claude-sonnet-5-5
[fable-plan]: https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan
[max-plan]: https://support.claude.com/en/articles/11049741-what-is-the-max-plan
[cursor-pools]: https://prod.cursor.com/help/models-and-usage/usage-limits
[grok-doc]: https://cursor.com/docs/models/grok-4-7
