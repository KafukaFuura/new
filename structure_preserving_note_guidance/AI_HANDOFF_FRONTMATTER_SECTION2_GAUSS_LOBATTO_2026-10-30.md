# Front matter correction and Section 2/Gauss--Lobatto revision — 2026-10-30

This note supersedes the immediately preceding front-matter/LGL plan where they conflict.

## Implemented front matter corrections

- The discussion line is now exactly: `This note is prepared for discussion and collaboration.`
- The abstract opening is now `In this note, we develop ...`; no new verb such as `analyze` was added, and the remainder of the original first sentence was preserved.
- PDF author metadata remains empty; the subject is `Discussion and collaboration`.

## Implemented Section 2 reordering

The mesh, DG space, Gauss--Lobatto nodes and quadrature, Lagrange basis, nodal variables, and interface traces now appear in the unnumbered opening block of Section 2. Subsection 2.1 `Outline and key ingredients of our method` now begins with the semidiscrete operator, the discrete hydrostatic equilibrium, and KI-1/KI-2/KI-3.

No formula labels or mathematical definitions were deleted in this move.

## Implemented terminology choice based on Wu/Shu papers

The body no longer uses the acronym `LGL`. In the Wu/Shu reference corpus, the more typical expressions are `Gauss--Lobatto points`, `Gauss--Lobatto quadrature nodes`, and `Gauss--Lobatto quadrature`. Accordingly:

- first setup: `Gauss--Lobatto nodes`;
- exactness/integration: `Gauss--Lobatto quadrature rule`;
- later local references: `nodes`, `adjacent nodes`, or `nodal set`;
- SBP section: `collocation matrices`, with the mass matrix identified through the Gauss--Lobatto weights;
- multiple dimensions: `tensor-product Gauss--Lobatto nodes/grids` at first mention, then `tensor-product grid` locally;
- the original bibliography title containing `Legendre--Gauss--Lobatto` is unchanged.

The full `Legendre--Gauss--Lobatto (LGL)` terminology is mathematically valid and common in DGSEM literature, but the adopted body wording follows the user's requested Wu/Shu style more closely and reduces acronym repetition.

## Verification

The revised source compiled in three consecutive passes to 35 pages. The final log contains no undefined references, duplicate labels, overfull boxes, or underfull boxes. The title page and the Section 2 opening page were rendered and visually inspected.
