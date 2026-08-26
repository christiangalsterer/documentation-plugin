---
name: remove-ai-slop
description: >-
  Review and clean AI-slop from writing: filler and marketing adverbs,
  empty openers, overused jargon, hedging, future tense for current behavior,
  and em-dash overuse. Use when asked to remove AI-sounding phrasing, tighten
  prose, de-AI text, edit out "simply/just/easily", flag or strip em-dashes,
  or de-jargon a draft — even when the input is just prose or a doc with a
  request to "clean this up". Do NOT use for commit messages (use the commit
  skill) or for rewriting meaning, restructuring documents, or line editing
  that is not about AI-slop.
metadata:
  author: Christian Galsterer
  version: "1.1.0"
---

# Remove AI Slop

Identify and remove AI-slop: the filler, hedging, marketing, and jargon
phrases that AI text generators lean on, plus em-dash overuse. Output is
cleaner prose with the meaning, facts, and technical terms intact.

This skill is a reviewer/cleaner, not a writer. It edits what is there; it
does not invent content or restructure the document.

## Workflow

1. **Identify the setting.** Determine the input: a file on disk to edit in
   place, or inline prose to return cleaned. If you write to a `.md` file,
   never wrap the result in a code fence — the file content IS markdown.
2. **Scan the text.** Flag every match of the categories below. Record the
   exact location (line or sentence), the current phrase, and a proposed
   replacement.
3. **Report before editing** (unless the user asked for auto-fix). Present
   findings as a numbered table where each entry gets a number starting at 1:

   | # | Location | Phrase | Suggested fix |
   |---|----------|--------|---------------|

   Let the user accept or reject findings before you apply changes.
4. **Apply the selected fixes.** The user picks which findings to fix by
   number. Keep the meaning, facts, and technical terms intact.

   **Selecting findings.** Selection is 1-based and can be a single number,
   a comma-separated list, a range, or any combination:

   - Single: `3`
   - List: `1,2,5`
   - Range: `1-3`
   - Combined: `1-3,5,7-8`

   Whitespace after commas is allowed and ignored (`1, 3` → findings 1 and
   3). An out-of-range number is not an error in the whole selection — apply
   the valid findings and report the ones that don't exist. Apply only what
   the user selected; leave the rest untouched for a later pass.
5. **Re-verify** against the validation checklist at the bottom, fix any
   remaining violations, then present the result.

## AI-slop detector

Flag each phrase below and replace it with plain, direct language. Many are
omittable outright.

- **Filler and marketing adverbs** — cut or rewrite:
  - "simply", "just", "easily", "effortlessly", "seamless(ly)",
    "obviously", "please" → omit or rephrase.
  - "we", "let's" → rephrase to second person ("you") or the active subject.
  - "might want to" → replace with a direct imperative.
- **Empty openers** — cut; the sentence usually reads better without them:
  - "In today's fast-paced world…", "It is important to note…",
    "It is worth mentioning that…", "In conclusion…", "As we all know…".
- **Overused jargon and leverage verbs** — plain-language replacement:
  - "utilize" → "use"; "leverage" → "use";
  - "streamline" → "simplify" or restate concretely;
  - "delve" → "examine" / "look into";
  - "harness", "unleash", "empower", "revolutionize", "unlock" → concrete verb;
  - "robust", "cutting-edge", "best-in-class", "state-of-the-art" → omit or
    state the specific property (reliable, up to date, etc.).
- **Future tense for current behavior** — change to present tense:
  - "the tool will create" → "the tool creates"; "this app will let you" →
    "this app lets you".
- **Wordiness and tone** — fix throughout:
  - No exclamation marks, no rhetorical questions, no emojis.
  - Sentences ≤ 25 words; split nested clauses.
  - Prefer common words: "use" not "utilize", "start" not "commence".
  - No marketing superlatives ("best", "unparalleled", "game-changing").

## Em-dash rule

Default = `true` (remove em-dashes). An em-dash (`—`) is a common AI-slop
tick; strip it unless the user explicitly opts out.

- Replace an em-dash with a comma, a parenthetical, or by splitting and
  restructuring the sentence — whichever reads most clearly.
- Treat more than one em-dash per paragraph as overuse even if the user
  opts to keep them.
- Preserve an em-dash only when it is technically necessary (rare) and the
  user asked to keep em-dash usage.

## Gotchas

- **Never change meaning.** Remove slop, but keep intent, facts, and
  technical terms. Ask if an ambiguous edit could change what the author
  meant.
- **Don't rewrite what isn't slop.** This skill edits AI-slop only; it does
  not impose a new structure or voice on competent existing prose.
- **Don't strip legitimate dashes.** Em-dashes in favor of a comma are an
  edit; a hyphen in a compound word (`state-of-the-art`) is not an em-dash.
- **Don't invent replacements.** Prefer omission or a known substitution to
  guessing at a synonym the author didn't intend.
- **Don't wrap the output in a code fence** when editing a `.md` file.

## Validation checklist

Before delivering, verify:

- [ ] No filler, hedging, or marketing adverbs remain ("simply", "just",
      "easily", "seamless(ly)", "effortlessly", "obviously", "please",
      "we", "let's", "might want to")
- [ ] No empty openers remain ("In today's fast-paced world…", "It is
      important to note…", "In conclusion…")
- [ ] No jargon or leverage verbs remain ("leverage", "utilize",
      "streamline", "delve", "harness", "robust", "cutting-edge",
      "best-in-class")
- [ ] No future tense for current behavior ("will create" → "creates")
- [ ] No em-dashes remain (unless the user opted to keep them)
- [ ] No exclamation marks, rhetorical questions, or emojis
- [ ] Every sentence ≤ 25 words
- [ ] Meaning, facts, and technical terms unchanged