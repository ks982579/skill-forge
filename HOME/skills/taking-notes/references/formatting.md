# Formatting

## Contents

- [Frontmatter](#frontmatter)
- [Callouts](#callouts)
- [LaTeX in Obsidian](#latex-in-obsidian)
- [Tables](#tables)
- [Internal links](#internal-links)
- [Citations](#citations)
- [File naming](#file-naming)

---

## Frontmatter

```yaml
---
source: <book or paper title>
section: "6.2"          # quote anything that could parse as a number
title: <section title>
genre: survey           # the inferred genre
tags:
  - <course or subject>
  - <topic>
status: notes-complete
verified: 2026-08-04    # omit entirely when verify: off
---
```

Quote `section:` values like `"6.2"` or `"1.10"` — YAML will otherwise read them as floats and silently drop trailing zeros.

---

## Callouts

Obsidian renders `> [!type] Title` as a coloured box. The syntax degrades gracefully to a blockquote in other Markdown renderers, so it is safe to use even if the notes travel.

**The prescribed scheme:**

| Callout | Purpose |
|---|---|
| `> [!abstract]` | Opening "what this source is doing" — the argumentative shape |
| `> [!tip]` | Reading conventions; occasional study advice |
| `> [!success]` | A verified claim that holds |
| `> [!warning]` | Imprecise, misleading, or a bent citation |
| `> [!danger]` | Flat factual or logical error |
| `> [!info]` | Missing context — true but incomplete, or post-publication developments |
| `> [!question]` | Open questions, exam and viva angles |
| `> [!example]` | Worked examples, including corrected versions of broken ones |
| `> [!quote]` | Extended verbatim passages where exact wording matters |

Rules that keep them useful:

- **Callouts are for verdicts and asides, not body content.** Claim, Evidence, Warrant and Scope are plain prose with bold labels. A claim moves inside a callout only when the callout is *about* it — a `[!danger]` correcting it, say. **If more than roughly a quarter of the note's paragraphs sit inside callouts, they have stopped signalling anything** and the note reads as an undifferentiated wall of boxes.
- **Title every callout with its verdict**, not its category: `> [!danger] Wrong — this inverts the definition` beats `> [!danger] Error`. The notes become skimmable.
- **Place verification callouts immediately after the claim**, never batched at the end.
- Callouts nest, but past two levels they stop rendering legibly. Keep to one.
- Blank-line rules inside callouts are strict: a list or table inside a callout needs `>` on every line, including the blank separator line.

**Foldable callouts** — append `-` to start collapsed, `+` to start expanded:

```markdown
> [!info]- Missing context — collapsed by default
> Long supplementary material the reader can skip on first pass.
```

Use the collapsed form for long "missing context" blocks so they do not swamp the main line of argument.

---

## LaTeX in Obsidian

Obsidian uses MathJax. Inline math is `$...$`; display math is `$$...$$` on its own lines.

### Escaping

**The percent sign starts a comment in LaTeX and will silently eat the rest of the line.** Always write `\%`:

```latex
$$P(\text{detect}) = 43.75\%$$     ✓
$$P(\text{detect}) = 43.75%$$      ✗ — everything after % vanishes
```

Other characters needing a backslash inside math: `\&`, `\#`, `\_`, `\{`, `\}`. Note that `_` and `^` are *operators* in math mode — escape them only when you want the literal character.

### The pipe problem in tables

A raw `|` inside a table cell breaks the table, and quantum/logic notation is full of them. Use `\vert` (or `\mid` for relations):

```markdown
| Claim | Verdict |
|---|---|
| Initial state is $\vert+\rangle^{\otimes n}$ | Correct |    ✓
| Initial state is $|+\rangle^{\otimes n}$ | Correct |        ✗ — table breaks
```

Outside tables, `|` is fine: `$|\psi\rangle$` renders normally.

### Display math needs its own lines

```markdown
$$
E = mc^2
$$
```

`$$E = mc^2$$` inline in a paragraph renders inconsistently across Obsidian versions.

### Other gotchas

- **`\tag{}` works** in display math and is the right way to carry a source's equation numbers: `$$\tag{6.3} (m^e)^d \equiv m \pmod{n}$$`
- **Underscores outside math** trigger italics. Write file and variable names in backticks.
- **`\text{}` for words inside math** — bare words render as italicised variable products.
- **Multi-line alignment** uses `\begin{aligned}...\end{aligned}` inside `$$`, not `\begin{align}` (MathJax rejects the starred/unstarred distinction Obsidian expects).
- **Braces in callouts** are safe; no extra escaping needed beyond normal LaTeX.

---

## Tables

- Keep them narrow. A table wider than the screen is worse than a list.
- Bold the verdict column in scorecards so severity is visible while scrolling.
- Escape `|` as `\vert` inside math, and as `\|` in plain text.
- For anything over ~8 columns, use a definition list or nested bullets instead.

---

## Internal links

When a set of notes spans several sections, link between them with `[[Note name#Heading|display text]]`:

```markdown
See [[Unit 6 Notes — 6.1 Applications#3.7 QAOA versus classical|the QAOA comparison]].
```

Cross-linking is worth the effort where later sections contradict earlier ones — putting the contradiction one click away is much more useful than describing it.

---

## Citations

Inline markers are numeric — `[1]`, `[2]` — accumulating into a `## References` section at the end.

**The reference list is your audit trail, not the source's bibliography.** Most entries will be works consulted to *check* the source, not works the source cited. This means a text with no citations of its own still produces a reference list, and that list is the more valuable artifact.

### IEEE (default)

```
[1] A. Author, B. Author, and C. Author, "Title of paper," Journal Name,
    vol. 12, no. 3, pp. 45–67, 2024, doi: 10.1234/abcd.
[2] D. Author, Title of Book, 3rd ed. City, Country: Publisher, 2019.
[3] E. Author, "Title of preprint," arXiv:2401.12345, 2024.
[4] F. Author, "Title of web page," Organisation, Jan. 2026. [Online].
    Available: https://example.com
```

### APA 7

```
Author, A., Author, B., & Author, C. (2024). Title of paper.
    Journal Name, 12(3), 45–67. https://doi.org/10.1234/abcd
Author, D. (2019). Title of book (3rd ed.). Publisher.
Author, E. (2024). Title of preprint. arXiv. https://arxiv.org/abs/2401.12345
```

### Practical notes

- **Cite what you actually consulted.** If you read the abstract, the reference is still to the paper — but do not imply depth you did not reach. The provenance note is where you record how deep the checks went.
- **Give both venues when a work has two.** Conference papers later published in journals, and preprints later published, are frequently cited inconsistently — listing both is what lets a reader find it.
- **Flag preprints as preprints.** "Not peer-reviewed" is material information about a claim's standing.
- **Where a citation in the source was wrong, cite the correct work** and note the discrepancy in the callout, not in the reference list. The list should contain only correct entries.

---

## File naming

`<Source short name> <section> — <Title>.md`

For example: `Unit 6.2 — Quantum Cryptography.md`

Keep the section identifier in the filename rather than only in frontmatter — it makes the vault sort correctly and makes `[[wikilinks]]` predictable.
