# Markdown Conventions

Microsoft Writing Style Guide flavored markdown rules. Apply these to every
document the tech-writer skill produces. Load this file before drafting and
re-check against it before delivering.

## Headings

- ATX style only (`#`, `##`), never Setext (underline-style).
- One space after the `#` characters; no trailing `#`.
- Exactly one H1 per document — the title.
- Never skip levels: H2 follows H1, H3 follows H2.
- Sentence case: capitalize only the first word and proper nouns.
- No punctuation at the end of a heading (no colons, no periods).
- Headings are surrounded by one blank line above and below.

## Text emphasis

- **Bold** (`**text**`) for UI elements, key terms on first use.
- *Italic* (`*text*`) rarely — for introducing a technical term.
- `Code font` (backticks) for file names, paths, commands, flags,
  parameter names, code identifiers, and values the user types literally.
- Never use emphasis as a substitute for a heading.
- Never use ALL CAPS for emphasis.

## Scannability

Readers scan docs — they don't read them linearly.

- One idea per paragraph; max 3–4 sentences per paragraph.
- Front-load the important word: put the action or object first
  ("Restart the service to apply…", not "To apply the changes, the
  service should be restarted").
- Break walls of text into lists, tables, or subsections.
- Readers scan headings and first sentences — make both self-sufficient.

## Lists

- Unordered lists: hyphen (`-`) marker only, never `*` or `+`.
- Ordered lists: use `1.` for every item; let the renderer number them.
- One space after the list marker.
- Indent nested items by two spaces, aligned under the parent text.
- Capitalize the first word of each item; end with a period only if the
  item is a complete sentence.
- Introduce a list with a complete sentence ending in a colon — never a
  bare heading followed immediately by a list.

## Code blocks

- Fenced blocks with triple backticks, always with a language tag:
  ` ```bash `, ` ```json `, ` ```python `. Use `text` for plain output.
- No inline triple-backtick blocks inside list items without proper
  indentation (indent the fence to align with the item text).
- Commands the user runs: show the complete command, no shell prompt
  (`$`) prefix.
- Placeholders in code: descriptive, lowercase-hyphenated, e.g.
  `<your-project-name>` — never `xxx` or `foo` in real examples.

## Links

- Inline style: `[link text](URL)`.
- Link text is descriptive — never "click here" or bare URLs.
- Reference-style links only when the same URL appears 3+ times.
- Relative links for files in the same repository.

## Tables

- Pipe tables with a header row and a delimiter row of hyphens.
- One space on each side of cell content; pipes aligned when practical.
- Keep cell content short — if a cell needs a paragraph, use a list or
  prose instead.
- Don't use tables for layout.

## Notes and callouts

Use blockquotes with a bolded label:

```markdown
> **Note:** Supplementary information the reader can skip.
> **Important:** Information the reader must know before continuing.
> **Caution:** Risk of data loss or security impact.
```

One blank line before and after the blockquote. Don't stack callouts.

## Tone and style (Microsoft Writing Style Guide)

- Second person ("you"), present tense, active voice.
- Imperative mood for steps: "Run the command", not "You should run…" or
  "The command should be run…".
- Avoid: "simply", "just", "easily", "obviously", "please", "we",
  "let's", hedging ("might want to"), future tense for current behavior
  ("the tool will create" → "the tool creates").
- No exclamation marks, no emojis, no rhetorical questions.
- Contractions are acceptable ("don't", "it's") but avoid overuse in
  formal reference docs.
- Spell out acronyms on first use: "Azure Resource Manager (ARM)".
- Numbers: spell out one through nine in prose; numerals for 10+ and for
  all technical quantities (versions, ports, sizes).
- Serial (Oxford) comma always.
- Sentences ≤ 25 words; split nested clauses. Prefer common words ("use",
  not "utilize"; "start", not "commence").

## Terminology

- Choose one term per concept at first use; never use synonyms for the
  same thing within a document (pick "plugin" *or* "extension", not both).
- Use the same verb for the same action throughout ("create", not
  alternating "create/set up/generate").

## Document mechanics

- One blank line between every block element (paragraphs, headings,
  lists, code blocks).
- No trailing whitespace; file ends with a single newline.
- Line length: no hard wrap requirement, but one sentence per line is
  preferred for easier diffs and reviews.
