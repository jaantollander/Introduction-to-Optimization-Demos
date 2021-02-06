+++
title = "Demo 4.1"
outputs = ["Reveal"]

[reveal_hugo]
transition = "fade"
theme = "black" # white
+++

# The Simplex $M$-method

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
& 3x_2 + 8x_2 ≥ 24 \\
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
& 3x_2 + 8x_2 \red{- s_2 =} 24 \\
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

## M-form

<div>
$$\begin{aligned}
\max_{x}\, & -4x_1 -6x_2 - \dorange{M}\cyan{R_1} - \dorange{M}\cyan{R_2} \\
\mathrm{s.t.}\, & x_1 + x_2 - s_1 + \cyan{R_1} = 5 \\
& 3x_2 + 8x_2 - s_2 + \cyan{R_2} = 24 \\
& x_1≥0, x_2≥0, s_1≥0, s_2≥0, \cyan{R_1≥0, R_2≥0}
\end{aligned}$$
</div>

{{% fragment %}}
Add variable $\cyan{R_i}$ to each constraint. They represent how much each constraint has to be violated.
{{% /fragment %}}

{{% fragment %}}
Add $\cyan{R_i}$ variables to the objective function with large coefficient $\dorange{M},$ forcing the variables to zero in the optimum.
{{% /fragment %}}

---

## Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $4$ | $6$ | $0$ | $0$ | $\dorange{20}$ | $\dorange{20}$ | $0$
$R_1$ | $1$ | $1$ | $-1$ | $0$ | $1$ | $0$ | $5$
$R_2$ | $3$ | $8$ | $0$ | $-1$ | $0$ | $1$ | $24$

{{% fragment %}}
Set $\dorange{M}$ large and positive. For example, $\dorange{M=20}.$
{{% /fragment %}}

{{% fragment %}}
We can choose $x_1=x_2=s_1=s_2=0$ as a feasible basic solution.
{{% /fragment %}}

---

## Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\cyan{z}$ | $4$ | $6$ | $0$ | $0$ | $\red{20}$ | $\red{20}$ | $0$
$R_1$ | $1$ | $1$ | $-1$ | $0$ | $1$ | $0$ | $5$
$R_2$ | $3$ | $8$ | $0$ | $-1$ | $0$ | $1$ | $24$

{{% fragment %}}
Use Gaussian elimination on $\cyan{z}$-row such that $\red{R_i}$ variables become zero.
{{% /fragment %}}

---

## Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\cyan{z}$ | $-76$ | $-174$ | $20$ | $20$ | $\red{0}$ | $\red{0}$ | $-580$
$R_1$ | $1$ | $1$ | $-1$ | $0$ | $1$ | $0$ | $5$
$R_2$ | $3$ | $8$ | $0$ | $-1$ | $0$ | $1$ | $24$

Use Gaussian elimination on $\cyan{z}$-row such that $\red{R_i}$ variables become zero.

---

## 1. Pivot Column

. | $x_1$ | $\dred{x_2}$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\dorange{z}$ | $-76$ | $\red{-174}$ | $20$ | $20$ | $0$ | $0$ | $-580$
$R_1$ | $1$ | $1$ | $-1$ | $0$ | $1$ | $0$ | $5$
$R_2$ | $3$ | $8$ | $0$ | $-1$ | $0$ | $1$ | $24$

{{% fragment %}}
On $\dorange{z}$-row, choose the column with the smallest coefficient as the pivot column.
{{% /fragment %}}

---

## 1. Pivot Row

. | Quotient
-:|-:
$R_1$ | $5/1=5$
$\dcyan{R_2}$ | $\cyan{24/8=3}$

{{% fragment %}}
Compute the feasibility condition, the quotient of the result and pivot columns.
{{% /fragment %}}

{{% fragment %}}
Choose the smallest positive value as the pivot row.
{{% /fragment %}}

---

## 1. Gaussian Elimination

. | $x_1$ | $\dred{x_2}$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\dorange{z}$ | $-76$ | $\red{-174}$ | $20$ | $20$ | $0$ | $0$ | $-580$
$R_1$ | $1$ | $1$ | $-1$ | $0$ | $1$ | $0$ | $5$
$\dcyan{R_2}$ | $3$ | $\cyan{8}$ | $0$ | $-1$ | $0$ | $1$ | $24$


{{% fragment %}}
Perform Gaussian elimination on the Simplex tableau usign the pivot row.
{{% /fragment %}}

---

## 2. Pivot Column

. | $\dred{x_1}$ | $x_2$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\dorange{z}$ | $\red{-10.75}$ | $0$ | $20$ | $-1.75$ | $0$ | $21.75$ | $-58$
$R_1$ | $0.625$ | $0$ | $-1$ | $0.125$ | $1$ | $-0.125$ | $2$
$x_2$ | $0.375$ | $1$ | $0$ | $-0.125$ | $0$ | $0.125$ | $3$

{{% fragment %}}
On $\dorange{z}$-row, choose the column with the smallest coefficient as the pivot column.
{{% /fragment %}}

---

## 2. Pivot Row

. | Quotient
-:|-:
$\dcyan{R_1}$ | $\cyan{2/(0.625)=3.2}$
$x_2$ | $3/(0.375)=8$

{{% fragment %}}
Compute the feasibility condition, the quotient of the result and pivot columns.
{{% /fragment %}}

{{% fragment %}}
Choose the smallest positive value as the pivot row.
{{% /fragment %}}

---

## 2. Gaussian Elimination

. | $\dred{x_1}$ | $x_2$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$\dorange{z}$ | $\red{-10.75}$ | $0$ | $20$ | $-1.75$ | $0$ | $21.75$ | $-58$
$\dcyan{R_1}$ | $\cyan{0.625}$ | $0$ | $-1$ | $0.125$ | $1$ | $-0.125$ | $2$
$x_2$ | $0.375$ | $1$ | $0$ | $-0.125$ | $0$ | $0.125$ | $3$

{{% fragment %}}
Perform Gaussian elimination on the Simplex tableau usign the pivot row.
{{% /fragment %}}

---

## Solution

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | $R_1$ | $R_2$ | Sol
:-|-:|-:|-:|-:|-:|-:|-:
$z$ | $0$ | $0$ | $2.8$ | $0.4$ | $17.2$ | $19.6$ | $\dorange{-23.6}$
$x_1$ | $1$ | $0$ | $-1.6$ | $0.2$ | $1.6$ | $-0.2$ | $\red{3.2}$
$x_2$ | $0$ | $1$ | $0.6$ | $-0.2$ | $-0.6$ | $0.2$ | $\cyan{1.8}$

{{% fragment %}}
Objective value is $\dorange{-(-23.6)=23.6}$
{{% /fragment %}}

{{% fragment %}}
Variable values are $\red{x_1=3.2}$ and $\cyan{x_2=1.8}$.
{{% /fragment %}}
