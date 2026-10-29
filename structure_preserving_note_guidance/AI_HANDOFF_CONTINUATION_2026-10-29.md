# AI HANDOFF CONTINUATION — Model Scope, Entropy/Free-Energy Structure, and Notation Status

> LATEST PRIORITY NOTICE — 2026-10-29: Read this continuation AFTER `AI_HANDOFF_ADDENDUM_NOTATION_AND_CURRENT_STATUS.md`. It records later user decisions and therefore overrides conflicting status statements in Sections 1–11 of the earlier addendum. The historical files must be preserved. Do not restore deleted sections, obsolete boundary discussions, or superseded notation merely because they remain documented in older notes.

This continuation records the structural deletions, pressure-law analysis, entropy/free-energy interpretation, innovation assessment, and notation decisions made after the 2026-10-25 handoff.

---

## 1. Current working scope and precedence

The current manuscript has moved beyond the status recorded in Section 11 of the previous addendum.

Later explicit user decisions always take precedence. In particular:

- former Subsection 4.6 has been removed as an independent subsection;
- former Section 5 on boundary conditions has been removed;
- reflecting-wall identities have been retained in a short appendix;
- the fixed-mesh relation between modified and original discrete energies remains only as a remark;
- the abstract no longer advertises the fixed-mesh `O(Delta t_max^3)` relation;
- the working title uses `Mean-Field Free Energy` rather than `Nonlocal Free Energy`;
- the present notation audit is intentionally local and must not trigger a new structural rewrite.

Do not assume that a remembered filename is the latest manuscript. Obtain the actual source from the current conversation or user-provided file before editing.

---

## 2. Structural deletions already completed

### 2.1 Former Subsection 4.6

The independent fixed-mesh consistency subsection, including its separate lemma, regularity assumption, theorem, and full discrete Gronwall proof, has been removed.

The retained remark is titled:

`Relation between the modified and original discrete energies`

It defines the discrepancy between the auxiliary and shifted discrete energies, states that the relaxation does not enlarge the preceding Runge--Kutta discrepancy, and records the fixed-mesh third-order relation under local smoothness. It also states explicitly that this is an energy-consistency result along the computed sequence, not a state-error estimate or a mesh-uniform convergence theorem.

This result is not to be restored to the abstract unless the user explicitly reverses the decision.

### 2.2 Former Section 5

The full boundary-condition section has been removed. This does not mean that the numerical method becomes unusable for every other physical boundary condition. It means that the paper no longer develops and proves the corresponding boundary mass and energy balances.

The main analysis is presently stated for periodic and reflecting-wall boundary conditions. The reflecting mirror state, zero mass flux, wall energy dissipation, and equilibrium reduction are collected in the appendix rather than repeated in Sections 2 and 3.

Do not reintroduce a long boundary taxonomy or new terms such as `exchange rate` without a new user decision.

---

## 3. Title and mean-field terminology

The adopted working title is:

`A Structure-Preserving Nodal Discontinuous Galerkin Method for Hydrodynamic Equations with Mean-Field Free Energy`

The manuscript terminology has been made more specific where possible:

- `interaction force` rather than repeatedly saying `nonlocal force`;
- `density-dependent potential` at the first definition of `H`, then simply `potential`;
- `interaction integral` and `discrete interaction operator`;
- `pairwise interaction energy` for the quadratic double-integral term;
- `velocity-alignment operator` for the alignment term.

The word `nonlocal` is retained only where it is part of an original reference title or where later context specifically requires it.

The sentence explaining the physical interpretation of the quadratic interaction term must remain modest: it represents the mean-field energy induced by pairwise interactions through the kernel `W`. Do not claim a particle-limit theorem that the manuscript does not prove.

---

## 4. Pressure law and model scope

### 4.1 Relation to the general-free-energy literature

The manuscript uses

`p(rho) = rho Pi'(rho) - Pi(rho)`

and therefore

`p'(rho) = rho Pi''(rho)`.

Carrillo et al. often begin directly from the differential relation

`P'(rho) = rho Pi''(rho)`.

The first relation implies the second. Conversely, the differential relation recovers

`P(rho) = rho Pi'(rho) - Pi(rho) + C`

for a constant `C`. The difference is therefore an energy/pressure normalization constant, not a distinct thermodynamic model. After fixing the constant in `Pi`, the two formulations are equivalent for the structural analysis.

The substantive convexity/hyperbolicity assumption is

`p'(rho) > 0`, equivalently `Pi''(rho) > 0` for positive density.

### 4.2 What the proofs actually use

The continuous free-energy relation, entropy convexity, entropy-conservative density mean, interface entropy inequality, hydrostatic reconstruction, pairwise low-order dissipation, positivity proof, and well-balanced proof principally use:

- thermodynamic compatibility;
- positive density;
- `p'(rho) > 0`, hence strict monotonicity of the enthalpy `ell(rho)=Pi'(rho)`.

The two explicit pressure laws are representative examples and provide closed-form density means and reconstruction coefficients. They are not the essential reason the structural proofs work.

### 4.3 The only current use of nondecreasing `p'`

The extra assumption that `p'` is nondecreasing appears only in the low-order construction when the sound speed at the original density is used to bound the sound speed at the hydrostatically reconstructed density:

`rho_K^HR <= rho_K` together with nondecreasing `p'` gives

`p'(rho_K^HR) <= p'(rho_K)`.

The high-order entropy-conservative flux construction does not require this monotonicity.

The algebraic positivity and energy-dissipation arguments for the low-order pair also do not intrinsically require nondecreasing `p'`; they require a nonnegative dissipation coefficient large enough to control the intermediate mass velocity.

### 4.4 Possible generalization, not yet adopted

A minimal generalization is to evaluate the low-order acoustic speed at the reconstructed states, for example by using a coefficient of the form

`max{|u_L|+sqrt(p'(rho_L^HR)), |u_R|+sqrt(p'(rho_R^HR)), |u_tilde_LR^HR|}`.

A stronger envelope version may maximize `sqrt(p')` over the interval between each reconstructed and original density. The envelope reduces to the current coefficient when `p'` is nondecreasing.

This modification has been analyzed but has NOT yet been adopted in the manuscript. Do not change the low-order dissipation coefficient until the user confirms the final form.

---

## 5. Entropy stability and free-energy stability

### 5.1 Homogeneous barotropic Euler part

The two-point convective flux satisfies the Tadmor entropy-conservation identity with the density mean

`rho^ec(r,s) = [p]/[ell]`.

The interface flux obtained by adding Rusanov-type dissipation satisfies the corresponding entropy inequality because the mathematical entropy is strictly convex.

It is accurate to say:

`The homogeneous interface flux is entropy stable in Tadmor's sense.`

### 5.2 Source-coupled high-order pair

The high-order nodal DG construction uses the same density mean in the pressure flux and the potential-force discretization. This combines pressure and potential differences into chemical-potential differences and yields pairwise cancellation with respect to the discrete total-energy variables:

`g_a^T Phi_e^{HO,a} + g_b^T Phi_e^{HO,b} = 0`.

This is more than merely reusing an entropy-conservative flux. It is a source-compatible flux-differencing extension that gives pairwise discrete free-energy conservation for the high-order volume contribution.

### 5.3 Low-order pair and MCL

The hydrostatic low-order pair satisfies

`g_a^T Phi_e^{LO,a} + g_b^T Phi_e^{LO,b} = -D_e^{LO} <= 0`.

With one scalar limiting factor shared by the two endpoints and all conservative components,

`Phi_e(theta) = (1-theta_e) Phi_e^LO + theta_e Phi_e^HO`,

so the limited pair satisfies

`-(1-theta_e) D_e^{LO} <= 0`.

Consequently, the limiter may be chosen from density-positivity constraints without imposing a separate pairwise free-energy constraint. The same pairwise compatibility also preserves mass cancellation and equilibrium cancellation.

### 5.4 Correct global terminology

For the complete source-coupled semidiscretization, prefer:

- `entropy-compatible and free-energy-stable`;
- `semidiscrete free-energy dissipative`;
- `entropy-stable homogeneous flux with a free-energy-compatible source discretization`.

Do not automatically call the complete scheme a standard convex-entropy-stable discretization for arbitrary symmetric interaction kernels, because the full mean-field free energy may be nonconvex.

The fully discrete analysis establishes a modified-energy law for the auxiliary energy. It does not currently prove monotonic decay of the original discrete total energy at every step. Do not claim fully discrete entropy stability with respect to the original energy.

---

## 6. Innovation positioning

The following ingredients are established methods and should not be presented individually as the main novelty:

- Tadmor-type entropy-conservative fluxes;
- logarithmic or polytropic density means in their classical explicit cases;
- SBP flux differencing;
- Rusanov interface dissipation;
- tensor-product Cartesian extension;
- MCL or subcell convex limiting as a general framework.

The stronger contribution is the compatible combination for hydrodynamic systems with density-dependent mean-field energy:

1. the global interaction energy has the correct discrete variation because the interaction operator is self-adjoint;
2. the high-order volume operator has pairwise free-energy cancellation;
3. the hydrostatic low-order operator has pairwise free-energy dissipation;
4. both operators share the same pairwise representation;
5. MCL therefore preserves mass, the equilibrium cancellation, and the free-energy inequality while enforcing positive nodal densities.

The novelty is a structural and analytical closure of these components, not the invention of a new homogeneous entropy-conservative flux.

Avoid unsupported priority claims such as `the first method`. A dedicated novelty search would be required before using such language.

---

## 7. Notation policy after the 2026-10-29 audit

### 7.1 General principle

Do not attempt to assign a globally unique letter to every mathematical object. Experienced mathematical writing allows local reuse when the scope is clear. Introducing a new symbol solely to avoid a distant conflict can increase, rather than reduce, reader burden.

Apply this hierarchy:

1. eliminate conflicts that occur on the same page or in the same derivation;
2. remove one-use intermediate registers;
3. use local scope declarations and suppress inactive indices;
4. name only objects that reveal structure or recur over a substantial part of the paper;
5. retain standard notation from the relevant literature when it remains clear in context.

The target is notation economy, not a global one-symbol-one-object rule.

### 7.2 `D` notation now fixed

Use:

- `D` for the LGL differentiation matrix;
- `nabla_U^2 eta(U)` for the Hessian matrix;
- `H_h'(U)[Z]` for the directional/Frechet derivative of the discrete energy;
- calligraphic `D` only for actual dissipation quantities.

The intermediate labels `physical`, `source`, `interface`, and `total` were not retained as a large hierarchy. The manuscript now names the total semidiscrete dissipation `D_h` and keeps the genuinely reusable local low-order pair dissipation `D_e^LO`. One-use components are written directly in the total formula.

### 7.3 Latest implemented notation changes

The following changes have been completed in the working source `structure_preserving_DG_MCL_notation_refined_20261029.tex`:

- normal-direction subscripts use the vector explicitly: `u_n`, `f_n`, `alpha_n`, and `Psi_n` became `u_{bold n}`, `f_{bold n}`, `alpha_{bold n}`, and `Psi_{bold n}`;
- the face quadrature weight uses `w_{Sigma q}` instead of `sigma_{Sigma q}`;
- the temporary selector `sigma in {HO,LO}` was removed by writing the high- and low-order pairwise formulas explicitly;
- appendix test velocities no longer use `v_{ell,q}`, which conflicted with entropy variables and the enthalpy symbol; they are written as `u_q^(j)`;
- the one-use energy-rate register `P_n(U)` was removed and its expression is used directly;
- unused local aliases `H_a` and `p_a` were removed from the fixed-cell notation declaration;
- a generic forward Euler step uses `tau`, while `s` remains available for density-mean arguments, integration variables, transverse weights, and Runge--Kutta stage indices.

The uppercase/lowercase `F/f` issue has been deliberately deferred. The user wants to inspect the flux notation before deciding whether one-sided low-order fluxes should change from uppercase `F` to lowercase `f`. Do not make that change without confirmation.

### 7.4 Verification of the latest notation pass

The modified source was compiled with all references resolved. The affected pages containing the forward Euler positivity proof, normal numerical fluxes, the two-dimensional pairwise representation, the semidiscrete dissipation, the auxiliary-energy discrepancy equation, and the appendix momentum-operator proof were rendered and inspected.

No undefined references, duplicate labels, overfull boxes, or underfull boxes remained in the final compilation log.

---

## 8. Remaining tasks after this continuation

The following issues remain open:

1. decide whether to retain the present low-order acoustic coefficient or generalize it to reconstructed-state/envelope sound speeds;
2. decide how much of the entropy/free-energy interpretation should enter the abstract, introduction, contribution statement, and Appendix B;
3. verify the exact Roe-related reference intended by the adviser before naming Ismail--Roe or another construction;
4. resolve the uppercase/lowercase `F/f` hierarchy;
5. retitle Sections 2 and 3 to make the semidiscrete scope explicit and harmonize `scheme` versus `method`;
6. decide the precise relocation of the mesh and quadrature setup before Subsection 2.1;
7. audit theorem and proposition titles for natural mathematical ordering;
8. decide which appendices remain necessary after the main text is stabilized;
9. replace the author block by a note indicating that the manuscript is prepared for research discussion and potential collaboration with the relevant professor;
10. perform a final whole-manuscript language, notation, citation, and rendered-layout audit after the mathematical choices above are fixed.

Do not combine all of these tasks into one uncontrolled rewrite. Handle them in the user's chosen order and preserve mature passages unless a specific mathematical or editorial reason requires change.
