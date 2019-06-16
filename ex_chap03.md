---
title: Mathematical Models in Ecology & Evolution 2019
subtitle: Exercise Chapter 03
author: Pratik Gupte
date: 16^th^ June, 2019
fontfamily: tgschola
geometry: margin=2.5cm
---

# Problem 3.16

**Problem statement:** Defining the fitnesses of three diploid phenotypes as follows, $W_{AA} = 1 + s$, $W_{Aa} = 1 + hs$, and $W_{aa} = 1$, we want to show that the recursion equation for the frequency $p$ of allele $A$ at time $t+1$:

\begin{equation} p(t+1) = {p(t)}^2 \frac{W_{AA}}{\overline{W}} + \frac{1}{2} (2 p(t) q(t) \frac{W_{Aa}}{\overline{W}}) \end{equation}

can be used to obtain the following continuous-time differential equation:

\begin{equation} \frac{dp}{dt} = sp(1-p)(p + h(1 - 2p)) \end{equation}

and that this is equivalent to:

\begin{equation} \frac{dp}{dt} = p(1-p)(p(W_{AA} - W_{Aa}) + (1-p)(W_{Aa} - W_{aa})) \end{equation}

**Part 1:**

1. We begin by writing the difference equation form of (1):

\begin{equation} \Delta p  = p(t+1) - p(t) \end{equation}

which works out to:

\begin{equation} \Delta p = {p(t)}^2 \frac{W_{AA}}{\overline{W}} + \frac{1}{2} (2 p(t) q(t) \frac{W_{Aa}}{\overline{W}}) - p(t) \end{equation}

2. Replacing $p(t)$ and $q(t)$ with $p$ and $q$, and $W_{AA}$, $W_{Aa}$, and $W_{aa}$ by the values above, and by fraction subtraction:

\begin{equation} \Delta p = \frac{p^2(1+s) + pq(1+hs) - p(\overline{W})}{\overline{W}} \end{equation}.

3. Replacing $q$ with $1-p$, and expanding $\overline{W}$ in the numerator:

\begin{equation} \Delta p = \frac{p^2(1+s) + pq(1+hs) - p(p^2(1+s) + (1-p)^2 + 2p(1-p)(1+hs)}{\overline{W}} \end{equation}

4. Factorising by $p(1-p)$:

\begin{equation} \Delta p = \frac{p(1-p)[p(1+s) + ((1+hs)(1-2p)) - (1-p)]}{\overline{W}} \end{equation}

which reduces the numerator on expansion to:

\begin{equation} \Delta p = \frac{p(1-p)[s(p+h - 2ph)]}{\overline{W}} \end{equation}

and finally upon exapanding $\overline{W}$ in the denominator:

\begin{equation} \Delta p = \frac{sp(1-p)[p+h(1-2p)]}{1 + s(p^2 + 2ph - 2p^2h)} \end{equation}

5. Over small timesteps $\Delta t$, the rate of change of $p$ is:

\begin{equation} \frac{\Delta p}{\Delta t} = \lim \limits_{\Delta t \to 0} \frac{s \Delta t p(1-p)[p+h(1-2p)]}{1 + s \Delta t (p^2 + 2ph - 2p^2h)} \cdot \frac{1}{\Delta t} \end{equation}

and at the limit of $\Delta t = 0$, we obtain equation (2):

\begin{equation} \frac{dp}{dt} = sp(1-p)[p + h(1-2p)] \end{equation}

**Part 2:**

6. Working from equation (3), and substituting the values of the phenotype fitnesses:

\begin{equation} \frac{dp}{dt} = p(1-p)(p(1+s - 1-hs) + (1-p)(1+hs-1)) \end{equation}

\begin{equation} p(1-p)(ps - 2phs + hs) \end{equation}

yields the continuous-time equation (12):

\begin{equation} sp(1-p)(p + h(1-2p)) \end{equation}

---