---
title: Mathematical Models in Ecology & Evolution 2019
subtitle: Exercise Chapter 05
author: Pratik Gupte
date: 14^th^ July, 2019
fontfamily: tgschola
geometry: margin=2.5cm
---

# Problem 5.4

**Problem statement:** Including a unidirectional mutation rate $mu$ from allele $A$ to $a$ during reproduction in the haploid model of selection, we want to find system equilibira and examine their stability.

We define the fitnesses of the two alleles $A$ and $a$ as $W_A = 1$ and $W_a = 1-s$. The recursion equation for allele frequency of $A$ is:

\begin{equation} p(t+1) = (1 - \mu)p' \end{equation}

where:

\begin{equation} p' = \frac{W_A p(t)}{W_A p(t) + W_a (1-p(t))} \end{equation}


## (a) Determining equilibria

One obvious equilibrium for the system is at $p = 0$, since there is no regeneration of allele $W_A$. The upper maximum of $p$ must be modulated by the mutation rate of $A$ to $a$, and thus cannot be 1 as in the simple model.


To find this equilibrium, we set $p(t+1) = p(t)$, and replacing each by $\hat{p}$:

\begin{equation} \hat{p} = (1-\mu) \frac{W_A \hat{p}}{W_A \hat{p} + W_a (1 - \hat{p})} \end{equation}

\begin{equation} W_A \hat{p} + W_a - W_a \hat{p} = W_A (1 - \mu) \end{equation}

\begin{equation} \hat{p} (W_A - W_a) = W_A (1- \mu) - W_a \end{equation}

and replacing the fitnesses as defined:

\begin{equation} \hat{p} = \frac{s- \mu}{s} = 1 - \frac{\mu}{s} \end{equation}

## (b) Biological validity

The non-obvious equilibrium $\hat{p} = 1 - \mu/s$ is only valid between 0 and 1, requiring $\mu/s \leq 1$, or the mutation rate to be lower than the selection coefficient.	

## (c) Mean fitness

The mean fitness of the population at the polymorphic equilibrium is $\overline{W} = W_A \hat{p} + W_A (1 - \hat{p})$, which on replacing $\hat{p}$ with $1 - \mu/s$ yields:

\begin{equation} \overline{W} = 1 - \frac{\mu}{s} + (1 - s) \frac{\mu}{s} \\ = 1 - \mu \end{equation}

## (d, e) Stability when either _A_ or _a_ is absent

To determine the local stability of each of the two equilibria, $\hat{p} = 0$, and $\hat{p} = 1 - \mu/s$ we differentiate the recursion equation $f(p)$, $p(t+1) = (1 - \mu)p'$, with respect to $p$.

\begin{equation} \frac{df}{dp} = \frac{d}{dp} \frac{(1-\mu) W_A p(t)}{W_A p(t) + W_a (1 - p(t))} \end{equation}

In _Mathematica_, the command ```D[p (1 - m)/(p + ((1 - s) (1 - p))), p]``` on simplification yields the derivative:

\begin{equation} \frac{df}{dp} = (m-1)(s-1)/(1 + (p-1)s)^{2} \end{equation}

At each of the two equilibria, we obtain the value of $(df/dp)|_{p = \hat{p}}$ by replacing $p$ with $\hat{p}$ and define these values as $\lambda_{eq1}$, when allele $A$ is nearly absent, and $\lambda_{eq2}$, when allele $a$ is nearly absent: $\lambda_{eq1} = (\mu - 1) / (s - 1)$, and $\lambda_{eq2} = (s - 1) / (\mu - 1)$.

These represent the stability conditions at these equilibria, and are dependent on the mutation rate $\mu$, and the selection coefficient $s$.

### (f) Stability conditions

The mutation rate $\mu$ and selection coefficient $s$ are constrained between 0 and 1. For the equilibrium $\hat{p} = 0$, the value of $\lambda_{eq1}$ is nearly always positive (or possibly 0 for unreasonable values of $\mu$), and takes values > 1 when $\mu << s$, which may be expected when allele $a$ is rare and $W_A > W_a$. This makes $\hat{p} = 0$ an unstable, non-oscillatory equilibrium, and allele $A$ will increase in proportion away from near this equilibrium. 
For the equilibrium $\hat{p} = 1 - \mu /s$, $\lambda$ is nearly always positive and less than 1 (except when $s \approx \mu$), making this a stable and non-oscillatory equilibrium.

---