---
layout: post
title: Mean field theory in phyics and machine learning 
categories: physics,machine learning
permalink: /articles/mean_field.html
excerpt: 'An example of mean field theory in physics and connection to Bayesian inference.'
author: Andrew Wong
---


* TOC
{:toc}

# Ising model and it's mean field approximation

An Ising model is a mathematical model that can explain the physical behavior of magnets. It was instrumental in understanding phase transition.


An Ising model with $N$ spins. The i-th spin is $S_i$. Each spin can only take one of the two states: $+1$ or $-1$. $B$ is magnetic field. $J$ is interaction strength between two neighboring spins. Total energy is:

$$
\begin{equation}
E = \sum_i B S_i + J \sum_{ij} S_i S_j
\label{ising}
\end{equation}
$$

The $j$ in second term sums over nearest neighbor.  The first term is the interaction between the external field $B$ and individual spins, which is easy to deal with. The second term is hard -- It is the interaction *between* the spins, a product of two unknowns. In other words, the second term denotes *coupling* between the spins.

To simplify the problem, we can imagine each spin $S_i$ feels an average spin $\bar{S}$ coming from each of its neighbors, much like the external field $B$. By doing that, the second term of Eq. ($\ref{ising}$) depends on a single spin instead of two. It is now just like the first term involving a single summation.

The total energy Eq.($\ref{ising}$) becomes 

$$
\begin{equation}
E_{MF} = \sum_i B S_i + J \sum_{i} S_i \bar{S} = (B+  z J \bar{S} ) \sum_{i} S_i
\label{E_mf}
\end{equation}
$$

We can define mean field 

$$
\begin{equation}
\Delta B = z J \bar{S}
\label{mean_field_B}
\end{equation}
$$ 

and $z$ is the number of nearest neighbor (e.g. 4 for a square lattice).

Note that although the mean field energy Eq.(\ref{E_mf}) is simpler than Eq.(\ref{ising}), it is still a function of all spins, i.e. $E_{MF}(s_1, s_2,..,s_N)$. Only that now the energy is a linear function of the spins.

# Deriving the mean field

## Gibbs-Bogoliubov-Feynman inequality

The mean field approximation is a way to simplify the partition function and make it possible for analytical treatment. In this section, we will show mean field approximation results in a lower bound to the partition function. (Partition function is defined as the sum of the  probabilities of all possible states.  It is an important expression in statistical mechanics. From it we can calculate many physical quantities such as average spin.)

Partition function of Ising model is

$$
\begin{equation}
Z = \sum_{s_1, s_2 ... s_N} \exp[-\beta E(s_1, s_2, ..., s_N)]
\end{equation}
$$

The sum is over all spin configurations, .i.e. $s_1 =\pm1, s_2=\pm1$ etc. 

This partition function is hard to evaluate. We can try to simplify it to make it computationally tractable. One way to do it is to find a way to replace the energy $E$ whith its mean value.

Let $E = E_{MF} + \Delta E$. $\Delta E$ is the energy difference from the mean field energy $E_{MF}$. The partition function can be rewritten as

$$
\begin{align}
Z &= \sum \exp[-\beta (E_{MF} + \Delta E)]  \\
&= \sum Z_{MF} \frac{\exp[-\beta (E_{MF} + \Delta E)]}{Z_{MF}}  \\
&=  Z_{MF} \langle \exp(-\beta \Delta E) \rangle_{MF} \label{mf_partition}
\end{align}
$$

$Z_{MF}=\sum \exp( - \beta E_{MF} )$ is the mean-field partition function, $\langle \rangle_{MF} $ denotes expectation value weighted over mean field probabilities. Now the expectation value is still hard to evaluate. We can *move* the expectation operator to the exponent of the exponential function by

$$
\begin{align}
\langle\exp(-\beta \Delta E )\rangle &=   \langle \exp(-\beta \langle \Delta E \rangle) \exp(-\beta (\Delta E - \langle \Delta E \rangle  ) \rangle  \\
&\ge \exp(-\beta \langle \Delta E \rangle)
\end{align}
$$

Where we used 

* $\exp(x) >= 1 + x$ (You can see this as Taylor's expansion or [Jensen's inequality](https://en.wikipedia.org/wiki/Jensen%27s_inequality))
* $ \exp(\langle \Delta E \rangle) $ is just a number and does not suject to the average.
* The second $\exp()$ became 1 after first order expansion $\exp(x) >= 1 + x$

The result is the **Gibbs-Bogoliubov-Feynman inequality**:

$$
\begin{equation}
Z \ge Z_{MF}\exp(-\beta \langle \Delta E \rangle_{MF})
\label{gbf}
\end{equation}
$$

We can use $Z_{MF}$ instead of $Z$. The trade-off is now we have the *lower bound* instead of the actual partition function, introducing a biased error. But this makes the function computable, so we would take it...

## Explicit expression of the lower bound

We can further calculate $\langle \Delta E \rangle$ for the Ising model.

$$
\begin{equation}
\Delta E = E - E_{MF}
\end{equation}
$$

Recall

$$
\begin{equation}
E = \sum_i B S_i + J \sum_{ij} S_i S_j
\end{equation}
$$

The mean field energy is

$$
\begin{equation}
E_{MF} = (B+ z J \bar{S}) \sum_{i} S_i
\end{equation}
$$

So

$$
\begin{equation}
\langle E_{MF} \rangle = N (B + \Delta B) \bar{S}
\end{equation}
$$

The factor 1/2 in interaction term accounts for double counting.


$$
\begin{equation}
\langle E \rangle = \sum_i B \bar{S_i} + J \sum_{ij} \bar{S_i} \bar{S_j} = N (B \bar{S} + \frac{J}{2} z \bar{S}^2)
\end{equation}
$$

Note that we can write $ \overline{S_i S_j} = \bar{S_i} \bar{S_j}$ becasue the mean field energy that's average over is a linear summation of the spins.

$$
\begin{equation}
\langle \Delta E \rangle = \langle E \rangle - \langle E_{MF} \rangle = N (\frac{J}{2} z \bar{S}^2-\Delta B \bar{S}  )
\end{equation}
$$

Note that the mean spin $\bar{S}$ is a function of the mean field $\Delta B$ because the field is created by the spin self-consistently.

Explicitly, The lower bound of partition function is:

$$
\begin{equation}
Z \ge Z_{MF}\exp(-\beta \langle \Delta E \rangle_{MF}) = Z_{MF}\exp(-\beta N ( \frac{J}{2} z \bar{S}^2-\Delta B \bar{S}  ) )
\end{equation}
$$

Note that $Z_{MF}$ and $\bar{S}$ depend on $\Delta B$.

## Variational mean field
What is the physical interpretation of the mean field Eq.(\ref{mean_field_B})? In this section, we show that it is the field that minimize the free energy. That sense sense because otherwise it won't be the mean observed value!

Holtmonz free energy is given by

$$
\begin{equation}
H = -k_B T \ln Z
\end{equation}
$$

We can find the mean field $\Delta B$ by minimziing the free energy $H$. Instead of working with $H$ directly, we minimize the upper bound (lower bound of partition function $Z$):

$$
\begin{equation}
H_{UB} = -k_B T \ln [ Z_{MF}\exp(-\beta N (\frac{J}{2} z \bar{S}^2  - \Delta B \bar{S} ) ) ]
\end{equation}
$$

$$
\begin{equation}
\quad\quad = -k_B T \ln Z_{MF} + N \frac{J}{2} z \bar{S}^2 -  N B \bar{S}
\end{equation}
$$

Minimizing the free energy upper bound w.r.t. the mean field $\Delta B$ (This is where the term **variation** comes from):

$$
\begin{equation}
 \partial H_{UB}/\partial \Delta B = 0
\end{equation}
$$

Using 

$$
\begin{equation}
 \partial Z_{MF}/\partial \Delta B = - N \beta \bar{S} Z_{MF}
\end{equation}
$$

It follows:

$$
\begin{equation}
 \partial H_{UB}/\partial \Delta B = 0
 \end{equation}
$$

$$
\begin{equation}
 \partial \bar{S}/\partial \Delta B (\Delta B - J z \bar{S}) = 0
 \end{equation}
$$

Therefore the mean field is 

$$
\begin{equation}
\Delta B = J z \bar{S}
\end{equation}
$$

the same result as using the mean field argument in the first section.  

# Connection to KL divergence

We wanted to approximate the true probability distribution

$$
\begin{equation}
p(\mathbf{s}) = \exp(-\beta E(\mathbf{s}) )/Z 
\label{p_dist}
\end{equation}
$$

with the mean field distribution

$$
\begin{equation}
q(\mathbf{s}) = \exp(-\beta E_{MF}(\mathbf{s}) )/Z_{MF}
\end{equation}
$$

where $\mathbf{s} = (s_1, s_2, ..., s_N)$ is a vector that defines configuration of all spins.

A way to measure how good $q(s)$ approximate $p(s)$ is through Kullback-Leibler divergence:

\begin{equation}
KL(q(s)|| p(s)) = \int ds[ q(s) \log \frac{q(s)}{p(s)} ]
\end{equation}

Putting in $p(s)$ and $q(s)$ gives

\begin{align}
KL(q(s)|| p(s)) &= \int ds \frac{\exp(-\beta E_{MF})}{Z_{MF}}  ( \beta (E-E_{MF}) + \log \frac{Z}{Z_{MF}})
\end{align}

$Z$ and $Z_MF$ does not depend on the integrating variables and can be taken out of the integral.

\begin{align}
KL(q(s)|| p(s)) &=  \beta \langle E-E_{MF} \rangle_{MF} + \log \frac{Z}{Z_{MF}}
\end{align}


Since KL divergence is always $\ge 0$, this gives

$$
\begin{align}
\log \frac{Z}{Z_{MF}} &\ge - \beta \langle E-E_{MF} \rangle_{MF} \\
Z &\ge Z_{MF}\exp(-\beta \langle \Delta E \rangle_{MF})
\end{align}
$$

which we recovers the Gibbs-Bogoliubov-Feynman inequality Eq.(\ref{gbf}). So one interpretation of mean field approximation is to find a distribution to closely approximate the true distribution Eq. (\ref{p_dist}). For this reason, [variational approaches](https://en.wikipedia.org/wiki/Variational_Bayesian_methods) to [Bayesian inference](https://en.wikipedia.org/wiki/Bayesian_inference) problems are sometimes called **mean-field theory**.


# Additional information
[Mean Field Theory Solution of the Ising Model](https://cpb-us-w2.wpmucdn.com/u.osu.edu/dist/3/67057/files/2018/09/Ising_model_MFT-25b1klj.pdf) is an excellent write up of mean field solution to Ising model. [Variational Inference: A Review for Statisticians](https://arxiv.org/pdf/1601.00670.pdf) is an excellent review of applications of variational methods.

