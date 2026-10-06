# documentation-plugin

A Claude Code compatible plugin that provides skills for writing and maintaining technical documentation.

## Skills

### `tech-writer`

Writes and edits technical documentation in a professional tone, following a fixed document structure (title, overview, prerequisites, steps, troubleshooting, next steps) and Microsoft Writing Style Guide markdown conventions. Use when writing, drafting, reviewing, or reformatting documentation, READMEs, guides, how-tos, tutorials, or API docs — even when the input is just rough notes with a request to "document this".

**How it works:**

1. Identifies the audience and goal (asks if missing).
2. Gathers the facts by reading the code, config, or notes the doc covers — never inventing commands, flags, file paths, or behavior.
3. Drafts using the fixed structure: title, overview, prerequisites, task sections, troubleshooting, next steps.
4. Applies the markdown conventions defined in `references/markdown-conventions.md`, loaded on demand.
5. Validates the draft against the built-in checklist (one H1, sentence-case headings, language-tagged code blocks, imperative numbered steps, verified examples) before presenting the result.

### `remove-ai-slop`

Reviews and cleans AI-slop from writing: filler and marketing adverbs ("simply", "just", "easily"), empty openers, overused jargon and leverage verbs ("leverage", "utilize", "robust"), hedging, future tense for current behavior, and em-dash overuse. Use when asked to de-AI or tighten a draft.

**How it works:**

1. Identifies the setting (file on disk vs. inline prose).
2. Scans for slop categories and records each location, phrase, and proposed replacement.
3. Reports findings as a numbered table (`# | Location | Phrase | Suggested fix`) before editing (unless auto-fix requested).
4. Applies only the selected fixes — the user picks findings by entering a number, a comma-separated list, a range, or a combination (`3`, `1,2,5`, `1-3`, `1-3,5,7-8`) — preserving meaning, facts, and technical terms.
5. Re-verifies against the built-in checklist (no filler, no jargon, no em-dashes by default, no exclamation marks, sentences ≤ 25 words) before presenting the result.

### `kafka-integration`

Provides reusable Kafka-specific guidance for designing, implementing, reviewing, and troubleshooting integrations. It can be used directly by human users or applied by agents and other skills. Its references cover design review, delivery and recovery, partitioning and capacity, schemas and connectors, security and operations, and managed Kafka-compatible services. Optional templates support substantial design reviews and troubleshooting.

For Kafka documentation, use this skill to establish the technical facts and `tech-writer` to apply document structure and writing conventions.

## Agent

### `kafka-integration-expert`

An on-demand Kafka specialist for designing, evaluating, troubleshooting, and discussing Kafka integrations. It uses the reusable `kafka-integration` skill for domain workflows and checklists, asks for version and deployment context when those details affect correctness, and makes assumptions explicit.

The agent is authored as an APM agent primitive in `.apm/agents/kafka-integration-expert.agent.md` and deploys to Claude Code and OpenCode. OpenCode installs the agent at `.opencode/agents/kafka-integration-expert.md`. Consult the [APM primitives and targets matrix](https://microsoft.github.io/apm/concepts/primitives-and-targets/) for support on other harnesses.

## Installation

This plugin is loaded automatically by Claude Code when placed in your project or global plugin directory. See the [Claude Code plugin documentation](https://docs.anthropic.com/en/docs/claude-code/plugins) for setup details.
