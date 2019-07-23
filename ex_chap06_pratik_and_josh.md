---
title: Mathematical Models in Ecology & Evolution 2019
subtitle: Exercise Chapter 06
author: Pratik Gupte and Josh Lambert
date: 27^th^ July, 2019
mainfont: TeX Gyre Schola
monofont: Hack
mathfont: TeX Gyre Schola Math
geometry: margin=2.5cm
header-includes:
	- \usepackage{listings}
	- \usepackage{xcolor}
 
	- \definecolor{codegreen}{rgb}{0,0.6,0}
	- \definecolor{codegray}{rgb}{0.5,0.5,0.5}
	- \definecolor{codepurple}{rgb}{0.58,0,0.82}
	- \definecolor{backcolour}{rgb}{0.97,0.97,0.96}
 
	- \lstdefinestyle{mystyle}{
    	backgroundcolor=\color{backcolour},   
    	commentstyle=\color{codegreen},
    	keywordstyle=\color{magenta},
    	numberstyle=\tiny\color{codegray},
    	stringstyle=\color{codepurple},
    	basicstyle=\ttfamily\footnotesize,
    	breakatwhitespace=false,         
    	breaklines=true,                 
    	captionpos=b,                    
    	keepspaces=true,                 
    	numbers=left,                    
    	numbersep=5pt,                  
    	showspaces=false,                
    	showstringspaces=false,
    	showtabs=false,                  
    	tabsize=2}
 
	- \lstset{style=mystyle}
---

# Problem 6.8

**Problem statement:** Given a model of infectious disease spread in a fixed population comprising either susceptible _S_ or infected _I_ individuals, whose rates of change are represented as $dS/dt = -acSI + \sigma I$, and $dI/dt = acSI - \sigma I$, where _a_ is the probability of transmission, _c_ is the per-capita contact rate between infected and susceptible individuals, and $\sigma$ is the recovery rate, we want to (a) prove that the proportion of infected individuals $P = I/(S+I)$ satisfies the differential equation 

\begin{equation} dP/dt = \alpha P(1 - P) - \sigma P \end{equation}

when $\alpha = ac (S+I)$, (b) Determine the equilibria for _P_ and their validity, (c) Determine the local stability of the equilibria and its implications, (d) Sketch the shape of the differential equation to determine the global stability of the equilibria, and (e) Determine the the general solution of _P_.

## (a) Proving the differential equation of _P_

Starting from equation (3), and substituting the value of $P$:

\begin{equation} dP/dt = \frac{d\frac{I}{(S+I)}}{dt}  \end{equation}

Applying the quotient rule:

\begin{equation} dP/dt = \frac{dI}{dt} (I+S) - I \frac{d(I+S)}{dt} \end{equation}

and then expanding $I d(I+S)/dt$:

\begin{equation} dP/dt = \frac{dI}{dt} (I+S) - I \frac{dI}{dt} - I \frac{dS}{dt} \end{equation}

and further cancelling oppositely signed $I (dI/dt)$ leaves us the following equation.

\begin{equation} dP/dt = S \frac{dI}{dt} - I \frac{dS}{dt} \end{equation}

Substituting the values of $dI/dt$ and $dS/dt$ as given:

\begin{equation} dP/dt = \frac{S(acSI - \sigma I) - I(-acSI + \sigma I)}{(I+S)^2} \end{equation}

and expanding:

\begin{equation} dP/dt = \frac{S^{2}acI - \sigma SI + acSI^2 - \sigma I^2}{(I+S)^2} \end{equation}

leaves us:

\begin{equation} dP/dt = \frac{ac(S+I) \cdot SI}{(I+S)^2} - \frac{\sigma I(I+S)}{(I+S)^2} \end{equation}

which, given $\alpha = ac(S+I)$, and $1 - P = S/(I+S)$, and on converting all $I/(S+I)$ to $P$, satisfies the condition $dP/dt = \alpha P (1-P) - \sigma P$.

## (b) Equilibria of _P_

One obvious equilibrium of _P_ is 0, since the infection does not spontaneously arise. The upper equilibrium of _P_ can be found from the osbervation that at equilibrium the rate of change of infection status is 0, i.e., $dP/dt = 0$. Hence at equilibrium:

\begin{equation} \alpha P (1-P) = \sigma P \end{equation}

and the second equilibrium value of $P$, $\hat{P} = 1 - (\sigma/\alpha)$. Given that _P_ is a proportion, $\sigma/\alpha$ cannot be greeater than 1, or the rate of recovery cannot be greater than the infectivity. In a special case of the parameters, any starting _P_ is an equilibrium when infectivity and recovery rates are equal.

## (c) Local stability of equilibria

Beginning with (3), the differential equation of _P_, we differentiate $f(P)$ w.r.t. $P$ so:

\begin{equation} \frac{df(P)}{dP} = \frac{d}{dP} \alpha P(1-P) - \sigma P \end{equation}

In _Mathematica_ the command `D[\Alpha P (1 - P) - \Sigma P, P]` yields the derivative $\alpha(1 - P) - \alpha P - \sigma$, which is defined near the equilibria as:

\begin{equation} r \equiv df/dP|_{P = \hat{P}} = \alpha(1 - \hat{P}) - \alpha \hat{P} - \sigma \end{equation}

At each of the two equilibria, $\hat{P} = 0$ and $\hat{P} = 1 - (\sigma/\alpha)$, the corresponding $r$ is obtained by substituting values of $\hat{P}$: $r_{0} = \alpha - \sigma$, and $r_{1 - (\sigma/\alpha)} = \sigma - \alpha$.

At $\hat{P} = 0$, $r$ is always positive since $\sigma < \alpha$, making it an unstable equilibrium, while $r$ is always negative at $\hat{P} = 1 - (\sigma/\alpha)$, making it a stable equilibrium. There are no oscillations in this one-variable, continuous-time model where $f(n)$ is not a function of time.

## (d) Global stability of equilibria

Assuming values of $\alpha = 0.8$ and $\sigma = 0.1$, the global stability of (3) is shown in Figure 1 derived from _Mathematica_ using:

\begin{lstlisting}[language=Mathematica]
f = \[Alpha] P (1 - P) - \[Sigma] P;

Plot[f /. \[Alpha] -> 0.8 /. \[Sigma] -> 0.1, {P, 0, 1},
 PlotTheme -> "Classic",
 PlotStyle -> {Black},
 AxesLabel -> {"P", "dP/dt"},
 PlotLabel -> "dP/dt ~ P, \[Alpha] = 0.8, \[Sigma] = 0.1"]

\end{lstlisting}

![Differential equation dP/dt versus P, for values of $\alpha$ = 0.8, $\sigma$ = 0.1. The equilibrium at P = 0 is unstable, while the equilibrium at P = 0.875 is stable.](figChap6.8d.eps){ width=50% }

## (e) General solution for $dP/dt = \alpha P (1-P) - \sigma P$

The general solution can be found with a separation of variables, where $f(P) = \alpha P (1-P) - \sigma P$, and $g(t) = 1$. The itnegrals for evaluation are

\begin{equation} \int \frac{1}{f(P)} dP = \int \frac{1}{\alpha P (1-P) - \sigma} dP \end{equation}

and $\int g(t)dt = \int 1 dt = t + c$. The first integral (14) is solved by passing it to _Mathematica_ using 

\begin{lstlisting}[language=Mathematica]
iP = Integrate[1/(\[Alpha] P (1 - P) - \[Sigma] P), P];

FullSimplify[iP]

\end{lstlisting}

which yields

\begin{equation} \frac{ln(P) - ln[(P - 1)(\alpha + \sigma)]}{\alpha - \sigma} \end{equation}

This is equated to $t + c$, and the whole equation solved for $P(t)$ using _Mathematica_:

\begin{lstlisting}[language=Mathematica]
eq2 = iP == t + c;

FullSimplify[Solve[eq2, P]]

\end{lstlisting}

which gives the general solution

\begin{equation} P(t) = \frac{e^{(c+t)\alpha} (\alpha - \sigma)}{\alpha e^{(c+t) \alpha} - e^{(c+t) \sigma}} \end{equation}


---