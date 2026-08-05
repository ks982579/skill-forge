# Statement Types

## Contents

- [The basic partition](#the-basic-partition)
- [The seven families](#the-seven-families)
- [Full type table](#full-type-table)
- [Obligations by type](#obligations-by-type)
- [Distinctions worth getting right](#distinctions-worth-getting-right)
- [Diagnosing fluff](#diagnosing-fluff)

---

## The basic partition

Treat a **sentence** as the outer set. It partitions into:

- **Statement** — carries a type from the table below, and either incurs an obligation or discharges one.
- **Fluff** — does neither.

This gives fluff a test rather than a feeling. "In this unit, we will look at some of the most exciting applications" carries no type and discharges no obligation, so it goes. A sentence naming what is about to be argued may earn its place as orientation, but one line of it, not a paragraph.

The point of typing is not taxonomy for its own sake. It is that **each type owes something different**, so knowing the type tells you what to look for next — and tells you when the source failed to provide it.

---

## The seven families

| Family | What it does | Truth-apt? |
|---|---|---|
| **Asserting** | Puts something forward as true | Yes |
| **Establishing** | Fixes meaning or foundations | No — stipulations, not truths |
| **Supporting** | Backs an assertion | — |
| **Connecting** | Licenses inference between statements | — |
| **Bounding** | Limits where an assertion holds | — |
| **Illustrating** | Shows the assertion in action | — |
| **Orienting** | Positions the reader | — |

The "truth-apt" column matters more than it looks. A definition cannot be *wrong*, only non-standard or unhelpful — so criticising a definition for being false is a category error. Conversely a claim that cannot be false is not a claim; it is either a definition in disguise or fluff.

---

## Full type table

Two ways to attach a type to a statement, both fine:

- **Bold label** — take the name from the Type column: `**Claim.** <content>`, `**Warrant.** <content>`. Preferred in the body of a claim unit, because an unfilled slot is visible at a glance.
- **Folded into the prose** — the third column gives openings. Preferred inside callouts and mid-paragraph, where a bold label would interrupt.

### Asserting

| Type | What it is | Label, or open with |
|---|---|---|
| **Claim** | The genus. Any assertion put forward as true. | "It is claimed that…" / "The section asserts that…" |
| **Finding / result** | An outcome reported from an experiment or computation. | "The reported finding is…" / "They measured…" |
| **Hypothesis** | Proposed *for testing*. Forward-looking, awaiting evidence. | "The hypothesis offered is…" / "It is proposed that…, to be tested by…" |
| **Conjecture** | Believed true, unproven, often with no clear test path. | "It is conjectured — believed but unproven — that…" |
| **Theory** | A *structure* of claims plus the machinery connecting them, with explanatory scope. | "The theory holds that…, and it explains…" |
| **Prediction** | A forward claim that could be checked later. | "It is predicted that…" |
| **Law / principle** | A regularity held to be exceptionless within its scope. | "The stated principle is…" |

### Establishing

| Type | What it is | Label, or open with |
|---|---|---|
| **Definition (stipulative)** | The author fixes a meaning for this text. | "The definition given is…" / "Here X is taken to mean…" |
| **Definition (standard)** | Reports the field's established usage. | "The standard definition is…" |
| **Definition (operational)** | Fixes meaning by how it is measured. | "X is operationalised as…" |
| **Notation / convention** | Symbol or naming choice. Carries no content. | "By convention, X denotes…" |
| **Axiom / postulate** | Taken as foundational by fiat, not argued for. | "It is postulated that…" / "Taken as axiomatic:…" |
| **Assumption** | Granted for the argument. Often unstated — surface it. | "It is assumed that…" / "The unstated assumption is…" |

### Supporting

| Type | What it is | Label, or open with |
|---|---|---|
| **Evidence** | Observation or measurement offered in support. | "The evidence offered is…" |
| **Proof** | Deductive derivation. In formal genres it *replaces* evidence. | "The proof proceeds by…" |
| **Attribution** | Who established it, and where. | "This is attributed to Author (year), who showed…" |
| **Backing** | Support for a *warrant* rather than for a claim. | "The warrant is itself justified by…" |

### Connecting

| Type | What it is | Label, or open with |
|---|---|---|
| **Warrant** | The principle licensing the step from support to claim. | "This supports the claim because…" / "The link is…" |
| **Implication** | What follows if the claim holds. | "It follows that…" |
| **Corollary** | A result that falls out of another with little extra work. | "A corollary is…" |
| **Mechanism** | The causal or procedural story behind a claim. | "The mechanism offered is…" |

### Bounding

| Type | What it is | Label, or open with |
|---|---|---|
| **Qualifier** | Strength or scope attached to the claim. | "This holds only when…" / "In the worst case…" |
| **Caveat / limitation** | An acknowledged weakness. | "The stated limitation is…" |
| **Failure condition** | Where the claim breaks. | "It fails if…" |
| **Rebuttal condition** | Circumstance under which the claim would be withdrawn. | "The claim would not hold if…" |
| **Counterexample** | An instance that refutes. | "A counterexample is…" |

### Illustrating

| Type | What it is | Label, or open with |
|---|---|---|
| **Example** | An instance of the claim in action. | "An example is…" |
| **Analogy / model** | A structural comparison. Not true or false — apt or misleading. | "The analogy offered is… — it holds because…, and breaks at…" |
| **Contrast / distinction** | X is not Y. Often the highest-value sentences in a text. | "This is distinct from…, which…" |
| **Case study** | An extended worked instance. | "The worked case is…" |

### Orienting

| Type | What it is | Label, or open with |
|---|---|---|
| **Motivation** | Why this matters. | "The motivation given is…" |
| **Open question** | Explicitly unresolved. | "This remains unresolved:…" |
| **Roadmap** | Structural signposting. Keep at most one line. | "The section proceeds by…" |

---

## Obligations by type

A universal checklist over-applies — a definition does not need evidence, an example does not need a warrant. Instead, let each type carry its own debts. **When an obligation goes undischarged in the source, mark it.** That mark is the most useful thing in the notes.

| Type | Owes |
|---|---|
| Claim | support + scope + attribution |
| Finding | method + conditions + who reported it |
| Hypothesis | a test that could fail |
| Conjecture | why it is believed, and that it is **explicitly flagged as unproven** |
| Theory | what it explains + what would falsify it |
| Theorem | proof + its hypotheses (the hypotheses *are* the scope) |
| Definition | whether it is stipulative or standard; if it diverges from standard usage, a note saying so |
| Axiom / postulate | acknowledgement that it is assumed, not derived |
| Assumption | to be surfaced even when the source leaves it implicit |
| Evidence | attribution + method |
| Attribution | that the cited work **actually says what it is cited for** |
| Warrant | backing, if the link is not self-evident |
| Analogy | the point where it breaks |
| Example | nothing — an example *is* the discharge of another statement's debt |
| Notation | nothing |

Two obligations deserve special attention because they fail most often:

**Attribution.** In survey and textbook genres, citation replaces argument — so a misreported citation silently destroys the support for a claim while looking perfectly sound. Checking what the cited work actually concluded is usually the single highest-yield verification available.

**Scope.** Claims stated without bounds read as universal. Most are not. When a source states a result without its conditions, the conditions did not cease to exist — they just became invisible, which is worse.

---

## Distinctions worth getting right

**Claim vs. theory.** A theory is not a big claim. It is a *structure* of claims plus the machinery connecting them. Typing something as a theory obliges you to record what it explains and what would falsify it; typing it as a claim does not.

**Hypothesis vs. conjecture.** A hypothesis is proposed *for testing* — it comes with, or implies, a procedure that could refute it. A conjecture is believed true with no clear test path (P ≠ NP). The distinction is load-bearing: an argument that treats a conjecture as established is making an error that is invisible unless the types are marked.

**Conjecture vs. theorem.** The most common failure in technical writing is the word "therefore" bridging a conjecture to a conclusion. Watch for it. If the support is conjectural, the conclusion inherits that status, and the notes should say so.

**Evidence vs. proof.** They are not interchangeable and they do not appear in the same genres. Evidence is defeasible and comes with a method; proof is deductive and comes with hypotheses. A mathematical text offering "evidence" is signalling that the result is not yet proved.

**Definition subtypes.** Stipulative definitions cannot be wrong, but they can silently diverge from standard usage, which misleads readers who know the field. When a source's definition departs from the standard one, that departure is worth a note even though neither is "false."

**Warrant vs. mechanism.** A mechanism explains how the phenomenon works. A warrant explains why the offered support bears on the claim. A source can supply an excellent mechanism and still have no warrant, if it never connects its evidence to its assertion.

**Qualifier vs. hedge.** "In the worst case" is a qualifier — it specifies scope. "Might potentially have significant implications" is a hedge — it specifies nothing and is fluff wearing a qualifier's clothes. Qualifiers narrow; hedges only soften.

---

## Diagnosing fluff

Fluff is a sentence with no type and no discharged obligation. It comes in recognisable varieties:

| Variety | Example shape | Handling |
|---|---|---|
| **Filler transition** | "In this unit, we will look at…" | Drop, or compress a run into one roadmap line |
| **Hype** | "enormous potential", "the fastest-growing area" | Drop. If it makes a checkable claim ("fastest-growing"), promote it to a claim and verify it |
| **Redundancy** | Restating a claim in new words without adding support | Merge into the first statement |
| **Unfalsifiable vagueness** | "may have strong consequences" | Drop, unless a real claim can be recovered from it |
| **Deferred content** | "as we will see" | Drop; go get the content and put it where it belongs |

Two cautions:

**Not all short sentences are fluff, and not all long ones are content.** A one-line contrast ("post-quantum cryptography is classical software; QKD is quantum hardware") can be the most valuable sentence in a chapter.

**Hype sometimes conceals a checkable claim.** "The fastest-growing research area in the field" looks like decoration but asserts something bibliometric. Promote it to a claim, note that no metric or citation was given, and — if verification is on — check it. Superlatives that survive checking are worth keeping; ones that do not are worth flagging, because they tell you something about how carefully the rest of the source was written.
