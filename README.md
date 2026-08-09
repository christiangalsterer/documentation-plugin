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

## Installation

This plugin is loaded automatically by Claude Code when placed in your project or global plugin directory. See the [Claude Code plugin documentation](https://docs.anthropic.com/en/docs/claude-code/plugins) for setup details.
