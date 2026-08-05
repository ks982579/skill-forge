# Genre Flows

## Contents

- [Why genre matters](#why-genre-matters)
- [Inferring the genre](#inferring-the-genre)
- [The five spines](#the-five-spines)
- [Mixed and nested genres](#mixed-and-nested-genres)

---

## Why genre matters

The statement types are universal. The **spine** — which slot is heavy, and what is allowed to fill it — is not.

Two questions change entirely with genre:

1. **What counts as support?** Proof, data, citation, case, or benchmark. These are not interchangeable, and a genre that substitutes one for another is telling you something about its reliability.
2. **Where does scope live?** In the hypotheses of a theorem, the sampled population, the assumed conditions, or the operating envelope.

Getting the genre wrong means looking for support in the wrong place and missing scope entirely.

---

## Inferring the genre

Read the opening, a middle section, and the closing. Match on these cues:

| Cue | Suggests |
|---|---|
| Numbered theorems, lemmas, QED, "let X be…" | Mathematical / formal |
| Methods section, sample size, p-values, error bars, "we measured" | Empirical / experimental |
| Dense citation, "researchers have shown", broad topical coverage, few original results | **Survey / textbook** |
| Competing interpretations, "some argue", extended cases, no formal apparatus | Interpretive / theoretical |
| Requirements, benchmarks, latency/throughput tables, tradeoff discussion | Engineering / systems |

**State the inference in the notes**, in the `genre:` frontmatter field and in the opening abstract callout. The user can correct it, and the correction changes what you look for.

Two useful tells:

- **Citation density with low originality** is the survey signature. If nearly every claim points elsewhere, the text is a map, not a territory — and its reliability is the reliability of its map-making.
- **Absence of a methods section in an empirical-sounding text** means results are being reported secondhand. Treat it as survey, not empirical, regardless of how it presents itself.

---

## The five spines

> [!important] These describe the shape of a *claim unit*, not the outline of the document
> Each spine below lists the slots a single assertion needs filling in that genre, and what is allowed to fill them. Apply the spine once per claim, so each unit is internally complete.
>
> Do **not** turn a spine into section headings — a document with one "Definitions" section, one "Evidence" section and one "Proofs" section scatters every argument across the file. Definitions and notation shared across the whole reading go once at the top under **Shared vocabulary**; everything else belongs inside the unit of the claim it serves.

### Mathematical / formal

**Spine:** Definition → Axiom/postulate → Lemma → Theorem → Proof → Corollary → Example → Counterexample

- **Support is proof.** Evidence plays no role. A "for example, simulations suggest" in a formal text marks an unproved gap — note it.
- **Scope lives in the hypotheses of the theorem.** These are frequently stated once and then dropped from all subsequent discussion. Carry them forward explicitly in the notes; a theorem quoted without its hypotheses is a different and usually false statement.
- **Notation is load-bearing.** Record it in the Establish slot even when it feels trivial, because a later step will silently depend on it.

**Characteristic failure:** scope stated but unread. The conditions are right there in the theorem statement and nobody carries them into the application.

**Verification focus:** re-derive small steps; check that the theorem as applied still satisfies its hypotheses.

### Empirical / experimental

**Spine:** Motivation → Hypothesis → Method → Data → Interpretation → Limitation → Implication

- **Support is data plus method.** The method *is* the warrant — it is what licenses moving from the numbers to the conclusion. If the method is not described, the warrant is missing regardless of how good the data look.
- **Scope lives in** the sampled population, the conditions of measurement, and the effect size.
- Interpretation and data are different types and often get merged in the writing. Separate them in the notes: what was observed, then what the authors think it means.

**Characteristic failure:** overreach beyond the sample — a result on 40 undergraduates or 12 qubits stated as a general truth.

**Verification focus:** does the reported effect support the stated conclusion at the stated strength? Are the limitations acknowledged the real ones?

### Survey / textbook

**Spine:** Motivation → Definition → Claim → Attribution → Evidence *(secondhand)* → Example → Caveat

This is the genre most course material belongs to, and it has a specific structural weakness worth naming:

- **Support is citation** — the text asserts that someone else established the claim. You are trusting the *summary*, not the result.
- **The warrant and the bounds are routinely compressed out.** A survey reports that X was shown; it rarely reports why the evidence bore on it, or under what conditions. Both slots will often come back empty.
- **Scope is usually omitted entirely.** Expect to mark this.

**Characteristic failure:** the citation misreports the source — wrong year, wrong author, or a paper cited for the opposite of its conclusion. This is not rare and it is not a sign of a bad author; compression is lossy and errors propagate through reference databases.

**Verification focus:** checking what cited works actually say is by far the highest-yield activity in this genre. See `verification.md` — most such errors are visible from the abstract.

### Interpretive / theoretical

*(Humanities, psychology, social theory, qualitative research, policy analysis.)*

**Spine:** Phenomenon → Existing accounts → Problem with them → Proposed account → Cases → Scope conditions → Rival readings

- **Support is cases plus argument**, and crucially, **the treatment of rival readings is itself a form of support.** An account that never engages an alternative has not earned its conclusion.
- **Scope lives in boundary conditions** — which populations, periods, or contexts the account claims to cover.
- Definitions do more work here than elsewhere and are more often contested. Note when a definition is doing argumentative work.

**Characteristic failure:** rival readings suppressed or strawmanned. When only one interpretation is presented as live, the Bound slot is empty even if the text never admits it.

**Verification focus:** are the strongest opposing accounts represented fairly? Are the cases cherry-picked?

### Engineering / systems

**Spine:** Requirement → Constraint → Design → Tradeoff → Result → Failure mode

- **Support is benchmarks**, and benchmarks are only as good as their representativeness.
- **Scope lives in the operating envelope** — load, scale, hardware, workload shape.
- **Tradeoffs are first-class content.** A design presented without what it gave up is incompletely described. If the source does not state the tradeoff, mark the slot empty.

**Characteristic failure:** the benchmark is not representative of the real workload, or the comparison baseline is weak or outdated.

**Verification focus:** what was the baseline, and was it the *best* available alternative or a convenient one?

---

## Mixed and nested genres

Most real texts mix genres, and that is normal rather than a problem.

- A **textbook chapter on a mathematical topic** runs the survey spine with mathematical islands inside it. Type each part by what it locally is: the theorem statement gets the formal treatment, the surrounding "researchers have applied this to…" gets the survey treatment and the survey scepticism.
- A **paper with a theory section and an experiments section** switches spines partway through. Note the switch; the two halves have different support standards and should be evaluated separately.
- A **survey that includes original results** should have those results held to the empirical standard, not the survey standard. Authors sometimes blur this, presenting their own new work with the same citational lightness as their summary of others'.

When genres mix, **the reliability of the whole is the reliability of its weakest genre**, because a formal result quoted inside a careless survey inherits the survey's transcription risk. Note where each part sits.
