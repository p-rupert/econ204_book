---
title: "Solow Model: Model and Measurement"
format: revealjs
---

## Capital and labor share

- From first order equation

$$
\begin{aligned}
f(k_t,n_t)
&= r_t k_t + w_t n_t \\
&= \alpha \frac{f(k_t,n_t)}{k_t}k_t
+ (1-\alpha)\frac{f(k_t,n_t)}{n_t}n_t
\end{aligned}
$$

- Hence

$$
\alpha
= \frac{r_t k_t}{f(k_t,n_t)}
= 1 - \frac{w_t n_t}{f(k_t,n_t)}.
$$

- With Cobb–Douglas production, capital’s and labor’s shares of output are constant and equal to $\alpha$.

---

## Summary

$$
\begin{aligned}
\text{Product approach:}\quad & y_t = k_t^\alpha n_t^{1-\alpha} \\
\text{Expenditure approach:}\quad & y_t = c_t + i_t + g_t + (x_t - m_t) \\
\text{Income approach:}\quad & y_t = r_t k_t + w_t n_t \\
\text{Law of motion:}\quad & k_{t+1} = (1-\delta)k_t + i_t
\end{aligned}
$$

---

## Match the model to the data

- Choose parameters so model behavior matches empirical moments
- Long-run ratios (e.g. factor shares) are relatively stable
- Parameters are calibrated to match means of these ratios

---

## Model and measurement

- Income decomposition:

$$
y_t = r_t k_t + w_t n_t
$$

- With Cobb–Douglas:

$$
\alpha
= \frac{r_t k_t}{y_t}
= 1 - \frac{w_t n_t}{y_t}
$$

- Set $\alpha$ to match the **average capital share of income**

---

## Model and measurement (continued)

- Along a detrended balanced growth path:

$$
\delta k = i
\qquad \Rightarrow \qquad
\delta = \frac{i}{k}
$$

- Use observable ratios:

$$
\delta = \frac{i}{y}\left(\frac{k}{y}\right)^{-1}
$$

---

## Simplifying assumptions

1. **Closed economy**

$$
x_t = m_t = 0
$$

2. **Fixed savings rate**

$$
i_t = s y_t
$$

---

## Reduced model

$$
\begin{aligned}
y_t &= f(k_t,n_t) \\
y_t &= c_t + i_t \\
y_t &= r_t k_t + w_t n_t \\
k_{t+1} &= (1-\delta)k_t + i_t \\
i_t &= s y_t
\end{aligned}
$$

---

## Per-capita formulation

$$
\begin{aligned}
y_t &= f(k_t) \\
y_t &= c_t + i_t \\
y_t &= r_t k_t + w_t \\
k_{t+1} &= (1-\delta)k_t + i_t \\
i_t &= s y_t
\end{aligned}
$$

(All variables are per capita.)

---

## The Solow model

- Mechanics of national accounts
- Strong behavioral assumption: constant savings rate
- For any $s \in [0,1]$, a unique steady state exists

$$
\delta k = s y
$$

$$
y = k^\alpha
$$

$$
k^* = \left(\frac{s}{\delta}\right)^{\frac{1}{1-\alpha}}
$$

---

## Steady-state values

$$
\begin{aligned}
y^* &= \left(\frac{s}{\delta}\right)^{\frac{\alpha}{1-\alpha}} \\
i^* &= s y^* \\
c^* &= (1-s)y^* \\
r^* &= \alpha \frac{\delta}{s}
\end{aligned}
$$

---

## Studying the model numerically

- Simple law of motion
- Low-dimensional dynamics
- Naturally suited for computational implementation

---

## Intertemporal choices

- Returns now vs. later:
  - consume or invest?
  - school or work?
  - rebuild or replace?
  - eat the cake now?

---

## Question 1

- $\alpha = 0.35$, $\delta = 0.06$, $s = 0.20$
- 50% capital destruction
- How much capital is rebuilt after 50 years?

---

## Question 2

- Write pseudo-code and program
- Track $y_t$, $i_t$, $c_t$
- Compute growth rates
- Plot levels and growth rates

---

## Question 3

- How long until output is within 0.5% of its pre-shock level?

---

## Pseudo-code (Question 1)

```text
α ← 0.35
δ ← 0.06
s ← 0.20
k* ← (s/δ)^(1/(1-α))

k1 ← 0.5 · k*
for t = 1,…,50:
    y_t ← k_t^α
    i_t ← s y_t
    k_{t+1} ← (1-δ)k_t + i_t

return k_51 / k*
