---
title: 'Transfer Matrix Method'
slug: transfer
tags: 
    - maths
    - physics
date: 2023-05-30
---
# Introduction

This article serves to provide a picture of how to use the transfer
matrix method in statistical physics to rewrite the partition function
as the trace of a matrix. We write the transfer matrices as quantum
mechanical operators, allowing us to see the correspondence between
statistical physics in a certain dimension and quantum physics in one
fewer. The transfer direction plays the role of time in quantum
physics.

# Ising model

The Ising model was proposed as a model of ferromagnetism by Lenz to
Ising in the 1920s and considers nearest-neighbour ferromagnetic
interactions with coupling strength \\(J\\), we can also include a magnetic
field, \\(h\\). We consider the model in one dimension with a field, then in higher dimensions without a field. The
field helps to illustrate how one builds up the partition function in
one dimension by the repeated multiplication of two transfer matrices,
in higher dimensions we do not need the field. 
## One dimension

This section considers the Ising model with a field on a cyclic chain of
$N$ sites. The transfer matrix method relies upon being able to write
the partition function as the product of independent matrices only
acting on certain sites. The Hamiltonian for the Ising model in one dimension with a field is given by
$$\begin{aligned}
        H(\lbrace s\rbrace)=-J\sum_{j} s_j s_{j+1}-h\sum_j s_j
    \end{aligned}$$ where the first sum is over nearest neighbours and the second
sum is over all individual sites, \\( s_j \in\lbrace-1,+1\rbrace \\) are Ising spin variables on
site \\(j\\) and the Hamiltonian is a function of all spins, \\( \lbrace s\rbrace \\). The partition function is
given by the sum over all spin configurations 
$$
\begin{aligned}
        Z=\prod_{j}\sum_{s_j}\mathrm{e}^{-\beta H(\lbrace s \rbrace)}
    \end{aligned}
    $$ 
    where \\(\prod_{j}\sum_{s_j}\\) adds in the spin
configurations for each lattice site.


 We motivate a matrix description by writing 
$$
\begin{aligned}
        Z&=\prod_{j}\sum_{s_j}\left[\exp\left(\beta Js_1 s_2\right)\exp\left(\beta h s_2\right)\right]\left[\exp\left(\beta Js_2 s_3\right)\exp\left(\beta h s_3\right)\right]\cdots \nonumber\newline
        &\quad \left[\exp\left(\beta Js_{N-1} s_N\right)\exp\left(\beta h s_{N}\right)\right]\left[\exp\left(\beta Js_N s_1\right)\exp\left(\beta h s_1\right)\right]\newline
        &=\prod_{j}\sum_{s_j} T_{s_1,s_2}T_{s_2,s_3}\cdots T_{s_{N-1},s_N}T_{s_N,s_1}
    \end{aligned}
    $$ where we have used cyclic boundary conditions
\\(s_{N+1}=s_1\\), the boundary conditions do not have any effect in the
thermodynamic limit, which we take whenever we calculate quantities. We
have defined the transfer matrix \\(T_{s_j,s_{j+1}}\\) that only considers
neighbouring sites, it adds in the interaction between spins at site \\(j\\)
and \\(j+1\\) and includes the on-site field on site \\(j\\). We write the
matrix elements as $$\begin{aligned}
        T_{s_j,s\_{j+1}} = \exp\left(\beta J s_j s_{j+1}\right)\exp\left(\beta h s_j\right)
    \end{aligned}$$ which we can further decompose into the part acting
between spins and the on-site part, $$\begin{aligned}
        T_{s_j,s_{j+1}} &=[T_\parallel]\_{s_j,s_{j+1}}[T_\perp]\_{s_j,s_{j+1}} =\langle\ s_j \mid T \mid s_{j+1}\ \rangle \newline
        [T_\parallel]\_{s_j,s_{j+1}} &= \exp\left(\beta J s_j s_{j+1}\right)\newline
        [T_\perp]\_{s_j,s_{j+1}} &= \exp\left(\beta h s_j \right)\delta_{s_j,s_{j+1}}
    \end{aligned}$$ where the Kronecker delta keeps ensures that only
on-site terms are added. We can write this matrix out explicitly,
$$
T= \begin{pmatrix}
\mathrm{e}^{\beta (J+h)} && \mathrm{e}^{\beta J} \newline \mathrm{e}^{\beta J} && \mathrm{e}^{\beta (J-h)}
\end{pmatrix}.
$$
We recognise that the partition function is just matrix multiplication and since the transfer matrix is identical on each site, 
$$
Z=\sum_{s_1} T^N_{s_1,s_1}=\mathrm{Tr}\ T^N.
$$
In the thermodynamic limit the largest eigenvalue of the transfer matrix becomes the partition function. Therefore if we can diagonalise the matrix or just find its largest eigenvalue then we can determine all thermodynamic quantities.
## Two or more dimensions


