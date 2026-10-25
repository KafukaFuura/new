# AI HANDOFF ADDENDUM — Notation Economy, Reference Calibration, and Current Status

> LATEST PRIORITY NOTICE — 2026-10-25: Read Section 11 of this file BEFORE applying Sections 1–10 or the earlier handoff/checklist. Section 11 records later user decisions and overrides conflicting historical advice. In particular, the MCL replacement and the first structural revision have already been completed in the working manuscript. The older statements that they are still pending are historical. Do not optimize the overview for minimum length. Explain the mathematical properties and their conditions at a readable pace.

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

---

## 11. LATEST OVERRIDES AND WORKING STATUS — 2026-10-25

### 11.1 Precedence and scope

This section is newer than Sections 1–10 and the original handoff/checklist. If an older instruction or status conflicts with this section, use this section. Future explicit user decisions take precedence over this section. Preserve the historical text for provenance, not as an instruction to restore obsolete prose or mathematics.

The latest request was to revise ONLY KI-1, KI-2, and KI-3 in Section 2.1 and synchronize the recent discussion. Section 5 remains pending discussion. The scope of this revision does not include a new boundary construction, new limiter design, or a general rewrite of the paper.

### 11.2 Latest user correction: readability is not maximum compression

The user objected to the opening sentence:

> The low-order scheme preserves positive nodal densities, is well-balanced, and dissipates the discrete total energy.

Coordinating `preserves`, `is`, and `dissipates` under one subject is grammatically possible. Do not turn this feedback into a universal ban on mixed predicate types, `is`, or `and`. The editorial problem is the concentration of three different mathematical claims before their different conditions and roles have been explained.

The user also objected to a sentence that began before a displayed positivity estimate, resumed after that display with a time-step qualification, and then used `Moreover` and `and` to introduce the equilibrium and energy claims. A display is part of its surrounding sentence. Count the full sentence across displays when assessing reading load.

The overview is a place where the writer may spend necessary words. Do not compress properties, assumptions, notation definitions, explanations, and section navigation into one sentence merely to shorten the page.

Use natural paragraphs that complete one mathematical task. Closely connected information may stay in one sentence. Different properties, different hypothesis scopes, and different stages of an argument should have room to unfold. Do not replace one overloaded sentence with an artificial row of disconnected fragments beginning `The ... The ... The ...`.

For KI-1, distinguish:

1. the forward Euler positivity statement and its step-size condition;
2. exact preservation of the discrete hydrostatic equilibrium;
3. the semidiscrete energy inequality along a positive-density trajectory.

Do not allow the prose to imply that the forward Euler CFL condition is also the condition for the semidiscrete energy identity, or that a forward Euler energy law has been proved.

### 11.3 What the overview must make visible

The three KI paragraphs must reveal the mathematical reason for combining the schemes.

- Low-order scheme: positive nodal density under its forward Euler step condition, well-balancedness, and semidiscrete energy dissipation.
- High-order DG scheme: high-order spatial discretization, preservation of the same discrete hydrostatic equilibrium, and exact cancellation of the high-order volume-pair energy contributions. Nodal positivity is not guaranteed by the high-order operator alone.
- MCL: shared pair coefficients enforce density positivity while preserving the pairwise mass cancellation, energy inequality, and equilibrium cancellation.

Keep necessary formulas in the overview, following Chen–Wu 2022 Section 3.1. A list of descriptive labels is insufficient. Conversely, do not move all hydrostatic-reconstruction details, one-sided pressure corrections, SBP algebra, or limiter formulas into the overview. Readers need to understand the object, its property, its condition, and its role before the technical construction.

If a defining or property formula is moved forward, update later references and remove redundant definitions. Explain the meaning of every newly used symbol at its first occurrence. A forward equation reference alone does not replace a minimal semantic explanation.

### 11.4 Nonnegotiable distinction in the energy statements

For a high-order volume pair, the manuscript proves

`g_a^T Phi_e^{HO,a} + g_b^T Phi_e^{HO,b} = 0`.

For a low-order volume pair, the analogous expression is

`-D_e^{LO} <= 0`.

For a limited pair with a coefficient shared by both endpoints and all conservative components, it becomes

`-(1-theta_e) D_e^{LO} <= 0`, with `0 <= theta_e <= 1`.

These statements explain why the MCL coefficients can be selected from the density constraints without imposing a separate pairwise energy constraint.

Do not describe the complete high-order operator as globally energy-conservative. Its common cell-interface fluxes can dissipate energy, the damping/alignment source contributes physical dissipation, and reflecting faces can contribute numerical dissipation. These terms remain when all limiter coefficients equal one. Periodicity does not remove the dissipation at interior cell interfaces.

Do not infer a general high-order accuracy theorem for the limited scheme merely from these structural identities.

### 11.5 Terminology and headings already agreed

Current Section 2 title:

`One-dimensional spatial discretization`

Current Section 2.1 title, taken from the structural reference:

`Outline and key ingredients of our method`

Use parallel component headings:

- `Low-order spatial discretization`
- `High-order spatial discretization`
- `Monolithic convex limiting`

Do not restore the asymmetric pair `Low-order well-balanced scheme` versus `High-order target ...`. Both low- and high-order operators have a well-balanced property. The word `target` has been removed from the working manuscript in favor of an explicit object name.

Do not call the complete high-order DG construction a `high-order reconstruction` merely because Chen–Wu 2022 uses that heading for a finite-volume reconstruction operator. In that paper the operator reconstructs a polynomial from cell averages. Our DG operator evolves nodal polynomial degrees of freedom. Retain `hydrostatic reconstruction` for the actual reconstruction operation in the low-order construction.

The user queried `hydrostatic equilibrium` and the plural `equilibria`. The term has been independently verified in Wu–Xing, arXiv:2005.07166, especially the abstract and introductory discussion. This is supplementary terminology verification, not a claim that this paper was in the original fifteen-file archive. Both singular and plural forms are legitimate. In the revised overview use the singular when referring to the already defined arbitrary state `U^{eq}` and give the equation reference. Do not claim a measured corpus frequency without measuring it.

### 11.6 A/B/C language audit must be real and inspectable

Use the following classification for newly written prose:

A. Reference-supported language or organization. Distinguish a directly attested short phrase from analogous paragraph organization. Give the file, section, and PDF page that support the comparison. The presence of a common word such as `satisfies` does not make an entire new sentence a quotation or an attested author sentence.

B. Neutral functional mathematical prose needed to state this manuscript's own construction, hypotheses, identities, or implications. State its mathematical basis. This category is legitimate. The manuscript has original content that cannot be copied from a reference.

C. High-risk prose: unsupported terminology, inflated implications, template motivation, or an academically substantive assertion with neither source support nor a verified manuscript derivation. Remove it, reduce it to a justified direct statement, or discuss it before insertion.

Do not relabel every newly generated sentence as A merely because the overall outline follows Chen–Wu. Do not paste together fragments from several papers and call the resulting sentence source-derived. Preserve mathematical scope when adapting a phrase. Review the resulting paragraph as a whole after checking individual sentences.

Reference locations used in recent work:

- Chen–Wu, JCP 466 (2022), 111398, Section 3.1, PDF pages 5–8: method outline, KI organization, essential formulas, and proof references.
- Wu–Shu, supplied `2002.03371v1.pdf`, Section 4.1, PDF pages 10–11: DG method outline, forward Euler property, and limiting.
- Wu–Shu, `WuShu_SISC2020entropy.pdf`, Section 4, PDF pages 13–18: separate statements of entropy equalities and dissipative inequalities.
- Sun–Wei–Wu, `SunWeiWu_SINUM2022.pdf`, Section 3.1, PDF pages 6–7: energy identities first, then analysis of their signs.
- Wu–Xing, arXiv:2005.07166, pages 1–3: supplementary direct verification of the term `hydrostatic equilibrium`.

Use the supplied versions for page references. Do not silently substitute preprint page numbers for journal-PDF page numbers.

### 11.7 Status updates that supersede the old pending-task lists

The user supplied a replacement MCL note. It was reviewed, corrected, and incorporated before the latest prose revisions. The working manuscript no longer uses the old nodal negative-correction-budget FCT limiter.

The high- and low-order residual constructions were retained. The replacement changed their limited combination and positivity time-step bound. The adopted multidimensional construction includes transverse quadrature scaling in pair weights and surface quadrature weights in face weights. Its convex decomposition and CFL include all cell faces, including interior interfaces, periodic pairings, and physical boundaries. Do not revert to a formula that counts only domain-boundary faces.

The working final spatial operator is now `F`, with local high-/low-order contributions distinguished by `LO` and `HO`. The step bound retains the MCL label. Inspect the current manuscript before changing notation. Historical references to a still-unresolved limiter or to a mandatory `F^{FCT}`/`F^{MCL}` notation are outdated.

An initial whole-manuscript structural revision has already been performed. It moved the low-order scheme earlier, introduced a visible low-order theorem, reorganized the multidimensional results, moved the one-step algorithm into Section 4.3, and collected the general-boundary discussion in Section 5. Formula, theorem, and section cross-references now use LaTeX labels and automatic numbering. Further refinement is expected. Do not report these tasks as wholly unstarted.

SBP references are already present in the working high-order subsection. Check the current bibliography before proposing to add the same references again.

Sections 3 and 4 have received a localized language audit. This does not certify them as final, and later structural edits must not overwrite their mature prose wholesale.

The author line is José A. Carrillo, Miaosen Jiao, Jie Shen, Kailiang Wu, ordered by surname. Do not restore the earlier Helzel guess.

### 11.8 Section 2.5 and boundary work: current scope

Section 2.5 now introduces the derivation of the energy identities and their use in the later semidiscrete energy balance. Do not describe energy identities as freely chosen definitions. The discrete energy functional itself may of course be defined. The user's concern was the rhetorical function of the introductory sentence, not a blanket ban on the verb `define`.

Section 5 still needs discussion before its next substantial revision. Proposed direction only: `Boundary conditions`, then concrete numerical boundary rules, then continuous/semidiscrete balances, then fully discrete changes. `Exterior state` denotes a numerical trace/state and is not by itself a physical boundary-condition category. Do not assert that every cited author's outflow treatment is `U^{ext}=U` without source evidence. Do not silently add that choice to the manuscript. The latest user request postpones Section 5 and focuses on the three KI paragraphs.

Keep the physical/mathematical distinctions already established: reflecting walls can have numerical energy dissipation despite zero numerical mass flux; general data may require a mass upper bound; closed-boundary auxiliary-energy bounds cannot be promoted to unconditional general-boundary results.

Appendix B's generic `understood by continuity` sentence and incomplete implementation tips involving `log1p`/`expm1` were removed. Equal-argument values are stated explicitly where needed. Do not restore software-function advice without a specific implementation task and adequate justification. Appendices A and C remain in the working manuscript.

### 11.9 Calibration against the other-AI transcript

The attached four-round dialogue is an advisory record, not mathematical authority. Keep suggestions only when they are compatible with the actual manuscript and the user's later decisions.

In particular, do not assume that the full vector pair contributions are antisymmetric. Density contributions cancel, but momentum pair contributions can sum to a nonzero potential-force term. Do not replace the endpoint notation by an allegedly antisymmetric flux without checking the exact vector identities.

Do not adopt mechanical rules such as deleting every symbol used only within three lines, banning every explanatory sentence, or requiring zero new concepts in a multidimensional extension. The supplied reference papers also introduce local intermediate quantities when they clarify a difficult argument.

The latest instruction explicitly allows enough prose to introduce important ideas clearly. Necessary explanation takes priority over a page-count or word-count reduction target. Keep routine algebra compact without making the conceptual overview cryptic.

### 11.10 Latest delivered prose revision and verification scope

Input working manuscript: `structure_preserving_DG_MCL_KI_energy_revised.tex`.

Latest revised manuscript: `structure_preserving_DG_MCL_KI_narrative_revised.tex`, with matching `.txt` and `.pdf`.

Short review extract: `KI_1_2_3_narrative_revised.txt`.

Only the block from KI-1 through KI-3 was changed in this pass. The source before KI-1 and from Section 2.2 onward is unchanged. All displayed mathematical expressions and labels were retained. One terminal comma in the low-order positivity display was changed to a period to close the newly separated sentence. No theorem, proof, residual, limiter formula, boundary formula, or time-stepping formula was changed in this pass.

The revised document compiled in two consecutive passes to 36 pages without undefined references, duplicate-label warnings, or overfull/underfull boxes. The affected overview pages were rendered for visual review. This was a localized prose revision, not a fresh proof certification or numerical validation of the whole scheme.

The actual manuscript files are delivered in the conversation. This repository stores editorial handoff notes. A future session must obtain the real latest manuscript before editing; a remembered filename does not establish an accessible sandbox file.

### 11.11 Carry-forward checklist from the latest user discussion

1. Later explicit user decisions override historical notes.
2. Introduce the method's properties and mathematical reason for the combination before technical implementation details.
3. Use necessary formulas in the outline, and synchronize their later use.
4. Do not compress separate conditions and properties into a single sentence across several displays.
5. Do not mechanically turn the prose into disconnected short sentences.
6. Retain standard mathematical terminology when it is accurate and reference-attested.
7. Apply A/B/C classification with concrete evidence and distinguish lexical evidence from organizational analogy.
8. Keep high-order volume energy cancellation separate from complete-operator dissipation.
9. Preserve the adopted MCL construction and all multidimensional face/weight factors.
10. Keep Section 5 on hold until its boundary choices and writing plan are discussed.
11. Make local changes to mature prose and verify both source diffs and the rendered PDF.
12. Continue to check the adviser-flagged words, vague cross-references, semicolons, connective `so`, and rhetorical dashes without extending the blacklist to ordinary grammatical words.
