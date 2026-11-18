---
date: 2026-11-18
---

# Benchmark update notes

Update cutoff and source access: 2026-11-18. Evidence levels and current routing are defined in [table.md](table.md). This update used published results, local version/help commands, and model listings. It launched no agent, inference request, benchmark, or installation.

## Recommendation changes

Compared with the table dated 2026-11-10:

| Cell or rule | Change | Reason and limit |
| --- | --- | --- |
| Ready-plan code, medium impact | GPT-6.1 Sol `medium`, `xhigh` for harder work, becomes GPT-6.2 Sol `medium` and `xhigh`. Sol 6.2 `max` is a candidate. | [T] FrontierCode 2.0, rescored: 6.2 `medium` 38.3%/$0.69 versus 6.1 `medium` 30.3%/$0.49 and 6.1 `high` 35.1%/$0.65; native AA v2.1 6.2 `medium` 45.4/$0.57. Counterexample: AA v2.1 at `max`, 6.2 48.6 versus 6.1 52.2, all from SWE-Atlas-QnA (46.2% versus 59.9%); 6.2 gains on Terminal-Bench. `max` leads on Cognition's data and trails `xhigh` on AA's, so it stays a candidate [I]. |
| Medium planning | GPT-6.1 Sol `max` becomes GPT-6.2 Sol `max` on a ChatGPT plan. | [T] AA Index v5.0.1: 57.3/$1.01 versus 54.6/$1.27. |
| Complex planning | Fable 5.2 `high`, Opus `xhigh` when Fable is excluded, becomes subscription-dependent: Fable `high` on a Claude plan that includes Fable, GPT-6.2 Astra `xhigh` on a ChatGPT plan, otherwise Opus `xhigh`. | [T] Index v5.0.1: Astra `xhigh` 61.6/$2.52 versus Fable `high` 61.8/$9.08, Opus `xhigh` 57.4/$6.05 and `max` 59.1/$10.04. The Astra-Fable gap is 0.2 point, so the pool decides, as in medium planning. Proxy only [I]. |
| Astra rule | "No recommended cell" becomes one cell, complex planning on a ChatGPT plan. | The old rule rested on Astra reaching the same tiers as Sol. On the planning proxy, Astra 6.2 `xhigh` now leads Sol 6.2 `max` by 4.3 points [T]. In code, Sol 6.2 `max` sits 0.4 point under Astra `max` on FrontierCode for a fifth of the cost [T], so Astra stays out of code cells. [V] Plus estimates: Astra 6 to 50 messages per five hours, Sol 6.2 17 to 180. [I] By the ratio of the bounds, Astra draws a ChatGPT plan roughly three times as fast as Sol 6.2. No source establishes a multiplier per task or per effort. |
| Long autonomous code | Opus `xhigh` kept; Sol 6.2 `max` added as a candidate. | [T] FrontierCode 2.0: Sol `max` 43.8%/$1.29 versus Opus `xhigh` 44.7%/$5.18. AA v2.1: Sol `max` 48.6 versus Opus `max` 58.2. The results conflict, so the cell keeps Opus [I]. |
| Ready-plan code, low impact | Luna `max` kept; Sol 6.2 `low` added as a candidate. | [T] Sol `low` 33.1%/$0.40 versus Luna `max` 22.7%/$0.17 on FrontierCode, 37.2 versus 25.9 on AA v2.1. [V] Plus estimates: Sol 6.2 17 to 180 messages per five hours, Luna 350 to 3,000. [I] The ratio of the bounds puts Sol's draw at roughly 17 to 20 times Luna's. No source establishes a multiplier per task or per effort. |
| Routine code review | The cross-vendor pass keeps GPT-6.1 Sol `xhigh`, now named in full; Sol 6.2 `xhigh` is a candidate. Authors above Opus `high` now include Astra 6.2 at `medium` or above and Sol 6.2 `max`. | [T] FrontierCode favors 6.2 `xhigh` (39.8% versus 33.0%), but AA's SWE-Atlas-QnA, the closest test to answering questions about a codebase, drops 14 points at `max` (46.2% versus 59.9%) because 6.2 omits key facts. AA lists no 6.1 `xhigh` result. [V] GPT-6.2 launched with tighter cybersecurity safeguards. Applicable results conflict, so the previous model stays [I]. |
| Moderate-stakes web research | Keeps GPT-6.1 Sol `high`, now named in full; Sol 6.2 `high` is an unmeasured candidate. | [T] Parallel's 2026-11-14 board has no GPT-6.2 row. Scores do not transfer between versions. |
| High-stakes web research | Opus `high` kept; Fable 5.2 `medium` becomes an independently measured candidate. | [T] Parallel, 2026-11-14: Fable 5.2 80.1/$2,426 versus Opus 76.1/$896. Four points without uncertainty, 2.7 times the cost, effort unstated [I]. |
| Unplanned or high-impact code | Unchanged; GPT-6.2 Astra does not enter. | [T] Astra `max` 44.2% on FrontierCode and 53.5 on AA v2.1, below Fable `high` (46.2%, 58.2) and Opus `max` (47.3%, 58.2). |
| Code figures | FrontierCode 2.0 figures replaced by Cognition's 2026-11-11 rescore; AA Coding Agent Index v1.5 and v2.0 replaced by v2.1. | [T] The rescore changed every score, for example Opus `max` 45.5% to 47.3% and Fable `high` 45.3% to 46.2%. No cell order changed. v2.1 swaps FrontierCode v1.1 for FrontierCode-AA 2.0 and now lists Fable 5.2, which ties Opus `max` at `high`. |
| Planning, search, and writing grids | Rebuilt with GPT-6.2 rows and the 2026-11-18 reads. | [T] AA comparisons and Parallel's 2026-11-14 board. Briefcase Elo shifted (Sonnet 1815, Opus 1800); GPT-6.2 does not enter professional documents (Astra 1644, Sol 1612). |
| Catalog | GPT-6 Astra row becomes GPT-6.2 Astra; the GPT-6.1 Sol row becomes GPT-6.2 Sol, plus a GPT-6.1 Sol row marked previous generation. | Local Codex catalog, 2026-11-18. The Cursor list failed with an authentication error. |
| Cost section | GPT-6.2 prices and credits, Plus estimates, Pro tiers, Fast and Ultrafast multipliers; Terra 6.1 credits recorded. | [V] Model pages and Codex pricing, read 2026-11-18. |

Unchanged: mechanical code, unplanned or high-impact code, simple planning, low-stakes web research, security-sensitive review, professional documents, and the prose fallback.

Sources for changes: [GPT-6.2 announcement][openai-62], [GPT-6.2 model pages][openai-sol62], [Codex pricing][codex-price], [FrontierCode 2.0][frontier2] and its [data][frontier2-data], [AA's GPT-6.2 article][aa-gpt62] and [comparisons][aa-astra-fable], [AA's coding board][coding], [Vals][vals-sol62], and [Parallel][parallel]. All were read on 2026-11-18.

## Discovery decisions

Discovery on 2026-11-18 covered [AA's dated article feed][feed] and [changelog][aa-changelog] back to 2026-11-10, its [coding-agent board][coding], [Cognition's FrontierCode page][frontier2] and changelog, [Vals' model list][vals-list], [Parallel][parallel], the [OpenAI changelog][openai], the GPT-6.2 model pages and guide, [Codex pricing][codex-price], OpenAI's [developer-forum announcement][openai-62], the [Dam Secure blog][dam-blog], the [Rails blog][rails-blog], and local catalogs. [OpenAI's launch page][openai-launch62] returned HTTP 403. Newly considered does not mean newly released: release dates are asserted only when a source states them. In the table below, release dates come from AA model pages (`artificialanalysis.ai/models/<slug>`), Vals model pages, or Parallel's board, and evaluation and endpoint dates from AA's changelog. Where sources disagree, both dates are given. All were read on 2026-11-18.

### New since 2026-11-10

| Model or version | Status / local identifier | Disposition and reason |
| --- | --- | --- |
| GPT-6.2 Sol, released 2026-11-17 | Codex `gpt-6.2-sol`, visible, default `low`, `low` through `max` plus `ultra`, Fast and Ultrafast; API `gpt-6.2-sol`, guide starts at `medium` [V]. Cursor unchecked because the list required authentication. ZDR for approved API organizations [V]. | Ranked: ready-plan medium-impact code, medium planning on a ChatGPT plan. Candidate: low-impact code at `low`, long autonomous code at `max`, moderate research, the review pass. AA evaluated Codex 0.166.0; local 0.169.0. Inference access unverified. |
| GPT-6.2 Astra, released 2026-11-17 | Codex `gpt-6.2-astra`, visible, default `low`, Fast only in the local catalog; API `gpt-6.2-astra`. | Ranked: complex planning on a ChatGPT plan. Not in code cells: below Fable 5.2 `high` and Opus `max` on both coding boards, and Sol 6.2 comes close for less. No search or review result. Inference access unverified. |
| GPT-6 Astra; GPT-6.1 Sol | Still listed; Codex labels 6.1 Sol the previous generation, and AA marks both deprecated. | GPT-6 Astra is replaced by Astra 6.2. GPT-6.1 Sol stays only in moderate web research and the review pass, for the reasons in the change table. Their measurements stay attributed to them. |
| Astra for Law 6.2, released 2026-11-17, AA evaluation the same day | OpenAI, closed weights. No Codex slug. Source: AA model page and changelog. | Ignored: domain product with no installed path. AA publishes no Index value. |
| Gemini 4 Hydrogen, released 2026-11-12 per Vals and Parallel, AA evaluation the same day | Google, closed weights. Absent locally, and so is Antigravity CLI. Sources: AA changelog, Vals, Parallel. | Unranked locally: Index v5 `xhigh` 53.9, FrontierCode 2.0 `xhigh` 38.9%/$4.95 and native AA v2.1 52.3/$4.45 in Antigravity CLI, Parallel 72.7/$175 [T]. |
| Qwen4 Max, released 2026-11-16 per AA, 2026-11-15 per Vals, AA evaluation 2026-11-15 | Alibaba, closed weights. Absent locally. Sources: AA model page and changelog, Vals. | Ignored: Index v5 43, Vals Index 63.20% [T]. No installed path. |
| Hy4, released 2026-11-04 per Vals and Parallel, first on Parallel's 2026-11-14 board | Tencent, open weights. Absent locally. Sources: Vals, Parallel. | Ignored for routing: Parallel 75.4/$94.4, Vals Index 59.35% [T]. No installed path. |
| Hy4 Flash, released 2026-11-16 per Vals | Tencent, closed weights. Absent locally. Not on Parallel's board. Source: Vals. | Ignored: Vals Index 50.78% [T]. No installed path. |
| K2 Horizon 32B, released 2026-09-03, AA evaluation 2026-11-18 | Institute of Foundation Models, open weights. Absent locally. Source: AA model page and changelog. | Ignored: Index v5 14 [T]. No installed path. |
| JoyAI-VL-Preview, released 2026-11-17, AA evaluation the same day | Joy Future Academy, preview, closed weights. Absent locally. Source: AA model page and changelog. | Ignored: preview, Index v5 28 [T]. No installed path. |
| Inkling (High), released 2026-07-15, AA evaluation 2026-11-17 | Thinking Machines, open weights. Absent locally. Source: AA model page and changelog. | Ignored: Index v5 11 [T]. No installed path. |
| Inkling Small (High), released 2026-07-30, AA evaluation 2026-11-17 | Thinking Machines, open weights. A different model from Inkling 2 Small. Absent locally. Source: AA model page and changelog. | Ignored: Index v5 10 [T]. No installed path. |
| Inkling 2 Small, new Together AI and Nebius endpoints on AA, 2026-11-16 | Thinking Machines. Absent locally. Source: AA changelog. | Ignored for lack of an installed path, as in the 2026-11-10 row below. |
| LFM3-1.7B, released 2026-10-27, AA evaluation and Liquid AI endpoint 2026-11-17 | Liquid AI, open weights, 1.7B parameters. Absent locally. Source: AA model page and changelog. | Ignored: Index v5 6 [T]. No installed path. |
| LFM3-VL-2B, released 2026-10-27, AA evaluation 2026-11-17 | Liquid AI, open weights, vision-language. Absent locally. Source: AA model page and changelog. | Ignored: Index v5 2 [T]. No installed path. |
| MiniMax-M3.1-Flash, released 2026-10-19 per AA, 2026-10-20 per Vals, new Makora endpoint on AA, 2026-11-17 | MiniMax, open weights. Absent locally. Sources: AA model page and changelog, Vals. | Ignored: Index v5 29 [T]. No installed path. |
| JT-4.1 Flash 236B A21B, released 2026-11-11, AA evaluation the same day | China Mobile, closed weights. Absent locally. Source: AA model page and changelog. | Ignored: Index v5 19 [T]. No installed path. |
| DeepSeek V4 Pro 0813 (High), released 2026-08-13, AA evaluation 2026-11-13 | DeepSeek, open weights. Absent locally. Source: AA model page and changelog. | Ignored: Index v5 21 [T]. No installed path. |
| Gemini 4 Argon (Medium), AA evaluation 2026-11-13 | Google. Cursor listed `gemini-4-argon-medium` on 2026-10-16. The Cursor list could not be read on 2026-11-18. Source: AA changelog. | Unranked for Cursor routing, unchanged: Index v5 48 [T]. |
| Gemini 4 Carbon, Vals release date 2026-11-10, after the 2026-10-28 announcement recorded below | Google. Antigravity CLI absent. Source: Vals. | Unranked locally, unchanged: Vals Index 70.45% [T]. Whether 2026-11-10 marks wider availability is unverified. |
| d1.2, released 2026-11-16 per Vals | Liquid AI, closed weights, a decision model (Vals URL prefix `decision_`). Absent locally. Source: Vals. | Ignored: decision model, best Vals result ClaimBench, 6th of 28. No installed path. |
| d1.2-ultra, released 2026-11-16 per Vals | Liquid AI, closed weights, a decision model. Absent locally. Source: Vals. | Ignored: decision model, best Vals result ClaimBench, 3rd of 28. No installed path. |
| Decider V1.3, released 2026-11-12 per Vals | Perplexity, open weights, a decision model. Absent locally. Source: Vals. | Ignored: decision model, best Vals result ClaimBench, 2nd of 28. No installed path. |
| Decider Flash V1.3, released 2026-11-12 per Vals | Perplexity, open weights, a decision model. Absent locally. Source: Vals. | Ignored: decision model, Vals ClaimBench 97.45% ± 0.36, 16th of 28, read 2026-11-18. No installed path. |
| Gemini Decision 1, released 2026-11-11 per Vals | Google, closed weights, a decision model. Absent locally. Source: Vals. | Ignored: decision model, Vals ClaimBench 97.50% ± 0.35, 15th of 28, read 2026-11-18. No installed path. |
| Kimi K3.1 Pro, new DigitalOcean and Databricks endpoints on AA, 2026-11-10 and 2026-11-11 | Absent locally. Source: AA changelog. | Ignored for lack of an installed path, as in the 2026-11-10 row below. |
| GLM-5.3, new SambaNova endpoint on AA, 2026-11-11 | Absent locally. Source: AA changelog. | Ignored for lack of an installed path, as in the 2026-11-10 row below. |
| DeepSeek V4.1 Flash 1017, new Fireworks endpoint on AA, 2026-11-13 | Absent locally. Source: AA changelog. | Ignored for lack of an installed path, as in the 2026-11-10 row below. |
| GPT-6.1 Terra, reassessed | Codex `gpt-6.1-terra`; Plus estimate 35 to 285 messages, 125 output credits per million [V]. | Still a candidate, unranked. Native AA v2.1 `max` 48.6/$1.53 [T] trails Sol 6.2 `xhigh` (49.8/$0.90) on score and cost, and Terra is absent from FrontierCode 2.0. Against Luna for low-impact code it costs more per task; Sol 6.2 `low` is the nearer candidate there. |
| GPT-6 Cyber, 2026-11-05 | OpenAI Daybreak program. | Ignored: trusted-access model, not selectable here. |
| FrontierCode 2.0 rescore, 2026-11-11; AA Coding Agent Index v2.1; Gemini 4 Carbon moved to Antigravity CLI on FrontierCode, 2026-11-12 | Methodology revisions. | Grids rebuilt. Pre-rescore and v2.0 values are no longer compared with current ones. |
| AA Multimodal Knowledge Agent, 2026-11-10; Endpoint Accuracy Index v1.1 | New AA evaluations. | Ignored: no routing cell uses them. |

### Considered on 2026-11-10, new since 2026-10-16

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
| GPT-6.1 Sol; Claude Sonnet 5.5 | Codex `gpt-6.1-sol`; Claude `claude-sonnet-5-5`, Cursor `claude-sonnet-5-5-<effort>`. | Sonnet ranked as in the table. GPT-6.1 Sol was replaced by GPT-6.2 Sol on 2026-11-18, except in moderate web research and the review pass. |
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

| Harness or executable | Local observation on 2026-11-18 | Disposition |
| --- | --- | --- |
| Codex | `codex-cli 0.169.0`; `debug models` succeeds; twelve slugs, adding `gpt-6.2-sol` and `gpt-6.2-astra`. | Retain. AA's GPT-6.2 runs used 0.166.0; Sol 6.1 and Luna 0.154.0; Terra 6.1 0.163.0 and 0.166.0. |
| Claude Code | 2.1.327; `--help` exposes aliases `fable`, `opus`, `sonnet`, full model names, `--effort`, and `--restricted`. | Retain. No non-interactive model-list command. Fable 5.2 needs 2.1.321 or later [V]; AA's Fable 5.2 runs used 2.1.291. |
| Cursor | 2026.09.28-64d2043, unchanged; `cursor-agent` and `agent` resolve to the same executable. `--list-models` failed: "Authentication required". | Retain one harness. GPT-6.2 availability in Cursor is unchecked. |
| Herdr | `herdr` found with `HERDR_ENV` unset; `hc` 0.1.21 found with `HC_TERMINAL_ID` set, so this session ran in Herdr App. | Retain as an orchestration tool. No terminal or session created. |
| Mistral Vibe | `vibe` 2.14.1, unchanged. `-p` runs non-interactively; help lists no model catalog. | Unranked locally; no recommended model runs in it. |
| Antigravity CLI, Muse Code, Devin Fusion, Grok Build, Kimi Code, OpenCode, GitHub Copilot CLI | `agy`, `antigravity`, `gemini`, `muse`, `devin`, `fusion`, `grok`, `kimi`, `opencode`, `copilot` absent. | Unranked locally. |
| Other known CLIs | `aider`, `goose`, `amp`, `droid`, `pi`, `qwen` absent. | No local ranking or launch form assumed; recheck at the next update. |

Executable names are search candidates, not inferred installation instructions. Missing `command -v` results establish absence from this PATH only. The tested-command history and current help checks are separate in [harness.md](harness.md).

## Fable 5.2 versus Opus 5.5

Reassessed on 2026-11-18, after Cognition's FrontierCode rescore and AA's Coding Agent Index v2.1. The verdict of 2026-11-10 holds. Independent results favor Fable 5.2 at equal effort on mergeable code and on reasoning proxies. They do not favor it on terminal tasks, professional documents, multimodal SWE-bench, or cost per task. Opus stays the default where Fable's limits apply: plan cap, retention, and safeguard fallbacks [I].

The 2026-10-16 notes set a symmetric threshold: comparable current evidence beyond small gaps, and no small gap without uncertainty treated as a winner. Rescored FrontierCode 2.0 gaps at equal effort are 5.5 to 20.5 points from `low` to `xhigh`, and 0.9 point at `max`. Index v5 gaps are 4.8 to 10.0 points from `medium` to `max`. They exceed the 3.7- and 5-point Opus leads that kept Opus first over Fable 5.1. Neither source reports uncertainty, so differences between neighboring efforts are not used to choose an effort.

For a future update to move Fable 5.2 out of its cells, require comparable current evidence that Opus matches it beyond uncertainty on mergeable code or reasoning proxies, at equal or lower cost. A user or project may still exclude Fable by preference; that choice belongs in their preference files, not here.

| Task | Published comparison, Opus 5.5 versus Fable 5.2 | Verdict and limits |
| --- | --- | --- |
| Planning | AA Index v5.0.1: `max` 59.1 versus 64.6; `xhigh` 57.4 versus 62.2; `high` 51.8 versus 61.8; `medium` 48.2 versus 56.4. HLE-Diamond `max` 67.9% versus 80.2%; Terminal-Bench-Science 59.0% versus 73.3% [T, API with default fallback]. | Fable leads every reasoning proxy at equal effort. No direct repository-plan test. Fable `high` for complex planning [I]. |
| General code | FrontierCode 2.0 in Claude Code, rescored 2026-11-11: `low` 14.8% versus 35.3%, `medium` 31.4% versus 38.8%, `high` 36.3% versus 46.2%, `xhigh` 44.7% versus 50.2%, `max` 47.3% versus 48.2%. AA's Stirrup run: `max` 46.4% versus 48.8%, `high` 35.9% versus 49.1%. Native AA v2.1: Opus `max` 58.2/$12.61 versus Fable `high` 58.2/$7.51 and `xhigh` 58.5/$15.47. Terminal-Bench 4.0: AA `max` 59.6% each; Vals 65.15% each. Vals SWE-bench Multimodal 70.21% versus 62.29%; ProgramBench 18.50% versus 19.00% [T]. | Fable leads mergeability in two harnesses and matches Opus `max` on AA's native board at lower cost. Terminal tasks tie and multimodal SWE-bench favors Opus. No Rails result exists for Fable 5.2. |
| Secure-code generation | No Fable 5.2 result. | Endor's Fable 5.1 counterexample does not transfer. |
| Security review | No independent Fable 5.2 result. Anthropic: safeguards block most cybersecurity tasks and route them to Opus 4.8, with about 60% fewer cybersecurity blocks than Fable 5.1; its CVE Rediscovery figures measure Mythos 5.2, not Fable [V]. | Unvalidated candidate; check the served model. |
| Research | Parallel, 2026-11-14: Opus 76.1/$896 versus Fable 80.1/$2,426 per 1,000 tasks, effort unstated [T]. Anthropic's WANDR run: 72.3% versus 82.1%, Fable `medium` matching Opus's best for about 40% of the cost [V]. | Independently measured candidate for high-stakes research. Four points without uncertainty at 2.7 times the cost keep Opus first. |
| Professional outputs | AA-Briefcase v1.1 `max`, 2026-11-18: 1800 versus 1785; GDPval-AA, 2026-11-10: 1866 versus 1831 [T]. Anthropic's Briefcase rubric 61.2% versus 66.1% [V]. | Opus and Sonnet lead on Elo; Fable does not enter. |
| Prose and reformulation | No reproducible direct comparison. | No verdict. |

The [Anthropic launch][fable52-vendor] adds vendor evidence [V]: FrontierSWE v2 69.9% versus 62.3%, AutomationBench 51.4% versus 42.5%, OSWorld 2.1 89.3% versus 87.2%, and Remote Labor Index 41.3% versus 21.3%. It recommends starting most coding and knowledge tasks with Opus 5.5 and moving to Fable for the most ambitious open-ended technical work. It says Fable `high` matched Opus `max` on FrontierCode 2.0 for roughly half the cost; Cognition's rescored data give 46.2% versus 47.3% for $8.40 versus $12.82, about two-thirds.

Fallbacks are part of the configuration [V]: blocked cybersecurity requests go to Opus 4.8, blocked biology requests to Opus 5, and a few AI research topics to Opus 5. Vals reports a 1.88% fallback rate at `high` [T]. AA's Fable entries include default fallback.

### Relative cost and quota

| Setup | Opus 5.5 versus Fable 5.2 | What it establishes |
| --- | --- | --- |
| Standard API, dollars/million input/output [V] | $4/$20 versus $8/$40; cache read $0.20 each; Fable fast mode $16/$80. | Fable tokens cost twice as much; cache reads cost the same. |
| AA Index v5.0.1 [T] | `max` $10.04 versus $26.54; `high` $3.46 versus $9.08 per task. | Fable costs about 2.6 times as much at equal effort. Fable `high` exceeds Opus `max` for 10% less. |
| FrontierCode 2.0, Claude Code [T] | `medium` $1.70 versus $3.10; `high` $2.42 versus $8.40; `xhigh` $5.18 versus $17.73; `max` $12.82 versus $55.87. | Fable costs 1.8 to 4.4 times as much at equal effort. At a near-equal score (Opus `max` 47.3%, Fable `high` 46.2%, rescored), Fable costs about a third less. |
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
[frontier2]: https://cognition.com/frontiercode
[frontier2-data]: https://cognition.com/data/frontier-code-2.0/data.json
[aa-terra]: https://artificialanalysis.ai/articles/gpt-6-1-terra-pushes-the-cost-efficiency-frontier
[aa-carbon]: https://artificialanalysis.ai/articles/gemini-4-carbon-new-number-1
[aa-kimi]: https://artificialanalysis.ai/articles/kimi-k3-1-pro-launch-benchmarks
[aa-ember]: https://artificialanalysis.ai/articles/meta-s-muse-ember-is-the-cheapest-model-scoring-36-on-the-intelligence-index
[aa-inkling]: https://artificialanalysis.ai/articles/thinking-machines-releases-inkling-2-small-highest-scoring-open-weights-model-outside-of-chinia-upon-weights-release-it
[aa-fusion]: https://artificialanalysis.ai/articles/github-copilot-fusion-orchestrates-anthropic-and-openai-models-to-balance-performance-and-cost
[rails-blog]: https://rubyonrails.org/blog
[notebookcheck]: https://www.notebookcheck.net/Claude-Fable-5-2-fallbacks-make-AI-agents-more-vulnerable.1446771.0.html
[anthropic-price]: https://platform.claude.com/docs/en/about-claude/pricing
[openai-62]: https://community.openai.com/t/gpt-6-2-astra-and-sol-are-now-available/1417531
[openai-launch62]: https://openai.com/index/introducing-gpt-6-2-astra-sol/
[openai-sol62]: https://developers.openai.com/api/docs/models/gpt-6.2-sol
[codex-price]: https://learn.chatgpt.com/docs/pricing
[aa-gpt62]: https://artificialanalysis.ai/articles/openai-has-the-2-model-in-the-intelligence-index-with-the-release-of-gpt-6-2-astra-and-gpt-6-2-sol
[aa-astra-fable]: https://artificialanalysis.ai/models/comparisons/gpt-6-2-astra-vs-claude-fable-5-2
[aa-changelog]: https://artificialanalysis.ai/changelog
[vals-sol62]: https://www.vals.ai/models/openai_gpt-6.2-sol
[vals-list]: https://www.vals.ai/models
