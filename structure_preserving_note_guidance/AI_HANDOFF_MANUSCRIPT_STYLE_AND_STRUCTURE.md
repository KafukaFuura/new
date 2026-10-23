# AI HANDOFF — Structure-Preserving DG Manuscript

## 0. Purpose of this file

This file is a persistent handoff for any future AI instance working on the manuscript currently titled approximately:

> A Structure-Preserving Nodal Discontinuous Galerkin Method for Hydrodynamic Equations with Nonlocal Free Energy

The goal is NOT to produce generic academic English. The goal is to preserve the mathematical content while making the manuscript read like a strong computational mathematics paper written by experienced numerical analysts, with particular attention to the writing and organization of Kailiang Wu and closely related authors.

This file should be read BEFORE making any substantive structural or prose revision.

---

## 1. Current overall assessment

The manuscript has already undergone many rounds of language polishing. Relative to a much earlier version, the obvious local "AI flavor" in the prose has been reduced substantially. This is a real improvement.

However:

1. AI-like language has NOT been eliminated.
2. The later parts of the manuscript, especially Sections 3 and 4, have NOT yet received the same line-by-line human-style scrutiny as Sections 1 and the first large part of Section 2.
3. The most serious current problem is STRUCTURAL rather than grammatical.

The user's adviser carefully reviewed mainly Section 1 and the first large portion of Section 2. The adviser looked less carefully at the later part of Section 2 and did not have time to review Sections 3 and 4 in detail.

Therefore, do NOT infer that Sections 3 and 4 are already stylistically safe just because earlier sections have been polished.

---

## 2. Main structural problem identified by the adviser

The manuscript is mathematically complete but too difficult to read in its current organization.

The dominant structural failure mode is:

> too many definitions, symbols, identities, preparatory facts, and technical details are introduced before the reader sees the central low-order scheme, its key properties, and the overall algorithmic architecture.

An AI can track a large number of symbols and dependencies simultaneously. A human reader cannot be expected to do this comfortably over a long paper.

The paper is already long before numerical experiments are added. Therefore the reader must learn quickly:

- what the numerical method is;
- what the low-order scheme is;
- what the high-order target is;
- where the flux correction / limiter enters;
- which structural properties are proved;
- how the main components fit together.

If a reader reaches many pages of notation before seeing the first meaningful low-order method and its first key theorem, the structure has failed.

### Required structural principle

Use a method-first organization:

> model / essential setup -> method overview -> low-order scheme -> main low-order property/properties -> high-order target -> correction/limiting mechanism -> structural analysis/proofs -> multidimensional and fully discrete extensions

This does NOT mean all proofs must be moved to the very end. It means the reader should understand the method before being asked to carry a large burden of technical preliminaries.

### Primary reference for this structural issue

Study Yaping Chen and Kailiang Wu (2022), especially the numerical-method section and the way the paper gives an outline / key ingredients before detailed analysis.

Also study multiple other Kailiang Wu papers. Do not imitate only one paper. Learn the recurring decisions:

- how early the scheme is shown;
- when auxiliary notation is introduced;
- how important properties are elevated into formal results;
- how long proofs are staged;
- what technical details are delayed;
- how the main line is kept visible.

---

## 3. Hard adviser feedback to treat as manuscript-wide requirements

The following points came directly from the user's adviser and should be treated as hard revision targets.

### 3.1 Opening of the note

Because this is a note rather than a conventional full article with a formal abstract, the beginning should still state quickly what the paper constructs and proves.

The reader should understand the main mathematical contribution near the beginning.

Do not let the paper drift through setup for too long before stating the main result.

### 3.2 Algorithm before analysis

The algorithm/method must appear before a long chain of technical proofs.

A reader should be able to read a limited portion and already understand what the paper is doing.

### 3.3 Important properties should be formal results

Important properties should be promoted to theorem/proposition/lemma form when appropriate.

Example explicitly raised by the adviser:

- the well-balanced property of the first-order / low-order scheme should be visible as an important formal result, rather than being buried in surrounding derivation.

Use mathematical judgment; do not create theorem environments for trivial facts.

### 3.4 Abbreviations

Every English abbreviation must be expanded at first occurrence.

Examples requiring audit:

- discontinuous Galerkin (DG)
- Legendre-Gauss-Lobatto (LGL)
- summation-by-parts (SBP)
- flux-corrected transport (FCT), if that terminology is retained
- strong-stability-preserving Runge-Kutta (SSPRK), if used
- scalar auxiliary variable (SAV), if used

Do not allow an abbreviation to appear before its full form.

### 3.5 SBP references

The use of summation-by-parts technology must be supported by appropriate references.

The manuscript should not introduce SBP identities as if they are isolated notation with no literature context.

Relevant literature should cover, as appropriate:

- SBP operators;
- the relation between SBP and nodal DG / DGSEM;
- flux differencing / split forms;
- entropy-stable high-order discretizations.

Do not add references mechanically. Use references in the place where the technique is first introduced or conceptually motivated.

### 3.6 Boundary terminology

The adviser specifically questioned expressions involving:

- "open boundary"
- "net boundary ..."

These terms should be checked throughout the paper for standard usage in numerical PDE literature.

The actual mathematical setup often uses physical boundary faces with prescribed exterior states, reflecting wall states, periodic pairing, and possibly inflow/outflow data.

Use terminology that accurately reflects the implemented mathematical boundary treatment.

### 3.7 Too many symbols

The notation burden is currently too high.

Only introduce notation that has real downstream value.

A local intermediate quantity that is used once or twice usually should not be given a permanent symbol unless it materially improves the proof.

If an important definition is introduced and used much later, it should have an equation number or other explicit reference so that the reader can find it again.

### 3.8 Explicit cross-references

Do not rely on vague navigation such as "above" or "below" when referring to a formula, definition, or theorem.

The adviser explicitly objected to isolated / vague words such as:

- above
- below

If a mathematical object is being recalled, use a specific equation number, theorem number, lemma number, or named object.

Exception: standard phrases such as "bounded from below" are not navigation and should not be mechanically changed.

---

## 4. Hard AI-flavor words and punctuation explicitly raised by the adviser

The adviser explicitly identified the following as suspicious / undesirable in this manuscript.

These MUST be included in every later stylistic audit.

### Words / phrases explicitly flagged

- images
- record
- need not
- defect
- obstruction

The issue is not that these words are always mathematically illegal. The issue is that they can appear as model-favored academic phrasing, especially when used repeatedly or without strong mathematical necessity.

For this project, treat them as high-risk and inspect every occurrence.

### Punctuation / connection patterns explicitly flagged

- semicolon `;
- "so"
- rhetorical dashes / dash-based parenthetical insertion

Do not let sentence reconstruction reintroduce these as default ways of joining ideas.

Technical hyphenation and conventional compound names are not the same issue. Examples such as Runge-Kutta, Gauss-Lobatto, well-balanced, and structure-preserving remain normal mathematical terminology.

---

## 5. User feedback accumulated over many rounds

The user often notices expressions that are grammatically valid but feel strange relative to the reference authors.

Do NOT dismiss this as subjective noise.

A recurring empirical pattern has been:

> when the user says an expression feels strange, very similar wording is often rare or absent in the supplied reference papers.

Therefore, user discomfort should trigger a reference-style check.

The user may not always propose the final replacement, and some individual suggestions may require mathematical or stylistic adjustment. But the signal itself is valuable.

Treat this as a two-sided screening process:

- AI should actively detect its own model-favored language;
- user reactions should be treated as additional evidence that a phrase may not match the target authorial style.

---

## 6. Critical constraint during structural reconstruction

Structural improvement MUST NOT reintroduce AI-like prose.

This is a major project constraint.

The danger is:

1. move or reorganize sections;
2. create many new transition sentences;
3. accidentally replace already-humanized prose with fresh model-generated prose;
4. obtain a better structure but worse language.

Therefore use this default order of operations:

1. move existing material;
2. reorder existing material;
3. delete redundancy;
4. reduce notation;
5. promote important results into formal theorem/proposition environments;
6. add equation/theorem cross-references;
7. write NEW prose only where structural continuity truly requires it.

Language changes should be as local as possible.

However, do not interpret "minimal changes" mechanically. Structural reconstruction will inevitably require some new sentences. Every new sentence must pass the AI-language screening described below.

---

## 7. AI self-screening framework for newly written prose

An AI cannot safely rely on the feeling that a sentence "sounds academic".

For every newly generated sentence, classify it conceptually into one of the following groups.

### A. Reference-supported

A similar rhetorical function and phrasing can be found in the target reference corpus, especially Wu / Shu / Chen-Wu / Shen papers in comparable mathematical situations.

This is preferred.

### B. Neutral mathematical prose

No special reference phrase is needed because the sentence is plain and functional.

Examples of safe functional patterns include:

- Differentiating ... gives ...
- Substituting (x) into (y) yields ...
- Summing over ... and using (x) gives ...
- Combining (x) and (y) proves ...
- Define ...
- Let ...
- By (x), ...

These are acceptable when mathematically accurate and not repeated mechanically.

### C. Model-generated / high-risk

A sentence sounds polished, explanatory, symmetric, or rhetorically complete, but no comparable usage is found in the reference corpus.

This category requires re-examination.

Typical warning signs:

- unnecessary motivational wrapping;
- every paragraph ending with a summary;
- every formula followed by an explanation of what it "means";
- overuse of abstract nouns;
- repeated rhetorical templates;
- excessively balanced sentence pairs;
- transitions that exist only to make prose sound polished.

---

## 8. High-risk model-favored expressions beyond the adviser’s explicit list

The following are NOT automatically banned. They are a screening list based on prior manuscript discussions and known model tendencies.

Check them when they appear, especially if frequent.

- A key feature is ...
- A key structural feature is ...
- The main idea is ...
- A natural way to ...
- A convenient way to ...
- It is useful to ...
- We note that ...
- We also note that ...
- We record that ...
- This provides ...
- This allows us to ...
- This makes it possible to ...
- The resulting ...
- We now give ...
- We next consider ...
- In what follows ...
- In particular ... used as generic filler rather than a real specialization
- while / whereas used repeatedly for sentence engineering
- "This observation" when the antecedent is not mathematically sharp
- "This relation" when an equation number would be clearer
- "the key point" unless there is genuinely one key logical point
- "the desired result follows" when the actual logical step should be stated

Also screen:

- consecutive sentences beginning with "The ...";
- repeated "Here ...";
- repeated "where ..." tails after displays;
- overly symmetric lists of three;
- "definition -> explanation -> consequence -> summary" repeated in every paragraph.

The problem is frequency and template behavior, not isolated legality.

---

## 9. Sentence-level style principles already established

### 9.1 One paragraph, one mathematical task

Do not mechanically enforce "one sentence = one fact".

That earlier strategy produced a new problem: several short disconnected sentences beginning with "The ..." or "Its ...".

Instead:

> organize a paragraph around one mathematical task.

Information at the same logical level can be naturally connected.

Different logical levels should be separated.

### 9.2 Proof language should reflect real mathematical operations

Prefer verbs that describe what the proof actually does.

Examples:

- differentiating
- substituting
- summing
- applying
- combining
- canceling
- using the SBP identity
- using consistency
- using symmetry / skew-symmetry

Avoid proof openings that merely announce a static fact when an operation is actually being performed.

A previously identified bad example was an opening of the form:

> With respect to the inner product ..., the local terms have gradient components ...

A more natural proof begins from the actual differentiation.

### 9.3 Explain only non-obvious proof steps

Explain:

- nontrivial identities;
- decisive cancellations;
- where positivity / convexity enters;
- where a CFL condition is used;
- dependencies on previous lemmas;
- a delicate boundary argument.

Do not narrate every algebraic substitution.

### 9.4 Do not over-name ordinary objects

The manuscript previously accumulated labels for intermediate quantities and ordinary structures.

Avoid creating names merely because an object appears in a proof.

Naming should reduce cognitive load, not increase it.

---

## 10. Structural AI-flavor patterns to avoid

The largest remaining AI-like feature is not vocabulary but organization.

### Pattern 1: exhaustive setup before method

AI tendency:

> define everything that might be needed later, then present the method.

Human-reader problem:

> the reader cannot see the point of the definitions.

Correction:

> expose the method early and introduce technical objects close to where they become necessary.

### Pattern 2: equal weight for unequal facts

AI tendency:

> every detail gets a complete explanatory sentence.

Correction:

> major design choices receive explanation; routine definitions stay compact.

### Pattern 3: perfect symmetry

AI tendency:

> every subsection follows exactly the same narrative template.

Correction:

> let mathematical importance determine length and emphasis.

### Pattern 4: proof-first completeness

AI tendency:

> establish all technical lemmas before telling the reader the algorithmic story.

Correction:

> let the reader first understand the object being analyzed.

---

## 11. Reference-author learning strategy

Do not use reference papers only to copy words.

Study them at four levels.

### Level 1: section architecture

Ask:

- when does the numerical scheme first appear?
- how much notation is introduced before it?
- where are key properties stated?
- are proofs immediate or postponed?

### Level 2: paragraph function

Ask:

- what is the paragraph trying to accomplish?
- how many definitions are introduced at once?
- what is explained versus left implicit?

### Level 3: proof rhetoric

Ask:

- how does the proof begin?
- which algebraic steps are verbalized?
- how are equations cross-referenced?
- when is a sentence added after a display?

### Level 4: lexical habits

Track:

- theorem-introduction phrases;
- proof verbs;
- transition phrases;
- boundary terminology;
- how rarely or frequently words such as "record", "need not", etc. appear.

A sentence should not be justified merely because it is grammatical English.

---

## 12. Core reference corpus already used in this project

The following papers / groups have been important in prior rounds.

### Wu / Shu core papers

- Wu & Shu, positivity-preserving high-order schemes for ideal MHD
- Wu, positivity-preserving analysis
- Wu / Shu geometric quasilinearization work
- entropy-minimum / positivity papers
- RMHD PCP DG papers
- Wu-Shu SIAM Review and SISC papers
- Wu-Jiang-Shu multidimensional CDG / positivity work
- Ding-Wu positivity work
- Sun-Wei-Wu energy identity work

### Important archive paper for current restructuring

- ChenWu_JCP2022.pdf

Use this especially for:

- numerical method setup;
- outline and key ingredients;
- ordering of construction versus proof;
- concise introduction of discrete objects.

### Shen / auxiliary-energy literature

Use Jie Shen and collaborators as references for:

- SAV / generalized SAV / relaxation formulation;
- energy-stable time discretization;
- how auxiliary variables and energy laws are introduced.

Do not over-import SAV jargon when the current method only draws inspiration from that framework.

---

## 13. Current manuscript-specific technical style decisions already made

Preserve these unless the mathematics itself changes.

### PDE wording

Use "balance-law form" rather than "conservative form" for the full PDE when source terms are present.

### Domain

Do not use torus notation.

Use an ordinary bounded connected domain and describe periodicity as a boundary condition.

### One-dimensional mesh

Use an interval with endpoints identified only when periodic boundary conditions are imposed.

### Geometry / interface terminology

Prefer:

- cell
- cellwise
- cell interface
- subcell interface
- physical boundary
- face for geometry
- interface for numerical coupling

### Density terminology

Prefer:

- nodal lower bound

Avoid reintroducing "density floor" unless technically necessary.

### Boundary framework

The current mathematics handles:

- periodic pairing;
- reflecting wall states;
- physical boundaries with prescribed exterior states.

The terminology should be audited against standard literature rather than mechanically retaining "open boundary".

### Fully discrete auxiliary energy

Current variables include:

- R = E_* exp(z)
- xi = R / E_h(U)

The current method is inspired by generalized / relaxed auxiliary-energy ideas but should not repeatedly advertise terminology distinctions such as G-SAV versus GSAV.

---

## 14. Important current theorem / analysis scope

The fully discrete analysis contains a distinction that should remain mathematically clear.

For periodic / reflecting wall boundaries:

- boundary energy input is zero;
- some auxiliary-energy monotonicity bounds are available;
- mass can be constant;
- specific ratio bounds can be simplified.

For physical boundaries with prescribed exterior states:

- boundary mass and energy contributions remain in the balance;
- do not force closed-boundary monotonicity statements to hold.

Do not "unify" boundary cases by making a false theorem.

---

## 15. Notation policy for future revision

Before introducing a symbol, ask:

1. Is it used repeatedly?
2. Does it shorten a genuinely complicated expression?
3. Does it appear in a theorem or proof dependency?
4. Will the reader need to remember it across pages?
5. Would equation numbering be clearer than a new name?

If the answer is mostly no, avoid the symbol.

If a symbol is necessary and reused much later:

- define it clearly;
- number the defining equation when useful;
- explicitly refer back to that equation.

---

## 16. Formula-layout policy

Formula layout must be judged visually in the compiled PDF, not only from source alignment.

Established preferences:

- center display blocks;
- align internally by meaningful relations such as "=";
- do not left-justify a display solely to create visual alignment;
- short parallel definitions may share a line;
- long definitions should be separated according to mathematical dependency;
- do not mechanically put every definition on its own line.

Example already revised:

For the multidimensional positivity step-size definition, the long definition of Lambda should occupy its own line, while the shorter dependent definitions of tau_K and Delta t_pos can be placed together beneath it.

---

## 17. Workflow for the next major restructuring

When restructuring Section 2:

### Phase A: mathematical skeleton only

Do not rewrite prose yet.

Map:

- what should appear before the low-order scheme;
- where the low-order scheme should first appear;
- where its well-balanced / positivity property should be stated;
- when the high-order target enters;
- when pairwise representation is actually needed;
- when limiter notation becomes necessary;
- which proofs can move later.

### Phase B: move existing material

Reuse existing prose and formulas as much as possible.

### Phase C: notation reduction

Remove symbols that no longer earn their cost.

### Phase D: formalize key properties

Promote important properties into theorem/proposition environments where appropriate.

### Phase E: add only necessary new transitions

Every new sentence must pass the reference / neutral / high-risk screening.

### Phase F: line-by-line AI-language audit

Search for adviser-flagged words and punctuation, then inspect context manually.

### Phase G: PDF visual audit

Compile and inspect section transitions, theorem spacing, formula layout, and page-level density.

---

## 18. Scope of adviser review versus remaining work

Very important for future AI instances:

- Section 1: relatively carefully discussed.
- Section 2 first large part: relatively carefully discussed.
- Later Section 2: less carefully reviewed.
- Section 3: still requires sentence-by-sentence AI-style review.
- Section 4: still requires sentence-by-sentence AI-style review.

Do NOT claim the later sections are stylistically finalized.

---

## 19. User's standing preferences

- Discuss major structural changes before rewriting large sections.
- Preserve mathematical meaning exactly.
- Preserve assumptions, quantifiers, scope, notation meaning, and proof logic.
- Do not simplify away technical content merely for readability.
- Do not introduce fashionable terminology unless needed.
- Do not create unnecessary names.
- Do not use multiple agents unless the user explicitly requests it.
- When citing reference-author style, distinguish:
  - direct phrase evidence;
  - analogous organizational evidence;
  - our own editorial judgment.
- Compile LaTeX and inspect PDF visually after substantive formatting changes.
- Language discussion may be in Chinese; manuscript prose is English.

---

## 20. Final decision rule for future AI editing

When choosing between two mathematically correct rewrites, prefer the one that:

1. makes the numerical method visible earlier;
2. introduces fewer new symbols;
3. requires the reader to remember less;
4. uses plainer mathematical English;
5. resembles the rhetorical behavior of the reference numerical-analysis papers;
6. preserves already-humanized prose whenever possible;
7. avoids adviser-flagged model habits;
8. makes theorem/proof dependencies explicit;
9. does not over-explain routine algebra;
10. remains mathematically exact.

If structural improvement requires many newly generated sentences, stop and reconsider whether existing prose can be moved instead.
