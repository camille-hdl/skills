---
date: 2026-10-16
---

# Benchmark update notes

Update cutoff and source access: 2026-10-16. Evidence levels and current routing are defined in [table.md](table.md). This update used published results, local version/help commands, and model listings. It launched no agent, inference request, benchmark, or installation.

## Recommendation changes

Compared with the table dated 2026-10-01:

| Cell or rule | Change | Reason and limit |
| --- | --- | --- |
| Mechanical code | Keep Luna `low`/`medium`; add Haiku 5.5 `medium` in Claude Code when the Claude pool is preferred. Replace "no low-effort coding score" with FrontierCode figures. | [I] FrontierCode Main gives Luna `low` 25.66%/$0.020, `medium` 35.53%/$0.051 and Haiku `medium` 41.63%/$0.130 [T]. That test grades mergeable feature work, not mechanical edits, so it does not justify displacing the cheaper Codex default. |
| Ready plan, low-impact code | Keep Luna `max`; add Haiku 5.5 `xhigh` as the Claude Code alternative. Replace the Rails Stage 2 figure with the Stage 3 combined score. | [I] Same tier: native AA Haiku `xhigh` 41.4/$0.61 versus Luna `max` 41.1/$0.18; FrontierCode 45.83% versus 42.42% [T]. Small gaps without uncertainty, and Luna costs less per task. Haiku `xhigh` beats Haiku `max` on native AA (41.4 versus 36.5), so `max` is not the default. |
| Long autonomous code | Keep Opus `medium`; record Opus `xhigh` as a candidate. | [T] Rails Stage 3 combined: Opus `xhigh` 65.3%/$10.53 versus `medium` 56.1%/$3.84, `xhigh` 72.2% on multi-step tasks. FrontierCode Main has `medium` 54.64% above `xhigh` 51.42%. Applicable results conflict, so the previous cell stands [I]. |
| Low-stakes web research | Keep Luna `high`; add Haiku 5.5 as the Claude pool alternative. | [T] Parallel, October 13: Haiku 62.9/$24.3 versus Luna 61.9/$33.1 per 1,000 tasks. One point without uncertainty; effort unstated [I]. |
| High-stakes web research | Keep Opus `high`; record Sonnet 5.5 as a candidate. | [T] Parallel now measures Sonnet: 74.1/$796 versus Opus 75.4/$949. Fable moves to 73.4/$1,762. |
| Planning proxy grid | Add Haiku 5.5 `max` (43) to the scoped tier; Luna `max` reads 38. | [T] AA Index v4.3.2. Luna's 37 to 38 change carries no rerun note, so it is a snapshot difference, not a measured trend. |
| Code grid | Add Haiku 5.5 at every effort, with fallback rates and the tiered-cost caveat; add AA's separate Stirrup FrontierCode run. | [T] AA board 2026-10-16; AA FrontierCode article 2026-10-12. Costs for Haiku exclude the step-up above 100k-token prompts. |
| Overrides section | Replace it with "User and project preferences": read the request, `AGENTS.md`, `CLAUDE.md`, project documentation, and readable memory or preference files, then let those preferences win over the table. Drop the user-specific decisions it held and the restrictions they repeated in the grids. Keep the Sol naming as a fact. | [I] The skill is public and reusable, so it carries recommendations drawn from measurements. One user's choices belong in that user's preference files. No measurement is removed. |
| Astra | No recommended cell, now for a stated reason: same measured tiers as Fable and Sol, with the heaviest draw on a ChatGPT plan. | [V] Plus estimate 5 to 45 messages per five hours against 15 to 160 for Sol, read 2026-10-16. |
| Prose for humans | Replace the Grok usage preference with a documented preference, otherwise Opus 5.5 `high`. | [I] No reproducible reformulation comparison exists for any candidate. The fallback transfers the professional-output proxy (AA-Briefcase `max` Opus 1822, Sonnet 1811 [T]) instead of keeping an unmeasured personal choice. |
| Cost section | Add monthly API credits of Claude plans, split Claude access by authentication, add cache read prices with Sonnet's new $0.10, add Ultrafast and the Pro five-hour rule for Codex, and date each check. Replace the fixed Plus, Max, and Cursor Pro assumption with asking for the user's plans. | [V] Haiku launch 2026-10-07; credits article, Anthropic pricing, Codex pricing, Claude Max, and Cursor pools read 2026-10-16. Benchmark task costs stay at their run-date prices. |

Unchanged: medium-impact ready-plan code uses Sol `medium`/`xhigh`; unplanned/high-impact code uses Opus `high`; all planning rows; moderate web research uses Sol `high`; review rows; professional documents; Terra has no recommended cell. No new Dam Secure or Endor result appeared, so the security-review row stands.

Sources for changes: [AA Haiku, October 7][haiku-aa], [native coding board][coding], [FrontierCode data][frontier], [AA FrontierCode, October 12][aa-frontier], [Rails Stage 3, October 13][rails-stage3], and [Parallel, October 13][parallel]. Live boards and datasets were read on October 16.

## Discovery decisions

Discovery covered [AA's dated article feed][feed] back to September 28, its [coding-agent board][coding], the [OpenAI changelog][openai], the [Anthropic Haiku launch][haiku-vendor], [Google's Antigravity post][argon-ga], the [Rails AI evaluation repository][rails-repo], the [Dam Secure blog][dam-blog], and local catalogs. Newly considered does not mean newly released: release dates are asserted only when a source states them.

### New since 2026-10-01

| Model or version | Status / local identifier | Disposition and reason |
| --- | --- | --- |
| Claude Haiku 5.5, released October 7 | Claude Code `claude-haiku-5-5` by exact ID (help aliases omit it); Cursor `claude-haiku-5-5-thinking-<effort>` and No Thinking `claude-haiku-5-5-<effort>`, `low` through `max`, no NO ZDR flag. API default `medium` [V]. | Ranked: scoped coding tier at `xhigh` (native AA 41.4/$0.61, Claude Code 2.1.289), scoped planning proxy (Index 43 at `max`), scoped search (Parallel 62.9). Claude pool alternative for mechanical code, low-impact ready-plan code, and low-stakes search [I]. Not ranked for review or professional documents (Briefcase 1578 versus Sonnet 1811). Cursor variants unmeasured. Inference access unverified. |
| Gemini 4 Argon, released to developers October 13 | Cursor `gemini-4-argon-low`, `-medium`, `-high`; previously a [selected-user preview][argon] absent locally. Antigravity CLI absent. | Unranked for Cursor routing. Its measurements belong to other harnesses: Antigravity CLI 1.2.10 native 63.8/$5.84 at `high`, FrontierCode chisel 47.55% at `medium`, Parallel 72.2/$270 [T]. Cursor pool and retention for Argon are undocumented here. |
| Muse Wonder 1.0 / Muse Wonder Full, AA article October 12 | Cursor `muse-wonder-1.0-<effort>`, `minimal` through `max`, labeled 300K context. Full is Muse Code only. `muse` absent. | Unranked for Cursor. Native Muse Code 1.4.5: Wonder `max` 63.5/$8.05, Full `max` 68.0 with no per-token price [T]. Index 52 for Wonder, 56 for Full; Parallel Wonder 71.3/$709 [T]. Neither harness nor 1M context transfers to the Cursor ID. |
| Mistral Large 4, research preview October 6 | Absent locally; open weights planned for end of October. | Ignored for routing: preview, no installed path, Index 38 at $1.13/task, FrontierCode chisel 39.43% at `high` [T]. |
| Nemotron 3.5 Super VL / Bolt, October 15 | Absent locally; pre-release endpoint. | Ignored: Index 26/21 [T], no coding-agent result, no installed path. |
| GPT-6 Sol (Daybreak Blue) | AA Cyber Index, October 8; OpenAI Daybreak program only. | Ignored: trusted-access model, not selectable here; cyber-defense tasks are not PR review. |
| GPT-Live 1; `chat-latest` snapshot | OpenAI changelog, October 7 and 15. | Ignored: realtime/chat products, not coding or research agents in the installed CLIs. |
| AA Decision Index v1.0 and decision models, October 13 | Haiku `low` 61, Luna `low` 55 [T]; Jev, GLiDE, and others are API decision models. | Ignored as planning evidence: fixed-option choice, not choosing a repository approach. Haiku's lead supports its classification/routing positioning, nothing more [I]. |
| GPT-5.6 Terra, now measured on FrontierCode | Codex `gpt-5.6-terra`; Cursor variants unchanged. | Still no recommended cell: `max` 41.31%/$1.87 trails Luna `max` 42.42%/$0.10 [T]. |

### Retained from 2026-10-01

| Model or version | Status / local identifier | Disposition and reason |
| --- | --- | --- |
| GPT-6.1 Sol; Claude Sonnet 5.5 | Codex `gpt-6.1-sol`; Claude `claude-sonnet-5-5`, Cursor `claude-sonnet-5-5-<effort>`. | Ranked as in the table. Sonnet now has a same-version Parallel score; AA's announced Sonnet reruns had no update note on October 16. |
| Solar Mini 4 | Absent locally. | Ignored: no installed path; [AA Index 24][solar] [T]. |
| Claude Fable 5.1 | Claude `claude-fable-5-1`; Cursor variants all marked NO ZDR. | Ranked only where evidence applies; unvalidated specialist review candidate. No blanket exclusion. Rails no longer reruns it. |
| Gemini 3.8/3.7/3.6 Flash and 3.1 Pro | Cursor `gemini-3.8-flash-<effort>` and others. | Unranked for Cursor: results come from Antigravity SDK or chisel, not Cursor. |
| Muse Spark 1.3 | Cursor `muse-spark-1.3-<effort>`. | Unranked for Cursor; native Muse Code `max` 54.3/$3.98 does not transfer. Superseded in Meta's line by Muse Wonder. |
| Kimi K3 / K2.7 Code; GLM 5.2 / 5.3 | Cursor `kimi-k3-<effort>`, `kimi-k2.7-code`, `glm-5.2-high`/`max`. | Unranked: native Kimi Code and OpenCode/chisel results do not transfer to Cursor or to GLM 5.2. |
| DeepSeek V4.1 Flash; GLM 5.3 Flash; DeepSeek V4 Pro/Flash; Mistral 3.5 Medium; Nemotron 3 Ultra; SWE-2 | No local model listing. | Ignored for default routing: no installed path. DeepSeek V4.1 Flash's 63.75%/$0.42 Dam Secure recall remains specialist evidence [T]. |
| Composer 2.5 | Cursor `composer-2.5`, `composer-2.5-fast`. | Unranked. FrontierCode via Cursor CLI is 25.64% [T], below every recommended configuration. |
| Older GPT, Claude, Grok, and Gemini versions | Still selectable, including Sol 6, GPT-5.6 Sol/Luna, GPT-5.5/5.4/5.3 Codex, Claude 4.x/5.0, Grok 4.5/4.6, Gemini 3/3.5. | Ignored for default routing. Preserve historical scores. |
| `gpt-reserve`, `codex-auto-review` | Hidden Codex catalog entries. | Ignored: internal identifiers. |
| Mythos 5.1; Pareto 26.9/26.10 | Restricted equivalent; Parallel's own product. | Ignored: no installed route; vendor result [V]. |
| AA-AgentPerf / AgentPerf-Local | Hardware speed articles, latest October 15. | Ignored: speed testing, not model quality. |

Preview and new-model sources: [AA Haiku][haiku-aa], [Haiku documentation][haiku-doc], [Muse Wonder][muse-wonder], [Mistral Large 4][mistral], [Nemotron 3.5][nemotron], [Cyber Index trusted access][cyber], [Decision Index][decision], and [Gemini Argon GA][argon-ga]. Catalog observations are local, not an account-access test.

### Harness inventory

| Harness or executable | Local observation on 2026-10-16 | Disposition |
| --- | --- | --- |
| Codex | `codex-cli 0.162.1`; `debug models` succeeds; same nine slugs as October 1. | Retain. AA Sol/Luna runs used 0.154.0. |
| Claude Code | 2.1.301; `--help` exposes aliases `opus`, `sonnet`, `fable`, full model names, and `--effort` `low` through `max`. | Retain. No non-interactive model-list command. AA Haiku used 2.1.289, Opus/Sonnet 2.1.280. |
| Cursor | 2026.09.28-64d2043, unchanged; `cursor-agent` and `agent` resolve to the same executable. | Retain one harness. The server-side list gained Haiku 5.5, Gemini 4 Argon, and Muse Wonder 1.0 without a CLI update. |
| Herdr | Found; `HERDR_ENV=1`. | Retain as an orchestration tool. No pane or session created. |
| Antigravity CLI / SDK | AA CLI 1.2.10; `agy`, `antigravity`, and `gemini` absent. Google opened Argon in the CLI on October 13 to AI Pro/Ultra plans [V]. | Unranked locally; not installed. |
| Muse Code | AA 1.4.5-R5426.1 for Wonder; `muse` absent. | Unranked locally; Wonder Full is exclusive to it. |
| Devin Fusion CLI | AA v3000.11.31/.34 for Opus 5.5 + Luna (68.1/$9.01); Anthropic names Haiku 5.5 as a Devin sidekick [V]; `devin` and `fusion` absent. | Unranked locally. Hybrid configurations are not solo-model results. |
| [Grok Build][grokbuild]; Kimi Code CLI; OpenCode | AA 1.0.40; 0.26 to 0.36.1; 1.18.29. Executables absent. | Unranked locally, as on October 1. |
| Other known CLIs | `aider`, `goose`, `amp`, `droid`, `pi`, `copilot`, `qwen` absent. | No local ranking or launch form assumed; recheck at the next update. |

Executable names are search candidates, not inferred installation instructions. Missing `command -v` results establish absence from this PATH only. The tested-command history and current help checks are separate in [harness.md](harness.md).

## Fable 5.1 versus Opus 5.5

Fable 5.1 has no general exclusion. Opus is the better-supported general default [I], but these evaluations do not prove that Fable is inferior on most real tasks, planning included. A count of benchmark components is not a distribution of real tasks. Reassessed on 2026-10-16: no direct planning comparison appeared and Endor's counterexample stands. Parallel and AA's Stirrup FrontierCode run add small Opus leads without uncertainty, which do not meet the criteria below.

For a future update to exclude Fable from general routing, require a direct repository-planning comparison that favors Opus beyond uncertainty on representative tasks, and comparable current coding evidence that resolves Endor's adjusted functional-pass counterexample. Keep the same evidence threshold for both models: a small gap without uncertainty is insufficient [I]. Until both are met, keep Fable eligible and record remaining counterexamples. A user or project may still exclude it by preference; that choice belongs in their preference files, not here.

| Task | Published comparison, Opus versus Fable | Verdict and limits |
| --- | --- | --- |
| Planning | AA Index `max` 58 versus 53; `xhigh` 56 versus 53; `high` 54 versus 51; `medium` 51 versus 49; `low` 42 versus 47 [T, API with default fallback]. | Opus leads reasoning proxies at equal effort from `medium` upward; Fable leads at `low`. No direct repository-plan-quality test was found. Prefer Opus for complex planning [I]; do not claim a measured planning win. |
| General code | Native AA index `max` 66.0 versus 62.2 [T]; FrontierCode 1.1 Main `medium` 54.64% versus 50.91%, but `low` 47.30% versus 49.82% [T]; AA's Stirrup FrontierCode run, October 12, `max` 52% versus 49% [T]. Rails' September Stage 2 figures (Opus `medium` 33.3% versus Fable 31.7%) were superseded by the October 13 regrade, which did not rerun Fable. | Several setups favor Opus, but FrontierCode reverses at `low`. That 2.52-point gap lacks uncertainty and establishes no reliable winner. AA CLI versions differ and both `max` configurations include fallback. No current Rails comparison exists. These are not all coding tasks. |
| Secure-code generation | Endor, September 24: adjusted FuncPass 68.7% versus 87.2%; SecPass 33.5% versus 37.4% [T]. | Coding counterexample after excluding memorized solutions: Fable has 33 more functional passes among 179 graded tasks. SecPass differs by only seven tasks and does not alone establish a reliable security winner. 200 tasks/179 graded, one run each, effort unstated, Claude Code 2.1.280 versus 2.1.258. This measures generation, not review. |
| Security review | Dam Secure, September 24: recall 56.25% versus 62.5%, both `high` [T]. | Weak signal, five extra detections in 80 reviews of only 16 distinct bugs, without uncertainty. Custom isolated API agent, CLI versions N/A. Fable costs $7.31/PR versus Opus $1.92; Sol 6 scores 63.75%/$1.81. No reliable security or general-review winner follows; Fable is an unvalidated candidate. |
| Research | Parallel, updated October 13: 75.4 versus 73.4; $949 versus $1,762 per 1,000 tasks [T]. | Opus leads this common Search Fast/Extract setup. Exact model effort is unstated; installed CLI search tools differ. |
| Professional outputs | AA-Briefcase combined Elo `max` 1822 versus 1678; GDPval-AA 1846 versus 1735 [T]. | Opus leads aggregates, but Fable's rubric subscore is slightly higher in AA's September 22 discussion. Analytical/presentation quality is not pure prose quality. |
| Prose and reformulation | No reproducible direct comparison used. Anthropic's Opus writing improvement is a vendor claim [V]. | Insufficient evidence for a general prose verdict or a measured prose default [I]. |

The [Anthropic Opus launch][opus-vendor], September 22, adds vendor evidence [V]: Terminal-Bench 4.0 66.4% Opus `xhigh` versus 55.8% Fable `max`, and CursorBench 57.8% versus 51.8% under its reported settings. Vendor harness and effort differences prevent treating these as replication of AA's native runs.

Endor counted 51 Opus versus 17 Fable tasks as memorization/cheating. Before those deductions, its pass figures favor Opus; retain the adjusted published figures. This penalty and single-run design are part of the counterexample, not evidence that Fable wins secure coding in general.

### Relative cost and quota

| Setup | Opus versus Fable | What it establishes |
| --- | --- | --- |
| Standard API, dollars/million input/output [V] | $4/$20 versus $10/$50; cached input $0.20 versus $0.25. | Fable input/output tokens cost 2.5 times as much; cached input costs 1.25 times as much. Completed-task and quota ratios differ. |
| AA Intelligence Index, `max` [T] | $5.98 versus $7.63/task. | Opus costs about 22% less in this workload. |
| AA native Coding Agent Index, `max` [T] | $13.04 versus $12.39/task. | Opus costs about 5% more here, despite cheaper token prices. |
| FrontierCode 1.1 Main, `medium` [T] | $0.802 versus $3.284/task. | Opus costs about 76% less in this workload. |
| Rails Stage 2 before the October regrade, Opus `medium` / Fable `high` [T] | $2.78 versus $9.14/run. | Historical; different efforts; not a universal price multiplier. |
| Endor, entire 200-task run [T] | $116 versus $672. | Opus costs about 83% less in that run; grading exclusions affect quality, not this total. |
| Claude Max, signed in with the plan [V] | Shared weekly allowance; Fable capped at 50% of the existing weekly allowance. | Fable adds no allowance. A model-specific per-task deduction ratio is unpublished; no exact quota comparison can be proved. |

Costs use the matching source in the task table, [Anthropic model documentation][fable-doc], [Opus documentation][opus-doc], and [Claude's Fable plan limits][fable-plan]. All accessed October 1; Claude prices and the Fable cap were reread October 16 and are unchanged for Opus and Fable. These API benchmark costs are not bills under a plan's included limits. A plan's monthly API credits, spent through an API key, are billed at these API prices [V, [credits][claude-credits]].

### Evidence excluded from ranking

An evaluator's [Reddit writing post][writing-post] reports ten script tasks, five samples each, and three LLM judges. It also gives conflicting Opus/Fable Elo figures (2631/2324 and 2600/2303), supplies no public rubric/dataset, and says details will be published later. Record it as an unverified report, not a reproducible writing rank. Publication date could not be established from the relative-time page; accessed 2026-10-01.

Sources for the comparison: [AA Opus article, September 22][opus], [AA effort comparison][efforts], [AA native coding board][coding], [FrontierCode revised data][frontier], [AA FrontierCode, October 12][aa-frontier], [Rails Stage 3, October 13][rails-stage3] superseding the [Stage 2 method][rails-method], [Endor, September 24][endor], [Dam Secure, September 24][dam], and [Parallel][parallel]. Live comparisons were read October 1; Parallel, FrontierCode, and Rails were reread October 16. Details of harnesses and revisions stay beside the figures in [table.md](table.md#sources).

[coding]: https://artificialanalysis.ai/agents/coding-agents
[efforts]: https://artificialanalysis.ai/models/releases/comparisons/claude-opus-5-5-vs-claude-fable-5-1
[frontier]: https://cognition.com/data/frontiercode-leaderboard/data.json
[parallel]: https://parallel.ai/leaderboard
[dam]: https://docs.damsecure.ai/blog/openai-gpt-6-sol-closes-in-on-deepseek-v4-1-flash-security-benchmark/
[feed]: https://artificialanalysis.ai/articles
[openai]: https://developers.openai.com/api/docs/changelog
[argon]: https://artificialanalysis.ai/articles/gemini-4-argon-google-top-three-labs
[solar]: https://artificialanalysis.ai/articles/korean-ai-lab-upstage-releases-solar-mini-4
[grokbuild]: https://x.ai/build
[opus]: https://artificialanalysis.ai/articles/claude-opus-5-5
[opus-vendor]: https://www.anthropic.com/claude-opus-5-5
[fable-doc]: https://platform.claude.com/docs/en/models/fable-5-1/overview
[opus-doc]: https://platform.claude.com/docs/en/models/opus-5-5/overview
[fable-plan]: https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan
[rails-method]: https://rubyonrails.org/2026/9/9/agents-on-rails-stage-2
[endor]: https://www.endorlabs.com/learn/opus-5-5-6x-cheaper-and-2x-faster-than-fable-5-1-but-memorization-keeps-it-off-the-top-spot
[writing-post]: https://www.reddit.com/r/ClaudeAI/comments/1wr03jc/55_is_insane_it_almost_broke_our_benchmark_i/
[haiku-aa]: https://artificialanalysis.ai/articles/claude-haiku-5-5
[haiku-doc]: https://platform.claude.com/docs/en/models/haiku-5-5/overview
[haiku-vendor]: https://www.anthropic.com/news/claude-haiku-5-5
[aa-frontier]: https://artificialanalysis.ai/articles/frontiercode
[rails-stage3]: https://rubyonrails.org/2026/10/13/agents-on-rails-stage-3
[rails-repo]: https://github.com/rails/ai-evals
[dam-blog]: https://docs.damsecure.ai/blog
[argon-ga]: https://antigravity.google/blog/gemini-4-argon-in-google-antigravity
[muse-wonder]: https://artificialanalysis.ai/articles/muse-wonder
[mistral]: https://artificialanalysis.ai/articles/mistral-large-4-france-ai
[nemotron]: https://artificialanalysis.ai/articles/nemotron-3-5-super-and-bolt
[cyber]: https://artificialanalysis.ai/articles/trusted-access-models-cyber-index
[decision]: https://artificialanalysis.ai/articles/artificial-analysis-decision-index
[claude-credits]: https://support.claude.com/en/articles/17154008-monthly-api-credits-for-max-and-team-plans
