# AI HANDOFF ADDENDUM — Notation Economy, Reference Calibration, and Current Status

Read this file after `AI_HANDOFF_MANUSCRIPT_STYLE_AND_STRUCTURE.md` and together with `AI_LANGUAGE_AND_STRUCTURE_AUDIT_CHECKLIST.md`.

This addendum records decisions and user feedback developed after the original handoff was written.

---

## 1. New major diagnosis: programming-style notation and decomposition

A recurring AI failure mode in mathematical writing is analogous to writing code with unnecessary intermediate variables.

Suppose the real mathematical task is to evaluate or analyze

> A + B + C.

A human mathematical writer may use the expression directly. An AI often behaves like a programmer:

1. define `D = A + B`;
2. introduce a name for `D`;
3. later write `D + C`;
4. explain the relation between `D` and the original expression.

The extra variable is harmless for machine reasoning but imposes a real memory cost on a human reader. Across a long manuscript, this produces a dense dependency graph of symbols that obscures the method.

### Required audit

For every intermediate symbol, operator, coefficient, residual, functional, stage quantity, or named relation, ask:

1. Can the original expression be used directly without making the formula unreadable?
2. Is the intermediate object used often enough to justify reader memory?
3. Does the symbol expose a real mathematical structure, or merely break a calculation into code-like steps?
4. Does it appear in a theorem, algorithm, or proof dependency that genuinely benefits from a name?
5. Is it separated from its definition by enough distance that numbering or naming is necessary?
6. Would an equation number and direct cross-reference be better than a new symbol?

If the symbol only serves as a temporary computational register, remove it or keep it local to the proof.

### Important distinction

Do not remove all intermediate notation. Some intermediate objects are mathematically essential because they:

- isolate a structural identity;
- encode a reusable operator;
- state a theorem compactly;
- distinguish high- and low-order constructions;
- make a conservation, positivity, energy, or well-balanced argument transparent;
- are repeatedly used over multiple pages.

The goal is notation economy, not notation minimalism.

---

## 2. Avoid overcorrection

The user explicitly warned against overcorrecting after identifying AI-like habits.

A reference paper may contain long explanations, auxiliary variables, intermediate lemmas, or named quantities when the mathematics requires them. Do not remove these merely because the manuscript has previously suffered from excessive notation.

The correct target is proportionality:

- important ideas receive enough explanation;
- routine algebra is compressed;
- essential notation is retained;
- temporary coding-style notation is removed;
- difficult steps may be detailed;
- obvious steps should not receive equal weight.

The user described the desired balance as roughly:

> relaxed where appropriate, strict where necessary; neither uniformly terse nor uniformly exhaustive.

This should be interpreted as a requirement for mathematical judgment, not a fixed sentence-length rule.

---

## 3. How to decide what is necessary: use the 15+1 reference corpus

The user emphasized that the judgments about notation, emphasis, and level of detail were learned from the supplied computational-mathematics papers.

Future AI instances should use:

- the original set of approximately fifteen Wu/Shu and related papers used throughout the project;
- `ChenWu_JCP2022.pdf` as the additional structural reference, especially for method-first organization.

Do not decide necessity by AI convenience.

For a disputed notation or paragraph, inspect comparable locations in the reference corpus:

- method overview;
- mesh and quadrature setup;
- low-order scheme definition;
- high-order target;
- limiter construction;
- theorem statement;
- proof of positivity;
- well-balanced proof;
- multidimensional extension;
- fully discrete analysis.

Ask how experienced authors distribute notation and explanation in the same rhetorical situation.

Reference evidence should be classified as:

1. **direct lexical evidence** — the same or closely related phrase appears;
2. **organizational evidence** — the reference handles the same mathematical function in a similar location;
3. **editorial inference** — our own judgment informed by the references.

Do not present category 3 as if it were a direct quotation-based fact.

---

## 4. Reference-attested does not automatically mean optimal in context

A word may occur in the reference corpus and still be unnecessary in the current sentence.

Example already discussed:

- `analogue` appears in Sun–Wei–Wu in the technical phrase `a discrete analogue of integration by parts`.
- In the present manuscript, a sentence about tensor-product quadrature accuracy was clearer when it stated the actual order `O(h^{N+1})` rather than saying `the tensor-product analogue of ...`.

Therefore the test is two-stage:

1. Is the expression authentic to the target literature?
2. Is it the clearest and most precise expression for this exact context?

Both conditions matter.

---

## 5. SAV writing rule

The scalar auxiliary variable (SAV) discussion requires special care because Jie Shen is an author and the manuscript relies materially on the SAV / generalized SAV / relaxation lineage.

### Required source hierarchy

For substantive SAV claims and historical description:

1. use Jie Shen and collaborators' own papers and review language;
2. use plain neutral mathematical prose for necessary local connections;
3. if a new substantive sentence cannot be supported by the source papers and is not neutral connective prose, stop and discuss it with the user.

Do not generate a polished mini-review from model memory.

The SAV discussion should be informative enough to acknowledge the original SAV framework, generalized variants, and relaxation motivation, but should avoid a template-like history of the entire field.

A recent revision compressed the Section 4 opening and the SAV review while retaining the direct inspiration and citations. Future restructuring must preserve this balance.

---

## 6. Formula-number and cross-reference policy updated

Recent revisions added numbers to several formulas that are reused later.

General rule:

- number a display if it is invoked later, particularly across subsections or pages;
- use the equation number instead of vague `above` / `below` language;
- do not number every one-use line in a local proof;
- reconsider numbering after major Section 2 restructuring because movement may change which definitions are remote.

An equation number can often replace an unnecessary named variable.

---

## 7. Status of Sections 3 and 4 language review

After the original handoff, Sections 3 and 4 received a dedicated sentence-level AI-style audit and a localized revision.

### Section 3

The language is relatively stable. Recent changes included:

- shortening the opening inventory of new ingredients;
- stating the nonlocal quadrature order directly as `O(h^{N+1})`;
- reducing list-like explanations after the multidimensional positivity step-size formula;
- removing a repeated definition of the nodal lower bound;
- shortening the defensive scope paragraph in the higher-dimensional extension.

Do not infer that Section 3 is permanently final. Boundary terminology and any consequences of a limiter change remain open.

### Section 4

Recent changes included:

- compressing the two opening paragraphs into one;
- retaining a concise statement that the construction is inspired by SAV, generalized SAV, and relaxation approaches;
- rewriting the SAV review from Shen-source language rather than model-generated survey prose;
- removing repeated explanations after the linear splitting and invariant-set lemma;
- shortening the explanation after the relaxation update;
- reducing defensive prose around the local smoothness assumptions and the analytical integrating factor.

The theorem and proof cores were mostly preserved.

The latest language revision should not be overwritten wholesale during structural work.

---

## 8. Current unresolved limiter issue

The user is separately discussing a possible mathematical problem in the limiter.

Current provisional understanding only:

- the low-order residual / reconstruction may remain unchanged;
- the high-order residual / flux-differencing construction may remain unchanged;
- the likely change concerns how the high- and low-order residuals are combined, including limiter coefficients or correction allocation.

This is NOT yet a confirmed final mathematical decision.

Until the user supplies the resolved limiter formulation:

- do not redesign the low-order or high-order residuals;
- do not rewrite limiter proofs as final;
- do not perform a large Section 2 structural rewrite that assumes the current limiter formulas are permanent.

Once the limiter is settled, recheck:

- nodal positivity;
- pairwise conservation;
- energy identities;
- well-balancedness;
- multidimensional limiting;
- fully discrete stagewise positivity;
- algorithmic summary.

---

## 9. Remaining major tasks at this stage

The following remain unfinished or nonfinal:

1. settle the limiter mathematics;
2. restructure Section 2 so the method and low-order scheme appear earlier;
3. promote important low-order properties, especially well-balancedness, into visible formal results where appropriate;
4. perform a systematic notation-reduction audit using the programming-style-variable test;
5. add appropriate summation-by-parts (SBP) references;
6. finish the boundary-terminology audit (`open boundary`, `net boundary`, and related phrases);
7. re-run language audits after every structural rewrite;
8. compile and inspect the PDF visually after formula or layout changes.

---

## 10. Updated decision rule

When considering a new symbol or an intermediate definition, do not ask only whether it is mathematically valid.

Ask:

> Does this object help a human reader see the mathematical structure, or does it merely help an AI execute the derivation like code?

Retain it only when the reader gains more than the reader must remember.
