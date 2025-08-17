# Mantel's Theorem — Constructive Graph Simulator

This repository implements a falsifiable, comparative construction of triangle-free graphs under Mantel’s Theorem.

---

## Theorem

Let \( G \) be a simple graph with \( n \) vertices and no triangles. Then:

\[
|E(G)| \le \left\lfloor \frac{n^2}{4} \right\rfloor
\]

Equality holds iff \( G \cong K_{\lfloor n/2 \rfloor, \lceil n/2 \rceil} \).

---

## System Overview

Two graph generation models are executed in parallel:

- **Structure-driven model**: Constructs a bipartite graph explicitly, using recursive shape constraints.  
  No triangle tests are required. \( Dₖ(P) = 1 \) for proposition “G is triangle-free.”

- **Classical greedy model**: Edges are added incrementally if they do not complete any triangle.  
  Each insertion checks adjacency lists for closure violations.

Both are executed with live visual rendering and step-by-step metric logging.

---

## Truth-Density Model

This simulation implements a recursive density metric from Doran (2025):

\[
Dₖ(P) = \lim_{i \to \infty} \frac{Fᵢ(P)}{Gᵢ}
\]

Where:
- \( Fᵢ(P) \): number of realizations of proposition \( P \) at recursion depth \( i \)  
- \( Gᵢ \): configuration space at depth \( i \)

For structured bipartite generation of triangle-free graphs, we have:
\[
Fᵢ(P) = Gᵢ \Rightarrow Dₖ(P) = 1
\]

---

## File Structure

- `index.html`: self-contained execution environment with both construction modes  
- Graphs rendered using SVG and D3.js  
- No external dependencies beyond D3 CDN

---
