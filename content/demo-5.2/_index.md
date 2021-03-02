+++
title = "Demo 5.2"
outputs = ["Reveal"]

[reveal_hugo]
transition = "fade"
theme = "black" # white
+++

# Dual Simplex

<div>
$$
\newcommand{\red}[1]{\textcolor{red}{#1}}
\newcommand{\dred}[1]{\textcolor{darkred}{#1}}
\newcommand{\cyan}[1]{\textcolor{cyan}{#1}}
\newcommand{\dcyan}[1]{\textcolor{darkcyan}{#1}}
\newcommand{\dorange}[1]{\textcolor{darkorange}{#1}}
\newcommand{\green}[1]{\textcolor{green}{#1}}
\newcommand{\lgreen}[1]{\textcolor{limegreen}{#1}}
\newcommand{\dviolet}[1]{\textcolor{darkviolet}{#1}}
\newcommand{\dsalmon}[1]{\textcolor{darksalmon}{#1}}
\newcommand{\gray}[1]{\textcolor{gray}{#1}}
$$
</div>

---

## Problem

<div>
$$\begin{aligned}
\max\, & z = -2x_1 - x_3 \\
\mathrm{s.t.}\, & x_1 + x_2 - x_3 ≥ 5 \\
& x_1 - 2x_2 + 4x_3 ≥ 8 \\
& x_1, x_2, x_3≥0
\end{aligned}$$
</div>

Solve above linear problem using the Dual Simplex method.

---

## Stardard Form

<div>
$$\begin{aligned}
\max\, & z + 2x_1 + x_3 = 0 \\
\mathrm{s.t.}\, & -x_1 - x_2 + x_3 + s_1 = 5 \\
& -x_1+ 2x_2 - 4x_3 + s_2 = 8 \\
& x_1, x_2, x_3, s_1, s_2≥0
\end{aligned}$$
</div>

We convert the problem into standard form.

---

## Simplex Tableau

. | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $2$ | $0$ | $1$ | $0$ | $0$ | $0$
$s_1$ | $-1$ | $-1$ | $1$ | $1$ | $0$ | $-5$
$s_2$ | $-1$ | $2$ | $-4$ | $0$ | $1$ | $-8$

{{% fragment %}}
Initial solution of $x_1=x_2=x_3=0$ satisfies optimality conditions as all $z$-row coefficients are $≥0$, but is infeasible as constraints do not hold $0+0-0≱5$.
{{% /fragment %}}

---

## Find Pivot Row

. | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $2$ | $0$ | $1$ | $0$ | $0$ | $0$
$s_1$ | $-1$ | $-1$ | $1$ | $1$ | $0$ | $-5$
$\dred{s_2}$ | $-1$ | $2$ | $-4$ | $0$ | $1$ | $\red{-8}$

{{% fragment %}}
Pivot row is $\dred{s_2}$ since the most negative value for variable on Sol row is $\red{-8}.$
{{% /fragment %}}

---

## Find Pivot Column

. | $x_1$ | $x_2$ | $\dcyan{x_3}$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $2$ | $0$ | $1$ | $0$ | $0$ | $0$
$s_1$ | $-1$ | $-1$ | $1$ | $1$ | $0$ | $-5$
$\dred{s_2}$ | $-1$ | $2$ | $\cyan{-4}$ | $0$ | $1$ | $\red{-8}$

{{% fragment %}}
We compute non-zero ratios between value on $z$ and pivot row: $\|1/(-4)\|=1/4$ and $\|2/(-1)\|=2.$
{{% /fragment %}}

{{% fragment %}}
Pivot column is $\dcyan{x_3}$ because $1/4$ is closer to zero than $2.$
{{% /fragment %}}

---

## Gaussian Elimination

. | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $7/4$ | $1/2$ | $0$ | $0$ | $1/4$ | $-2$
$s_1$ | $-5/4$ | $-1/2$ | $0$ | $1$ | $1/4$ | $-7$
$\dcyan{x_3}$ | $1/4$ | $-1/2$ | $1$ | $0$ | $-1/4$ | $2$

{{% fragment %}}
We perform Gaussian elimination using pivot row and change leaving variable $\dred{s_2}$ to entering variable $\dcyan{x_3}.$
{{% /fragment %}}

{{% fragment %}}
We repeat the process until all $z$-row is non-negative and $b$-column is feasible.
{{% /fragment %}}

---

## Solution

. | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\dorange{z}$ | $1/2$ | $0$ | $0$ | $1$ | $1/2$ | $\dorange{-9}$
$\cyan{x_2}$ | $5/2$ | $1$ | $0$ | $1$ | $-2$ | $\cyan{14}$
$\dsalmon{x_3}$ | $3/2$ | $0$ | $1$ | $-1$ | $-1/2$ | $\dsalmon{9}$

{{% fragment %}}
The solution is $\dorange{z=-9},$ $\gray{x_1=0},$ $\cyan{x_2=14},$ and $\dsalmon{x_3=9}.$ Due to strong duality it is optimal.
{{% /fragment %}}
