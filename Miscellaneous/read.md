# Graph Rewiring: Mathematical Formulation

Given a connected graph $G=(V,E)$, we aim to rewire the graph while preserving the number of nodes and edges such that the node–frequency distributions associated with two types of shortest paths become as similar as possible.

## Rewiring Strategy: Formal Mathematical Formulation

Let $G=(V,E)$ be a simple, connected, undirected graph with $|V|=n$ nodes and $|E|=m$ edges. We fix the labeled vertex set:

$$V =\\{
1,\dots,n  
\\}
$$

<!--{ A' : A'^T = A', diag(A') = 0, ..., lambda2(...) > 0 }-->

## Graph Space

Define the set of all connected graphs with the same number of nodes and edges as:

$$
\mathcal{G}_{n,m}^{\mathrm{conn}} := \\{ G'=(V,E') : |E'|=m \; G' \text{ connected} \\}.
$$

Each graph $G'$ is represented by a symmetric adjacency matrix:

$$
A' = (a'_{ij})_{i,j=1}^n \in \\{0,1\\}^{n\times n},
$$

with constraints:

$$
a'_{ij}=a'_{ji},\quad a'_{ii}=0,\quad \sum_{1\le i<j\le n} a'_{ij}=m.
$$

If preserving degree sequence:

$$
\sum_{j=1}^n a'_{ij}=d_i.
$$

- ### Connectivity:
  The connectivity of the network via the Laplacian $L'=D'-A'$ satisfies:

$$
G' \text{ is connected} \Longleftrightarrow \lambda_2(D'-A')>0.
$$

 Hnece the feasible adjacency matrices are:

<!--$$
\mathcal{A} = { 
A' : A'^T = A', \mathrm{diag}(A') = 0, \sum_{i<j} a'_{ij} = m,  \lambda_2(D' - A') > 0 
} 
$$ -->
<p align="center">
  <img src="math_A_set.svg" style="max-width:900px; width:100%;" alt="Equation A" />
</p>


## Shortest-Path Node–Frequency Distributions

Regular shortest-path node counts:

$$
c_R(i;G)=\sum_{ P\in \mathcal{P}_R(G)} \mathbf{1}_{\\{i\in P\\}} .
$$

Communicability shortest-path node counts:

$$
c_C(i;G)=\sum_{P\in \mathcal{P}_C(G)} \mathbf{1}_{\\{i\in P\\}}.
$$

The normalization factors are given by:

$$
Z_R= \sum_{j=1}^n c_R(j),\qquad Z_C=\sum_{j=1}^n c_C(j).
$$

Distributions:

$$
	\tilde f_R(G)=\left(\frac{c_R(1)}{Z_R},\dots,\frac{c_R(n)}{Z_R} \right),
$$

$$
	\tilde f_C(G)=\left(\frac{c_C(1)}{Z_C},\dots,\frac{c_C(n)}{Z_C} \right).
$$

In fact, for a rewired graph $G'$ with adjacency matrix $A'$:

$$ 
\tilde f_R^{A'}= \tilde f_R^{G'},       \tilde f_C^{A'}= \tilde f_C^{G'}.
$$

## Distance Between Distributions

For $1\le p\le\infty$:

$$
\Phi_p(A')=\||	\tilde f_C^{A'}-	\tilde f_R^{A'}\|\|_p.
$$

## Optimization Problem

$$
\boxed{
\begin{aligned}
\text{minimize} &\quad \Phi_p(A') \\
\text{subject to} &\quad A' \in \mathcal{A}
\end{aligned}}
$$

which can be written equivalently as:

$$
\min_{G'\in \mathcal{G}_{n,m}^{\mathrm{conn}}}\||	\tilde f_C(G')-	\tilde f_R(G')\||_p.
$$
