# Front matter revision and Section 2/LGL plan — 2026-10-30

This note supplements the earlier handoff files. Later explicit user decisions prevail.

## Front matter now implemented

- Removed the four-name author list.
- Replaced the author line with: `This note is prepared for research discussion with Professor [Name] and to explore potential collaboration.` The placeholder is deliberate because the exact professor name has not been supplied; do not invent it.
- Changed the abstract opening from `This note develops and analyzes` to `In this note, we develop and analyze`.
- Replaced `arise in continuum descriptions of collective behavior` with `provide continuum models of collective behavior`.
- Retained `attractive--repulsive`: this is a standard compound modifier in the directly relevant literature and in the cited review title.
- Cleared the PDF author metadata and added a subject field describing the research-discussion/potential-collaboration purpose.

## Section 2 plan — not yet implemented

Move the common discretization setup from inside Subsection 2.1 to the unnumbered introduction immediately after the Section 2 opening paragraph:

1. mesh and cells;
2. DG space and semidiscrete approximation;
3. reference/physical LGL nodes and weights;
4. quadrature exactness;
5. Lagrange nodal basis and expansion;
6. nodal variables and interface traces.

Then begin Subsection 2.1 with the semidiscrete operator, discrete hydrostatic equilibrium, and KI-1/KI-2/KI-3. This makes `Outline and key ingredients of our method` match its actual content.

## LGL terminology

Keep `Legendre--Gauss--Lobatto (LGL) nodes`: it is precise and standard. The problem is repetition rather than correctness.

Recommended usage:

- first occurrence: `Legendre--Gauss--Lobatto (LGL) nodes`;
- rule/accuracy statements: `LGL quadrature nodes and weights`, `LGL quadrature rule`;
- after setup: `nodes`, `nodal points`, or `adjacent nodes` when the exact quadrature family is no longer the focus;
- SBP matrix discussion: `LGL collocation matrices`;
- multiple dimensions: first `tensor-product LGL nodes/grid`, then `tensor-product nodes/grid` locally.

Do not globally replace LGL by `collocation nodes` or generic `Gauss--Lobatto nodes`; those expressions describe only the role or omit the Legendre specification.
