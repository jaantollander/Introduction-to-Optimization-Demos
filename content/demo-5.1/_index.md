+++
title = "Demo 5.1"
outputs = ["Reveal"]

[reveal_hugo]
transition = "fade"
theme = "black" # white
+++

# Formulation of Dual Problem
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

## Parameters

Food | EUR/Unit | Protein g/unit | Calcium mg/unit
:----|---------:|---------------:|--------------:
Potato | $\dred{0.6}$ | $\dviolet{3.7}$ | $\dviolet{22.7}$
Tomato | $\dred{2.7}$ | $\dsalmon{1.1}$ | $\dsalmon{6.2}$
Milk   | $\dred{2.3}$ | $\dcyan{8.1}$ | $\dcyan{296}$

{{% fragment %}}
Minimum requirements:

* $\dorange{50}$ g of protein and
* $\dorange{800}$ mg of calcium.
{{% /fragment %}}

---

## Jeff's problem
Make a meal that minimizes cost and satisfies the minimum requirements for protein and calcium.

---

### Decision variables

<div>
$$\begin{aligned}
x_1&:=\text{quantity of potatoes} \\
x_2&:=\text{quantity of tomatoes} \\
x_3&:=\text{quantity of milk}
\end{aligned}$$
</div>

---

### Objective
Minimize the total cost of the meal

<div>
$$\min.\, \dred{0.6}x_1 + \dred{2.7}x_2 + \dred{2.3}x_3$$
</div>

---

### Constraints
The meal needs to satisfy the daily requirements for protein and calcium.

<div>
$$\begin{aligned}
\dviolet{3.7}x_1+\dsalmon{1.1}x_2+\dcyan{8.1}x_3&≥\dorange{50} \\
\dviolet{22.7}x_1+\dsalmon{6.2}x_2+\dcyan{296}x_3&≥\dorange{800}
\end{aligned}$$
</div>

Also, the quantities cannot be negative.

$$x_1,x_2,x_3\green{≥0}$$

---

### Solution

Unit quantity for potatoes $\gray{x_1=9.12}$, tomatoes $\gray{x_2=0},$ and milk $\gray{x_3=2}.$

Minimum cost of $\lgreen{10.08}$ EUR.

---

## Pharmacist's Problem
Find highest prices for subtitution tablets for protein and calcium that are competitive with the food prices.

---

### Decision Variables

<div>
$$\begin{aligned}
y_1&:=\text{unit price of protein} \\
y_2&:=\text{unit price of calcium}
\end{aligned}$$
</div>

---

### Objective
Maximize the profit from the subtitution tablets.

<div>
$$\max.\, \dorange{50}y_1 + \dorange{800}y_2$$
</div>

---

### Constraints
Prices of subsitutions tablets cannot surpass the prices of foods.

<div>
$$\begin{aligned}
\dviolet{3.7}y_1+\dviolet{22.7}y_2&≤\dred{0.6} \\
\dsalmon{1.1}y_1+\dsalmon{6.2}y_2&≤\dred{2.7} \\
\dcyan{8.1}y_1+\dcyan{296}y_2&≤\dred{2.3}
\end{aligned}$$
</div>

The unit prices are non-negative.

$$y_1,y_2\green{≥0}$$

---

### Solution
Unit price for protein $\gray{y_1=0.138}$ and calcium $\gray{y_2=0.004}.$

Maximum profit of $\lgreen{10.08}$ EUR.

---

## Comparison

<div>
$$\begin{aligned}
\min.\, & \dred{0.6}x_1 + \dred{2.7}x_2 + \dred{2.3}x_3 \\
& \dviolet{3.7}x_1+\dsalmon{1.1}x_2+\dcyan{8.1}x_3≥\dorange{50} \\
& \dviolet{22.7}x_1+\dsalmon{6.2}x_2+\dcyan{296}x_3≥\dorange{800} \\
& x_1,x_2,x_3\green{≥0}
\end{aligned}$$
</div>

By comparing the problems, we see that Jeff's problem is the dual of Pharmacist's problem and vice versa.

---

## Comparison

<div>
$$\begin{aligned}
\max.\, & \dorange{50}y_1 + \dorange{800}y_2 \\
& \dviolet{3.7}y_1+\dviolet{22.7}y_2≤\dred{0.6} \\
& \dsalmon{1.1}y_1+\dsalmon{6.2}y_2≤\dred{2.7} \\
& \dcyan{8.1}y_1+\dcyan{296}y_2≤\dred{2.3} \\
& y_1,y_2\green{≥0}
\end{aligned}$$
</div>

By comparing the problems, we see that Jeff's problem is the dual of Pharmacist's problem and vice versa.
