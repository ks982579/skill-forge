# Verification

## Contents

- [The governing idea](#the-governing-idea)
- [Four depth levels](#four-depth-levels)
- [Escalation triggers](#escalation-triggers)
- [Stopping rules](#stopping-rules)
- [What source errors look like](#what-source-errors-look-like)
- [Verifying your own corrections](#verifying-your-own-corrections)
- [Severity and callouts](#severity-and-callouts)
- [The reliability scorecard](#the-reliability-scorecard)
- [Fairness to the author](#fairness-to-the-author)

---

## The governing idea

**Verification is risk-weighted spot-checking, not a foundationalist chain to bedrock.** You are not grounding every claim in certainty; you are finding errors at acceptable cost. This dissolves the infinite-regress worry: the question is never "how deep does the citation tree go" but "where is an error likely enough to justify a look."

Two activities get confused and should not be. **Recursing to verify** is bounded by error risk. **Recursing to understand** — going a level down because you do not know what a term means — is bounded by your learning goal. Conflating them is how a verification pass turns into an unbounded research project.

---

## Four depth levels

| Level | Check | Catches | Cost |
|---|---|---|---|
| **L0** | Does the citation exist as described — author, year, venue, title? | Transcription and date errors | Seconds |
| **L1** | Does the **abstract** support the claim as characterised? | Misrepresentation of the source | A minute |
| **L2** | Do the paper's actual results and stated conditions support it? | Scope errors, wrong numbers, dropped qualifiers | Longer |
| **L3** | Are the cited paper's *own* sources sound? | Propagated error | Expensive |

**Default to L1, escalate on trigger, never traverse the whole tree.**

The reason L1 is the right default is empirical: **most citation errors are visible from the abstract or even the title.** A paper cited as demonstrating something when its title is a question; a paper cited in support of an optimistic claim when its abstract states the requirements are out of reach; a threshold quoted for one protocol when the source paper explicitly says another protocol cannot reach it. All L1 catches. Date and author errors are L0 — cheaper still.

L3 earns its place in the table for one reason: **propagated error is invisible from above.** Mangled author names, mis-transcribed constants, and figures detached from their original conditions replicate through reference databases. A source can inherit an error rather than commit one.

---

## Escalation triggers

Go one level deeper when any of these hold:

- **Load-bearing** — something else in the notes depends on this claim.
- **Surprising, superlative, or too clean** — a "first", a "proven", an exact-sounding figure, a suspiciously round number.
- **The citation is doing argumentative work** — "X proved that…" rather than "see also X". Pointers can stay unchecked; load-bearers cannot.
- **The current level came back inconclusive** rather than confirming. Ambiguity is a reason to look further; confirmation is a reason to stop.
- **Two or more real errors already found in this section.** Error rates cluster. A source that got two things wrong in five pages is not a source whose remaining claims deserve the benefit of the doubt — escalate the whole section.

Arithmetic gets special handling: **if a worked example contains numbers, recompute it.** This is cheap, deterministic, and catches errors that no amount of source-checking would. Run the actual computation rather than checking it by eye — the failure mode of eyeballing is that plausible-looking wrong answers pass. Where a worked example is broken, give the corrected version in full, because a student who cannot see the right answer cannot use the correction.

---

## Stopping rules

**The primary rule:** stop when you can state the claim's **scope conditions** in your own words. If you can say when it fails, you have reached bedrock for practical purposes. If you cannot, you have not checked deeply enough regardless of how many levels you descended.

Secondary rules:

- If a check at level *N* confirms cleanly, do not go to *N+1*. Confirmation is the stop signal.
- If a claim is decorative — no other claim depends on it — L0 is sufficient.
- If the marginal chance of finding an error no longer justifies the cost, stop and **say so in the provenance note**. Unchecked is fine; silently unchecked is not.

---

## What source errors look like

Recognising the shapes speeds up detection. In rough order of frequency:

| Shape | Example | Level |
|---|---|---|
| **Transcription** | Year off by a decade; mangled author name; digit transposition in a constant | L0 |
| **Citation misuse** | Paper cited in support of a claim it contradicts, or for a result it does not contain | L1 |
| **Mischaracterised source** | A feasibility question reported as a demonstration; a lower bound reported as a proof | L1 |
| **Dropped qualifier** | "At worst" removed, turning an upper bound into an equality; conditions omitted | L2 |
| **Wrong complexity class or scaling** | Missing a symbol that changes the meaning; quoting input size as if it were runtime | L1–L2 |
| **Invalid inference** | "Therefore" bridging a conjecture to a conclusion | No lookup needed — read the logic |
| **Internal contradiction** | Two incompatible figures in the same passage; a definition contradicting the formula beneath it | No lookup needed — read carefully |
| **Category error** | Conflating a classical algorithm with a quantum one; treating a key-distribution protocol as an encryption scheme | No lookup needed |
| **Arithmetic** | Worked example that does not compute | Recompute |
| **Currency** | True when written, superseded since | Search for later work |

The last five need no external lookup at all. **Read the source adversarially before reaching for a search engine** — internal contradictions, invalid inferences, and broken arithmetic are free to find and are often the most damaging errors present.

---

## Verifying your own corrections

**Run this pass whenever `verify: full`. It is not optional and it is not ceremonial.**

A confident wrong correction is worse than the original error, because the reader trusts it and reproduces it. In practice, a first pass of corrections will contain real mistakes — transposed exponents, over-strong claims, misattributed results, and inverted definitions are all common. Assume yours does.

The pass: take each correction, try to **refute** it. Recompute the arithmetic independently. Pull the primary source and check the quote is verbatim. Ask whether the correction over-corrects — whether the source's phrasing was loose rather than false, which is a different and gentler verdict.

Failure modes specific to corrections:

- **Over-correction.** Marking as *wrong* something that was merely imprecise. If a definition is logically equivalent to the standard one but badly phrased, say that, not "wrong."
- **Right conclusion, wrong reason.** The verdict holds but the supporting argument is unsound. This survives casual review because the conclusion looks correct.
- **Inverted technical relations.** Complexity-theoretic hardness is a lower bound, not an upper bound. Direction errors in definitions are easy to make and hard to spot.
- **Citation grafting.** Attaching one paper's authors or result to another paper's title or identifier.
- **Quote drift.** Words changed inside quotation marks; qualifiers silently dropped from a quoted passage.

When the pass finds errors, **fix them and say so in the provenance note.** Reporting that the corrections were themselves corrected is not an admission of weakness — it tells the reader how much weight the remaining corrections can bear.

---

## Severity and callouts

Map verdicts onto Obsidian callouts consistently, so severity is readable at a glance:

| Verdict | Callout | Use for |
|---|---|---|
| Holds as stated | `> [!success] Verified` | Confirmed claims, correct citations, sound worked examples |
| Imprecise, misleading, or citation bent | `> [!warning]` | Directionally right but wrongly stated; dropped qualifiers; overclaims |
| Factually or logically wrong | `> [!danger]` | Flat errors, invalid inferences, broken arithmetic, category errors |
| True as far as it goes, but incomplete | `> [!info] Missing context` | Omissions, post-publication developments, unstated caveats |

Place the callout **immediately after the claim it concerns**, not in a section at the end. The reader should never encounter an uncorrected claim without the correction adjacent to it.

Give each callout a title that states the verdict — `> [!danger] Wrong — this inverts the definition` — so the notes are skimmable.

---

## The reliability scorecard

When verification ran, close with a triage table covering **every checkable claim**, including the ones that held. Readers need to know what to trust as much as what to doubt.

```markdown
| # | The source's claim | Verdict | Severity |
|---|---|---|---|
| 1 | <claim, compressed> | **Wrong** — <one-line correction> | 🔴 Flat error |
| 2 | <claim> | **Misleading** — <why> | 🟠 |
| 3 | <claim> | **Imprecise** — <why> | 🟡 |
| 4 | <claim> | **Correct** | 🟢 |
```

Order by severity, worst first. Then add one line naming **the pattern** — sources fail in characteristic ways, and telling the reader "definitions are reliable here, claims of advantage are not" is more useful than any individual row.

---

## Fairness to the author

Distinguish two things that look identical in a scorecard and are not:

- **Errors** — wrong when written, checkable at the time.
- **Currency failures** — true when written, superseded since.

A source that describes a result as standing, before the result was overturned, made no error. Say so. Mixing the two categories overstates the case against the source and makes the genuine errors easier to dismiss.

Also give credit explicitly. When a worked example is internally consistent, when a hedge is correctly placed, when the source flags its own uncertainty — note it. Notes that only ever criticise are not calibrated, and a reader cannot tell whether the critic is finding real problems or manufacturing them.
