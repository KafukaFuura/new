# AI-LANGUAGE AND STRUCTURE AUDIT CHECKLIST

Read together with AI_HANDOFF_MANUSCRIPT_STYLE_AND_STRUCTURE.md and AI_HANDOFF_ADDENDUM_NOTATION_AND_CURRENT_STATUS.md.

## A. Adviser-explicit language flags

Search every substantive revision for:

- record
- need not
- defect
- obstruction
- images
- semicolon ;
- standalone / connective "so"
- rhetorical dash insertion
- vague navigation: above, below

Do not apply blind global replacement. Inspect mathematical context.

## B. Abbreviation audit

At first occurrence, confirm full form appears before abbreviation:

- DG
- LGL
- SBP
- FCT
- SSPRK
- SAV
- any newly introduced abbreviation

## C. Structure audit

Before approving a section, ask:

- Can a first-time human reader see the scheme early enough?
- Is the low-order method visible before long technical analysis?
- Are its main properties stated prominently?
- Is there a method overview before many pages of notation?
- Are important properties formal results?
- Can any technical lemma/proof be moved after the algorithm?
- Is any symbol introduced much earlier than needed?

## D. Notation audit

For each new symbol:

- repeated use?
- reduces real complexity?
- necessary for theorem/proof?
- worth reader memory cost?
- definition numbered if reused much later?

Delete or inline symbols that fail this test.

## E. New-sentence AI-risk audit

Classify new sentences:

1. reference-supported;
2. neutral functional mathematical prose;
3. model-generated/high-risk.

Recheck category 3.

High-risk patterns:

- A key feature ...
- A key structural feature ...
- The main idea ...
- A natural way ...
- A convenient way ...
- It is useful to ...
- We note that ...
- We also note that ...
- We record ...
- This provides ...
- This allows us to ...
- This makes it possible to ...
- The resulting ...
- We now give ...
- We next consider ...
- generic "In what follows ..."
- repeated "while/whereas"
- repeated "Here ..."
- consecutive "The ..." sentences
- paragraph-ending summary sentence added only for polish
- formula followed by unnecessary explanation of obvious meaning

## F. Proof-action audit

Prefer actual operations:

- differentiating
- substituting
- summing
- applying
- combining
- canceling
- using symmetry / skew-symmetry
- using SBP
- using consistency

Explain only:

- nontrivial identity;
- decisive cancellation;
- positivity/convexity step;
- CFL use;
- boundary subtlety;
- dependency on prior result.

Do not narrate routine algebra.

## G. Cross-reference audit

Replace vague navigational references with specific:

- equation number;
- theorem / proposition / lemma number;
- explicitly named object.

Do not leave isolated "above" / "below" references.

## H. Boundary terminology audit

Check every occurrence of:

- open boundary
- net boundary
- boundary input

Ask whether the actual numerical treatment is better described through:

- physical boundary;
- prescribed exterior state;
- inflow/outflow condition;
- reflecting wall;
- periodic pairing;
- boundary contribution / flux term.

Use standard terminology supported by the relevant literature.

## I. Reference-style audit

Compare new organization and prose with:

- Yaping Chen & Kailiang Wu (2022), especially numerical-method organization;
- other Kailiang Wu papers in the project corpus;
- Wu/Shu proof style;
- Jie Shen and collaborators for auxiliary-energy time discretization.

Do not copy phrases mechanically. Learn placement, emphasis, notation economy, and proof density.

## J. Minimal-change rule during restructuring

Priority:

1. move;
2. reorder;
3. delete redundancy;
4. reduce notation;
5. formalize important result;
6. add explicit cross-reference;
7. only then generate new prose.

After any structural rewrite, re-run all language checks because better structure must not reintroduce AI-like prose.

## K. Programming-style intermediate-variable audit

For every newly introduced intermediate symbol or named quantity, ask:

- Does this expose a real mathematical structure?
- Is it reused often enough to justify reader memory?
- Does it shorten a genuinely complicated expression?
- Is it needed in a theorem, algorithm, or long proof dependency?
- Could the original expression be used directly?
- Would an equation number and direct cross-reference be clearer than a new name?

Warning sign:

> The mathematics is conceptually A+B+C, but the prose first defines D=A+B and later works with D+C only because this resembles a program with temporary variables.

Remove coding-style temporary registers. Retain notation that clarifies conservation, positivity, energy, well-balancedness, operator structure, or repeated dependencies.

## L. Anti-overcorrection audit

Do not turn notation economy into notation minimalism.

Before deleting notation or explanation, check comparable passages in the 15+1 reference corpus:

- the core Wu/Shu and related papers previously supplied;
- ChenWu_JCP2022.pdf for method-first structure.

Retain an intermediate object when experienced authors would use it to expose a structural identity, state a theorem clearly, or avoid repeating a genuinely complicated formula.

The target is proportionality:

- important step: explain;
- routine step: compress;
- essential notation: retain;
- temporary coding-style notation: remove.

## M. Reference-evidence classification

When justifying a revision, distinguish:

1. direct lexical evidence;
2. analogous organizational evidence;
3. editorial inference informed by the references.

Do not present editorial inference as a phrase directly attested in the source papers.

A word appearing in a reference paper is not automatically the best choice in the current context. Check both authenticity and local precision.

## N. SAV-specific language audit

For substantive SAV history or claims:

1. prefer Shen and collaborators' own wording and framing;
2. use neutral functional prose only for local connections;
3. if a necessary substantive sentence has no source analogue and is not neutral, discuss it before inserting it.

Avoid regenerating a polished template literature review after structural edits.

## O. Current-status safeguards

- Sections 3 and 4 received a localized sentence-level audit, but boundary terminology and limiter-dependent passages remain nonfinal.
- The limiter mathematics is under separate review. Do not treat the current limiter formulas or proofs as permanent until the user confirms the replacement.
- Any limiter change requires rechecking positivity, pairwise conservation, energy identities, well-balancedness, multidimensional limiting, fully discrete stage conditions, and the algorithmic summary.
