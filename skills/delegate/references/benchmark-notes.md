---
date: 2026-11-10
---

# Benchmark update notes

Update cutoff and source access: 2026-11-10. Evidence levels and current routing are defined in [table.md](table.md). This update used published results, local version/help commands, and model listings. It launched no agent, inference request, benchmark, or installation.

## Recommendation changes

Compared with the table dated 2026-10-16:

| Cell or rule | Change | Reason and limit |
| --- | --- | --- |
| Unplanned or high-impact code | Opus 5.5 `high` becomes Fable 5.2 `high`, with Opus `xhigh` when Fable is excluded. Fable `xhigh` is recorded as a candidate. | [T] FrontierCode 2.0 in Claude Code: Fable `high` 45.3%/$8.40 versus Opus `high` 34.5%/$2.42 and `max` 45.5%/$12.82; AA's Stirrup run gives 49.1% versus 35.9%. Fable `xhigh` leads Cognition's run (49.1%) but trails Fable `high` in AA's, so it stays a candidate [I]. |
| Long autonomous code | Opus `medium` becomes Opus `xhigh`; Fable 5.2 `high` is a candidate. | [T] The 2026-10-16 cell kept `medium` because FrontierCode 1.1 and Rails disagreed on effort. FrontierCode 2.0 (43.4% versus 30.1%) now agrees with Rails Stage 3 (65.3% versus 56.1%). Fable `high` leads Opus `xhigh` by 1.9 points without uncertainty, at 1.6 times the cost, with no long-horizon independent test. |
| Complex planning | Opus `xhigh` becomes Fable 5.2 `high`, with Opus `xhigh` when Fable is excluded. | [T] AA Index v5.0.1: Fable `high` 61.8/$9.08 versus Opus `xhigh` 57.4/$6.05 and `max` 59.1/$10.04. Proxy only [I]. |
| Medium planning | Opus `medium` (Sol `max` candidate) becomes Sol `max` on a ChatGPT plan, Fable 5.2 `medium` on a Claude plan that includes Fable, otherwise Opus `high`. | [T] Index v5.0.1: Fable `medium` 56.4/$3.80, Sol `max` 54.6/$1.27, Opus `high` 51.8/$3.46, Opus `medium` 48.2/$2.45. The one-point v4.3.2 gap that kept Opus `medium` is now 6 to 8 points. This follows from the index revision, not only from Fable 5.2. |
| High-stakes web research | Keep Opus `high`; add Fable 5.2 `medium` as a vendor-measured candidate. | [V] No independent search result for Fable 5.2. Anthropic's WANDR run gives 82.1% versus Opus 72.3%. Parallel, updated 2026-10-31, still has Opus first and no Fable 5.2 row. |
| Routine code review | Keep Opus `high` for authors up to its tier; use Fable 5.2 `high` or Opus `max` above it. | [I] Review transfers the coding grid. On FrontierCode 2.0 several authors now sit above Opus `high` (34.5%): Fable 5.2 `high`, Opus `xhigh`/`max`, Sonnet `max`, Sol `max`. |
| Security-sensitive review | Fable 5.1 candidate becomes an unvalidated Fable 5.2 candidate, with a safeguard caveat. | [V] Dam Secure measured only Fable 5.1. Anthropic says Fable's safeguards block most cybersecurity tasks and route them to Opus 4.8, with about 60% fewer cybersecurity blocks than Fable 5.1. |
| Code cells' FrontierCode figures | FrontierCode 1.1 figures replaced by FrontierCode 2.0. | [T] Cognition replaced 1.1 with 2.0 on 2026-10-27. The order in the mechanical and ready-plan cells is unchanged. |
| Planning proxy grid | Rebuilt on AA Intelligence Index v5.0.1. | [T] v5 replaced v4.3.2 on 2026-10-27; values are not comparable across versions. Grok 4.7 `xhigh` drops to the scoped tier (35.5). |
| Code grid | Adds a FrontierCode 2.0 table, keeps the native AA v1.5 grid as a dated snapshot, and lists v2.0 values. | [T] AA's native board moved to Coding Agent Index v2.0 with fewer configurations and no Fable 5.2 entry. |
| Catalog | Fable 5.1 row becomes Fable 5.2; GPT-5.6 Terra row becomes GPT-6.1 Terra, candidate. | Local catalogs, 2026-11-10. |
| Cost section | Fable 5.2 prices; Fable cap and plan coverage reread; Ultra noted. | [V] Anthropic pricing, Fable plan page, and Max plan page, read 2026-11-10. |
| Professional documents and prose fallback | Figures move to AA-Briefcase v1.1; order kept. | [T] Sonnet `max` 1816 now leads Opus `max` 1801: a 15-point gap without uncertainty, so the previous order stays. Fable 5.2 (1785) does not enter. |

Unchanged: mechanical code, ready-plan code at low and medium impact, simple planning, low- and moderate-stakes web research, professional documents, the prose fallback, and Astra's absence from recommended cells.

Sources for changes: [Fable 5.2 launch][fable52-vendor], [Fable 5.2 documentation][fable52-doc], [FrontierCode 2.0 data][frontier2-data], [AA Opus/Fable 5.2 comparison][aa-pair52], [AA Index v5][aa-v5], [Vals][vals-fable], [Parallel][parallel], and the [Fable plan page][fable-plan]. All were read on 2026-11-10.

## Discovery decisions

Discovery covered [AA's dated article feed][feed] back to 2026-10-16, its [coding-agent board][coding], [Cognition's FrontierCode page][frontier2], [Vals' model list][vals-fable], [Parallel][parallel], the [OpenAI changelog][openai], the [Anthropic Fable 5.2 launch][fable52-vendor], the [Dam Secure blog][dam-blog], the [Rails blog][rails-blog], a search for independent Fable 5.2 evaluations, and local catalogs. Newly considered does not mean newly released: release dates are asserted only when a source states them.

### New since 2026-10-16

| Model or version | Status / local identifier | Disposition and reason |
| --- | --- | --- |
| Claude Fable 5.2, released 2026-11-09 | Claude Code `claude-fable-5-2` (alias `fable`), needs 2.1.321 or later; local 2.1.322. Cursor `claude-fable-5-2-low` through `-max`, all NO ZDR. API default `high`, Claude Code `medium` [V]. | Ranked: complex planning, unplanned or high-impact code, higher-tier review; candidate for long autonomous code and high-stakes research; unvalidated security-review candidate. See the [comparison](#fable-52-versus-opus-55). Inference access unverified. |
| Claude Mythos 5.2 | Verification programs only. | Ignored: not selectable here. |
| GPT-6.1 Terra, released 2026-10-26 | Codex `gpt-6.1-terra`, default `low`; Cursor lists only GPT-5.6 Terra. | Candidate, unranked. Index v5 `max` 51.3/$0.96; native Codex v2.0 `xhigh` 48.2/$0.69 and `medium` 42.0/$0.39, versus Luna `max` 31.2/$0.16 and Sol `max` 54.1/$1.50; Parallel 69.7 [T, [AA][aa-terra]]. Not on FrontierCode 2.0. Its Codex credit rate was not checked. Evaluate against Luna for low-impact code at the next full update. |
| Gemini 4 Carbon, announced 2026-10-28 | Selected-user rollout; absent from Cursor; Antigravity CLI absent. | Unranked locally: Index v5 `high` 60.0/$7.76, Antigravity CLI 1.4.3 native 59.4/$7.74, FrontierCode 2.0 `medium` 40.0% in devin-cli [T, [AA][aa-carbon]]. |
| Kimi K3.1 Pro, 2026-10-23 | Absent locally (Cursor lists Kimi K3 only); weights not yet released. | Ignored for routing: no installed path. Index v5 46.5, Parallel 74.2/$268, FrontierCode 2.0 `max` 19.6% in devin-cli [T, [AA][aa-kimi]]. |
| Muse Ember, 2026-11-09 | Absent locally; `muse` absent. | Ignored: no installed path. Index v5 `max` 36.0/$0.14; native Muse Code 45.9 [T, [AA][aa-ember]]. |
| Inkling 2 Small, 2026-11-05 | Tinker platform only; weights planned. | Ignored: no installed path. Index v5 31; FrontierCode 2.0 `max` 22.6% [T, [AA][aa-inkling]]. |
| GitHub Copilot Fusion, 2026-10-28 | Router in GitHub Copilot CLI; `copilot` absent. | Unranked locally: native v2.0 59.9/$5.59 [T, [AA][aa-fusion]]. A router is not a solo-model result. |
| Mistral Large 4, Vals release date 2026-10-29 | `vibe` 2.14.1 found (Mistral Vibe); AA evaluated 3.0.0-v14. | Ignored for routing: native v2.0 35.4/$0.78, FrontierCode 2.0 `high` 19.7% [T]. Help exposes no model catalog. |
| DeepSeek V4.1 Flash 1017; GLM-5.3; Muse Spark Open; Beam 1.0; SWE-2 Flash; Nanbeige4.3 | Absent locally. | Ignored: no installed path; below recommended configurations where measured. |
| GPT-6 Rosalind, 2026-10-30 | OpenAI trusted-access biology model. | Ignored: not selectable here. |
| AA Index v5 and Coding Agent Index v2.0; FrontierCode 2.0; AA Decision Index v2 | Methodology revisions, 2026-10-27 and after. | The first three rebuild the grids. Decision Index v2 is ignored as planning evidence, as v1 was. |

### Considered on 2026-10-16, new since 2026-10-01

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
| Claude Fable 5.1 | Claude `claude-fable-5-1`; Cursor variants all marked NO ZDR; still listed on 2026-11-10. | Replaced by Fable 5.2 in every cell on 2026-11-10; its measurements stay attributed to it. |
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

| Harness or executable | Local observation on 2026-11-10 | Disposition |
| --- | --- | --- |
| Codex | `codex-cli 0.167.0`; `debug models` succeeds; ten slugs, adding `gpt-6.1-terra`. | Retain. AA Sol/Luna runs used 0.154.0; Terra 6.1 used 0.163.0. |
| Claude Code | 2.1.322; `--help` exposes aliases `fable`, `opus`, `sonnet`, full model names, and `--effort` `low` through `max`. | Retain. No non-interactive model-list command. Fable 5.2 needs 2.1.321 or later [V]. |
| Cursor | 2026.09.28-64d2043, unchanged; `cursor-agent` and `agent` resolve to the same executable. | Retain one harness. The server-side list gained Fable 5.2 variants without a CLI update. |
| Herdr | Found; `HERDR_ENV=1`. | Retain as an orchestration tool. No pane or session created. |
| Mistral Vibe | `vibe` 2.14.1, a uv tool, found for the first time because earlier inventories did not search for it. `-p` runs non-interactively; help lists no model catalog. | Unranked locally; no recommended model runs in it. |
| Antigravity CLI, Muse Code, Devin Fusion, Grok Build, Kimi Code, OpenCode, GitHub Copilot CLI | `agy`, `antigravity`, `gemini`, `muse`, `devin`, `fusion`, `grok`, `kimi`, `opencode`, `copilot` absent. | Unranked locally. |
| Other known CLIs | `aider`, `goose`, `amp`, `droid`, `pi`, `qwen` absent. | No local ranking or launch form assumed; recheck at the next update. |

Executable names are search candidates, not inferred installation instructions. Missing `command -v` results establish absence from this PATH only. The tested-command history and current help checks are separate in [harness.md](harness.md).

## Fable 5.2 versus Opus 5.5

Reassessed on 2026-11-10, the day after Fable 5.2's release. Independent results favor Fable 5.2 at equal effort on mergeable code and on reasoning proxies. They do not favor it on terminal tasks, professional documents, multimodal SWE-bench, or cost per task. Opus stays the default where Fable's limits apply: plan cap, retention, and safeguard fallbacks [I].

The 2026-10-16 notes set a symmetric threshold: comparable current evidence beyond small gaps, and no small gap without uncertainty treated as a winner. FrontierCode 2.0 gaps at equal effort are 5.7 to 19.5 points from `low` to `xhigh`, with a tie at `max`. Index v5 gaps are 4.8 to 10.0 points from `medium` to `max`. They exceed the 3.7- and 5-point Opus leads that kept Opus first over Fable 5.1. Neither source reports uncertainty, so differences between neighboring efforts are not used to choose an effort.

For a future update to move Fable 5.2 out of its cells, require comparable current evidence that Opus matches it beyond uncertainty on mergeable code or reasoning proxies, at equal or lower cost. A user or project may still exclude Fable by preference; that choice belongs in their preference files, not here.

| Task | Published comparison, Opus 5.5 versus Fable 5.2 | Verdict and limits |
| --- | --- | --- |
| Planning | AA Index v5.0.1: `max` 59.1 versus 64.6; `xhigh` 57.4 versus 62.2; `high` 51.8 versus 61.8; `medium` 48.2 versus 56.4. HLE-Diamond `max` 67.9% versus 80.2%; Terminal-Bench-Science 59.0% versus 73.3% [T, API with default fallback]. | Fable leads every reasoning proxy at equal effort. No direct repository-plan test. Fable `high` for complex planning [I]. |
| General code | FrontierCode 2.0 in Claude Code: `low` 14.7% versus 34.2%, `medium` 30.1% versus 37.6%, `high` 34.5% versus 45.3%, `xhigh` 43.4% versus 49.1%, `max` 45.5% versus 45.6%. AA's Stirrup run: `max` 46.4% versus 48.8%, `high` 35.9% versus 49.1%. Terminal-Bench 4.0: AA `max` 59.6% each; Vals 65.15% each. Vals SWE-bench Multimodal 70.21% versus 62.29%; ProgramBench 18.50% versus 19.00% [T]. | Fable leads mergeability in two harnesses. Terminal tasks tie and multimodal SWE-bench favors Opus. No native AA board or Rails result exists for Fable 5.2. |
| Secure-code generation | No Fable 5.2 result. | Endor's Fable 5.1 counterexample does not transfer. |
| Security review | No independent Fable 5.2 result. Anthropic: safeguards block most cybersecurity tasks and route them to Opus 4.8, with about 60% fewer cybersecurity blocks than Fable 5.1; its CVE Rediscovery figures measure Mythos 5.2, not Fable [V]. | Unvalidated candidate; check the served model. |
| Research | No independent result; Parallel lists Fable 5.1 only. Anthropic's WANDR run: 72.3% versus 82.1%, Fable `medium` matching Opus's best for about 40% of the cost [V]. | Vendor-measured candidate for high-stakes research. |
| Professional outputs | AA-Briefcase v1.1 `max` 1801 versus 1785; GDPval-AA 1866 versus 1831 [T]. Anthropic's Briefcase rubric 61.2% versus 66.1% [V]. | Opus and Sonnet lead on Elo; Fable does not enter. |
| Prose and reformulation | No reproducible direct comparison. | No verdict. |

The [Anthropic launch][fable52-vendor] adds vendor evidence [V]: FrontierSWE v2 69.9% versus 62.3%, AutomationBench 51.4% versus 42.5%, OSWorld 2.1 89.3% versus 87.2%, and Remote Labor Index 41.3% versus 21.3%. It recommends starting most coding and knowledge tasks with Opus 5.5 and moving to Fable for the most ambitious open-ended technical work. It says Fable `high` matched Opus `max` on FrontierCode 2.0 for roughly half the cost; Cognition's data give $8.40 versus $12.82, about two-thirds.

Fallbacks are part of the configuration [V]: blocked cybersecurity requests go to Opus 4.8, blocked biology requests to Opus 5, and a few AI research topics to Opus 5. Vals reports a 1.88% fallback rate at `high` [T]. AA's Fable entries include default fallback.

### Relative cost and quota

| Setup | Opus 5.5 versus Fable 5.2 | What it establishes |
| --- | --- | --- |
| Standard API, dollars/million input/output [V] | $4/$20 versus $8/$40; cache read $0.20 each; Fable fast mode $16/$80. | Fable tokens cost twice as much; cache reads cost the same. |
| AA Index v5.0.1 [T] | `max` $10.04 versus $26.54; `high` $3.46 versus $9.08 per task. | Fable costs about 2.6 times as much at equal effort. Fable `high` exceeds Opus `max` for 10% less. |
| FrontierCode 2.0, Claude Code [T] | `medium` $1.70 versus $3.10; `high` $2.42 versus $8.40; `xhigh` $5.18 versus $17.73; `max` $12.82 versus $55.87. | Fable costs 1.8 to 4.4 times as much at equal effort. At an equal score (Opus `max`, Fable `high`), Fable costs about a third less. |
| Claude plans, signed in with the subscription [V] | Max, Ultra, and premium seats cap Fable at 50% of the weekly limit and say it draws that limit faster; Pro and standard seats pay usage credits from the start. | No per-task quota ratio is published. Fable's cap can run out well before the weekly limit. |

Costs use the matching source in the task table, [Anthropic pricing][anthropic-price], and the [Fable plan page][fable-plan], read 2026-11-10. These API benchmark costs are not bills under a plan's included limits. A plan's monthly API credits, spent through an API key, are billed at API prices [V, [credits][claude-credits]].

### Fable 5.1 history

Recorded on 2026-10-16 for Fable 5.1 and kept as history: it explains the earlier routing and holds the Endor, Dam Secure, FrontierCode 1.1, and Rails Stage 2 figures. Fable 5.2 replaced Fable 5.1 in recommendations on 2026-11-10. None of these figures transfers to Fable 5.2.

| Task | Published comparison, Opus versus Fable 5.1 | Verdict and limits |
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

### Evidence excluded from ranking

Press and aggregator articles about Fable 5.2 (DataCamp, llm-stats, and others found on 2026-11-10) repeat Anthropic's launch table. Only the launch page itself is cited, as [V]. A [Notebookcheck article][notebookcheck] reports prompt-injection figures from Anthropic's system card, higher when Opus 4.8 answers a blocked request than when Fable does; it measures safety, not task quality.

For Fable 5.1, an evaluator's [Reddit writing post][writing-post] reports ten script tasks, five samples each, and three LLM judges. It also gives conflicting Opus/Fable Elo figures (2631/2324 and 2600/2303), supplies no public rubric/dataset, and says details will be published later. Record it as an unverified report, not a reproducible writing rank. Publication date could not be established from the relative-time page; accessed 2026-10-01.

Sources for the Fable 5.1 history: [AA Opus article, September 22][opus], [AA effort comparison][efforts], [AA native coding board][coding], [FrontierCode revised data][frontier], [AA FrontierCode, October 12][aa-frontier], [Rails Stage 3, October 13][rails-stage3] superseding the [Stage 2 method][rails-method], [Endor, September 24][endor], [Dam Secure, September 24][dam], and [Parallel][parallel]. Live comparisons were read October 1; Parallel, FrontierCode, and Rails were reread October 16. Details of harnesses and revisions stay beside the figures in [table.md](table.md#sources).

[coding]: https://artificialanalysis.ai/agents/coding-agents
[efforts]: https://artificialanalysis.ai/models/releases/comparisons/claude-opus-5-5-vs-claude-fable-5-1
[frontier]: https://cognition.com/data/frontiercode-leaderboard/data.json
[parallel]: https://parallel.ai/leaderboard
[dam]: https://docs.damsecure.ai/blog/openai-gpt-6-sol-closes-in-on-deepseek-v4-1-flash-security-benchmark/
[feed]: https://artificialanalysis.ai/articles
[openai]: https://developers.openai.com/api/docs/changelog
[argon]: https://artificialanalysis.ai/articles/gemini-4-argon-google-top-three-labs
[solar]: https://artificialanalysis.ai/articles/korean-ai-lab-upstage-releases-solar-mini-4
[opus]: https://artificialanalysis.ai/articles/claude-opus-5-5
[opus-vendor]: https://www.anthropic.com/claude-opus-5-5
[fable-plan]: https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan
[rails-method]: https://rubyonrails.org/2026/9/9/agents-on-rails-stage-2
[endor]: https://www.endorlabs.com/learn/opus-5-5-6x-cheaper-and-2x-faster-than-fable-5-1-but-memorization-keeps-it-off-the-top-spot
[writing-post]: https://www.reddit.com/r/ClaudeAI/comments/1wr03jc/55_is_insane_it_almost_broke_our_benchmark_i/
[haiku-aa]: https://artificialanalysis.ai/articles/claude-haiku-5-5
[haiku-doc]: https://platform.claude.com/docs/en/models/haiku-5-5/overview
[aa-frontier]: https://artificialanalysis.ai/articles/frontiercode
[rails-stage3]: https://rubyonrails.org/2026/10/13/agents-on-rails-stage-3
[dam-blog]: https://docs.damsecure.ai/blog
[argon-ga]: https://antigravity.google/blog/gemini-4-argon-in-google-antigravity
[muse-wonder]: https://artificialanalysis.ai/articles/muse-wonder
[mistral]: https://artificialanalysis.ai/articles/mistral-large-4-france-ai
[nemotron]: https://artificialanalysis.ai/articles/nemotron-3-5-super-and-bolt
[cyber]: https://artificialanalysis.ai/articles/trusted-access-models-cyber-index
[decision]: https://artificialanalysis.ai/articles/artificial-analysis-decision-index
[claude-credits]: https://support.claude.com/en/articles/17154008-monthly-api-credits-for-max-and-team-plans
[fable52-vendor]: https://www.anthropic.com/claude-fable-and-mythos-5-2
[fable52-doc]: https://platform.claude.com/docs/en/models/fable-5-2/overview
[frontier2]: https://cognition.com/frontiercode
[frontier2-data]: https://cognition.com/data/frontier-code-2.0/data.json
[aa-pair52]: https://artificialanalysis.ai/models/comparisons/claude-opus-5-5-vs-claude-fable-5-2
[aa-v5]: https://artificialanalysis.ai/articles/artificial-analysis-intelligence-index-v5
[vals-fable]: https://www.vals.ai/models/anthropic_claude-fable-5-2
[aa-terra]: https://artificialanalysis.ai/articles/gpt-6-1-terra-pushes-the-cost-efficiency-frontier
[aa-carbon]: https://artificialanalysis.ai/articles/gemini-4-carbon-new-number-1
[aa-kimi]: https://artificialanalysis.ai/articles/kimi-k3-1-pro-launch-benchmarks
[aa-ember]: https://artificialanalysis.ai/articles/meta-s-muse-ember-is-the-cheapest-model-scoring-36-on-the-intelligence-index
[aa-inkling]: https://artificialanalysis.ai/articles/thinking-machines-releases-inkling-2-small-highest-scoring-open-weights-model-outside-of-chinia-upon-weights-release-it
[aa-fusion]: https://artificialanalysis.ai/articles/github-copilot-fusion-orchestrates-anthropic-and-openai-models-to-balance-performance-and-cost
[rails-blog]: https://rubyonrails.org/blog
[notebookcheck]: https://www.notebookcheck.net/Claude-Fable-5-2-fallbacks-make-AI-agents-more-vulnerable.1446771.0.html
[anthropic-price]: https://platform.claude.com/docs/en/about-claude/pricing
