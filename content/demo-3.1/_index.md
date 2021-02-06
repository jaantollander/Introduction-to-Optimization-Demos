+++
title = "Demo 3.1"
outputs = ["Reveal"]

[reveal_hugo]
transition = "fade"
theme = "black" # white
+++

# Tabular Simplex Algorithm

$$
\newcommand{\red}{\color{red}}
\newcommand{\dred}{\color{darkred}}
\newcommand{\cyan}{\color{cyan}}
\newcommand{\dcyan}{\color{darkcyan}}
\newcommand{\dorange}{\color{darkorange}}
$$

---

## Linear Optimization Problem
<div>
$$\begin{aligned}
\max\, & z = 5x_1 + 4x_2 \\
\mathrm{s.t.}\, & x_1 + x_2 ≤ 4 \\
& 6x_2 + 3x_2 ≤ 18 \\
& x_1≥0, x_2≥0
\end{aligned}$$
</div>

{{% fragment %}}
1) Modify into standard form
{{% /fragment %}}

{{% fragment %}}
2) Solve using Simplex tableau
{{% /fragment %}}

{{% note %}}
We do not explain the theory behind Simplex tableau in this demo.
{{% /note %}}

---

## Standard Form

<div>
$$\begin{aligned}
\max_{𝐱}\, & z = 𝐜⋅𝐱 \\
\mathrm{s.t.}\, & 𝐀⋅𝐱=𝐛 \\
& 𝐱≥0
\end{aligned}$$
</div>

where $𝐜∈ℝ^n,$ $𝐀∈ℝ^{m×n},$ $𝐱∈ℝ^n$ and $𝐛∈ℝ_{+}^{m}.$

---

## Standard Form
<div>
$$\begin{aligned}
\max\, & z = 5x_1 + 4x_2 \\
\mathrm{s.t.}\, & x_1 + x_2 ≤ 4 \\
& 6x_2 + 3x_2 ≤ 18 \\
& x_1≥0, x_2≥0
\end{aligned}$$
</div>

Change constraints to equalities and add the slack variables

---

## Standard Form

<div>
$$\begin{aligned}
\max\, & z = 5x_1 + 4x_2 \\
\mathrm{s.t.}\, & x_1 + x_2 + \textcolor{darkred}{s_1 =} 4 \\
& 6x_2 + 3x_2 + \textcolor{darkred}{s_2 =} 18 \\
& x_1≥0, x_2≥0, \textcolor{darkred}{s_1≥0, s_2≥0}
\end{aligned}$$
</div>

Change constraints to equalities and add the slack variables

---

## Simplex Tableau

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $\red -5$ | $\red -4$ | $\red 0$ | $\red 0$ | $ 0$
$s_1$ | $\cyan 1$ | $\cyan 1$ | $\cyan 1$ | $\cyan 0$ | $\dorange 4$
$s_2$ | $\cyan 6$ | $\cyan 3$ | $\cyan 0$ | $\cyan 1$ | $\dorange 18$

{{% fragment %}}
* Form Simplex tableau from the coefficients $\cyan 𝐀$, $\dorange 𝐛$, and negative $\red 𝐜$
{{% /fragment %}}

{{% fragment %}}
* Objective is given in form $z-5x_1 - 4x_2=0$
{{% /fragment %}}

---

## 1. Pivot Column

. | $\red x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $\dred -5$ | $-4$ | $0$ | $0$ | $0$
$s_1$ | $1$ | $1$ | $1$ | $0$ | $4$
$s_2$ | $6$ | $3$ | $0$ | $1$ | $18$

On $z$ row, pivot the variable with lowest negative coefficient to maximize the objective value

---

## 1. Pivot Row

. | $\textcolor{red}{x_1}$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $\textcolor{darkred}{-5}$ | $-4$ | $0$ | $0$ | $0$
$\textcolor{cyan}{s_1}$ | $\textcolor{red}{1}$ | $1$ | $1$ | $0$ | $\textcolor{darkcyan}{4}$
$\textcolor{cyan}{s_2}$ | $\textcolor{red}{6}$ | $3$ | $0$ | $1$ | $\textcolor{darkcyan}{18}$

Compute the quotients for the basic variables

---

## 1. Pivot Row

.|Quotient
-|-
$s_1$ | $\textcolor{darkcyan}{4}/\textcolor{red}{1}=4$
$\textcolor{darkred}{s_2}$ | $\textcolor{darkcyan}{18}/\textcolor{red}{6}=\textcolor{darkred}{3}$

Select the basic variable with smallest positive value as the pivot row to advances the solution as far as possible while retaining feasibility

---

## 1. Gaussian Elimination

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $-5$ | $-4$ | $0$ | $0$ | $0$
$s_1$ | $1$ | $1$ | $1$ | $0$ | $4$
$\textcolor{red}{x_1}$ | $6$ | $3$ | $0$ | $1$ | $18$

Change basic variable on pivot row to pivot variable

---

### Eliminate Pivot Row

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $-5$ | $-4$ | $0$ | $0$ | $0$
$s_1$ | $1$ | $1$ | $1$ | $0$ | $4$
$\textcolor{red}{x_1}$ | $\textcolor{darkred}{6}/6$ | $3/6$ | $0/6$ | $1/6$ | $18/6$

---

### Eliminate Pivot Row

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $-5$ | $-4$ | $0$ | $0$ | $0$
$s_1$ | $1$ | $1$ | $1$ | $0$ | $4$
$x_1$ | $1$ | $1/2$ | $0$ | $1/6$ | $3$

---

### Eliminate Other Rows

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $0$ | $-3/2$ | $0$ | $5/6$ | $15$
$s_1$ | $0$ | $-1/2$ | $1$ | $-1/6$ | $1$
$x_1$ | $1$ | $1/2$ | $0$ | $1/6$ | $3$

---

## 2. Pivot Column

. | $x_1$ | $\textcolor{red}{x_2}$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $0$ | $\textcolor{darkred}{-3/2}$ | $0$ | $5/6$ | $15$
$s_1$ | $0$ | $\textcolor{red}{1/2}$ | $1$ | $-1/6$ | $1$
$x_1$ | $1$ | $\textcolor{red}{1/2}$ | $0$ | $1/6$ | $3$

{{% note %}}
Repeat the process
{{% /note %}}

---

## 2. Pivot Row

. | $x_1$ | $\textcolor{red}{x_2}$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $0$ | $\textcolor{darkred}{-3/2}$ | $0$ | $5/6$ | $15$
$\textcolor{cyan}{s_1}$ | $0$ | $\textcolor{red}{1/2}$ | $1$ | $-1/6$ | $\textcolor{darkcyan}{1}$
$\textcolor{cyan}{x_1}$ | $1$ | $\textcolor{red}{1/2}$ | $0$ | $1/6$ | $\textcolor{darkcyan}{3}$

---

## 2. Pivot Row

.|Quotient
-|-
$\textcolor{darkred}{s_1}$ | $\textcolor{darkcyan}{1}/\textcolor{red}{(1/2)}=\textcolor{darkred}{2}$
$x_1$ | $\textcolor{darkcyan}{3}/\textcolor{red}{(1/2)}=6$

---

## 2. Gaussian Elimination

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$z$ | $0$ | $0$ | $3$ | $1/3$ | $18$
$\textcolor{darkred}{x_2}$ | $0$ | $1$ | $2$ | $-1/3$ | $2$
$x_1$ | $1$ | $0$ | $-1$ | $1/3$ | $2$

---

## Solution

. | $x_1$ | $x_2$ | $s_1$ | $s_2$ | Sol
:-|-:|-:|-:|-:|-:
$\textcolor{darkcyan}{z}$ | $0$ | $0$ | $3$ | $1/3$ | $\textcolor{darkcyan}{18}$
$\textcolor{darkgreen}{x_2}$ | $0$ | $1$ | $2$ | $-1/3$ | $\textcolor{darkgreen}{2}$
$\textcolor{darkgreen}{x_1}$ | $1$ | $0$ | $-1$ | $1/3$ | $\textcolor{darkgreen}{2}$

- All coefficients of $z$ row are positive
  - → solution is the maximum
- We can read the solution from solution column
