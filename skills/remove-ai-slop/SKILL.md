---
name: remove-ai-slop
description: >-
  Review and clean AI-slop from writing: filler and marketing adverbs,
  empty openers, overused jargon, hedging, false agency, structural tells,
  future tense for current behavior, and em-dash overuse. Use when asked to
  remove AI-sounding phrasing, tighten prose, de-AI text, edit out
  "simply/just/easily", flag or strip em-dashes, or de-jargon a draft — even
  when the input is just prose or a doc with a request to "clean this up".
  Do NOT use for commit messages (use the commit skill) or for rewriting
  meaning, restructuring documents, or line editing that is not about
  AI-slop.
metadata:
  author: Christian Galsterer
  version: "1.0.0"
---

# Remove AI Slop

Identify and remove AI-slop: the filler, hedging, marketing, and jargon
phrases that AI text generators lean on, the structural tells they use to
manufacture insight, plus em-dash overuse. Output is cleaner prose with the
meaning, facts, and technical terms intact.

This skill is a reviewer/cleaner, not a writer. It edits what is there; it
does not invent content or restructure the document.

It covers two kinds of slop:

- **Word-level** (words and phrases) — see
  [references/phrases.md](references/phrases.md).
- **Structural** (constructions and rhythm) — see
  [references/structures.md](references/structures.md).

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

Flag each pattern below and replace it with plain, direct language. Many are
omittable outright. Full detail is in the reference files.

### Word-level

- **Adverbs** — cut all of them (the -ly blanket rule). This includes
  "simply", "just", "easily", "effortlessly", "seamless(ly)", "obviously",
  "actually", "literally", "truly", "really", and all -ly softeners,
  intensifiers, and hedges. See [references/phrases.md](references/phrases.md).
- **Filler and throat-clearing openers** — cut: "Here's the thing/why/this/
  that", "It turns out", "The uncomfortable truth is", "Let me be clear",
  "In today's fast-paced world", "It is important to note", "In conclusion".
- **Emphasis crutches and generic filler** — cut: "Full stop.", "Let that
  sink in.", "Make no mistake", "At its core", "At the end of the day",
  "When it comes to", "In a world where".
- **Jargon and leverage verbs** — plain-language replacement: "utilize" →
  "use"; "leverage" → "use"; "streamline" → "simplify"; "delve" → "examine";
  "harness/unleash/empower/revolutionize/unlock" → concrete verb;
  "navigate/unpack/lean into/deep dive/circle back/moving forward/
  game-changer/double down/landscape" → plain synonym. See the jargon tables in
  [references/phrases.md](references/phrases.md).
- **Meta-commentary** — cut self-referential asides ("The rest of this essay
  explains…", "In this section, we'll…").
- **Vague declaratives** — cut or name the specific thing ("The implications
  are significant", "The stakes are high").
- **Telling instead of showing** — name the concrete thing ("This is genuinely
  hard", "this is what X actually looks like").
- **Future tense for current behavior** — change to present tense:
  "the tool will create" → "the tool creates"; "this app will let you" →
  "this app lets you".

### Structural

- **Binary contrasts** — cut "not X, it's Y", "isn't X, it's Y", "X isn't the
  problem, Y is". State Y directly.
- **Negative listing** — cut "not a X... not a Y... a Z". State Z.
- **Dramatic fragmentation** — cut "X. And Y. And Z.", "[Noun]. That's it."
  Use complete sentences.
- **Rhetorical setups** — cut "What if [reframe]?", "Here's what I mean:",
  "Think about it:".
- **False agency** — inanimate things doing human verbs ("the decision
  emerges", "the market rewards", "the data tells us"). Name the human.
- **Passive voice** — "X was created", "It is believed that". Find and name
  the actor.
- **Starters to avoid** — Wh- openers, paragraphs starting "So", sentences
  starting "Look,".
- **Rhythm** — two items beat three; vary paragraph endings; no stacked
  fragments; no metronomic cadence.
- **Lazy extremes** — "every/always/never/everyone/nobody" as false authority;
  use specifics.

See [references/structures.md](references/structures.md) for the pattern tables.

## Wordiness and tone

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
- **Don't write what isn't slop.** This skill edits AI-slop only; it does
  not impose a new structure or voice on competent existing prose.
- **Don't invent an actor.** When fixing false agency or passive voice, name
  a real actor or use "you". Never fabricate who did something.
- **Don't strip legitimate dashes.** Em-dashes in favor of a comma are an
  edit; a hyphen in a compound word (`state-of-the-art`) is not an em-dash.
- **Don't invent replacements.** Prefer omission or a known substitution to
  guessing at a synonym the author didn't intend.
- **Don't wrap the output in a code fence** when editing a `.md` file.

## Validation checklist

Before delivering, verify:

- [ ] No filler, hedging, or marketing adverbs remain ("simply", "just",
      "easily", "seamless(ly)", "actually", "literally", "truly", "really",
      "-ly" softeners)
- [ ] No empty openers remain ("Here's the thing", "In today's fast-paced
      world", "It is important to note", "In conclusion")
- [ ] No jargon or leverage verbs remain ("leverage", "utilize",
      "streamline", "delve", "navigate", "lean into", "deep dive",
      "circle back", "robust", "cutting-edge", "best-in-class")
- [ ] No meta-commentary remains ("The rest of this essay explains…")
- [ ] No vague declaratives remain ("The implications are significant") —
      the specific thing is named
- [ ] No false agency or passive voice remains — a real actor is named
- [ ] No binary contrasts, negative listing, or dramatic fragmentation remain
- [ ] No rhetorical setups or rhetorical questions remain
- [ ] No future tense for current behavior ("will create" → "creates")
- [ ] No em-dashes remain (unless the user opted to keep them)
- [ ] No exclamation marks, rhetorical questions, or emojis
- [ ] Every sentence ≤ 25 words
- [ ] Rhythm is varied — no metronomic cadence, no stacked fragments
- [ ] Meaning, facts, and technical terms unchanged