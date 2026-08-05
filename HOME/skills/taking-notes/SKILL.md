---
name: taking-notes
description: "Take structured, optionally fact-checked notes on textbook chapters, academic papers, and other readings. Produces Obsidian-flavoured Markdown in which every statement declares what it is — claim, definition, evidence, warrant, caveat, example — organised into self-contained claim units, with inline verification callouts and a reference list. Use this whenever the user is reading something and wants notes, a breakdown, study material, or help working out what matters in it — textbook sections, journal articles, book chapters, lecture readings, standards documents, technical specs, or long reports. Trigger even when the user never says the word notes; asking to understand a chapter, asking what is important in a passage, asking whether a source is actually right, or simply pasting a long extract and asking about it all call for this skill."
---

# Reading Notes

## Why this exists

Ordinary notes are prose, and prose hides structure. When you reread "quantum machine learning offers exponential speedups," you cannot tell whether that was proven, conjectured, measured, or asserted by an author in a hurry. The information needed to judge it was present in the source and got flattened out in the copying.

These notes keep that information. **Every sentence declares its own type**, so a claim looks different from a definition, and an unsupported claim looks different from a supported one. This does two things: it makes gaps visible without rereading, and it makes fluff hard to write, because a sentence that has no type and discharges no obligation has nowhere to sit.

The framework is Toulmin's (*The Uses of Argument*, 1958) — claim, grounds, warrant, qualifier, rebuttal — extended with the statement types technical writing actually uses.

## Two flags

Establish these before writing. Infer from context and state the assumption rather than blocking on a question, unless the choice is genuinely unclear.

**`verify:`** — how hard to check the source's factual claims.

| Value | Behaviour | Use when |
|---|---|---|
| `off` | No fact-checking. Structure and typing only. | Trusted source, or the user wants speed, or the material is definitional/mathematical with nothing external to check |
| `light` | L0–L1 checks on load-bearing claims only (citation exists; abstract supports the characterisation) | Default for unfamiliar sources |
| `full` | L0–L2 on everything checkable, plus an adversarial pass over your own corrections | The user has said the source is unreliable, the notes feed an exam or a publication, or early checks found errors |

Escalate mid-task if `light` turns up errors — two or more real errors in a section is strong evidence there are more.

**`cite:`** — `ieee` (default) or `apa7`. Governs the reference list.

## The pipeline

**1. Read the whole source before writing anything.** Structure is only visible in retrospect; a claim on page 2 is often supported on page 9, and you cannot mark a slot empty until you know it was never filled.

**2. Infer the genre.** This determines what counts as support and where scope lives. Load `references/genre-flows.md` and match against the cues there. State the inference in the notes — the user may correct it.

**3. Extract and type every statement.** Load `references/statement-types.md`. For each sentence in the source, ask: what type is this, and what does that type owe? Sentences that are neither a type nor a discharge of another statement's obligation are fluff — drop them, or compress a run of them into one navigational line.

**4. Find the empty slots.** For each claim, check its obligations. A claim owes support, scope, and attribution; a theorem owes a proof and its hypotheses; an analogy owes the point where it breaks. **Missing obligations are the most valuable thing in the notes** — they are what the source did not tell you, and they are invisible in prose.

**5. Verify, if the flag is on.** Load `references/verification.md` for the depth protocol and escalation triggers.

**6. Write.** Build one claim unit per assertion, using the template below — *not* a document-wide outline grouped by statement type. Load `references/formatting.md` for callouts, LaTeX escaping, and citation templates.

**7. Check your own corrections adversarially, if `verify: full`.** A confident wrong correction is worse than the original error, because the reader will reproduce it. In practice this pass catches errors at a meaningful rate — do not skip it and do not assume your first-pass corrections are sound.

**8. Deliver** the file, with a reference list and, when verification ran, a provenance note saying what was checked and how.

## The claim unit — the core structure

> [!important] Read this twice. It is the single easiest thing to get wrong.
> **The spine is a template for one claim, not an outline for the document.**
>
> The tempting misreading is to file the material by type — all the definitions in one section, all the claims in another, all the evidence in a third. That produces a tidy-looking document in which **every argument is scattered across it**, and you cannot see which evidence supports which claim without reassembling it in your head. It defeats the entire purpose.
>
> Instead: **each assertion gets its own section, and its support, warrant, bounds, attribution and examples live inside that section.** A reader should be able to stop at any one unit and have the complete case for that one thing.

Each unit runs the same sequence. Slots the source never filled are **stated as empty** — that is the highest-value content in the notes, because an unfilled slot is a hole in the argument that prose would have hidden.

| Slot | Contains | Reader question answered |
|---|---|---|
| Assert | claim, hypothesis, conjecture, finding, theory | What is being asserted? |
| Support | evidence, proof, attribution | What backs it? |
| **Warrant** | the link from support to claim | **Why does that backing support this claim?** |
| Bound | qualifier, caveat, failure condition | When does it fail? |
| Illustrate | example, analogy, contrast | What does it look like? |

**Warrant is the slot most often empty**, and its absence is where bad reasoning hides. "Paper X computed a lower bound" (support) → "therefore supremacy is proven" (claim) fails at the warrant, not at the evidence.

### The unit template

```markdown
### 2.3 <Short name for the claim>

**Claim.** <the assertion, in one sentence>

**Attribution.** <who established it, where — or *Not given.*>

**Evidence.** <what the source offers in support>

**Warrant.** <why that evidence bears on this claim>

**Scope.** <the conditions under which it holds>

**Example.** <an instance>
```

Mark empty slots explicitly and say what the gap costs:

```markdown
**Warrant.** *Not given.* The section reports the measurement and asserts the
conclusion without connecting them — the effect is compatible with at least two
rival explanations the source does not address.
```

Not every unit needs every slot. A definition-only unit has no Support or Warrant, and forcing them produces filler. But **when a claim lacks support, warrant, or scope, say so** rather than silently omitting the heading.

### Document shape

Orientation and shared vocabulary happen once, at the top. Everything after is claim units.

1. **Orient** — motivation and at most one line of roadmap. Once, at the top.
2. **Establish** — definitions and notation used *throughout*. Once, at the top. Definitions local to a single claim belong inside that claim's unit, not here.
3. **Claim units** — the body. One section per assertion, each internally complete, in whatever order makes the argument clearest.

**The order in the source is rarely the right order in the notes.** Textbooks bury the warrant, omit the bounds, and open with three paragraphs of orientation. Pulling each claim's scattered support back into one unit *is* the work — a note that preserves the source's ordering has mostly just retyped it.

## Genre inference, in brief

Full cues and per-genre failure modes are in `references/genre-flows.md`. The short version:

| Genre | Support is… | Scope lives in… | Characteristic failure |
|---|---|---|---|
| Mathematical / formal | proof | the hypotheses of the theorem | scope stated but unread |
| Empirical / experimental | data + method | population, conditions, effect size | overreach beyond sample |
| **Survey / textbook** | **citation** — secondhand | usually **omitted** | citation misreports the source |
| Interpretive / theoretical | cases + rival readings | boundary conditions | rival readings suppressed |
| Engineering / systems | benchmarks | operating envelope | benchmark not representative |

Mixed genres are normal. A textbook chapter on a mathematical topic runs the survey spine around mathematical islands — type each part by what it locally is.

## Output structure

```markdown
---
source: <title>
section: <identifier>
genre: <inferred genre>
tags: [...]
verified: <date, if verification ran>
---

# <Section identifier> — <Title>

> [!abstract] What this source is doing
> The argumentative shape, in three or four sentences. What it is trying to
> establish, and where the load actually sits.

> [!tip] Reading conventions
> One line on the labelling convention and the callout scheme.

## Orientation
Motivation, and at most one line of roadmap.

## Shared vocabulary
Definitions and notation used throughout. Local definitions go in their unit.

## 1. <First claim cluster>
### 1.1 <Claim name>
Claim / Attribution / Evidence / Warrant / Scope / Example — the unit template,
with verification callouts adjacent to whatever they concern.

### 1.2 <Claim name>
…

## Reliability scorecard          (only when verification ran)
Every checkable claim, with a verdict and severity marker, worst first.

## The N things worth carrying forward
The compressed takeaway — what survives, what fails, what to remember.

## Open questions
What the source leaves unresolved, and what to ask about it.

## References
Numbered list in the requested style.

## Provenance                     (only when verification ran)
What was checked, at what depth, and what remains unchecked.
```

## Labelling statements

Label each statement with its type using a **bold prefix**, then state the content in prose:

> **Claim.** The p-value threshold of 0.05 marks statistical significance.
>
> **Attribution.** Introduced by Fisher, *Statistical Methods for Research Workers* (1925), ch. III.
>
> **Evidence.** *Not given.* The section asserts the convention without argument.

This is more scannable than folding the type into the sentence, and it makes an unfilled slot visible at a glance. Where prose reads better — inside a callout, or mid-paragraph — fold the type in instead: *"It is claimed that…"*, *"The evidence offered is…"*, *"It is conjectured — believed but unproven — that…"*. Both forms are fine; **what matters is that every statement carries its type**, not which of the two shapes it takes.

Vary the wording. Mechanical repetition of one formula is its own kind of fluff.

The full table of types, with their labels and obligations, is in `references/statement-types.md`.

## Callout discipline

Callouts are for **verdicts and asides**, not for body content. When most paragraphs sit inside one, they stop signalling anything and the note becomes hard to read.

**Use a callout for:** the opening abstract, reading conventions, a verification verdict, a missing-context block, an open question, a worked example, or an extended quotation.

**Do not use a callout for:** ordinary Claim / Evidence / Warrant / Scope content. That is plain prose with a bold label. A claim only moves inside a callout when the callout is *about* it — a `[!danger]` correcting it, for instance.

A rough gauge: if more than about a quarter of the note's paragraphs are inside callouts, they have stopped carrying signal. Prefer fewer, better-titled ones.

## Quality bar

A finished note should let a reader do five things without returning to the source:

1. **Tell what kind of thing each statement is** — no inference required.
2. **Read one claim unit in isolation** and have the complete case for that claim: what is asserted, what backs it, why that backing counts, when it fails.
3. **See which claims are unsupported**, because the missing slot is marked rather than silently absent.
4. **State when each claim fails** — scope is present or explicitly flagged as absent.
5. **Trace any factual assertion to a source** via the reference list.

Two failure modes to check for before delivering:

- **The filing cabinet.** If the document is organised into a definitions section, a claims section and an evidence section, the claim units were never built. Each argument is now scattered and the reader has to reassemble it.
- **The wall of boxes.** If nearly every paragraph is inside a callout, the callouts have stopped distinguishing anything. Body content is prose; callouts are verdicts.

If the notes read like a shorter version of the source, the restructuring step was skipped. The value is in the re-assembly and the marked gaps, not the compression.

## Reference files

| File | Load when |
|---|---|
| `references/statement-types.md` | Always — during extraction and typing (step 3) |
| `references/genre-flows.md` | At step 2, to infer genre and pick the spine emphasis |
| `references/verification.md` | Whenever `verify` is not `off` |
| `references/formatting.md` | Before writing — callouts, LaTeX escaping, citations |
