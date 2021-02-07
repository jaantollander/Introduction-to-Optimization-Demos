+++
title = "Demo 4.2"
outputs = ["Reveal"]

[reveal_hugo]
transition = "fade"
theme = "black" # white
+++

# The Simplex 2-Phase Method

$$
\newcommand{\red}[1]{\textcolor{red}{#1}}
\newcommand{\dred}[1]{\textcolor{darkred}{#1}}
\newcommand{\cyan}[1]{\textcolor{cyan}{#1}}
\newcommand{\dcyan}[1]{\textcolor{darkcyan}{#1}}
\newcommand{\dorange}[1]{\textcolor{darkorange}{#1}}
$$

---

## Linear Problem

<div>
$$\begin{aligned}
\min\, & 4x_1 + 6x_2 \\
\mathrm{s.t.}\, & x_1 + x_2 ≥ 5 \\
& 3x_1 + 8x_2 ≥ 24 \\
& x_1≥0, x_2≥0
\end{aligned}$$
</div>

{{% fragment %}}
The initial solution $x_1=x_2=0$ is not feasible!
{{% /fragment %}}

---

## Standard Form

<div>
$$\begin{aligned}
\dred{\max}\, & -4x_1 -6x_2 \\
\mathrm{s.t.}\, & x_1 + x_2 \red{- s_1 =} 5 \\
& 3x_1 + 8x_2 \red{- s_2 =} 24 \\
& x_1≥0, x_2≥0, \red{s_1≥0, s_2≥0}
\end{aligned}$$
</div>

{{% fragment %}}
Change minimization to maximization.
{{% /fragment %}}

{{% fragment %}}
Add surplus variables $\red{s_i}.$
{{% /fragment %}}

---

## Phase 1: Auxiliary Problem

<div>
$$\begin{aligned}
\max\, & -\cyan{z_1} -\cyan{z_2} \\
\mathrm{s.t.}\, & x_1 + x_2 - s_1 + \cyan{z_1} = 5 \\
& 3x_1 + 8x_2 - s_2 + \cyan{z_2} = 24 \\
& x_1≥0, x_2≥0, s_1≥0, s_2≥0, \cyan{z_1≥0, z_2≥0}
\end{aligned}$$
</div>

{{% fragment %}}
Variables $\cyan{z_i}$ measure infeasibility.
{{% /fragment %}}

{{% fragment %}}
We use it to form the Simplex tableau.
{{% /fragment %}}

---

## Phase 1: Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | $\dred{z_1}$ | $\dred{z_2}$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\cyan{z}$ | $0$ | $0$ | $0$ | $0$ | $\red{1}$ | $\red{1}$ | $0$
$z_1$ | $1$ | $1$ | $-1$ | $0$ | $1$ | $0$ | $5$
$z_2$ | $3$ | $8$ | $0$ | $-1$ | $0$ | $1$ | $24$

{{% fragment %}}
Use Gaussian elimination on $\cyan{z}$-row such that $\dred{z_i}$ variables become $\red{0}.$
{{% /fragment %}}

---

## Phase 1: Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | $\dred{z_1}$ | $\dred{z_2}$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\cyan{z}$ | $-4$ | $-9$ | $1$ | $1$ | $\red{0}$ | $\red{0}$ | $-29$
$z_1$ | $1$ | $1$ | $-1$ | $0$ | $1$ | $0$ | $5$
$z_2$ | $3$ | $8$ | $0$ | $-1$ | $0$ | $1$ | $24$

Use Gaussian elimination on $\cyan{z}$-row such that $\dred{z_i}$ variables become $\red{0}.$

---

## Phase 1: Solution

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | $\dred{z_1}$ | $\dred{z_2}$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $0$ | $0$ | $0$ | $0$ | $\red{1}$ | $\red{1}$ | $0$
$x_1$ | $1$ | $0$ | $-1.6$ | $0.2$ | $1.6$ | $-0.2$ | $3.2$
$x_2$ | $0$ | $1$ | $0.6$ | $-0.2$ | $-0.6$ | $0.2$ | $1.8$

{{% fragment %}}
We obtain the solution by using Simplex algorithm.
{{% /fragment %}}

{{% fragment %}}
All artificial variables $\dred{z_i}$ are non-basic $(\red{=0}).$ We can remove them so that optimal cost coefficient is equal to zero, hence feasible.
{{% /fragment %}}

---

## Phase 2: Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\dorange{z}$ | $4$ | $6$ | $0$ | $0$ | $0$
$x_1$ | $1$ | $0$ | $-1.6$ | $0.2$ | $3.2$
$x_2$ | $0$ | $1$ | $0.6$ | $-0.2$ | $1.8$

{{% fragment %}}
We remove all artifical variables and reintroduce the objective function.
{{% /fragment %}}

{{% fragment %}}
We can use Gaussian elimination on $\dorange{z}$-row to obtain the solution.
{{% /fragment %}}

---

## Phase 2: Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $0$ | $0$ | $2.8$ | $0.4$ | $\dorange{-23.6}$
$x_1$ | $1$ | $0$ | $-1.6$ | $0.2$ | $\red{3.2}$
$x_2$ | $0$ | $1$ | $0.6$ | $-0.2$ | $\cyan{1.8}$

{{% fragment %}}
The coefficients on the objective row are positive, so we have reached the optimum.
{{% /fragment %}}

{{% fragment %}}
Objective value is $\dorange{-(-23.6)=23.6}$
{{% /fragment %}}

{{% fragment %}}
Variable values are $\red{x_1=3.2}$ and $\cyan{x_2=1.8}$.
{{% /fragment %}}
