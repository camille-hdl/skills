---
date: 2026-10-01
---

# Benchmark update notes

Update cutoff and source access: 2026-10-01. Evidence levels and current routing are defined in [table.md](table.md). This update used published results, local version/help commands, and model listings. It launched no agent, inference request, benchmark, or installation.

## Recommendation changes

Compared with the table whose frontmatter was 2026-09-30 and compilation date was 2026-09-24:

| Cell or rule | Change | Reason and limit |
| --- | --- | --- |
| Sol override | Keep `gpt-6.1-sol`; replace provisional Sol 6 proxies with Sol 6.1 results. | [T] AA's September 29 evaluation now measures the exact model. Rails and Dam Secure still measure Sol 6; those scores retain that name. |
| Ready plan, medium-impact code | Add Sol `medium`, with `xhigh` for harder work. | [I] Native Codex index 61.4/$0.70 at `medium`, 62.9/$1.04 at `xhigh` [T] supplies a measured option between Luna and Opus. |
| Medium planning | Retain Opus `medium`; record Sol `max` as a subscription-dependent candidate. | [I] Sol's AA proxy 52/$0.72 versus Opus 51/$1.34 [T] is one point without uncertainty. It justifies neither a quality replacement nor a Claude Max versus Codex Plus quota saving. No direct planning measurement. |
| Simple planning | Make Luna `medium` explicit. Replace the old optional Sol `high` escalation with the medium-planning row. | [I] Retains the checkable-work preference; escalation follows the retained Opus default, with Sol as a subscription-dependent candidate. |
| Moderate web research | Add Sol `high`. | [I] Parallel now lists Sol 6.1 at 70.4/$130 per 1,000 tasks [T]. Transfer to Codex tools and this effort remains unmeasured. |
| Low/high-stakes web research | Keep Luna `high` / Opus `high`; replace missing/old search evidence. | [T] Updated Parallel scores are 61.9 and 75.4; Fable is now 72.7. These replace the September 22 snapshot, not a controlled before/after test. |
| Routine review | Retain independent Opus `high` as the primary default; the additional Sol review becomes `xhigh`. Record Sonnet, preferably `xhigh`, as a candidate. | [I] Sonnet `max` leads native AA 68.4 versus 66.0 but loses FrontierCode 46.21% versus Opus `medium` 54.64%, `high` 53.99%, and `max` 54.43% [T]. The small AA gap without uncertainty does not establish a winner. Sonnet `xhigh` outperforms its `max` on FrontierCode and costs less on AA. General-review quality remains unmeasured; apply the author's configuration/tier rule. |
| Security review | Keep Grok `high` as a supplement; record Fable `high` as an unvalidated specialist candidate for permitted data. | [T] Dam Secure recall is 77.5% Grok, 62.5% Fable, 56.25% Opus at `high`. Fable's five extra detections over 80 reviews of 16 bugs are a weak signal. Sol 6 scores 63.75%/$1.81 per PR versus Fable $7.31; do not transfer that result to Sol 6.1. The equal-tier primary review remains required. |
| Professional documents | Add Opus `high`, with Sonnet `max` as an alternative. | [I] AA-Briefcase/GDPval aggregate results favor these models at `max` [T]. Opus `high` transfers effort; literary style is not measured. |
| Fable eligibility | Add measured Fable tiers and an unvalidated security-review candidate; do not activate a general exclusion. | [I] Endor's coding counterexample and the planning gap prevent activation. Dam Secure is only a weak signal; `low` comparisons also favor Fable without proving broad superiority. |
| Fallback/review grids | Add Sonnet and measured efforts; place Astra with Fable/Sol in the good reasoning tier and the good native coding tier. | [I] Named configurations, not model families, carry ranks. Astra's explicit-request-only override still wins. |
| Code escalation | Drop the generic instruction to raise Opus from `medium` to `high` on failure. | [I] FrontierCode is non-monotonic by effort. Retry or change configuration based on the failure, not a presumed gain. |

Unchanged: mechanical code uses Luna `low`/`medium`; low-impact ready-plan code uses Luna `max`; long autonomous code uses Opus `medium`; unplanned/high-impact code uses Opus `high`; complex planning uses Opus `xhigh`; human-facing editing uses Grok `high`; Astra requires an explicit request; Terra has no recommended cell. These are choices [I], not claims of winning every benchmark.

Removed ancillary ARC/PHP figures from the routing table; they neither grade plans nor compare these exact current models on Symfony. The gaps remain explicit. No fresh Symfony head-to-head was found in this search.

Sources for changes: [AA Sol, September 29][sol], [AA Sonnet, September 28][sonnet], [native coding board][coding], [effort comparison][efforts], [FrontierCode data][frontier], [Parallel][parallel], and [Dam Secure, September 24][dam]. Live boards were read on October 1; Parallel states September 30 as its update date.

## Discovery decisions

Discovery covered [AA's dated article feed][feed], its [coding-agent board][coding], the [OpenAI changelog][openai], [Anthropic's Sonnet release][sonnet-vendor], and local catalogs. Newly considered does not mean newly released: release dates are asserted only when a source states them.

| Model or version | Status / local identifier | Disposition and reason |
| --- | --- | --- |
| GPT-6.1 Sol, released September 29 | Codex `gpt-6.1-sol`; absent from this Cursor catalog. | Ranked for reasoning proxies, native coding, and search. Its identifier was already adopted September 30; the new discovery is its dated evidence and local `low` default. |
| Claude Sonnet 5.5, released September 28 | Claude `claude-sonnet-5-5`; Cursor `claude-sonnet-5-5-<effort>`, `low` through `max`. | Ranked for reasoning/native coding/professional work; review use [I]. No same-version direct search or security-review result used. |
| Gemini 4 Argon, announced September 30 | Selected-user preview; absent locally. | Unranked for local routing despite AA Index 53 at `high` and Antigravity native coding 63.8/$5.84 [T]. AA marks that agent unavailable. Do not install or assume preview access. |
| Solar Mini 4, released September 30 | Absent locally. | Ignored for current routing: no installed path; AA Index 24 and $0.36/task versus Luna 37/$0.07 [T]. This does not exclude specialized uses. |
| Claude Fable 5.1 | Claude `claude-fable-5-1`; Cursor `claude-fable-5-1-<effort>` and thinking variants, all marked NO ZDR. | Ranked only where evidence applies; unvalidated specialist review candidate. No blanket exclusion; confidentiality policy still applies. |
| GPT-5.6 Terra | Codex `gpt-5.6-terra`; Cursor variants including `none`, `low` through `max`, and Fast. | Unranked against current alternatives; no new same-version task comparison used. |
| Gemini 3.8/3.7/3.6 Flash and 3.1 Pro | Cursor examples `gemini-3.8-flash-high`, `gemini-3.7-flash-high`, `gemini-3.6-flash-high`, `gemini-3.1-pro`. | Unranked for Cursor routing. AA's Gemini 3.8 native result is Antigravity SDK, not Cursor; Rails/Parallel offer partial evidence, not a complete task grid. |
| Muse Spark 1.3 | Cursor `muse-spark-1.3-<effort>`, `minimal` through `max`. | Unranked for Cursor. AA's 54.3/$3.98 native result is Muse Code at `max`; that CLI is absent. |
| Kimi K3 / K2.7 Code | Cursor `kimi-k3-low`, `kimi-k3-high`, `kimi-k3-max`, `kimi-k2.7-code`. | Unranked for Cursor. AA's K3 51.9/$5.05 is Kimi Code CLI with no effort in its label; it is not the Cursor `max` result. |
| GLM 5.2 / GLM 5.3 | Cursor `glm-5.2-high`/`max`; no local GLM 5.3 listing. | Unranked. AA's 53.6/$4.24 is GLM 5.3 `max` in OpenCode; neither model-version nor harness transfers to GLM 5.2 in Cursor. |
| DeepSeek V4.1 Flash; GLM 5.3 Flash | Dam Secure's September 24 API review comparison; absent from local catalogs. | Unranked for local routing. DeepSeek recall 63.75%/$0.42 is useful specialist evidence [T], but no installed model path was found. GLM Flash is a different version from Cursor's GLM 5.2. |
| DeepSeek V4 Pro/Flash, Mistral 3.5 Medium, Nemotron 3 Ultra, SWE-2 | Additional models in the FrontierCode dataset; no local model listing. | Ignored for current default routing: no installed model path. SWE-2 in a hybrid agent is not a result for its host model alone. |
| Composer 2.5 | Cursor `composer-2.5`, `composer-2.5-fast`. | Unranked; no comparable current independent result used. Its Cursor Models pool is documented [V], not a quality rank. |
| Older GPT, Claude, Grok, and Gemini versions | Still selectable in local catalogs, including Sol 6, GPT-5.6 Sol/Luna, GPT-5.5, Claude 4.x/5.0, Grok 4.5/4.6, Gemini 3/3.5. | Ignored for default routing because current families are the scope. Preserve historical scores; re-evaluate if a user requests one. |
| `gpt-reserve`, `codex-auto-review` | Hidden Codex catalog entries. | Ignored: internal/non-user-facing identifiers, not selectable recommendations. |
| Mythos 5.1 | Fable documentation names a restricted equivalent. | Ignored for this catalog: restricted access, no installed route verified. |
| Pareto 26.9 | Parallel's own product appears in its search board. | Ignored for agent routing: vendor result [V] and no installed CLI path. |
| AA-AgentPerf-Local, September 29 | Performance measurement tool in the article feed. | Ignored as an agent candidate: local speed testing is a different purpose, not a model-quality score. |

Preview and new-model sources: [Gemini Argon][argon], [Solar Mini][solar], [Fable overview][fable-doc], and [Parallel][parallel]. Catalog observations are local, not an account-access test.

### Harness inventory

| Harness or executable | Local observation on 2026-10-01 | Disposition |
| --- | --- | --- |
| Codex | `codex-cli 0.159.3`; `debug models` succeeds. | Retain. AA Sol/Luna runs used 0.154.0, not this installed version. |
| Claude Code | 2.1.286; `--help` exposes `opus`, `sonnet`, `fable`, exact IDs, and effort. | Retain. No non-interactive model-list command found; help/docs do not verify inference access. AA Opus/Sonnet used 2.1.280. |
| Cursor | 2026.09.28-64d2043; both `cursor-agent` and `agent` resolve to the same executable. | Retain one harness; record `agent` as an alias. `--list-models` succeeds; help also exposes `models`. No duplicate benchmark/rank for the alias. |
| Herdr | Found by `command -v`. | Retain as an orchestration tool. No pane or session created; no claim about its version or availability in this session. |
| Grok Build | AA 1.0.40; neither `grok` nor `grokbuild` installed. | Newly considered, unranked for local use; its published result remains attributed to that CLI. See [vendor][grokbuild]. |
| Antigravity CLI / SDK | AA CLI 1.2.10 / SDK 0.1.12 to 0.1.16; `agy`, `antigravity`, and `gemini` absent. | Newly considered, unranked locally; Argon is a restricted preview. |
| Muse Code | AA 1.0.3-R2198.1; `muse` absent. | Newly considered, unranked locally; account/installation unknown. |
| Kimi Code CLI | AA 0.26, 0.36, 0.36.1; `kimi` absent. | Newly considered, unranked locally; no access test. |
| OpenCode | AA 1.18.29; `opencode` absent. | Newly considered, unranked locally; GLM 5.3 results do not transfer to Cursor GLM 5.2. |
| Devin Fusion CLI | AA v3000.10.7; `devin` and `fusion` absent. | Newly considered, unranked locally. Hybrid Astra/SWE-2 and Fable/SWE-2 configurations are not solo-model results. |
| Other known CLIs | `aider`, `goose`, `amp`, `droid`, `pi`, `copilot`, `qwen` absent. | No local ranking or launch form assumed; recheck at the next update. |

Executable names are search candidates, not inferred installation instructions. Missing `command -v` results establish absence from this PATH only. The tested-command history and current help checks are separate in [harness.md](harness.md).

## Fable 5.1 versus Opus 5.5

The user's conditional exclusion is not activated. Opus is the better-supported general default [I], but "Fable is inferior on most real tasks, especially planning" is not proved by these evaluations. A benchmark-component count is not a distribution of the user's tasks.

For a future update to activate that conditional exclusion, require a direct repository-planning comparison that favors Opus beyond uncertainty on representative tasks, and comparable current coding evidence that resolves Endor's adjusted functional-pass counterexample. Establish that the affected categories cover most of the user's work rather than counting benchmark components. Keep the same evidence threshold for both models: a small gap without uncertainty is insufficient. These are evidence requirements for the existing conditional decision [I], not new model restrictions. Until they are met, keep Fable eligible and record remaining counterexamples.

| Task | Published comparison, Opus versus Fable | Verdict and limits |
| --- | --- | --- |
| Planning | AA Index `max` 58 versus 53; `xhigh` 56 versus 53; `high` 54 versus 51; `medium` 51 versus 49; `low` 42 versus 47 [T, API with default fallback]. | Opus leads reasoning proxies at equal effort from `medium` upward; Fable leads at `low`. No direct repository-plan-quality test was found. Prefer Opus for complex planning [I]; do not claim a measured planning win. |
| General code | Native AA index `max` 66.0 versus 62.2 [T]; FrontierCode 1.1 Main `medium` 54.64% versus 50.91%, but `low` 47.30% versus 49.82% [T]; Rails Opus `medium` 33.3% versus Fable `high`/`max` 31.7% [T]. | Several setups favor Opus, but FrontierCode reverses at `low`. That 2.52-point gap lacks uncertainty and establishes no reliable winner. AA CLI versions differ and both `max` configurations include fallback; Rails' gap is one success in 60 runs and effort differs. These are not all coding tasks. |
| Secure-code generation | Endor, September 24: adjusted FuncPass 68.7% versus 87.2%; SecPass 33.5% versus 37.4% [T]. | Coding counterexample after excluding memorized solutions: Fable has 33 more functional passes among 179 graded tasks. SecPass differs by only seven tasks and does not alone establish a reliable security winner. 200 tasks/179 graded, one run each, effort unstated, Claude Code 2.1.280 versus 2.1.258. This measures generation, not review. |
| Security review | Dam Secure, September 24: recall 56.25% versus 62.5%, both `high` [T]. | Weak signal, five extra detections in 80 reviews of only 16 distinct bugs, without uncertainty. Custom isolated API agent, CLI versions N/A. Fable costs $7.31/PR versus Opus $1.92; Sol 6 scores 63.75%/$1.81. No reliable security or general-review winner follows; Fable is an unvalidated candidate. |
| Research | Parallel, updated September 30: 75.4 versus 72.7; $949 versus $1,655 per 1,000 tasks [T]. | Opus leads this common Search Fast/Extract setup. Exact model effort is unstated; installed CLI search tools differ. |
| Professional outputs | AA-Briefcase combined Elo `max` 1822 versus 1678; GDPval-AA 1846 versus 1735 [T]. | Opus leads aggregates, but Fable's rubric subscore is slightly higher in AA's September 22 discussion. Analytical/presentation quality is not pure prose quality. |
| Prose and reformulation | No reproducible direct comparison used. Anthropic's Opus writing improvement is a vendor claim [V]. | Insufficient evidence for a general prose verdict or a replacement of the Grok usage preference [I]. |

The [Anthropic Opus launch][opus-vendor], September 22, adds vendor evidence [V]: Terminal-Bench 4.0 66.4% Opus `xhigh` versus 55.8% Fable `max`, and CursorBench 57.8% versus 51.8% under its reported settings. Vendor harness and effort differences prevent treating these as replication of AA's native runs.

Endor counted 51 Opus versus 17 Fable tasks as memorization/cheating. Before those deductions, its pass figures favor Opus; retain the adjusted published figures. This penalty and single-run design are part of the counterexample, not evidence that Fable wins secure coding in general.

### Relative cost and quota

| Setup | Opus versus Fable | What it establishes |
| --- | --- | --- |
| Standard API, dollars/million input/output [V] | $4/$20 versus $10/$50; cached input $0.20 versus $0.25. | Fable input/output tokens cost 2.5 times as much; cached input costs 1.25 times as much. Completed-task and quota ratios differ. |
| AA Intelligence Index, `max` [T] | $5.98 versus $7.63/task. | Opus costs about 22% less in this workload. |
| AA native Coding Agent Index, `max` [T] | $13.04 versus $12.39/task. | Opus costs about 5% more here, despite cheaper token prices. |
| FrontierCode 1.1 Main, `medium` [T] | $0.802 versus $3.284/task. | Opus costs about 76% less in this workload. |
| Rails, Opus `medium` / Fable `high` [T] | $2.78 versus $9.14/run. | Different efforts; not a universal price multiplier. |
| Endor, entire 200-task run [T] | $116 versus $672. | Opus costs about 83% less in that run; grading exclusions affect quality, not this total. |
| Claude Max [V] | Shared weekly allowance; Fable capped at 50% of the existing weekly allowance. | Fable adds no allowance. A model-specific per-task deduction ratio is unpublished; no exact quota comparison can be proved. |

Costs use the matching source in the task table, [Anthropic model documentation][fable-doc], [Opus documentation][opus-doc], and [Claude's Fable plan limits][fable-plan]. All accessed October 1. These API benchmark costs are not bills under Claude Max.

### Evidence excluded from ranking

An evaluator's [Reddit writing post][writing-post] reports ten script tasks, five samples each, and three LLM judges. It also gives conflicting Opus/Fable Elo figures (2631/2324 and 2600/2303), supplies no public rubric/dataset, and says details will be published later. Record it as an unverified report, not a reproducible writing rank. Publication date could not be established from the relative-time page; accessed 2026-10-01.

Sources for the comparison: [AA Opus article, September 22][opus], [AA effort comparison][efforts], [AA native coding board][coding], [FrontierCode revised data][frontier], [Rails method, September 9][rails-method] and [board][rails], [Endor, September 24][endor], [Dam Secure, September 24][dam], and [Parallel][parallel]. Live comparisons were read October 1. Details of harnesses and revisions stay beside the figures in [table.md](table.md#sources).

[sol]: https://artificialanalysis.ai/articles/gpt-6-1-sol-replaces-gpt-6-sol-after-just-7-days-with-near-astra-intelligence
[sonnet]: https://artificialanalysis.ai/articles/claude-sonnet-5-5
[coding]: https://artificialanalysis.ai/agents/coding-agents
[efforts]: https://artificialanalysis.ai/models/releases/comparisons/claude-opus-5-5-vs-claude-fable-5-1
[frontier]: https://cognition.com/data/frontiercode-leaderboard/data.json
[parallel]: https://parallel.ai/leaderboard
[dam]: https://docs.damsecure.ai/blog/openai-gpt-6-sol-closes-in-on-deepseek-v4-1-flash-security-benchmark/
[feed]: https://artificialanalysis.ai/articles
[openai]: https://developers.openai.com/api/docs/changelog
[sonnet-vendor]: https://www.anthropic.com/claude-sonnet-5-5
[argon]: https://artificialanalysis.ai/articles/gemini-4-argon-google-top-three-labs
[solar]: https://artificialanalysis.ai/articles/korean-ai-lab-upstage-releases-solar-mini-4
[grokbuild]: https://x.ai/build
[opus]: https://artificialanalysis.ai/articles/claude-opus-5-5
[opus-vendor]: https://www.anthropic.com/claude-opus-5-5
[fable-doc]: https://platform.claude.com/docs/en/models/fable-5-1/overview
[opus-doc]: https://platform.claude.com/docs/en/models/opus-5-5/overview
[fable-plan]: https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan
[rails-method]: https://rubyonrails.org/2026/9/9/agents-on-rails-stage-2
[rails]: https://rubyonrails.org/ai
[endor]: https://www.endorlabs.com/learn/opus-5-5-6x-cheaper-and-2x-faster-than-fable-5-1-but-memorization-keeps-it-off-the-top-spot
[writing-post]: https://www.reddit.com/r/ClaudeAI/comments/1wr03jc/55_is_insane_it_almost_broke_our_benchmark_i/
