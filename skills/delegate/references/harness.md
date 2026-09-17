# Harness

How to launch a delegated agent from any harness: everything goes through shell commands. The installed CLI’s `--help` is authoritative; this file keeps what it does not say.

Marked **✔**: executed on 2026-09-16 with codex-cli 0.154.0, Claude Code 2.1.273, and cursor-agent 2026.09.10. The rest is a form to verify before use.

## Model inventory

- **Codex**: `codex debug models`.
- **Cursor**: `cursor-agent --list-models`. Models without zero data retention are marked “(NO ZDR)” there.
- **Claude Code**: aliases `opus` and `fable` for `--model`.
- **Any CLI**: a trivial prompt (“Reply with PONG only”) with the intended model and effort confirms access for a few tokens.

## Common form

Write the brief to a file and pass it **on standard input** (`< brief.md`). The three CLIs below read it that way ✔, and that avoids quoting a long text in the shell.

Grant the permissions of the brief’s **scope**, no more: read-only for a search, a planning task, or a review; write for an implementation.

For a long task, run the command in the background if your harness allows it, or redirect its output to a file you will read.

## Codex

```sh
codex exec --ephemeral -s read-only -m gpt-5.6-luna -c model_reasoning_effort="low" - < brief.md
```

✔ as written. Variants:

- **write**: `-s workspace-write`;
- **outside a git repository**: `--skip-git-repo-check`;
- **web**: `--search`, or `web_search = "live"` in the Codex configuration ([doc](https://developers.openai.com/codex/config-basic)) ✔;
- **last message to a file**: `-o <file>`.

## Claude Code

```sh
claude -p --model opus --effort low < brief.md
```

✔ as written. Variants:

- **web**: `--allowedTools "WebSearch,WebFetch"` ✔. This option is **variadic**: it swallows a prompt placed after it. The brief therefore goes on standard input, never as an argument.
- **write and shell**: `--permission-mode` and `--allowedTools` set the rights; check the values in `claude --help`.

## Cursor

```sh
cursor-agent -p --trust --mode ask --model cursor-grok-4.6-low --output-format text < brief.md
```

✔ as written, in read-only mode. Variants:

- **shell or web**: `-f --sandbox enabled` ✔. Without `-f`, an agent in `-p` mode is denied shell and web search, **even in a trusted directory**. `--sandbox enabled` bounds what `-f` opens.
- **write**: drop `--mode ask`.
- **model**: effort is part of the identifier (`gpt-5.6-luna-high`, `cursor-grok-4.6-high`); take the exact identifier from `cursor-agent --list-models`.

## Herdr

Herdr launches the agent in a pane, where the user can follow it. If a `herdr` skill is installed, follow it; `herdr --help` and `herdr agent` are authoritative.

1. Find or create a free shell pane (`herdr pane`).
2. Start the agent with its model and effort options:
   ```sh
   herdr agent start <name> --kind codex --pane <id> -- --model gpt-5.6-luna -c model_reasoning_effort="high"
   ```
   `--kind` also accepts `claude`, `cursor`, and others; options after `--` are those of the interactive CLI.
3. Send it a pointer to the brief:
   ```sh
   herdr agent prompt <name> "Read and execute the brief in file <path>." --wait
   ```
4. Read its deliverable with `herdr agent read <name>`, or in the files the brief designates.

## Other CLIs

Gemini CLI, OpenCode, and the others: in their `--help`, find non-interactive mode, model and effort selection, standard-input reading, and permissions. Verify the form with a trivial prompt before sending the brief.

## Confidentiality

For confidential data, keep a model and a harness that retain zero data:

- **Cursor**: discard models marked “(NO ZDR)” in `cursor-agent --list-models`. On 2026-09-16, that was the case for all `claude-fable-5-1-*`.
- **Anthropic**: Fable models impose 30 days of retention by default ([Claude support](https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan)).
- For the others, the provider’s retention policy and the user’s contract are authoritative; when in doubt, ask.
