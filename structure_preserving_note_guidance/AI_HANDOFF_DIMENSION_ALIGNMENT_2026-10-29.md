# AI HANDOFF — Dimension Alignment Between Sections 3 and 4

> Date: 2026-10-29. Read this note after `AI_HANDOFF_CONTINUATION_2026-10-29.md`. It records a later local revision and therefore overrides any earlier claim that the arbitrary-dimensional scope of Section 4 remains unresolved.

## 1. User decision and scope

The user decided to leave the uppercase/lowercase `F/f` flux notation unchanged for now. Do not modify the one-sided low-order flux notation until the user revisits that question.

The present revision addresses only whether Section 4 is notationally and logically compatible with the extension of Section 3 to arbitrary fixed dimension `d >= 3`.

No time integrator, proof, theorem statement, limiter formula, flux formula, pressure law, or section structure was redesigned.

## 2. Mathematical conclusion

The abstract time-discretization formulas in Section 4 already apply to one-dimensional and multidimensional nodal vectors. The linear alignment operator, exponential Runge--Kutta stages, density SSPRK3 reduction, auxiliary-energy equation, relaxation, mass balance, and well-balanced argument are dimension independent once the spatial operator and quadrature weights are interpreted consistently.

The issue was one of scope and notation:

- Section 3 stated the arbitrary-dimensional extension after the two-dimensional theorem;
- Section 4 then cited the two-dimensional equation numbers directly;
- the global nodal index `q` and weight `M_q` were explained only for one dimension;
- Section 4 used bold momentum and velocity even when referring to the one-dimensional operator;
- the maximum norm in the appendix was ambiguous for vector-valued momentum.

## 3. Implemented changes

### 3.1 End of Section 3

The higher-dimensional paragraph now states explicitly that, with the tensor-product weights in equation (139),

- the multidimensional MCL operator (131),
- the positivity bound (130), and
- the structural relations (133)--(138)

retain the same form in any fixed dimension `d >= 3`.

It then states that Lemma 3.1 and Theorem 3.2 apply in that arbitrary-dimensional setting.

### 3.2 Opening of Section 4

A one-time convention has been added:

`Equations (130)--(138) and Theorem 3.2 are understood in the d-dimensional form specified after Remark 3.6.`

This avoids repeating dimensional qualifications throughout the time-discretization proofs and avoids introducing unnecessary notation such as `F^(d)`, `D_h^(d)`, or `M_q^(d)`.

### 3.3 Global nodal index and quadrature weight

Section 4 now explains that `q` denotes a global nodal degree of freedom and `M_q` the corresponding quadrature weight.

- In one dimension, `q=(i,a)` and `M_q=w_{i,a}`.
- In multiple dimensions, `q` includes the cell index and local tensor-product multi-index.
- `M_q` is taken from equation (109) for `d=2` and equation (139) for `d>=3`.

### 3.4 Scalar and vector notation

At the first use of the step-dependent linear operator, Section 4 now states that, for `d=1`, the boldface variables `m` and `u` are identified with the scalar variables used in Section 2.

This permits one common formulation of the time discretization without maintaining separate scalar and vector copies of every equation.

### 3.5 Block maximum norm

Appendix C now defines the block maximum norm for vector-valued nodal momentum by

`||m||_infinity = max_q |m_q|_2`.

The operator norm `||L_n||_{infinity -> infinity}` is explicitly the induced norm. This is the norm used in the proof of the bound cited in Section 4.

## 4. Verification

The revised full manuscript source is named:

`structure_preserving_DG_MCL_dimension_aligned_20261029.tex`

The document compiled to 35 pages with no unresolved references, duplicate labels, overfull boxes, or underfull boxes in the final log.

The end of Section 3, the opening pages of Section 4, and the appendix block-norm definition were rendered and inspected.

Separate comparison extracts were created:

- `Section4_before_dimension_alignment_20261029.tex`
- `Section4_after_dimension_alignment_20261029.tex`
- `Section4_dimension_alignment_20261029.diff`

These files are delivered in the conversation rather than stored in this guidance repository.

## 5. Remaining notation decision

The following issue remains deliberately unresolved:

- whether the one-sided pressure-corrected low-order fluxes should retain uppercase `F` or be changed to lowercase `f` so that uppercase `F` is reserved for the semidiscrete spatial operator.

Do not make that change without a later explicit user decision.
