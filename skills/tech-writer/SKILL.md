---
name: tech-writer
description: >-
  Write and edit technical documentation in a professional tone, following a
  fixed document structure (title, overview, prerequisites, steps,
  troubleshooting, next steps) and Microsoft Writing Style Guide markdown
  conventions. Use when writing, drafting, reviewing, or reformatting
  documentation, READMEs, guides, how-tos, tutorials, or API docs — even
  when the input is just rough notes with a request to "document this".
  Do NOT use for commit messages (use the commit skill), code comments, or
  non-markdown formats like Word or Confluence pages.
metadata:
  author: Christian Galsterer
  version: "1.0.0"
---

# Tech Writer

Write technical documentation in a professional tone with a fixed document
structure and Microsoft Writing Style Guide markdown conventions. Output is
always a single markdown document.

## Workflow

1. **Identify the audience and goal.** If the user hasn't said who the doc
   is for or what the reader should be able to do afterwards, ask — the
   overview and prerequisites depend on it. Do not ask about anything else;
   use the defaults below.
2. **Gather the facts.** Read the code, config, or notes the doc covers.
   Never invent commands, flags, file paths, or behavior you haven't
   verified in the source. Collect at least one concrete example for every
   feature, parameter, or config option you will document.
3. **Draft using the fixed structure** below. Skip a section only when it
   is genuinely empty (e.g. no prerequisites) — never invent content to
   fill one. Each task section and every non-obvious parameter must include
   at least one verified example.
4. **Apply the conventions.** Read `references/markdown-conventions.md`
   before writing and again as a checklist after drafting. It defines
   headings, lists, code blocks, links, tables, and tone rules.
5. **Validate the draft** against the checklist at the bottom of this file,
   fix any violations, then present the result.

## Fixed document structure

Every document follows this order:

```markdown
# <Title: concise, sentence case, states the task or topic>

<Overview: 1–3 short paragraphs. What is this, who is it for, what will
the reader achieve. No heading — this text directly follows the title.>

## Prerequisites

<Bullet list of required tools, access, knowledge, or prior steps. Omit
the whole section if nothing is required.>

## <Task sections — one H2 per major step or topic>

<Numbered steps for procedures; prose for concepts. Each step: one action,
imperative mood, starts with a verb.>

1. First action.
1. Second action. (Use `1.` for every item — let the renderer number them.)

### <Optional H3 subsections within a task>

## Troubleshooting

<Problem → cause → solution, one H3 per issue or a table. Omit if nothing
is known to go wrong.>

## Next steps

<Bullet list of links to related docs or follow-up tasks.>
```

Rules:

- Exactly one H1 (the title). All sections are H2 or below — never skip a
  heading level.
- Section titles use sentence case ("Next steps", not "Next Steps").
- Task section H2s are named after the goal, not the tool: "Configure the
  plugin", not "Plugin configuration".
- Task-based organization: structure the doc by what the reader wants to
  accomplish, not by the product's internal feature layout. Bad: "Settings
  panel" — good: "Change the default region".
- Troubleshooting entries are keyed by the observable symptom (the exact
  error message or behavior the user sees), followed by cause, then fix.
  Users search by symptom, not by root cause.

## Tone

Professional means: second person ("you"), present tense, imperative for
instructions, no humor, no exclamation marks, no marketing language
("easily", "simply", "just", "seamless"). State what to do; explain *why*
only where a wrong choice has consequences.

## Gotchas

- **Don't pad the overview.** If the topic is covered in one paragraph,
  write one paragraph. Filler sentences ("In today's fast-paced world…")
  are the most common failure mode.
- **Don't document aspirational behavior.** Only document what the code
  does now, verified against the source. If a feature is planned, leave it
  out.
- **Don't use bold as a heading substitute.** If text needs a label, it
  needs a heading level.
- **Don't wrap the output in a code fence** when writing into a `.md` file
  — the file content IS markdown.
- **Code examples must be runnable.** Use realistic placeholder values
  (`my-project`, not `xxx`), tag every fenced block with its language, and
  prefer complete commands over fragments.

## Validation checklist

Before presenting the document, verify:

- [ ] Exactly one H1; no skipped heading levels; sentence-case headings
- [ ] Sections appear in the fixed order; empty sections omitted entirely
- [ ] Every fenced code block has a language tag
- [ ] Numbered steps use `1.` throughout and imperative mood
- [ ] Every task section and non-obvious parameter has a verified example
- [ ] No "simply/just/easily", no exclamation marks, no future tense
      ("will") for current behavior
- [ ] All conventions in `references/markdown-conventions.md` applied
